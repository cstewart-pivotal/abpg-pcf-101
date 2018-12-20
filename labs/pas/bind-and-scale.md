Estimated Time: 25 minutes

# What you will learn

* How to create a service instance
* How to bind service instances to your app
* How to scale an app
* See Cloud Foundry Self Healing in action

# Exercises

## Push the PCF Demo App

### Edit the app manifest

1) Download the [sample app](../resources/pcfdemo.zip).  Copy the file to folder: `~/pcf-101`

2) Extract the zip file to `~/pcf-101/pcfdemo`.  

This application contains a Java app that we will push. This app has a `manifest.yml` file where we set application metadata for Cloud Foundry to use.

3) Edit the manifest. From the root directory of the *PCFDemo* app, open up the `manifest.yml` file in your favorite text editor. There are 2 values you'll need to replace in the manifest. Append your name to both the app `name` as well as to the `host`. See below for an example. Save manifest.

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
### Push it. Push it real good.
4) From the root directory of the PCFDemo app, push the app

```
$ cf push
```
### View the app
This application is expecting to have access to a RabbitMQ message queue. Notice it will alert no RabbitMQ service is bound. The link "Stream Data" will not work either. Let's fix that!

## Bind a RabbitMQ Service Instance
1) From your terminal, view the PCF Marketplace. Note all of the services available to you as a developer!

```
$ cf marketplace
```
### Create Service instance

2) View the RabbitMQ service available to you by viewing the services available in your space.

```
$ cf services
```

### Bind Service instance

1) Bind the service instance to your application providing your APP-NAME (that you specified in the manifest) and the service instance name (`rabbitmq`)

```
$ cf bind-service APP-NAME rabbitmq
```
2) Re-push the application

```
$ cf push
```

3)View the application again. Click "Stream Data" and see the fun start. Click on a state to detail orders going throw it.

## Self Healing and Scaling
## Scale your app
1) Scale app to 3 instances

```
$ cf scale APP-NAME -i 3
```

If you visit the application in the browser, you will see Cloud Foundry round-robin-ing through your app instances by looking at the index value.

## Self Healing
1) Kill App

In the app UI, click "Kill App" and watch the application crashing. Notice that the application is still up, because we have multiple instances running.

2) View the logs from the terminal

```
$ cf logs APP-NAME
```
If you kill the app again, it will show as "crashed" when you visualize events from the terminal. Health manager will automatically restart the app for you. How neato is that??
