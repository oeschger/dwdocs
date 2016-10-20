---
ID: 1
post_title: >
  Controlling Drones with the Internet of
  Things
author: Dr M Bradley
post_date: 2014-04-09 14:40:22
post_excerpt: ""
layout: post
permalink: >
  https://nextstage.torolab.ibm.com/iotplatform/2014/04/09/hello-world/
published: true
---
At the M2M Hackathon earlier this year some of the team had the pleasure of hooking up quadracopter Drones to the Internet of Things.

<img src="http://nextstage.torolab.ibm.com/iot/wp-content/uploads/sites/24/2014/04/tumblr_inline_mwxczu60MF1sp6j3f.png" alt="tumblr_inline_mwxczu60MF1sp6j3f" width="423" height="750" class="alignright size-full wp-image-164" />

Here is the requisite video footage of them controlling the drone having hacked it! <a href="http://www.youtube.com/watch?v=j5QSK9UJvcA" title="http://www.youtube.com/watch?v=j5QSK9UJvcA">http://www.youtube.com/watch?v=j5QSK9UJvcA</a>

<b>Step 1</b> getting to pilot your drone through the power of code!

Actually this is easier than you’d think, especially with the deliciously hackable Parrot AR Drone and some node.js wizardry.

First, get node.js up and running here: <a href="http://nodejs.org/download" title="http://nodejs.org/download">http://nodejs.org/download</a>

Next install these awesome node.js libraries using the node package manager (npm) by running this command from your command line:

<code>$ npm install ar-drone</code>

You can read all about the AR-Drone node.js package in git hub, and if you’re a bit old skool when it comes to installing node.js packages you can do that here too, just here…

<a href="https://github.com/felixge/node-ar-drone" title="https://github.com/felixge/node-ar-drone">https://github.com/felixge/node-ar-drone</a>

Cool. So now you have the ability to access your Drones’ brain directly with javascript! (If only hacking brains was this easy for everything!)

Now, get your Drone ready (put battery in, wait for the blades to twitch and the lights to turn green). Wirelessly connect your laptop to the little fella and step back a bit.

To get a handle to your drone put these lines of javascript in your code…

<code>vararDrone=require('ar-drone');
var maDrone =arDrone.createClient();</code>
 
<a href="http://nextstage.torolab.ibm.com/iot/wp-content/uploads/sites/24/2014/04/tumblr_inline_mwxd124NJQ1sp6j3f.jpg"><img src="http://nextstage.torolab.ibm.com/iot/wp-content/uploads/sites/24/2014/04/tumblr_inline_mwxd124NJQ1sp6j3f.jpg" alt="tumblr_inline_mwxd124NJQ1sp6j3f" width="500" height="667" class="alignleft size-full wp-image-172" /></a>
Now you can issue commands to maDrone to get your Drone to do stuff. 
 
Like…

<code>Take off and hover - maDrone.takeoff();<br>Rotate clockwise (speed 0..1) - maDrone.clockwise(0.5);<br>Rotate counterclockwise (speed 0..1) - maDrone.counterclockwise(1);<br>Descend and land - maDrone.land();<br>Stop moving and hover in place - maDrone.stop();<br>Ascend (speed 0..1) - maDrone.up(0.2);<br>Descend (speed 0..1) - maDrone.down(0.3);<br>Roll left (speed 0..1) - maDrone.left(0.3);<br>Roll right (speed 0..1) - maDrone.right(0.3);<br>Pitch forward (speed 0..1) - maDrone.front(0.3);<br>Pitch back (speed 0..1) - maDrone.back(0.3);<br>Recover from a crash landing by resetting the drone - maDrone.disableEmergency();<br>Make the lights flash (pattern, frequency, duration) - maDrone.animateLeds('blinkRed', 5, 2)</code>

If you’re fortunate enough to have the newer 2.0 Drone, you can also do flips as follows:
 
<code>maDrone.animate('flipLeft', 1000);</code>
 
The full developer guide for Parrot AR Drone can be found here:
 
<a href="http://nodecopter.com/hack#connect-to-access-point" title="http://nodecopter.com/hack#connect-to-access-point">http://nodecopter.com/hack#connect-to-access-point</a>
<a href="https://projects.ardrone.org/attachments/download/365/ARDrone_SDK_1_7_Developer_Guide.pdf" title="https://projects.ardrone.org/attachments/download/365/ARDrone_SDK_1_7_Developer_Guide.pdf">https://projects.ardrone.org/attachments/download/365/ARDrone_SDK_1_7_Developer_Guide.pdf</a>
 
To start simple try…
 
<code>vararDrone=require('ar-drone');
var maDrone =arDrone.createClient();
 
maDrone.takeoff();
 
maDrone
.after(5000, function() { this.clockwise(0.5); })
.after(3000, function() { this.stop(); this.land(); });</code>
 
Want your Drone to get social? Here’s how to get your drone to tweet what it’s up to. First get the twit package.

<code>$ npm install twit</code>

And then, use the following code to report your Drone’s activity each time you call the droneReport function. Note: You’ll need to go to Twitter’s developer site and set up tokens for your application.

<a href="https://dev.twitter.com/docs/auth/tokens-devtwittercom" title="https://dev.twitter.com/docs/auth/tokens-devtwittercom">https://dev.twitter.com/docs/auth/tokens-devtwittercom</a>

Once you get the tokens set up, make sure to go into the settings and change the access control to Read & Write so you can post as well as read tweets. Then copy and paste your key, token and secret codes into your code between the quote marks below. 
 
<code>var Twit = require('twit');
var T = new Twit({
    consumer_key:         '....',
    consumer_secret:      '....',
    access_token:         '....',
    access_token_secret:  '....'
  });</code>
 
Now you can post to your twitter account using the .post function. For my script I made a little function called droneReport to mirror the tweets to the console and add some text at the start of each tweet so it’s clear they can from my Drone.

<code>function droneReport (msg) {
        //T.post('statuses/update', { status: 'My Drone: '+ msg }, function(err, reply) { });
        console.log ("Tweeted: " + msg);
}
T.post('statuses/update', { status: droneMsg }, function(err, reply) {
  //  ...
})</code>
 
Cool. So now you’ve got an automated, tweeting drone!
Enjoy. I know the team did :-)


Great articles on flying drones:
<a href="http://nodecopter.com/hack" title="http://nodecopter.com/hack">http://nodecopter.com/hack</a>
<a href="https://github.com/felixge/node-ar-drone" title="https://github.com/felixge/node-ar-drone">https://github.com/felixge/node-ar-drone</a>