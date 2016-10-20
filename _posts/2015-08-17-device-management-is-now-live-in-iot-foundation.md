---
ID: 2525
post_title: >
  Device Management is now live in IoT
  Foundation
author: AndrewSchofield
post_date: 2015-08-17 15:27:49
post_excerpt: ""
layout: post
permalink: >
  https://nextstage.torolab.ibm.com/iotplatform/2015/08/17/device-management-is-now-live-in-iot-foundation/
published: true
---
<p>I’d like to tell you about a major new enhancement we’ve just made to the Internet of Things Foundation service. We call it Device Management, and it’s all about making it easy and efficient to manage lots of IoT devices.
<h1>What is Device Management anyway?</h1>
When I talk to customers about their IoT plans, they generally mention the phrase “device management”. It doesn’t matter whether they’re talking about connected cars, connected light bulbs or connected refrigerators, there’s usually device management in there somewhere. So, what does it mean and why does everyone want it? Well, it includes things like:
<ul>
	<li>Bulk operations on many devices at a time</li>
	<li>Rich device metadata and status information</li>
	<li>Diagnostic information, both for connectivity and for the devices themselves</li>
	<li>Device management actions, most notably firmware update</li>
</ul>
<p>And all of these things need to be made easily accessible via APIs and dashboards.
<h1>Managed devices</h1>
<p>In order to benefit from device management, your devices need to be a bit smarter. Specifically they need to be managed devices. A managed device has a piece of code called a <b>device management agent</b> which exchanges special device management messages with IoT Foundation over MQTT. There’s nothing very complicated about a device management agent. The device management messages are quite simple, and you need only use as much or as little of the capabilities as your device requires.
<p>We will provide sample implementations of device management agents, and you can use these as the basis of the agent for your own devices. That typically will mean adding a few lines of code to the sample. The step from an unmanaged device using MQTT to a managed device with a basic device management agent is very small indeed. We will also provide recipes for device management.
<p>At a minimum, a device management agent needs to send a message to IoTF telling it that it wants to be a managed device. This message also includes a summary of the device’s capabilities, such as whether it can have its firmware updated.
<p>You can pick and choose the features of device management that you want to use. For example, if you want your device to be able to send diagnostic information to IoTF, you add that capability to your device management agent. If your device is mobile and you want it to update its location information in IoTF, you can add that feature to your device management agent.
<h1>Device metadata</h1>
<p>Imagine that you’re producing a new range of connected blenders. Each blender has a manufacturer, model and serial number. So that the blenders can connect to IoT Foundation, you add them as new devices to your IoTF organisation. When you do this, it would be nice to be able to associate the serial number and so on with the devices. Then, you can tie back information from a device in IoTF to the actual blender you produced.
<p>These are examples of <b>device metadata</b>. As the number of devices increases, having the ability to associate metadata with the devices helps you manage the devices efficiently. For example, if a customer calls the service line with a blender problem, you can ask for the serial number and then use this to find the device in IoTF which corresponds to that blender. You can dive down into the diagnostic information for the device and perhaps work out how to resolve the problem.
<p>Another example of device metadata is called <b>descriptive location</b>. There’s longitude and latitude too, but in many cases a less rigorous idea of location such as “Building 43, floor 2” is much more useful. That’s a much more descriptive way of expressing location.
<h1>Diagnostic information</h1>
<p>If you’re managing a large number of devices, some of them are bound to have problems. These might include connectivity problems, or perhaps an unexpected situation discovered by the device firmware.
<p>We’ve added <b>connectivity logs</b> to our API and dashboard. These let you see significant connectivity events for devices, such as why a device disconnected. If you are having connectivity problems, these logs will help you figure out what’s wrong.
<p>Devices can also report diagnostic information to IoT Foundation. The simplest are <b>error codes</b>. These are just numbers which represent error conditions, suitable for the simplest devices. If a device notices an error, its device management agent can send the error code to IoT Foundation. 
<p>More sophisticated devices can report <b>error logs</b> instead. Each error log entry includes a timestamp, a description of the problem and perhaps a block of diagnostics data captured by the device.
<p>When a device reports an error code or a high-severity error log, IoT Foundation automatically highlights the device as being in an <b>alert</b> state in the IoT Foundation dashboard. This makes it simple for the operator to notice the problem and act on it.
<p>Again, it’s all about efficiently managing devices.
<h1>Device management actions</h1>
<p><b>Device management actions</b> are a way of remotely managing devices from IoT Foundation. There are four actions supported initially:
<ul>
<li>Reboot</li>
<li>Factory reset</li>
<li>Firmware download</li>
<li>Firmware update.</li>
</ul>
<p>You can initiate device management actions from the API or the dashboard. You can perform an action on up to 5000 devices at a time in a single request. Of course, a request such as rebooting 5000 devices doesn’t complete immediately, so you can see the requests in progress and whether the devices successfully performed the action.
<p>Managed devices don’t have to support any actions, but if they do, the device management agent is responsible for receiving the initiation command and performing the action. For example, to reboot a device, it’s likely that there’s a system call in the device firmware which actually reboots the device. The device management agent would simply invoke this system call when it receives the command from IoTF. Once the device has rebooted, it reconnects to IoT Foundation and sends a message indicating that it’s back. This completes the device’s part in the overall management request.
<h1>Building your own tools with our API</h1>
<p>As part of this, we’ve massively enhanced our API. Having an easy-to-use API is important because it makes automation simple. We had three principles in mind:
<ul>
<li>The API must work well even if you have millions of devices. So, there is filtering of results (“give me a list of the washing machines of type ‘WM123’ at firmware level 17”) and paging so you can get a huge set of results in manageable chunks.</li>
<li>Everything we do in our dashboard UI can be done with the API. Soon, in the dashboard, we will add “API” buttons which you will be able to press to reveal the API calls we use to request the data shown in the dashboard. If you’re trying to create your own tools based on the IoTF API, this will be a big help.</li>
<li>Whenever possible, the API follows REST principles. Basically, this means that the behaviour of the API is predictable to developers familiar with REST. For example, resources are grouped into collections. If you use HTTP GET on a collection, you get a list of the resources in the collection. If you use HTTP GET on a single resource such as a device, you get the details about that device. In neither case are any resources modified, so you can safely use these operations.</li>
</ul>
<p>Also, we have documented the API using a notation called Swagger. There are a lot of tools for Swagger, so whether you want an easy-to-browse view of the API or a generated client library so you don’t have to use HTTP directly yourself, having a Swagger definition is great.
<h1>Designing the service</h1>
<p>In the IoT Foundation team, we put a lot of effort into designing the service so it meets the needs of specific target users. We have people dedicated to designing the user experience and the visuals of the dashboard. You can clearly see the importance we place on the experience when you first start using the service. Sophie Riches, who is a User Experience Designer in our team, will tell you much more about this soon.
<h1>What next?</h1>
<p>A good place to start is the documentation about device management in IoTF which can be found <a href="https://docs.internetofthings.ibmcloud.com/devices/device_mgmt/index.html" target="_blank">here</a>.
<p>If you’re already using Internet of Things Foundation, you’ll notice the changes in your dashboard. You can convert existing unmanaged devices into managed devices by adding a device management agent. We will be providing sample implementations of device management agents, which you can refer to or use as the basis of your own agent.
<p>We will be adding new recipes for device management over the coming weeks, so if you’ve already got experience with using IoT Foundation, you’ll easily be able to start using device management also.