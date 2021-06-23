+++
title = "3.2 Troubleshoot timeouts (asynchronous functions)"
chapter = true
weight = 20
+++

## Troubleshoot timeouts (asynchronous functions)

Asynchronous Lambda functions (such as those handling background tasks via SNS topics, EventBridge buses or SQS queues) are often tricky to debug because their failures are silent. These failures can go unnoticed for months or even years! The problems they cause would often manifest in unpredictable ways that makes it difficult to trace the symptoms to the original errors.

So let's take a moment to see how we can troubleshoot timeouts for these asynchronous Lambda functions.

* Go to back the [Issues](https://platform.lumigo.io/issues) page and you'll see that the `calcSalaries` function has also timed out a few times. As before, click on the timed out issue for `calcSalaries` and see the timed out invocations.

![calcSalaries timeouts](/images/mod03-lumigo-calcSalaries-timeouts.png)

* Click on one of the timed out transactions to see what happened.

![calcSalaries timed out](/images/mod03-lumigo-calcSalaries-timeout-transaction.png)

* Unfortunately, there's nothing in the logs to indicate what happened. But let's click on `Timeline` tab to see what happened.

![requestUnicorn timed out](/images/mod03-lumigo-requestUnicorn-timeout-transaction-timeline.png)
