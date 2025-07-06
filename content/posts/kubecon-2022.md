+++
date = '2022-10-29T00:00:00Z'
draft = false
title = 'KubeCon + CloudNative North America 2022 Experience (Virtual)'
description = 'My virtual experience of attending KubeCon and my learnings'
tags = ['kubecon', 'cncf', 'kubernetes', 'cloud-native', 'open-source']
categories = ['conferences']
+++

# KubeCon + CloudNative North America 2022 Experience (Virtual)

Hi! I am going to share my virtual experience of attending KubeCon and my learnings.

I won't go into details about what is KubeCon as they have their official site you can go check it out on [CNCF](https://cncf.io).

## How did I get to know about CNCF community?

As I've been curious about open source and I've been exploring recently about DevOps and projects related to it, I get to know some great people part of this community and I've been active in their socials. I came to know about the **Dan Kohn Diversity Scholarship** for (KubeCon + CloudNativeCon North America 2022) to receive complimentary VIRTUAL conference registration! access through the CommunityClassroom of Kunal Kushwaha. I can't thank enough everyone who've been providing everything they can and do for people & spreading awareness of OSS and their experiences.

## Game on!

I'll go straight to the events I attended and my learnings from them + what I really liked.

## Azure Day with Kubernetes Hosted by Microsoft Azure

Okay so this was my first time getting to know AKS & Microsoft Azure. The starting of the session begin with an overview and logistics & some keynotes and got to know about cilium OSS & ebpf. I personally really enjoyed the session **From code-to-cloud, the end-to-end path** and got to know about GitHub Codespaces, Draft, Developer Tools for Azure Kubernetes Service (AKS) in VScode extension, Debug with Bridge to Kubernetes, GitHub action workflows and much more.

The whole point of this session was to explain to developers the real cycle of building an application doesn't include only code but also taking it to the cloud securely and making it available without any downtime.

There was another session on **Troubleshooting your apps on AKS** which was really informative and another on **Operators and Security** talks about:
- Operate AKS at scale
- Multi-cluster management  
- Secure your Kubernetes environment and more

I also got to know about **WASM** which I had no idea about at all, it was really interesting and I enjoyed the whole event and liked the energy of everyone including the management girl (super energetic!).

![Azure Day with Kubernetes](/images/kubecon-2022/azure-day.webp)

## Hands-on Hacking K8s Workshop by Snyk

This workshop was for demonstrating some common attack vectors and how to mitigate or otherwise minimize their blast radius.

My personal takeaway from this workshop was to be aware of vulnerabilities & misconfiguration as we build our application.

## Keynote Sessions

They're so amazing and you can get insights on a lot of things and all the updates in the projects. My personal favorites were:

### Beyond Automation: Kubernetes Success Requires a GitOps Mindset - Shatarupa Nandi, Senior Director of Engineering, VMware Tanzu

The talk was about an introduction to how you can manage your production software on k8s, securely, reliably, and with automation built-on top of cloud-native k8s API following GitOps principles.

### What We Learned Dissecting the World's Most Popular Containers - Ayse Kaya, Head of Strategic Insights + Analytics, Slim.Al

One thing I learned from this session was that there are a lot of vulnerabilities present out there in the k8s applications if not built with care.

### A Cloud Native Swiss Knife - Ricardo Rocha, Computing Engineer, CERN

Just WOW! This was super helpful, Ricardo presented what could be a cloud-native swiss knife. A set of tools and functionalities he wishes he knew existed from the start, which has significantly improved the daily life of developers and operators. He further said everyone should have their Swiss Knife to help them improve their day-to-day work.

### How to Become an Open Source Mechanic - Emily Fox, Security Engineer, Apple

![Emily Fox Session](/images/kubecon-2022/emily-fox.webp)

**BEST! BEST!** I really enjoyed the way Emily represented a really great example of vehicles, the cloud-native road trip full of potholes, unpredictability, congestion in traffic, and flat tires. The things you can prepare to face all that, the key takeaways:

- Find a Community
- Keep your community  
- Unburden
- Maintainers

## Maintainer Track

I've attended a few, which are:

### How To Build Production Grade DevOps Platform Using Argoproj - Alexander Matyushentsev, Akuity & Leonardo Luz Almeida, Intuit

- Got to know more about **Argoproj** (it covers many use cases from GitOps-based continuous deployment to event-based workflow automation, and can be used to create a powerful DevOps platform)
- Why to not use dependent git repo (pros and cons) and why prefer an independent git repo
- The manifest generation using **Kustomization**
- Using multi-tenancy to protect your environment in a group/team and a hands-on Demo showing how to assign RBAC to users

### Crossplane Intro And Deep Dive - The Cloud Native Control Plane Framework

![Crossplane](/images/kubecon-2022/crossplane.webp)

It is a CNCF Incubating project. They explained how **Crossplane** enables you to compose cloud infrastructure and services into your custom platform APIs, how best to get started building a platform of your own, and how you can adopt them into your control planes.

## Tutorial

### Unleash the Full Potential Of Kubernetes Scheduler: Configuration, Extension, And Operation In Production - Yuan Chen, Yibo Zhuang Wei Huang, Apple; Chen Wang, IBM Research

This was something new for me, I really liked how the speaker went from explaining everything about **Kube-scheduler** to hands-on showcases. Kube-scheduler is a key component of kubernetes. It has evolved with many new features over the years. In order to better use and manage kubernetes to meet the practical needs of today's increasingly diverse workloads in large production clusters with complex configurations, it's essential to understand how Kube-scheduler works, what features are available, and how to properly configure and manage them.

## LIVE OFFICE HOURS

### Intro to Control Plane - Dan Wilson Co-Founder & CTO

It was so interesting to know about **Control Plane**, which abstracts the complexity of going multi-cloud, and about **GeoKeeper**. Dan Wilson nicely explained how to use it with a quick demo and more, I really liked the energy and all the hard work people are putting in.

### Deploying Unreal Pixel Streaming on Kubernetes and creating your own metaverse by Oracle

Again it's something that got my interest as I'm always been fascinated by video games and have played a few epic games like Fortnite, Rocket League, Fall guys, etc. Epic game provides **Unreal Engine** application in the cloud. It is the most popular game development engine on the market. I learned about Unreal Pixel Streaming, Pixel Streaming k8s architecture, and more.

## CI/CD

### From Security Testing To Deployment In a Single PR - Sarah Khalife, GitHub & Grant Griffiths, Portworx

This was really a great talk. Simplifying and automating the process all in a single pull request makes it much easier for any cloud app developer to add security! They also showed up a step-by-step demonstration on how to set it up all within a PR to provide consistency and push the containerized application to a Kubernetes environment.

## Final Remarks

Due to time constraints, I wasn't able to attend most of the 101 tracks and other great sessions but no worries you can refer to the [CNCF YouTube channel](https://www.youtube.com/c/cloudnativefdn).

This KubeCon was super amazing and I got a lot of insights on so many different things and met some great maintainers to name a few **Rin Oliver**, **Justin Garrison**, **Carolyn Van Jai Campbell** and Founder/CTO of Control Plane Corporation **Dan Wilson**, SE **Grant Griffiths** his session was amazing I really enjoyed it, and **Ihor Dvoretskyi** made me so emotional his story is so inspirational (you're doing great).

I made a lot of connections, and I ❤️ it. Thanks to everyone who is putting in so much time and hard work every day, I really appreciate you all. Glad to know such a great community & looking forward to learning from everyone.

Thank you so much for reading even if you don't it's okay, you're really an amazing person ❤️.
