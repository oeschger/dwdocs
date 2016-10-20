---
ID: 3033
post_title: 'Create new custom Device Management actions [Beta]'
author: bkufluk
post_date: 2016-06-14 13:42:17
post_excerpt: ""
layout: post
permalink: >
  https://nextstage.torolab.ibm.com/iotplatform/2016/06/14/create-new-custom-device-management-actions-beta/
published: true
---
I'm pleased to announce that you can now add custom device management actions in the IBM Watson IoT Platform.  <br /><h2>What's new? </h2>In addition to the four device management actions supported by the platform; Download Firmware, Update Firmware, Reboot and Factory Reset, you can now extend the platform to support additional actions.   <br /><br /><a href="http://nextstage.torolab.ibm.com/iotplatform/wp-content/uploads/sites/24/2016/06/4devicemgmtactions.jpg"><img src="http://nextstage.torolab.ibm.com/iotplatform/wp-content/uploads/sites/24/2016/06/4devicemgmtactions.jpg" alt="4devicemgmtactions" width="649" height="472" class=" wp-image-3075 size-full aligncenter" /></a><br />For example if your gateway or device supports additional actions that let you change and update packages or plugins, enable and disable features (or anything else!), you can tell the platform what those features are so that they can be enabled as additional actions.  <br /><h2>How does it work?</h2>
<p>The platform needs to understand what the new actions are, and what it should do when they are invoked.  That's defined in a file in Json format called a <em>device management extension package.</em> <br />The short extract below shows an example defining a new action called <strong>Install Plug-in</strong> with two parameters <em>pluginId</em> and <em>pluginURI.  </em></p>

<pre>        "version": "1.0",
        "provider": "some company",
        "actions": {
                "installPlugin": {
                        "actionDisplayName": {
                                "en_US": "Install Plug-in"
                        },
                        "description": {
                                "en_US": "Install a new plug-in on the device"
                        },
                        "parameters": [
                                {
                                        "name": "pluginId",
                                        "value": "\\w+",
                                        "required": true
                                },
                                {
                                        "name": "pluginURI",
                                        "value": "((http:\\/\\/|https:\\/\\/)(.*)+)",
                                        "required": true
                                }
                        ]
                }
</pre>
<p>See the <a href="https://docs.internetofthings.ibmcloud.com/devices/device_mgmt/custom_actions.html">full documentation</a> to get the full syntax including a complete example.<br /><br />The <em>device management extension package</em> needs to be loaded into the platform, either through the API or from the settings page of the Platform dashboard.  <br /><br /><em><a href="http://nextstage.torolab.ibm.com/iotplatform/wp-content/uploads/sites/24/2016/06/devicemgmtsettings.jpg"><img src="http://nextstage.torolab.ibm.com/iotplatform/wp-content/uploads/sites/24/2016/06/devicemgmtsettings.jpg" alt="devicemgmtsettings" width="832" height="299" class="aligncenter size-full wp-image-3080" /></a></em><br />Once the extension is loaded then the new device actions become available, both from the API or from the UI.  <br />Actions are grouped, with the original four actions in two preloaded groups called device actions and firmware actions.  <br /><a href="http://nextstage.torolab.ibm.com/iotplatform/wp-content/uploads/sites/24/2016/06/groups.jpg"><img src="http://nextstage.torolab.ibm.com/iotplatform/wp-content/uploads/sites/24/2016/06/groups.jpg" alt="groups" width="575" height="94" class="aligncenter size-full wp-image-3081" /></a>Selecting the new group shows us the new available actions: <br /><a href="http://nextstage.torolab.ibm.com/iotplatform/wp-content/uploads/sites/24/2016/06/newactions.jpg"><img src="http://nextstage.torolab.ibm.com/iotplatform/wp-content/uploads/sites/24/2016/06/newactions.jpg" alt="newactions" width="734" height="559" class="aligncenter size-full wp-image-3082" /></a><br />If you select an action, you'll be prompted to select which devices the action should be executed against.  Only those devices that support the action will appear in the list.  Devices have to use the device management API to tell the system that they are 'managed' and support the different device management actions. <a href="http://nextstage.torolab.ibm.com/iotplatform/wp-content/uploads/sites/24/2016/06/selectdevices.jpg"><img src="http://nextstage.torolab.ibm.com/iotplatform/wp-content/uploads/sites/24/2016/06/selectdevices.jpg" alt="selectdevices" width="739" height="227" class="aligncenter size-full wp-image-3085" /></a><br />In this example I pick myNewPi to execute the action against.  <br />The system prompts me to enter the parameters that we saw earlier in the extension package file: <br /><br /><a href="http://nextstage.torolab.ibm.com/iotplatform/wp-content/uploads/sites/24/2016/06/specfiyparms.jpg"><img src="http://nextstage.torolab.ibm.com/iotplatform/wp-content/uploads/sites/24/2016/06/specfiyparms.jpg" alt="specfiyparms" width="742" height="354" class="aligncenter size-full wp-image-3084" /></a><a href="http://nextstage.torolab.ibm.com/iotplatform/wp-content/uploads/sites/24/2016/06/selectdevices.jpg"></a>Then the action is initiated.  We can see the progress of all actions in the actions view.  <br /><br /><a href="http://nextstage.torolab.ibm.com/iotplatform/wp-content/uploads/sites/24/2016/06/actionsview.jpg"><img src="http://nextstage.torolab.ibm.com/iotplatform/wp-content/uploads/sites/24/2016/06/actionsview.jpg" alt="actionsview" width="1098" height="536" class="aligncenter size-full wp-image-3086" /></a></p><h2>How can I try it? </h2><p>We have a developer tool that you can use connect to your IoT organisation and simulate a device.  Once you've connected, you can use the simulator to make the device managed, and select which custom actions the device supports.  In the tool you can see the communications between the device and the platform.  <br /><br />
Find the simulation tool here:  <a href="https://device-mgmt-demo.mybluemix.net/" target="_blank">https://device-mgmt-demo.mybluemix.net/<br /></a>
</p><h2>What next?</h2><p>
See the<a href="https://docs.internetofthings.ibmcloud.com/devices/device_mgmt/custom_actions.html" target="_blank"> full documentation for device management custom actions.</a>  <br /><br />This feature is in Beta, which means that we're interested in your feedback - <a href="https://nextstage.torolab.ibm.com/answers/smartspace/internet-of-things/">please let us know what you think</a>! </p>