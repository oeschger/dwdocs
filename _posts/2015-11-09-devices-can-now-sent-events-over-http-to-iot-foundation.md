---
ID: 2546
post_title: >
  Devices can now send events over HTTP to
  IoT Foundation
author: bkufluk
post_date: 2015-11-09 17:57:18
post_excerpt: ""
layout: post
permalink: >
  https://nextstage.torolab.ibm.com/iotplatform/2015/11/09/devices-can-now-sent-events-over-http-to-iot-foundation/
published: true
---
<h2>What's changed?</h2>You now have more choices about how your device communicates with IoT Foundation.  When publishing messages to IoT Foundation you can use: <br /><ul><li>MQTT</li><li>MQTT over WebSockets</li><li><strong>HTTP</strong> - <span style="color: #008000;">New!</span></li></ul><h2>Why might you want to use it?</h2>MQTT is a great protocol for the Internet of Things and offers reliable and lightweight communication.  But, as a device developer, sometimes you find you're constrained by the libraries available in a particular environment, or existing code.  Your device might be trapped behind a firewall which only allows communication over port 80.  <br />The widespread availability of HTTP client support means that almost any device can now easily publish data into the Internet of Things Foundation.<br /><h2>How do I get started?</h2>Get started quickly with our <a target="_blank" href="https://nextstage.torolab.ibm.com/recipes/tutorials/publish-device-events-to-ibm-iot-foundation-using-https/">HTTP recipe</a>.  <br /><br />If you want to try out this support but haven’t signed up and created an organization then you can use the Quickstart service.  Quickstart supports HTTP without security to allow you to quickly try things out.  <br /><br />See the <a target="_blank" href="https://docs.internetofthings.ibmcloud.com/messaging/HTTPSIntro.html">full documentation for HTTP/S support</a>. <br /><h2>How is it secured?</h2>HTTP events are secured using TLS and sent over HTTPS.  Unsecured HTTP is only supported for Quickstart.  All communication with registered organizations must be secured. <br />To send events to registered organizations, the HTTP/S request must have an Authorization header. <br /><br />Username and password are dealt with in this way:<br />For Devices:<br /><ul><li>There is only one valid username "use-token-auth" for any device. This username indicates that the password field will contain the authentication token.</li><li>The password should be the authentication token for the device.</li></ul>In an HTTP/S request, a Content-Type request header must be provided. Only the following values are currently supported, and mapped to the Internet of Things Foundation event formats.<br />
<table border="1">
<tbody>
<tr>
<th>Content-Type Header Volume</th>
<th>IoT Foundation Format</th>
</tr>
<tr>
    <td>text/plain</td>
    <td>text</td>
</tr>
<tr>
    <td>application/json</td>
    <td>json</td>
</tr>
<tr>
    <td>application/html</td>
    <td>xml</td>
</tr>
<tr>
    <td>application/octet-stream</td>
    <td>bin</td>
</tr>
</tbody></table>

Use HTTP/S POST to this URL:<br /><em>&lt;target server: org_id.internetofthings.ibmcloud.com&gt;/api/v0002/device/types/{DeviceType}/devices/{DeviceID}/events/{eventID}</em><br /><br />Request body = event payload<br /><br />