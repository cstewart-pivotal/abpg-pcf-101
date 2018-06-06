Estimated Time: 25 minutes

# What you will learn

* How to create a service instance
* How to bind service instances to your app
* How to scale an app
* See Cloud Foundry Self Healing in action

# Exercises

##Push the PCF Demo App

1) Download the [demo applications](../resources/pcfdemo.zip).  Copy the file to folder: `~/pivotal-cloud-foundry-developer-workshop`

2) Extract the zip file to `~/pivotal-cloud-foundry-developer-workshop/pcfdemo`.  

The zip file contains four directories; each directory contains an application developed in a different language.
##Create and bind a RabbitMQ Service Instance
1) Create Service instance
2) Bind Service instance
3) Re-push application
4) See it in action

##Self Healing and Scaling
##Scale your app
1) Scale App

##Self Healing
1) Kill App
2) cf logs - crashed status. App will restart for you!
3) But because we have multiple instances running, we're still up.



CF Demo
=========

Push the application initially with no service bound.
Notice it will alert no RabbitMQ service is bound.. the link "Stream Data" will not work either.

Now, bind a RabbitMQ service. Re-push the app.
Click "Stream Data" and see the fun start. Click on a state to detail orders going throw it.

Additional fun: click "Kill App" and watch the application crashing.. it will show as "crashed" when you visualize events (cf events <app_name>). Health manager will automatically restart the app for you. => makes a good demo, too.
