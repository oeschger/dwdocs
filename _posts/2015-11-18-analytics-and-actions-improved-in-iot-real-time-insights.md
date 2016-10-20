---
ID: 2571
post_title: >
  IoT Real-Time Insights integrates IFTTT
  and Node-RED
author: Greg Knowles
post_date: 2015-11-18 14:25:49
post_excerpt: ""
layout: post
permalink: >
  https://nextstage.torolab.ibm.com/iotplatform/2015/11/18/analytics-and-actions-improved-in-iot-real-time-insights/
published: true
---
<p><img src="http://nextstage.torolab.ibm.com/iotfoundation/wp-content/uploads/sites/24/2015/11/RTI_logo.png" alt="RTI_logo" width="215" height="215" class="alignright size-full wp-image-2573" /> Real-time analytics provide insights from streaming IoT data, but the key is taking the appropriate action as a result of those insights, and <a href="https://console.ng.bluemix.net/catalog/services/iot-real-time-insights">IoT Real-Time Insights helps</a> you do both.  Recently, we made some significant updates to the service that dramatically improve the insights (improved analytics capabilities) and the available actions allowing you to:</p>
<ul>
<li>Create a service request in your Enterprise Asset Management system when an asset has an issue</li>
<li>Notify your sales team when a customer needs new supplies for your product</li>
<li>Send a text message to personnel and alert your Safety Team when unsafe conditions exist</li>
<li>Or closer to home, remind yourself when you’ve left the garage door open at night</li>
</ul>
<p>These examples are made possible in part through three new actions:  Node-RED, IFTTT, and webhook (a general purpose RESTful service call).  We’ve also made some other enhancements to improve analytics capabilities, ease of use (and reuse), and the user interface for the rules editor.</p>
<h2>Analytics and actions improvements</h2>
<p>The new action types allow nearly limitless ways to drive real-time alerts and actions into other systems automatically!</p>
<ul>
<li><b>Node-RED action</b> provides an easy way to invoke a Node-RED flow where you can perform additional logic, massage the data, store it or simply send notifications to other systems.</li>
<li><b>IFTTT action</b> enables integration with <a href="https://ifttt.com/">IFTTT</a> through the Maker channel, and from there you can easily link to hundreds of other actions from turning the lights on in your house to posting an image snapshot from a security camera to Box.</li>
<li><b>Webhook action</b> is a RESTful service call that can trigger an alert or activity in just about any system through RESTful APIs. For example, creating a service request in Maximo Enterprise Asset Management to investigate an asset that is operating out of normal tolerances.</li>
</ul>
<p>More information about these actions and how to create them can be found in the <a href="">online doc</a>.</p>
<p>Below is a summary of other new features:</p>
<ul>
<li><b>Reusable Actions</b>: You can create actions as separate entities and reuse them with multiple rules.  For example, if you create a Node-RED flow to process the payload from an alert and then send that off to an order management system, you could then use that same action across many rules that monitor inventory levels for hundreds of items.</li>
<li><b>Analytics Enhancements</b>: We’ve also made some general improvements to the analytics rules editor.  The user interface has been updated to be cleaner and a bit more compact allowing more real estate to work with complex conditions and actions.  You can also compare two values in the same message to monitor correlated properties, and you can compare data points to context parameters to apply rules to subsets of devices based on asset ID or location, for example.  Rules also have a severity indicator that is associated with all alerts.  The severity can be used to prioritize the processing of actions and is displayed in the real-time dashboards.</li>
<li><b>Streamlined administration</b>: The administrative task of creating message schemas is now much easier.  Simply connect your device and Real-Time Insights parses the incoming messages and provides a guided path allowing you to select incoming properties and then add friendly names, units, and context descriptors in a few simple steps.</li>
<li><b>Dashboard improvements</b>: Another update to the real-time dashboard allows you to filter alerts for your devices over the last day, week or arbitrary date ranges to help you see just the right level of alert history.</li>
</ul>
<h2>We&#8217;re listening to you!</h2>
<p>Our team has been listening to you and we’ve been hard at work delivering these new capabilities which will provide a tremendous amount of flexibility and value, providing you with tools to make your real-time analytics smarter while easily integrating with other systems.</p>
<p>Log into Bluemix and give these new features in the <a href="https://console.ng.bluemix.net/catalog/services/iot-real-time-insights/">IoT Real-Time Insights service</a> a try!</p>