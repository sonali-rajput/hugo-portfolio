+++
date = '2023-04-26T00:00:00Z'
draft = false
title = 'Automating Docker and Terraform Deployment with Ansible'
description = 'A comprehensive guide to automating Docker application deployment using Terraform and Ansible on AWS'
tags = ['ansible', 'terraform', 'aws', 'docker', 'devops', 'automation']
categories = ['tutorials']
+++

# Automating Docker and Terraform Deployment with Ansible

This is a project that aims to automate the deployment of a Docker application using Terraform and Ansible.

## Table of Contents

- Overview
- Prerequisites
- Configure AWS CLI to connect to AWS account
- Part 1: Ansible and Docker
- Part 2: Ansible Integration in Terraform
- Part 3: Automating Docker and Terraform Deployment with Ansible

## Overview

The project is divided into three main parts:

1. **Part 1: Ansible & Docker**
2. **Part 2: Ansible Integration in Terraform**
3. **Part 3: Automating Docker and Terraform Deployment with Ansible**

## Prerequisites

- AWS account with IAM credentials
- AWS CLI
- Terraform
- Ansible
- Docker

## Configure AWS CLI to connect to AWS account

Connect with an AWS user:

- UI access through password
- CLI Access through Access key ID and Secret Access key

```bash
aws configure
```

- **AWS Access Key ID**: (which is given in the IAM users section)
- **AWS Secret Access Key**: (which is given in the IAM users section)
- **Default region name**: (set your preferred region, for ex: ap-south-1)
- **Default output format**: (set your preferred output format, for ex: json)

Configuration is automatically stored in your home directory under `/.aws`

## Part 1: Ansible and Docker

### Overview

1. Create an AWS EC2 Instance with Terraform
2. Configure Inventory file to connect to AWS EC2 Instance
3. Install Docker and docker-compose
4. Copy docker-compose file to the server
5. Start docker containers

### Create an AWS EC2 Instance with Terraform

Create your own `terraform.tfvars` file and include the following:

```hcl
vpc_cidr_block = "10.0.0.0/16"
subnet_1_cidr_block = "10.0.0.0/24"
avail_zone = "your preferred az" # example: "ap-south-1a"
env_prefix = "dev"
instance_type = "t2.micro"
ssh_key = "your public ssh key" # like "/home/sonali-rajput/.ssh/id_rsa.pub"
my_ip = "your IP"
ssh_private_key = "private ssh key" # like "/home/sonali-rajput/.ssh/id_rsa"
```

```bash
terraform init # for initializing
terraform apply
```

Your EC2 instance will be created and you'll get the server-ip in your console output.

### Configure Inventory file to connect to AWS EC2 Instance

Create a `hosts` file and save the server-ip address as:

```ini
[docker_server]
<your_server_ip> ansible_ssh_private_key_file=~/.ssh/id_rsa ansible_user=ec2-user
```

Now, we will write the Ansible Playbook for installing the necessary tools.

### Install Docker and docker-compose

Create a `deploy-docker.yml`:

```yaml
---
- name: Install Docker, Docker-compose
  hosts: docker_server
  become: yes
  tasks:
    - name: Install Docker
      yum:
        name: docker
        update_cache: true
        state: present
    - name: Install docker-compose
      get_url:
        url: https://github.com/docker/compose/releases/download/1.27.4/docker-compose-Linux-{{lookup('pipe', 'uname -m')}}
        dest: /usr/local/bin/docker-compose
        mode: +x
    - name: Start docker daemon
      systemd:
        name: docker
        state: started
    - name: Install docker python module
      pip:
        name: 
          - docker
          - docker-compose
```

### Add ec2-user to docker group

```yaml
- name: add ec2-user to docker group
  hosts: docker_server
  become: yes
  tasks:
    - name: add ec2-user to docker group
      user: 
        name: ec2-user
        groups: docker
        append: yes
    - name: reconnect to server session
      meta: reset_connection
```

### Copy docker-compose file to the server and Start docker containers

```yaml
- name: start docker containers
  hosts: docker_server
  tasks:
    - name: copy docker compose
      copy:
        src: /home/sonali-rajput/Projects/ansible/docker-compose.yml
        dest: /home/ec2-user/docker-compose.yml
    - name: start container
      docker_compose:
        project_src: /home/ec2-user
        state: present
```

Now run:

```bash
ansible-playbook deploy-docker.yml
```

Now ssh to the server by running `ssh ec2-user@<your-server-ip>` and do `docker ps`

You will see your containers running successfully.

We want the playbook to be more generic and re-usable so instead of using only ec2-user we can create a new user.

### Manual tasks between provisioning and configuring

- We get the IP address manually from TF output
- Update the hosts file manually
- Execute Ansible command

We want to automate this complete process.

## Part 2: Ansible Integration in Terraform

First, destroy the current setup by running `terraform destroy`

We're going to add a local-exec provisioner in our `main.tf` file. It basically invokes a local executable after a resource is created and it is invoked on the machine running TF, not on the resource!

Run `pwd` and copy the path and paste it in the `working_dir` attribute

We can use `--inventory` flag to use the Host IP of newly created server dynamically.

```hcl
provisioner "local-exec" {
  working_dir = "/home/sonali-rajput/Projects/ansible"
  command = "ansible-playbook --inventory ${self.public_ip}, --private-key ${var.ssh_private_key} --user ec2-user deploy-docker-newuser.yml"
}
```

However, using provisioners is not the recommended way in TF as it is not Idempotent.

Also, we might have an issue if this gets executed before even server started so for this ansible needs to check if the EC2 is ready.

## Part 3: Automating Docker and Terraform Deployment with Ansible

For that we'll add a play in ansible playbook to check if the server is accessible on its ssh port.

Add the following:

```yaml
- name: wait for ssh connection
  hosts: all
  tasks: 
    - name: ensure ssh port open
      wait_for:
        port: 22
        delay: 10
        timeout: 100
        host: '{{ (ansible_ssh_host|default(ansible_host))|default(inventory_hostname) }}'
        search_regex: OpenSSH
      vars:
        ansible_connection: local
```

### Another way to execute a provisioner

If you want to separate it from the aws instance resource and have it as a separate task in Terraform we can actually do that by using a resource type called "null_resource".

```hcl
resource "null_resource" "configure_server" {
  triggers = {
    trigger = aws_instance.myapp-server.public_ip
  }
  provisioner "local-exec" {
    working_dir = "/home/sonali-rajput/Projects/ansible"
    command = "ansible-playbook --inventory ${aws_instance.myapp-server.public_ip}, --private-key ${var.ssh_private_key} --user ec2-user deploy-docker-newuser.yml"
  }
}
```

As we have added a new provider, we have to do `terraform init` then do `terraform apply`

SSH into the server `ssh ec2@"server-ip"` and check the containers are running by `sudo docker ps`

If you want to check your application running, in your browser type `your-server-ip:port-number`

![Docker Terraform Automation](/images/docker-terraform-ansible/automation-diagram.webp)

---

Thank you so much for reading! If you found this helpful, please share your thoughts and feedback. This automation approach significantly reduces manual intervention and makes deployment more reliable and repeatable.

**Tags:** #ansible #terraform #aws #docker #devops #automation