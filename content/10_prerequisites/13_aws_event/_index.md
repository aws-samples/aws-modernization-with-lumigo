---
title: "At an AWS Event..."
chapter: false
weight: 13
---


To complete this workshop, you are provided with an AWS account via the AWS Event Engine service. A team hash will be provided to you by event staff.

{{% notice warning %}}
If you are currently logged in to an AWS Account, you can logout using this [link](https://console.aws.amazon.com/console/logout!doLogout)
{{% /notice %}}


### Access AWS Account

1. Connect to the portal by clicking the button or browsing to [https://dashboard.eventengine.run/](https://dashboard.eventengine.run/). The following screen shows up. Enter the provided hash in the text box. The button on the bottom right corner changes to **Accept Terms & Login**. Click on that button to continue.
![Event Engine](/images/10_prerequisites/event-engine-initial-screen.png)

1. You will be asked to Sign in. Simply choose "Email One-Time Password (OTP)" option, enter your email, and click "Send Passcode". Check you email for OTP 6-digit code and enter it on the screen.
   ![Event Engine Sign In](/images/10_prerequisites/eventengine-signin.png)
   ![Event Engine OTP](/images/10_prerequisites/eventengine-otp.png)
{{% notice tip %}}
Leave the Event Engine tab open (A new tab will be used for the next step)
{{% /notice %}}

1. Choose **AWS Console**, then **Open AWS Console**
![Event Engine Dashboard](/images/10_prerequisites/event-engine-dashboard.png)

1. Use a single region for the duration of this workshop. This workshop supports the following regions:

* us-east-1 (US East - N.Virginia)

Make sure **US East (N.Virginia)** region is selected in the top right corner.

![Event Engine Region](/images/10_prerequisites/event-engine-region.png)

{{% notice warning %}}
This account will expire at the end of the workshop and the all the resources created will be automatically deprovision-ed. You will not be able to access this account after today.
{{% /notice %}}

### Next step

Once you have completed the step above, you can leave the AWS console open. You can now move to the [**Launch Cloud9 IDE Workspace**](/10_prerequisites/16_start_cloud9workspace.html) section.
