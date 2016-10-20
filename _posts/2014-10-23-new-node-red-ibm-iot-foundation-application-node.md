---
ID: 1630
post_title: >
  New Node-RED IBM IoT Foundation
  Application Node
author: Ben Bakowski
post_date: 2014-10-23 10:04:53
post_excerpt: ""
layout: post
permalink: >
  https://nextstage.torolab.ibm.com/iotplatform/2014/10/23/new-node-red-ibm-iot-foundation-application-node/
published: true
---
In you took part in the IoT Foundation beta, you may well have used Node-RED in the beta IoT Starter Community Bluemix boilerplate. We are pleased to announce improvements in the IBM IoT Application nodes that are now available.

<ul>
	<li>Previously, the (beta) IoT App node assumed that the application developer would specify the complete MQTT topic string, and therefore manually control what events the application is interested in. We have now introduced an improved IBM IoT App node which provides out-of-the-box capability to control the events the application is interested in: 
<ol>
 <li>Publish and Subscribe Device Commands: The IBM IoT App node can be used, in a registered mode, to create a flow that shows device commands being published by an application. The same command can be subscribed to by another application, on the behalf of a device.</li>
 <li>Publish and Subscribe Device Events: The node can be used to add a flow that shows device events being published by an application, on behalf of a device, and the same event being subscribed to by another application.</li>
 <li>Subscribe to Device Status: The IBM IoT App node can be used to add a flow that shows how an application can detect the connection status of a device.</li>
</ol>
</li>
	<li>The node adds properties to the message in addition to the payload, including: device id, device type, event type, and format. This makes it easier for the application developer to construct flows and analyze the event or command, device or application type and format of each. 
</li>
	<li>The new node is intended to be easier to use as it changes intuitively depending upon the selections done, again, making it easier for you to create new IoT apps quickly.
</li>
</ul>