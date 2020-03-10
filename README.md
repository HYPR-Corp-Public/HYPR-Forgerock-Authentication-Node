# HYPR-Forgerock-Authentication-Node

HYPR and [ForgeRock](https://www.forgerock.com/) have partnered to deliver a true passwordless authentication to the enterprise. HYPR is the first Authentication Platform designed to eliminate passwords and shared secrets. Forgerock, as the leader in CIAM, works closely with HYPR to enable a true passwordless identity.

HYPR’s native plugins for Forgerock enable easy integration and deployment with Auth Trees. In 2019, Forgerock and HYPR announced a Go to Market partnership to deliver true passwordless security to more than 1 Billion identities powered by Forgerock.

## Pre-Requisites 
* Have a deployed ForgeRock OpenAM 6.0+ instance deployed
* Have a deployed HYPR Server with access to the HYPR Control Center
* Have an application in the Control Center created for ForgeRock
* Have access to the HYPR Authentication Node for ForgeRock. You must contact HYPR or ForgeRock to gain access to this Authentication Node. 

Contact HYPR or ForgeRock for any assistance in the deployment of HYPR or ForgeRock OpenAM.

### Building from the Source

To build this node from the source you will need to contact HYPR for the HYPR Java SDK jar, which is used by the authentication node. 

``` 
$ git clone https://github.com/HYPR-Corp-Public/HYPR-Forgerock-Authentication-Node.git
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
