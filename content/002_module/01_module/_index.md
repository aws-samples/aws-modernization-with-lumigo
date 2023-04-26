+++
title = "Part 1: Deploying demo app"
chapter = false
weight = 100
+++

## Deploying the Wild Rydes demo app

In this step of the workshop you will create and deploy the *Wild Rydes* demo app. The demo app lets you order rides from... unicorns!

![](/images/mod02-001.png)

The full architecture for the ecs demo app looks like this:

![architecture diagram](/images/mod02-002.png)

This CloudFormation template sets up a basic infrastructure to deploy an ECS task that runs a web server to demonstrate various problems that can arise in a production environment.

The template provisions the following resources:

- A DynamoDB table for storing data related to unicorn rides.
- An IAM user, policy, and access key with permissions to read and write to the DynamoDB table.
- A VPC with a public subnet and an internet gateway to allow access to the ECS task.
- An ECS cluster with container insights enabled.
- A CloudWatch Logs group to store logs from the ECS task.
- A security group to enable access to the ECS task over port 80.
- An IAM role and task definition for the ECS task, which runs a web server using a public Docker image.
- An ECS service that deploys the task in the cluster and configures its networking.

The ECS task will run a web server that serves traffic on port 80, and the `LUMIGO_TRACER_TOKEN` and other environment variables are passed as parameters to the task definition.

This CloudFormation template is intended to be used as a demo app to showcase problems that can arise in a production environment and how to debug them.