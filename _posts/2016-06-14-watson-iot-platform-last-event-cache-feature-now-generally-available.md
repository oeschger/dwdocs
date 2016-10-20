---
ID: 3093
post_title: >
  Watson IoT Platform Last Event Cache
  feature now Generally Available
author: afoster
post_date: 2016-06-14 16:57:20
post_excerpt: ""
layout: post
permalink: >
  https://nextstage.torolab.ibm.com/iotplatform/2016/06/14/watson-iot-platform-last-event-cache-feature-now-generally-available/
published: true
---
I’m pleased to announce that IBM Watson IoT Platform has now made the Last Event Cache feature Generally Available. 
This builds on the beta functionality that we first made available in April this year – making it now production ready and fully supported.<br /><h2>What is the Last Event Cache?</h2><span>In the world of connected devices whether it be a temperature sensor on an engine or a heart rate monitor on a patient, an IoT application's most common question of a device is "What was the last value of ....". Watson IoT Platform wants to make accessing the most recent information from a connected device as quick and straight forward as possible. </span><br /><h2>How it Works</h2><span>The API can now return the last recorded value of an event-id for a specific device, or the last recorded value for each event-id reported by a specific device. The last event cache applies to values sent in the last 12 months. This means entries in the cache are overwritten by the next entry and the oldest value in the cache is 12 months old after which values are discarded.<br /></span><br /><span>To request the most recent value for a specific event-id, use the following API request. This request will return the last recorded value for the event-id “power”.</span><br /><pre>GET /api/v0002/device/types/&lt;device-type&gt;/devices/&lt;device-id&gt;/events/power

</pre><span>The response is returned as JSON in the following format:</span><br /><pre>{
        "deviceId": "&lt;device-id&gt;",
        "eventId": "power",
        "format": "json",
        "payload": "eyJzdGF0ZSI6Im9uIn0=",
        "timestamp": "2016-03-14T14:12:06.527+0000",
        "typeId": "&lt;device-type&gt;"
}</pre><span><strong>Note</strong>: While the API response is JSON, event payloads can be written in any format. Payloads returned by this API will be encoded in base64.<br /><br />Alternatively, to request the most recent value for each event-id reported by this device, use the following API request.</span><br /><br /><pre>GET /api/v0002/device/types/&lt;device-type&gt;/devices/&lt;device-id&gt;/events</pre><br /><span>The response will include all event-id’s sent by the device. In this instance, it returns values for the “power” and “temperature” events.</span><br /><pre>[
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
]</pre><span>So now you can quickly and easily get at the last event values sent by your devices even if your devices have gone offline. </span><span>Login and check out this new feature.</span><br /><br /><span>Documentation on this new feature can be found at:</span><br /><p><a href="https://console.ng.bluemix.net/docs/services/IoT/getting_started/features.html#last-event-cache">https://console.ng.bluemix.net/docs/services/IoT/getting_started/features.html#last-event-cache</a></p><br /><br />