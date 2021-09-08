---
title: "Launch Cloud9 IDE Workspace"
chapter: true
weight: 16
---

[AWS Cloud9](https://aws.amazon.com/cloud9/) is a cloud-based integrated development environment (IDE) that let you write, run, and debug your code with just a browser. It includes a code editor, debugger, and terminal. Cloud9 comes prepackaged with essential tools for popular programming languages, including JavaScript, Python, PHP, and more, so you don’t need to install files or configure your development machine to start new projects.

We will use Amazon Cloud9 to access our AWS account via the AWS CLI in this workshop. There are a few steps to complete to set this up

1. If you are attending AWS Event:
    - Navigate to the [cloud9 console](https://console.aws.amazon.com/cloud9/home) or just search for it under the **AWS console services** menu
    - Run pre-deployed **lumigo-workshop** Cloud9 environment 
  
2. In your own AWS Account:
    - [Create a new Cloud9 IDE environment](/15_workspace_setup/150_cloud9.html)
    - [Create an IAM role for your workspace](/15_workspace_setup/151_iamrole.html)

Now we will attach the proper role to our Cloud9 EC2 instance and configure a bit more our Cloud9 environment:
{{% notice info %}}
Cloud9 normally manages IAM credentials dynamically. This isn't currently compatible with
the EKS IAM authentication, so we will disable it and rely on the IAM role instead.
{{% /notice %}}

- [Attach the IAM role to your workspace](/15_workspace_setup/152_workspaceiam.html)
- [Configure workshop specific requirements](/15_workspace_setup/153_cloud.html)
