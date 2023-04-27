+++
title = "Part 3: Troubleshooting"
chapter = false
weight = 300
+++

## Troubleshooting with Lumigo

In this module, we'll use Lumigo to troubleshoot simulated issues in the demo app and using the Lumigo Dashboard. This will demonstrate the type of errors that will be thrown in the application and how they will be found inside trace data using Lumigo. 

### Timeouts

Try to register with `timeout` as the username during registration, The app route will start a 60 second timer before returning a response. There is also a Lumigo execution tag as part of the route response which will help identify it within the Lumigo trace. 

![](/images/mod23-101.png)


### HTTP Errors

Register with `http` and use a http status code as the password, this will return that error instantly without querying the database. Note: If the password is not numerical it will default to a `500` response. 

![](/images/mod23-102.png)


### Logic Errors

Try to sign in with `badtable` as the username, this will change the table name being queried to `WildRydes` instead of `wildrydes` which will throw an error and c

![](/images/mod23-103.png)

Let us know what other simulated errors would you like to see appearing in the demo app! 