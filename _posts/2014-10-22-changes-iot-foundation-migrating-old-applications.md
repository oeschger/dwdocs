---
ID: 1596
post_title: 'Changes to the IoT Foundation &#8211; and migrating your old applications'
author: Ben Bakowski
post_date: 2014-10-22 16:39:22
post_excerpt: ""
layout: post
permalink: >
  https://nextstage.torolab.ibm.com/iotplatform/2014/10/22/changes-iot-foundation-migrating-old-applications/
published: true
---
You will all now be aware that the production IBM Internet of Things Foundation is now live! 

Those of you who had been using the beta Internet of Things Foundation (IoTF) service will also be aware that productionising the IoTF has required some unavoidable changes to the beta experience. We'd like to clarify what these changes are, how they impact your beta applications and - more importantly - what you need to do to get your applications running once more.

<h2>Changes introduced by the beta to production deployment on Oct 21st</h2>

<ol>
 <li>Organizations are no longer created or deleted manually. Instead, organizations are managed automatically through Bluemix and/or IBM Marketplace</li>
 <li>Customer beta data has been deleted, so you will no longer see beta organizations, devices, API Keys or historical device data</li>
 <li>API Key has ":" delimiter has changed to "-"</li>
 <li>The Bluemix beta IoTF service has been removed and replaced by a new production service</li>
 <li>The Bluemix VCAP_SERVICES format has changed</li>
 <li>The Node-RED nodes have been improved, and their interface has changed</li>
 <li>The orgId is now 6, rather than 5, characters long</li>
</ol>


<h2>I'm an existing beta IoTF/Bluemix user: how do these changes impact me?</h2>

Your existing Bluemix applications will no longer work with the IoTF. This is what you need to do to get running again.

<ol> 
 <li>You will need to create a new IoTF organization. 
  <ul>
   <li>An IoTF organization is created for you every time you create a new instance of the Internet of Things service in Bluemix.</li>
   <li>From the Catalog, create a new Internet of Things service from the Internet of Things category. You can leave the service as unbound for now.</li>
  </ul>
 </li>

 <li>Once created, click on your new Internet of Things service tile, and then click on the Launch button; this will take you to the IoT Foundation dashboard for your new organization.</li>

 <li>You may wish to add yourself as a member to the IoTF organization - this will allow you to view the IoTF organization without navigating via Bluemix first.</li>
 <li>You can now register any devices and recreate any API Keys needed by your applications.
  <ul>
   <li>Note that an API Key will be created automatically every time you bind a Bluemix application to your service, so there is no longer a need to create them manually</li>
  </ul>
 </li>

 <li>The final step is to migrate your applications in Bluemix. 
  <ul>
   <li>Node-RED: We encourage you to migrate your Node-RED applications to the new boilerplate and nodes that are now provided
    <ul>
     <li>Create a new instance of the Internet of Things Foundation Starter boilerplate application</li>
     <li>Click on "bind service" to bind this boilerplate to the IoT service you have created</li>
     <li>You will see a flow that uses the new IoTF input node. You may wish to copy your existing business logic from your IoTF beta application and wire it to this new node.</li>
     <li>Configure the new input node to use an authentication method of "Bluemix Service". Note there is no need to configure the node with API Keys, as binding the service takes care of this step for you.</li>
     <li>Configure the remaining properties of the input node to refer to your device of interest.</li>
    </ul>
   </li>
   <li>Java and JavaScript applications can be migrated manually.
    <ul>
     <li>The VCAP_SERVICES entry has changed. You now need to search on an object called "iotf-service"; an example is shown below.</li>
     <li>Further information is available in VCAP_SERVICES, so there is no need to split the API Key to extract the orgId.</li>
    </ul>
   </li>
  </ul>
 </li>
 <li>Don't forget that:
  <ul>
   <li>all applications will be using a new 6-character organization ID</li>
   <li>all devices and API Keys will have new credentials as you will have recreated them all</li>
   <li>API Keys are now constructed with "-" rather than ":" delimiters</li>
   <li>You create a new organization with every IoT Foundation service you create, so unless you explicitly do NOT want to share data between applications, we encourage you to use a single service shared across applications where possible</li>
  </ul>
 </li>
</ol>

<h2>Sample VCAP_SERVICES entry</h2>

<code>{
  "iotf-service": {
    "name": "Internet of Things-lp",
    "label": "iotf-service",
    "plan": "iotf-service-free",
    "credentials": {
      "iotCredentialsIdentifier": "a3g6k39sl6r5",
      "mqtt_host": "<orgId>.messaging.internetofthings.ibmcloud.com",
      "mqtt_u_port": 1883,
      "mqtt_s_port": 8883,
      "base_uri": "https://internetofthings.ibmcloud.com:443/api/v0001",
      "org": "<orgId>",
      "apiKey": "<apiKey>",
      "apiToken": "<apiToken>"
    }
  }
}
</code>