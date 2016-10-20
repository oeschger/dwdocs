---
ID: 3451
post_title: >
  Enhanced Security Controls for IBM
  Watson IoT Platform
author: James_Murphy
post_date: 2016-09-23 08:26:08
post_excerpt: ""
layout: post
permalink: >
  https://nextstage.torolab.ibm.com/iotplatform/2016/09/23/enhanced-security-controls-for-ibm-watson-iot-platform/
published: true
---
Operational security is a top priority when selecting IoT platforms and we’re proud to say that Watson IoT Platform regularly proves its mettle in meeting and exceeding the exacting security expectations of IoT innovators. <br /><br />
We’ve blogged before about the <a href="https://nextstage.torolab.ibm.com/iotplatform/2016/09/01/secure-your-iot/" target="_blank">robust security standards</a> supported by Watson IoT Platform. These complement the use of open standard secure communications protocols, such as TLS v1.2, that ensure IoT device interactions are <a href="https://console.ng.bluemix.net/docs/services/IoT/reference/security/index.html#secure-device-connection" target="_blank">authenticated and encrypted</a>. Further, the Watson IoT Platform benefits from Bluemix and Softlayer <a href="https://new-console.stage1.ng.bluemix.net/docs/security/index.html#platform-security" target="_blank">operational security capabilities</a> compliant with a wide range of <a href="https://new-console.stage1.ng.bluemix.net/docs/security/index.html#compliance" target="_blank">Industry Standards</a>.
<br /><br />
So, with robust operational platform security in place, how can you configure and manage a security environment appropriate for your device, application and user requirements?
<br /><br />
Watson IoT Platform now offers configuration and management of Roles which enable controls to be defined for Users, Applications and Gateways. Configuration of Role permissions grant or restrict the ability to perform particular platform operations. The Watson IoT Platform now allows the categorization of Users, Applications, and Gateways into logical access action classes, called <em>Roles. </em>The Roles provide flexibility by controlling the level of access Users, Applications and Gateways have when interacting with services and data within the Watson IoT Platform.  This introduces a way to specify the allowed behaviors for different types of Users, Applications and Gateways within the platform at a much increased level of granularity. 
<br /><br />
Watson IoT Platform offers five different predefined roles for Users, six different predefined roles for Applications and two different predefined roles for Gateways. Defining Role permissions at such a level is a robust and accurate way to protect and manage interaction with your IoT resources. It provides options for validating role authorization to create, access, update and delete services and data within platform. 
<br /><br />
Now, for example, you can:<br /><ul><li>Distinguish between Users able to perform privileged operations such as configure services and resources in the Watson IoT Platform and Users only able to view the data intended for them relating to pre-configured services. This  ensures that data resources are accurately managed and not accessed or changed for unintended purposes.</li></ul><ul><li>Assign privilege to trusted Gateways to create or activate devices.  This reduces manual administration, and improves automated device provisioning, whilst controlling interaction with Gateways outside the trusted portion of the network.</li></ul><ul><li>Specify Applications able to issue device commands and initiate device management actions distinguishing them from application simply able to subscribed to device events or view device information.  This protects your solution from unexpected application behavior.</li></ul><br />
With Role based access control the integrity of Wason IoT Platform is enhanced making your solution more secure. You can read more about the full range of the new <a href="https://console.ng.bluemix.net/docs/services/IoT/roles_index.html" target="_blank">Role based security capabilities</a> in the Official Watson IoT Platform Documentation.