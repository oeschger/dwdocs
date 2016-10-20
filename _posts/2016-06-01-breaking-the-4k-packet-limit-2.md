---
ID: 3048
post_title: Breaking the 4K packet limit
author: bkufluk
post_date: 2016-06-01 13:53:36
post_excerpt: ""
layout: post
permalink: >
  https://nextstage.torolab.ibm.com/iotplatform/2016/06/01/breaking-the-4k-packet-limit-2/
published: true
---
I'm pleased to announce that the Watson IoT Platform can now support larger message packet sizes.  <br /><br /><a href="http://nextstage.torolab.ibm.com/iotplatform/wp-content/uploads/sites/24/2016/06/packets.jpg"><img src="http://nextstage.torolab.ibm.com/iotplatform/wp-content/uploads/sites/24/2016/06/packets.jpg" alt="packets" width="1212" height="448" class="alignnone size-full wp-image-3049" /></a><br /><br />Previously when devices sent events to the platform, or when commands are sent to a device from the platform, then you were limited to a 4K byte packet size.<br />  <br />We have now increased that limit to <strong>128K byte per message</strong>.  So if you are sending more detailed event information from a device, or saving several values up and sending them in at once, then you'll find that easier with the new limits.  <br /><br />See the <a href="https://docs.internetofthings.ibmcloud.com/devices/mqtt.html">documentation</a> for more details.<p>&nbsp;</p><br /><br /><br />