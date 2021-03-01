+++
title = "4.2 Identifying slow cold starts"
chapter = true
weight = 20
+++

## Identifying slow cold starts

Ah, yes, the dreaded Lambda cold starts! So often the cause of many performance concerns, especially for user-facing API functions.

If you go to the [Functions page](https://platform.lumigo.io/functions) and navigate to any of your function, you can see information about that function's cold starts in the `Metrics` tab.

![cold start metrics](/images/mod04-lumigo-cold-start-metrics.png)

When you have lots of functions, it's not feasible to go through each functions individually. In the [Dashboard](https://platform.lumigo.io/dashboard) you can use the `Functions with most Cold Starts` widget to quickly identify problematic functions.

![functions with most coldstarts](/images/mod04-lumigo-dashboard-cold-starts.png)

User-facing functions, such as those behind API Gateway, are often latency sensitive. In some cases, you may wish to use [Provisioned Concurrency](/https://lumigo.io/blog/provisioned-concurrency-the-end-of-cold-starts/) to eliminate cold starts altogether. For instance, when you have really strict latency requirements, or if you're using JVM/.Net Core runtimes and cannot optimize your code any further to keep cold start duration under an acceptable latency range.

In some really unfortunate cases, cold starts can also stack up when one API function calls another (via API Gateway) and can cause further delays. You can easily spot these cases in the [Transactions page](https://platform.lumigo.io/transactions), by looking at the `Cold Starts` column.

![stacked cold starts](/images/mod04-lumigo-transaction-cold-starts.png)

If this happens frequently, then it might also be a good reason to use Provisioned Concurrency. Maybe one cold start of a few hundred milliseconds is acceptable, but when a few of them stack up on a single transaction, that can result in noticeable delays to users.

Finally, you can alos use the [lumigo-cli](https://www.npmjs.com/package/lumigo-cli), our open source CLI tool, and run the [analyze-lambda-cold-starts command](https://www.npmjs.com/package/lumigo-cli#lumigo-cli-analyze-lambda-cold-starts) to analyze the cold start performance for all your functions in an AWS account.

![analyze-lambda-cold-starts](/images/mod04-lumigo-cli-analyze-cold-starts.png)
