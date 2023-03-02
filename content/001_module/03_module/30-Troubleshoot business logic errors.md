+++
title = "3.3 Troubleshoot business logic errors"
chapter = false
weight = 330
+++

## Troubleshoot business logic errors

Lumigo is not just great at monitoring your production application and alerting you to problems. Turns out our customers also love using it for debugging business logic errors during development because they can easily peek into the internal state of their application - every invocation event, event environment variable that was used, and the request and response for every HTTP/TCP requests their functions make to other services!

Let's see how we can use this information to help us debug a problem in our business logic.

* Go to back the [Issues](https://platform.lumigo.io/issues) page and you'll see that the `uploadReceipt` function has thrown a few `TypeError`.

![uploadReceipt errors](/images/mod03-lumigo-uploadReceipt.png)

As before, click on the row to see the invocations.

* Click on one of the transactions to see what happened.

![uploadReceipt TypeError](/images/mod03-lumigo-uploadReceipt-errors.png)

* In this transactions view, you can see that whole transaction starting from the original request to find a unicorn. You can see the `uploadReceipt` function being highlighted as where the problem is. Since SNS is an async event source for Lambda, these failed invocations are retried automatically. From the overlapped Lambda icon (and the fact that it says `3 retries`), you can tell that this invocation was indeed retried, but still failed.

![uploadReceipt TypeError](/images/mod03-lumigo-uploadReceipt-transaction.png)

* Click on the `uploadReceipt` function's icon to see more details about these invocations.

![uploadReceipt TypeError](/images/mod03-lumigo-uploadReceipt-transaction-invocation.png)

Well, we see the error `Cannot read property 'Name' of undefined` and probably have some suspicion as to what it might be - maybe the SNS message is missing properties.

To find evidence to support our hypothesis, let's look for a successful invocation and compare that with this.

* Click **Show Similar Transactions** on the top right.

{{% notice note %}}
If you don't see full graph and **Show Similar Transactions** button you need to click **See Full Transaction** button on the left top corner of the graph window.
{{% /notice %}}

![show similar transactions](/images/mod03-lumigo-show-similar-transactions.png)

As you can see, a lot of the transactions had a `TypeError`, we're looking for a successful transaction without any issues.

![similar transactions](/images/mod03-lumigo-show-similar-transactions-successful.png)

* Click on one of the successful transaction.

![successful transaction](/images/mod03-lumigo-uploadReceipt-successful.png)

* Click on the `uploadReceipt` function to bring up its details. One thing that jumps out is that the SNS message contains an object in `RideDetail` which has a `Name` property.

![uploadReceipt function](/images/mod03-lumigo-uploadReceipt-invocation-successful.png)

contrast that with the failed invocation, which complained about being to read `Name` of `undefined`:

![uploadReceipt TypeError](/images/mod03-lumigo-uploadReceipt-transaction-invocation.png)

So there's the problem. Looking at the code for `uploadReceipt` confirms this:

![uploadReceipt](/images/mod03-lumigo-uploadReceipt-error.png)
