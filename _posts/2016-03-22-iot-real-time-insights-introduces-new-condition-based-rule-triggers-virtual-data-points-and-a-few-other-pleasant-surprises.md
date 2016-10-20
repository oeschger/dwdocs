---
ID: 2796
post_title: >
  IoT Real-Time Insights introduces new
  condition-based rule triggers, virtual
  data points, and a few other pleasant
  surprises
author: Greg Knowles
post_date: 2016-03-22 04:39:46
post_excerpt: ""
layout: post
permalink: >
  https://nextstage.torolab.ibm.com/iotplatform/2016/03/22/iot-real-time-insights-introduces-new-condition-based-rule-triggers-virtual-data-points-and-a-few-other-pleasant-surprises/
published: true
---
<p>Every now and then you get a pleasant surprise. Case in point, I was at an NCAA tournament basketball game in Raleigh the other night with my old college roommate. We had good seats and were enjoying the view and talking during the pre-game when we were approached by an older lady who was clearly rooting for the same team. She asked us if we wanted to move down to the lower level into better seats, and she offered us the two tickets on the spot. Needless to say, we took her up on the offer and got MUCH better seats closer to the action about 15 rows up from mid-court. Perhaps I’m stretching my comparison a bit, but Bluemix services can also offer pleasant surprises in the form of new features that just show up every three to four weeks!

</p><p>It’s been a few weeks since I last wrote about updates to Real-Time Insights, and some of you may have seen some of recent updates (perhaps even been pleasantly surprised). But, in case you haven’t, I wanted to highlight a few of them.

</p><h2>Service name changed to align with Watson IoT Platform</h2><p>
</p><p>The official name of the service has been changed to align with the Watson IoT Platform and is now ‘IBM® Watson™ IoT Platform Analytics Real-Time Insights’. The name of the tile in the Bluemix catalog is still the same, ‘IoT Real-Time Insights’, but the official name is referenced a few places in the service web pages and documentation.

</p><h2>Time- and count-based rule triggering</h2><p>
</p><p>You can now specify additional time and count-based conditions for when a rule does or doesn’t trigger. Rules have additional time- and count-based conditions to help you control the number of alerts that are generated and the actions that are taken for a given condition. By default, a rule is triggered every time its conditions are met. With conditional triggering, you can now specify how often a rule fires. For example, you can specify that a rule should fire only once in a 15 minute window, or a rule should only fire if the conditions are met a specific number of times in a given time period.

</p><h2>Virtual data points using mathematical operations</h2><p>
</p><p>You can now create virtual data points which are derived from existing data points. In the Message Schema page you can create new virtual data points using mathematical operations such as "+", "-", "\", "*", "(", and ")" to manipulate and combine existing data points. For example, if the device data point ‘temp’ returns a temperature value in Fahrenheit, and you want to use Celsius instead, you can create a virtual data ‘temp_c’ using the mathematical operations to convert Fahrenheit to Celsius, e.g. temp_c=(temp-32)/1.8. Then, you can use the new ‘temp_c’ in your rules instead of the original ‘temp’ value.

</p><h2>On-the-fly rule and action editing</h2><p>
</p><p>To streamline the rule creation process, you can now modify an active rule. For example, you can edit a rule to fine tune the conditions while it is still active, and when you save the rule, it takes effect immediately. To further reduce steps in the rule-making process, you can now create and modify actions directly from the rules editor.

</p><h2>Action metadata customization</h2><p>
</p><p>The BODY component of Webhook and Node-RED actions is now fully customizable in JSON, XML, WWW form URL encoding, and plain text formats. You can also embed dynamic content directly in the BODY field, such as device ID, timestamp, and raw device message to enable more dynamic and reusable actions.

</p><h2>Nested device data points for improved gateway support</h2><p>
</p><p>Real-Time Insights fully supports nested JSON data in device message payloads that follow the IoT Platform specification. These types of payloads are common in gateway devices which aggregate and forward data from several sensors or devices. During schema creation, you can automatically import the nested data points as needed, or you can manually create the nested message schema. Nested data points can be used when you are creating rules as well as dashboards and templates. 

</p><h2>Online API documentation</h2><p>
</p><p>IoT Real-Time Insights API documentation is now available. You can extend your existing applications to manage and update your Real-Time Insights service instance directly through APIs that allow you to create/update/delete rules, actions, and message schemas, as well as retrieve alerts and associated data.

</p><p>Since you made it this far, you get the bonus part of my story--which wasn’t over with that pleasant surprise and great seats. Before the game started, we decided that we’d ‘pay it forward’ and go find some other fans who might enjoy our original seats. So, we went up to the 3rd level of the arena and scoured the stands for a couple of people wearing orange and blue (our team colors). We found a young man of about 12 with his grandfather and gave them our original tickets. Like us, they were pleasantly surprised and took us up on the offer. And the cherry on top? We thoroughly enjoyed the beat down our team delivered to their opponent, and we’re on to round two of the tournament!

</p><p>Go check out Real-Time Insights and give these new features a try! Then let us know what you think—hopefully you’ll be pleasantly surprised!
</p>