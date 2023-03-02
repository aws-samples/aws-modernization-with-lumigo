+++
title = "Module 1: Serverless observability"
chapter = true
weight = 17
+++

## Overview

AWS Lambda is the glue that holds serverless architectures together. Before its release, most users felt it was a matter of luck as to whether AWS would let you connect a service to another. If not, you had to spin up a VM or a container to transform the events from one service in a way that your target service could handle them.

Since Lambda was easier to set up, people assumed that all code they would deploy on it would run faster and cheaper than on other compute services. But the truth is, there’s no free lunch. Lambda functions are easier to set up and manage than VMs or containers, but Lambda is still a professional service that requires understanding to get the most out of it.

In this module you will learn how to get observability at your Lambda-based application, find if any issues or optimizations can have place and get understanding at your transactions flow.

## What we will cover in this module

- Deploying a full-stack application using the [Serverless framework](https://www.serverless.com/open-source/).
- One-click distributed tracing with Lumigo
- Troubleshooting Lambda timeout errors
- Troubleshooting errors in business logic
- Troubleshooting performance issues
- Configuring alerts in Lumigo
