---
ID: 2820
post_title: >
  Watson IoT Platform Last Event Cache
  (beta)
author: afoster
post_date: 2016-04-04 12:46:05
post_excerpt: ""
layout: post
permalink: >
  https://nextstage.torolab.ibm.com/iotplatform/2016/04/04/watson-iot-platform-last-event-cache-beta/
published: true
---
In the world of connected devices whether it be a temperature sensor on an engine or a heart rate monitor on a patient, an IoT application's most common question of a device is "What was the last value of ....". Watson IoT Platform wants to make accessing the most recent information from a connected device as quick and straight forward as possible. That is why we have introduced a new feature into our service called <b>Last Event Cache</b>.
<br />
<br />
The API can now return the last recorded value of an event-id for a specific device, or the last recorded value for each event-id reported by a specific device. The last event cache applies to values sent in the last 30 days. This means entries in the cache are overwritten by the next entry and the oldest value in the cache is 30 days after which values are discarded. We are looking to expand this to values sent in the last 12 months in the near future.
<br />
<br />
To request the most recent value for a specific event-id, use the following API request. This request will return the last recorded value for the event-id “power”.
<br />


<pre>GET /api/v0002/device/types/&lt;device-type&gt;/devices/&lt;device-id&gt;/events/power

</pre>



The response is returned as JSON in the following format:
<br />
<pre>{
        "deviceId": "&lt;device-id&gt;",
        "eventId": "power",
        "format": "json",
        "payload": "eyJzdGF0ZSI6Im9uIn0=",
        "timestamp": "2016-03-14T14:12:06.527+0000",
        "typeId": "&lt;device-type&gt;"
}</pre>

Alternatively, to request the most recent value for each event-id reported by this device, use the following API request.
<br /><br />
<pre>GET /api/v0002/device/types/&lt;device-type&gt;/devices/&lt;device-id&gt;/events</pre>
<br /><br />
The response will include all event-id’s sent by the device. In this instance, it returns values for the “power” and “temperature” events.
<br />
<pre>[
    {
        "deviceId": "&lt;device-id&gt;",
        "eventId": "power",
        "format": "json",
        "payload": "eyJzdGF0ZSI6Im9uIn0=",
        "timestamp": "2016-03-14T14:12:06.527+0000",
        "typeId": "&lt;device-type&gt;"
    },
    {
        "deviceId": "&lt;device-id&gt;",
        "eventId": "temperature",
        "format": "json",
        "payload": "eyJpbnRlcm5hbCI6MjIsICJleHRlcm5hbCI6MTZ9",
        "timestamp": "2016-03-14T14:17:44.891+0000",
        "typeId": "&lt;device-type&gt;"
    }
]</pre>

So now you can quickly and easily get at the last event values sent by your devices even if your devices have gone offline. 
Login and check out this new feature.
<br />
<br />
Documentation on this new feature can be found at:<br /> <a href="https://docs.internetofthings.ibmcloud.com/getting_started/features.html" target="_blank">https://docs.internetofthings.ibmcloud.com/getting_started/features.html</a><br /><br />

This feature is in beta which means it’s available and you can start using it now; but we are continuing to improve it, so please let us know your thoughts and comments on the <a href="https://nextstage.torolab.ibm.com/answers/topics/iot.html">forum</a>.