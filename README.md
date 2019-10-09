# My First Camel K


## Task 1 - Create your workspace

1. Go to codeready console login with your ID and PWD {user-username}/openshift
```
http://codeready-codeready.apps.cluster-jpcamel-8899.jpcamel-8899.open.redhat.com
```
1. Go to the factories on the top left, choose dilii, it will take you to the factory setting page.
1. Click on OPEN on the top right.
1. Wait for the workspace to start
1. Click on the manage command on the top, run the following in orders:
	* 	Download Kamel Binary
	* 	Unzip Kamel
	* 	Setup Kamel



## Task 2 - Intall your Camel K Operator

1. Go to OpenShift Console
```
https://console-openshift-console.apps.cluster-jpcamel-8899.jpcamel-8899.open.redhat.com
```
1. Go to your user project, userX
1. Go to the Installed Operators and click on Camel K Operator
1. Click on the Integration Platform
1. Create Integration Platform by clicking on the button, and save .
## Task 3 - First Camel K

***
*NOTE: The Terminal timeout every 30 secs if you don't touch it. Simply create another one by right click on the devmachine. And don't forget to go back to your working directory. (mycamelk)*
***

1. Go back to the codeready env.In the terminal, login to Openshift with your ID/PWD(openshift) and go to your project

```
oc login https://api.cluster-jpcamel-8899.jpcamel-8899.open.redhat.com:6443
     -yes
     -YOUR_USERID
     -passwaord

oc project YOUR_USERID
```
2. In your workspace, open **mycamelk** directory, open File ***FirstCamelK.java***
Place the following camel route in your configure method and save.

```
    from("timer:tick?fixedRate=true&period=2000")
       .log("Hello! ");
```
***
*NOTE: The Terminal timeout every 30 secs if you don't touch it. Simply create another one by right click on the devmachine. And don't forget to go back to your working directory. (mycamelk)*
***
3. In the terminal, and run the following command in the terminal
```
bash kamel run FirstCamelK.java --dev
```

4. Change the camel route to following and save, see what is happening in the terminal log!!

```
   from("timer:tick?fixedRate=true&period=2000")
      .log("Hello! YOUR_NAME");
```

## Task 4 - Connecting to Kafka

I have setup a AMQ Streams(kafka) topic ***my-topic*** and sends in greeting into it. The boostrap address is as follows, 
 
```
my-cluster-kafka-bootstrap.streams.svc:9092
```

Try and see if you can have Camel K conntect to ***my-topic*** and receive my message.