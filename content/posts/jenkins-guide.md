+++
date = '2022-09-09T00:00:00Z'
draft = false
title = 'What is Jenkins really?'
description = 'A comprehensive guide to understanding Jenkins - an open-source build automation tool for continuous integration and delivery'
tags = ['jenkins', 'devops', 'ci-cd', 'automation', 'build-tools']
categories = ['tutorials']
+++

# What is Jenkins really?

Jenkins is an open-source build automation tool that allows continuous integration and continuous delivery of projects, and it is written in Java.

## Why do we need Jenkins?

Before Jenkins, the process of building and testing used to happen manually, and while doing this the locating and fixing of bugs was quite long and difficult.

This leads to slowing down the process of software delivery.

The Developers had to wait for the test result and the complete deployment process was manual.

## What is Build Automation?

The traditional workflow looks like this:

**Developer** (develop the application on your machine) → **Git Repo** (check your code changes in the remote repository) → **should be tested and built**

So while you publish a new Release/Feature to your application:

1. Login to your docker repo
2. You have to set up the test environments to run tests
3. Execute those tests (meanwhile you can't code) and wait for the tests to execute which may take a longer time
4. Build a docker image and push it to the repo

So if one of the developers in the team had to do this every time you decide to release a new version then there should be always one person willing to do this. This can actually slow down the team and interfere with the normal workflow.

### For this you want:

- A dedicated server to execute all those things
- The test is to be run, and the application version is to be built and pushed to a repository automatically

### In the server:

- The test environment should be prepared to run the tests
- Docker credentials should be configured
- All the necessary tools must be installed to execute commands like Docker, npm, and Gradle

## Trigger Build Automatically

This process of Automatically Triggering the workflow:

**Test Code** → **Build Application** → **Push to repository** → **Deploy to Server**

is called **Build Automation**.

There are special tools that do this Build Automation and one of them is **JENKINS**

It has UI for configuration like:
- Installing all the tools you need (Docker, Gradle/Maven/npm, etc.)
- To configure the tasks (run tests, build an app, deployment, etc.)
- Configure the automatic trigger of the workflow

## What can you do with Jenkins?

- **Run Tests**
- **Build Artifacts**
- **Publish those Artifacts**
- **Deploy Artifacts** (to a deployment server, a dev/staging/Production environment)
- **Send notifications** (like to your team like whether the test got failed/Successful)
- **And many More...**

So, it is a powerful tool to help you manage this build automation process and you can build very advanced workflows in Jenkins.

Jenkins needs to integrate with many other tools for ex, Docker, Different Build tools, and Repositories(like Nexus), Deployment Servers.

Because of this, Jenkins has a lot of **Plugins** to make integrating with all these technologies easier.

## How does it work?

### Run tests → Build tools need to be available:

With build tools you execute the test commands:
- `npm test`
- `gradlew test` 
- `mvn test`

Configure test environment (e.g. test database)

### Build Application → Build Tools or Docker available

### Publish Docker Image → Store Credentials in Jenkins

Like to authenticate to a Docker Repository, so Jenkins users must have access to all these technologies and platforms.

And many more.

---

Jenkins is essentially your automation server that takes care of all the repetitive tasks in your software development lifecycle, allowing developers to focus on what they do best - writing code!

**Tags:** #jenkins #devops #ci-cd #automation #build-tools
