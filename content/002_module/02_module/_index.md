+++
title = "Part 2: Container Observability "
chapter = false
weight = 200
+++

In this module, you will learn how to navigate [Lumigo](https://lumigo.io) with the demo application.

### Viewing your application in Lumigo

Lumigo will trace the invocations and health of your ECS apps. The first thing we will use it for is to get an understanding of how our application looks in real life.

Click on [ECS Tab](https://platform.lumigo.io/ecs/clusters) to view an overview of your ECS Clusters currently monitored by Lumigo:

![](/images/mod23-001.png)

Here you should see the `UniECSCluster` we deployed during the setup and deployment steps. 

This page displays an overview of all clusters being monitored showing information over the status of each cluster, number of services and tasks currently being run for each monitored cluster. 

Its important to note that the cluster metrics are only available on an ECS clusters when `CloudWatch Container Insights` have been enabled. 

You'll also see resource graphs for CPU Utilization, Memory Utilization and Runnings Tasks as an overview for all the clusters being monitored. When additional clusters are present, these graphs are filterable by cluster by clicking the cluster name under each graph. 

![](/images/mod23-002.png)

Clicking through on a cluster name from the ECS page displays more granular information about the selected cluster's monitored services and tasks. This view shows the launch type, status, tasks along with the CPU and Memory averages over the selected timespan. 

Similar to the ECS overview page, the CPU Utilization, Memory Utilization and Running Task graphs are filterable by clicking the service names below each graph when multiple services are available. 

![](/images/mod23-003.png)

Clicking the `details` button on a service will display additional information about the selected service on the cluster. 

![](/images/mod23-004.png)

The tasks tab will display all monitored tasks running on the cluster, and additional details are displayed in a slide out window by clicking `details` on a selected monitored task.

![](/images/mod23-005.png)

Now lets delve into the app a little more by clicking on the `See Traces` button from the task detail view. This will navitate to the Explore tab and automatically filter the view using the selected task that we traced from.

![](/images/mod23-006.png)

Additional filters can be added to refine the traces displayed on the page such as Issues, Execution tags, http method, etc. Each filter item from the list can be added to either add or subtract the nominated value from the refined list of traces. 

For example 404 errors from the list of traces on this cluster task can be isolated for further investigation by clicking the tick against the issue filter. 

![](/images/mod23-007.png)

Additionally items from the trace list can also be excluded by clicking the cross against a filter item.

![](/images/mod23-008.png)

As each filter is added you will be able to see the filter query be built at the top of the screen. These can be removed as needed by either clicking the X next to the filter item which will then refresh the identified traces in the view. 

The other area to become familiar with is the Transactions tab which shows a list of all monitored transactions sorted by datetime, along with some basic high level information about each transaction and the traced services detected in each transaction. 

![](/images/mod23-009.png)

The transactions view can also be filtered by typing the transactions name in the Search by entry point box. This can be especially hand when searching for a particular grouping of transactions when there are a lot visible. 

![](/images/mod23-010.png)

Now click through on a transaction entry of interest and lets dig into some of the information in a trace some more. Here you can see a more granular view of the trace data collated from the cluster. 

![](/images/mod23-011.png)

Starting with the distributed mapping, you can see a line of events as they happened from the container application through any additional distributed services like SNS, SQS, DynamoDB etc. The distributed tracing line displays the order in which each service was triggered and will display a multiple of services if they were involved in the trace transaction. 

![](/images/mod23-012.png)

Clicking on a service will display additional information, along with any logs or metrics gathered from the trace for that distributed service. 

![](/images/mod23-013.png)

Its important to note that by default sensitive information will be masked from this view, additional secret maskings can be added (see the [Secret Masking](https://docs.lumigo.io/docs/secret-masking) documentation for more on masking).

The other section to highlight on this page are the Timeline view, which shows additional timing on elements detected in the trace. 

![](/images/mod23-014.png)

And the logs view, that show a collated list of all logs from the associated traces. 

![](/images/mod23-015.png)

Now that you are more familiar with Lumigo, let's use it to troubleshoot some issues.
