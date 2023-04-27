---
title: "Deploying the Wild Rydes Container Demo"
chapter: false
weight: 110
---

## Deploy the demo app using CLI

As a first step, we'll deploy the demo app to your AWS account and then see how we can debug different problems with Lumigo.

{{% notice info %}}
**RECOMMENDATION**: you shouldn't deploy this to your production AWS account. Use your personal account, or a playground account.
{{% /notice %}}

For this method your AWS CLI will need to be authenticated with the required permissions and accesses to deploy the demo application. 

Update `YOUR_LUMIGO_TRACER_TOKEN` in the line below with your [Lumigo Tracer Token](https://docs.lumigo.io/docs/lumigo-tokens), Then run the following:

```
aws cloudformation create-stack --stack-name WildRydesDemo --template-url https://lumigoworkshop.s3.amazonaws.com/WildrydesECS.yaml --parameters ParameterKey=LumigoToken,ParameterValue=YOUR_LUMIGO_TRACER_TOKEN --capabilities CAPABILITY_NAMED_IAM
```

That should then return a message like this: 

```
{
    "StackId": "arn:aws:cloudformation:us-east-1:[AWS User ID]:stack/WildRydesDemo/79e73fb0-e3fe-11ed-b120-0ae4419fb0aaaa9"   
}
```

You can check the status of the deployment by running the following to check the `StackStatus`
```
aws cloudformation describe-stacks --stack-name WildRydesDemo
```

Once finished we then need the public ip address from the ECS task, run this to get the public IP so we can check out app:  

```
aws ec2 describe-network-interfaces --network-interface-ids $(aws ecs describe-tasks --cluster UniECSCluster --tasks $(aws ecs list-tasks --cluster UniECSCluster --family UniTaskFamily --query "taskArns[]" --output text) --query "tasks[].attachments[].details[?name=='networkInterfaceId'].value[]" --output text) --query "NetworkInterfaces[].Association[].PublicIp[]" --output text
```

Enter the returned IP address into a browser and you should see the screen below

![](/images/mod01-002.png)

Congratulations, you have successfully deployed the ECS WildRydes app 🎉🎉

## Register and sign in

Now lets take that newly deployed ECS Demo app for a spin by clicking on the `Giddy Up!` button on the home page. 

* Then register a new account.

![](/images/mod22-001.png)

* And then sign in using the same username and password used during registration 

![](/images/mod22-002.png)

* Wait a moment for the map to load, then click anywhere on the map to put down a marker. This is where you'll hail for a ryde.

![](/images/mod22-003.png)

So, looks like there are a few problems in this app, let's find them!





