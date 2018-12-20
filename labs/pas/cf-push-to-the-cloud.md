Estimated Time: 25 minutes

# What you will learn

* How to target a Pivotal Cloud Foundry instance with the `cf` CLI
* How to `cf push` apps
* How to access Apps Manager

# Exercises
These exercises require a PCF Pivotal Application Service environment. You have a few options here:
* The APBG PCF instance. Please fill out [this brief form](TO DO!!!!!) to gain access to that environment. 
* Pivotal Web Services (PWS): Hosted PCF instance. New accounts get the equivalent of 60 days free credit. Follow the instructions [here](https://run.pivotal.io/) to sign up for an account.
* [PCF Dev](https://pivotal.io/pcf-dev): running PCF locally on your machine
## Access the PCF sandbox

## Login to Pivotal Cloud Foundry with the `cf` CLI

1) Access the PCF environment by logging in via the `cf` CLI

```
$ cf login -a api.sys.apbg.apcf.io --skip-ssl-validation
```

2) Your org will be automatically targeted for you. Target the `LPW-PCF-101` space by either typing it in or selecting it from the list (#5).

3) Review where you are targeted (what user you are logged in as, your org and space)
```
$ cf target
```


***What Just Happened?***

You have logged into Pivotal Cloud Foundry from the `cf` CLI and targeted a Pivotal Cloud Foundry instance.  You are ready to `push` apps.

## Pushing apps

Next we will push (deploy) several applications.

1) Download the [demo applications](../resources/demo-apps.zip).  Create a directory in your home directory called '~/pcf-101'. (`~` is shorthand for the home directory in Linux, Mac and Unix based operating systems).
```
$ cd ~
$ mkdir pcf-101
```
2) Copy the file to the new folder you created: `~/pcf-101`

2) Extract the zip file to `~/pcf-101/demo-apps`.  

The zip file contains four directories; each directory contains an application developed in a different language.

3) Open a terminal window and push the `node` application. **Note, you will need to append your name to the name of the application to make it unique to you.

```
$ cd ~/pcf-101/demo-apps/node
$ cf push node-[your name] --random-route -m 128M
```

4) View the `node` application in your browser or use `curl`.  The url can be obtained from the `cf push` output or by issuing the command `cf apps`.

Example:
```
$ curl node-northeasterly-zygoma.cfapps.io
Hello Node
```

***NOTE:*** Windows users without curl can just enter the URL in the browser to see the response

5) Repeat steps 3 - 4 for the `php`, `python`, and `ruby` applications.  

***NOTE:*** Make sure you `cd` into each directory before pushing.

***What Just Happened?***

You just deployed four applications each based on a different language and runtime.  Pivotal Cloud Foundry is a polyglot platform, meaning it supports multiple languages and does so in a pluggable way (via buildpacks)!

### Questions

* What are some common items in the output that occurred when pushing each application?

## Explore Apps Manager

1) Log in to Apps Manager. Visit `https://login.sys.apbg.apcf.io/login` and use your user credentials to log in. Find the `LPW-PCF-101` space and click into it and find the name of the apps you have pushed. Notice you can see things like app events, logs, services, etc.

***What Just Happened?***

You have interfaced with Pivotal Cloud Foundry from two separate clients (`cf` and Apps Manager).  Many of the operations that are available in `cf` CLI are also available in Apps Manager.

## Clean up

1) Delete the applications you just pushed.  

This is very important for resource constrained environments.

```
$ cf delete php
```

Repeat for `python`, and `ruby`  and `node` applications.

# Beyond the class

Check out the Cloud Foundry <a href=https://github.com/cloudfoundry-samples target="_blank">sample applications</a>.  

<a href=https://github.com/cloudfoundry-samples/spring-music target="_blank">Spring Music</a> is a favorite.
