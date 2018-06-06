Estimated Time: 25 minutes

# What you will learn

* How to create a service instance
* How to bind service instances to your app
* How to scale an app
* See Cloud Foundry Self Healing in action

# Exercises

## Push the PCF Demo App

1) Download the [sample app](../resources/pcfdemo.zip).  Copy the file to folder: `~/pcf-101`

2) Extract the zip file to `~/pcf-101/pcfdemo`.  

This application contains a Java app that we will push. This app has a `manifest.yml` file where we set application metadata for Cloud Foundry to use.

3) Edit the manifest. From the root directory of the *PCFDemo* app, open up the `manifest.yml` file in your favorite text editor. There are 2 values you'll need to replace in the manifest. Append your name to both the app `name` as well as to the `host`. See below for an example.

```
---
applications:
- name: apbg-pcf-demo-[YOUR-NAME]
  memory: 1GB
  instances: 1
  host: pcfdemo-[YOUR-NAME]
  path: ./target/pcfdemo.war
  env:
   JAVA_OPTS: -Djava.security.egd=file:///dev/urandom
``` 

## Create and bind a RabbitMQ Service Instance
1) Create Service instance
2) Bind Service instance
3) Re-push application
4) See it in action

## Self Healing and Scaling
## Scale your app
1) Scale App

## Self Healing
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
