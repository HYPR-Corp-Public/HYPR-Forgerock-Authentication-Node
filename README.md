# HYPR-Forgerock-Authentication-Node

HYPR and [ForgeRock](https://www.forgerock.com/) have partnered to deliver a true passwordless authentication experience to the enterprise. The HYPR solution ensures that your users’ credentials always remain safe on personal devices. Eliminating centralized passwords enables HYPR to remove the target and provide a secure password-less experience for your customers and employees.

By decentralizing user authentication, HYPR minimizes the risk of a breach, eliminates credential reuse, and enables enterprises to Trust Anyone.

## Pre-Requisites 
* Have a deployed ForgeRock OpenAM 6.0+ instance deployed
* Have a deployed HYPR Server with access to the HYPR Control Center
* Have an application in the Control Center created for ForgeRock

Contact HYPR or ForgeRock for any assistance in the deployment of HYPR or ForgeRock OpenAM.

### Building from the Source

To build this node from the source you will need to contact HYPR for the HYPR Java SDK jar, which is used by the authentication node. 

``` 
$ git clone ...
$ cd Forgerock-Authentication-Node
$ mvn clean package 
```

# Installation
  
To install the HYPR Authentication Node to ForgeRock you will want to follow these steps: 
1. Stop the instance of Tomcat hosting ForgeRock
2. Copy the HYPR node .jar file to `../tomcat/webapps/openam/WEB-INF/lib/`
3. Start the instance of Tomcat hosting ForgeRock

### Setup
With the HYPR Authentication Node deployed within the OpenAM installation you will be able to create an authentication tree which utilizes HYPR for authentication. 

Log into the OpenAM administrative console and navigate to: `Realm\Authentication\Trees`

![ForgeRock Trees](https://files.readme.io/ec41b1a-2018-07-09_14-05-31.png)

Select the authentication tree you want to include HYPR Authentication on. 

Within the Authentication Tree you will see the `HYPR Auth Initiator` and  `HYPR Auth Decision` nodes are available. The HYPR Auth nodes require the use of the `Username Collector` node to identify the user. 

You will want to include these nodes in the tree in this order, as depicted in the image below: 
1) `Username Collector`
2) `HYPR Auth Initiator` 
3) `HYPR Auth Decision`

![HYPR Authentication Trees](https://files.readme.io/e1436dc-2018-07-09_14-05-51.png)
