+++
title = "Part 4: Alerting"
chapter = false
weight = 400
+++

In this module, we'll set up alerts in Lumigo for our ECS app. Head to the [Alerts](https://platform.lumigo.io/config/issues) page, you can see that Lumigo has a couple of alerts configured by default. 

![](/images/mod05-0001.png)

Alerts are triggered when certain criteria are met on specified traced resources. When alert criteria is met they can be used to send out notifivations via email or sent directly to platforms like Slack, PagerDuty, Microsoft Teams, VictorOps or OpsGenie.

### Creating a new alert  

Click on the Create New Alert button on the Alerts page. 

![](/images/mod05-0002.png)

The first section gives you the option for 3 different alert types for the notification: 

- **Event Alert:** When a event occurs that matches the alert condition. For example, when an ECS service throws an exception or a Lambda function times out.

- **Metric Alert:** When a metric exceeds a specific threshold for a specified period of time. Metrics are an aggregation of event occurrences over time. For example, the error rate of a Lambda function increases by 10% over the last 10 minutes.

- **CloudWatch Metric Alert:** When a CloudWatch metric exceeds a specific threshold for a specified period of time. For example, the number of messages added to an SQS queue is greater than 10 in the last 10 minutes.

For our new alert we want to use the Event Alert type, then set a description for the alert and select ECS from the Resource Type dropdown. 

![](/images/mod05-0003.png)

In the condition section we can define specific events that we might be interested in for our Alert. A multiple of options can be selected here depending on what the Alert is intended to monitor, there is also the option to alert on any error or any application error. 

![](/images/mod05-0004.png)

The final step for the condition section is to then select the specific resources required to be watched to meet the condition criteria. This can be at the cluster, service level or they can be defined by referencing specific execution tags. 

![](/images/mod05-0005.png)

The last step in setting up the Alert is to define where and how the alert will be sent. 

![](/images/mod05-0006.png)

Email is always available by default and additional platform integrations, like slack, can be defined from the [settings integration page](https://platform.lumigo.io/settings/integrations)

![](/images/mod05-0007.png)


Finally, click `Add Alert` to finish the process.

![](/images/mod05-0008.png)
