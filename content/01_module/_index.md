+++
title = "Module 1"
chapter = true
weight = 11
+++

# Module 1: deploying the Wild Rydes demo app

In this step of the workshop you will create and deploy the *Wild Rydes* demo app. The demo app lets you order rides from... unicorns!

![](/images/mod01-000.png)

The architecture for the demo app looks like this:

![architecture diagram](/images/mod01-001.png)

There's a user-facing API Gateway, and a single `POST /ride` endpoint (backed by the `requestUnicorn` Lambda function) to order a ride.

This `requestUnicorn` function would:

1. Find available unicorns in the area, using an external API (`Unicorn Stable API`).

2. Validate that the unicorn it found from step 1. is not occupied already by checking in the `OccupiedUnicorns` DynamoDB table.

3. Publish details of the ride to the `UnicornDispatched` SNS topic.

These kick off a series of background processing tasks through both SNS and DynamoDB Streams.

We will use this demo app to demonstrate various problems you can run into in a production environment and how you can go about debugging them.