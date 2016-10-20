---
ID: 2711
post_title: >
  Watson IoT Platform Integration with
  Orange (beta)
author: bkufluk
post_date: 2016-03-30 10:52:49
post_excerpt: ""
layout: post
permalink: >
  https://nextstage.torolab.ibm.com/iotplatform/2016/03/30/watson-iot-platform-integration-with-orange-beta/
published: true
---
<p>The platform now has integration with Orange built in. <br /><br /> This means that with your Orange sim card installed in a device and configured you can see it's properties in the device details:  <br /><a href="http://nextstage.torolab.ibm.com/iotfoundation/wp-content/uploads/sites/24/2016/02/orange.png"><img src="http://nextstage.torolab.ibm.com/iotfoundation/wp-content/uploads/sites/24/2016/02/orange.png" alt="orange" class="alignnone wp-image-2690 size-full" height="347" width="694" /><br /></a>To enable the integration, you just need to go to settings, turn on the integration and set the username and password to access your Orange account:<br /><br /><a href="http://nextstage.torolab.ibm.com/iotfoundation/wp-content/uploads/sites/24/2016/03/orangesetup.jpg"><img src="http://nextstage.torolab.ibm.com/iotfoundation/wp-content/uploads/sites/24/2016/03/orangesetup.jpg" alt="orangesetup" width="687" height="168" class="alignnone wp-image-2813 size-full" /><br /></a>Then you need to create a link between your IoT device and the SIM card that's it's using.  To do that, you add the serial number to the extension configuration section for the device configuration in the IoT Platform dashboard.  If you were adding a large number of devices, then you'd probably find it easier to use the REST api to automate both registration and adding the serial numbers to the extension configuration.  <br /><a href="http://nextstage.torolab.ibm.com/iotfoundation/wp-content/uploads/sites/24/2016/03/orangeextensionconfiguration.jpg"><img src="http://nextstage.torolab.ibm.com/iotfoundation/wp-content/uploads/sites/24/2016/03/orangeextensionconfiguration.jpg" alt="orangeextensionconfiguration" width="781" height="237" class="alignnone size-full wp-image-2814" /></a><br />Once you hit confirm, you'll immediately see the Orange section appear in the Extensions section of the device definition.  <br /><a href="http://nextstage.torolab.ibm.com/iotfoundation/wp-content/uploads/sites/24/2016/02/orange.png"><img src="http://nextstage.torolab.ibm.com/iotfoundation/wp-content/uploads/sites/24/2016/02/orange.png" alt="orange" width="694" height="347" class="alignnone size-full wp-image-2690" /></a><br />In addition you can ask Orange to provide the location of the device, by clicking Request Update.  If the location can be determined through mobile phone mast triangulation then it will appear, including it's latitude, longitude and accuracy:<br /><br /><a href="http://nextstage.torolab.ibm.com/iotfoundation/wp-content/uploads/sites/24/2016/03/orangelocalised.jpg"><img src="http://nextstage.torolab.ibm.com/iotfoundation/wp-content/uploads/sites/24/2016/03/orangelocalised.jpg" alt="orangelocalised" width="733" height="338" class="alignnone size-full wp-image-2815" /><br /><br /></a>This feature is in beta which means it's available and you can start using it now; but we are continuing to improve it, so please let us know your thoughts and comments on the <a href="https://nextstage.torolab.ibm.com/answers/topics/iot.html">forum</a>. </p>