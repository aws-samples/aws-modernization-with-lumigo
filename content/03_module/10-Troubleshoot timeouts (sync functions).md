+++
title = "3.1 Troubleshoot timeouts (synchronous functions)"
chapter = true
weight = 10
+++

## Troubleshoot timeouts (synchronous functions)

Let's see how we can use Lumigo to troubleshoot timeouts for synchronous Lambda functions such as those handling API requests.

1. If you click on the `Timeout` issue for the `requestUnicorn` function, it will take you to the function details page for the function and show you the invocations that timed out.

![requestUnicorn timeouts](/images/mod03-lumigo-requestUnicorn-timeouts.png)

2. Click on one of the timed out transactions to see what happened in that transaction.

![requestUnicorn timed out](/images/mod03-lumigo-requestUnicorn-timeout-transaction.png)

3. From the function logs, you can see a message like `2020-10-20T11:40:37.402Z	3ea3b770-2986-4926-a0b3-2c6a045bfa20	INFO	Finding unicorn for  42.34963749150315 ,  -71.05718295574066`

and then 6 seconds later, the invocation timed out.

![requestUnicorn timed out](/images/mod03-lumigo-requestUnicorn-timeout-transaction-log.png)

4. Click on the `Timeline` tab and you will see that the request to `4fsay0n12a.execute-api.us-east-1.amazonaws.com` never completed, hence the `N/A`. So this was the cause for the invocation timing out.

![requestUnicorn timed out](/images/mod03-lumigo-requestUnicorn-timeout-transaction-timeline.png)
