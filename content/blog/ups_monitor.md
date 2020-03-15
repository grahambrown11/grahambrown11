---
title: "UPS Monitoring"
date: 2020-03-14
draft: false
menu: blog
weight: 1
---
In order to run any computer you need power - so without power your computer is rendered useless, and that effectively renders a modern business dead too.
<!--more-->
An Uninterruptible Power Supply (commonly shortened to UPS) is a device that sits between the power and your computer. 
It has built-in batteries so when the power goes off your computer can still operate until 1 of 2 things happen: the power is restored or the batteries run out of juice.
Recently the latter happened at work where the UPS had lost power due to the circuit breaker tripping and was running on its batteries. We were not aware of this even though the UPS has an annoying beep, when it has no power, it was not heard due to the server room not being 2 stories down from our office space. We only became aware when the batteries ran out of juice, turning it's self off and ironically interrupting the power for our computers.

Most UPS systems have an option to monitor them, so after our incident we needed a solution to monitor our UPS.
The UPS we have is not a well known brand - PowerWise+ it's from a company in our area EDSUPS, it came with UPSilon 2000 software which is made for Windows computers. We have an HP server running virtual machines all Linux based, so no Windows to the provided software. I searched the web and found
[Network UPS Tools (NUT)](networkupstools.org) and with a little time tinkering we now have a notification in Slack when the power is lost, restored and the batteries are low.

Many of the Linux distributions have a package for NUT, so its pretty easy to install. We run Ubuntu so `sudo apt-get install nut` got the software installed. Below are some of the settings and a script to setup NUT for our UPS and send the Notifications to Slack.

1. Set the mode to `standalone` in `/etc/nut/nut.conf`
1. Add the UPS in `/etc/nut/ups.conf`
{{< gist grahambrown11 08867dc72bba22982edce042f8eeabe4 "ups.conf" >}}
1. Add a user to monitor the UPS in `/etc/nut/upsd.users`
{{< gist grahambrown11 08867dc72bba22982edce042f8eeabe4 "upsd.users" >}}
1. Setup the monitor, messages and command in `/etc/nut/upsmon.conf`
{{< gist grahambrown11 08867dc72bba22982edce042f8eeabe4 "upsmon.conf" >}}
1. Add the shell script to send the slack `/usr/local/bin/upsnotiftyslack` (make sure it is executable `chmod +x /usr/local/bin/upsnotiftyslack`)
   Follow the instructions for the [Slack Webhook](https://api.slack.com/messaging/webhooks), we have the Legacy webhook were you can specify the channel, not sure if you can do that anymore...
{{< gist grahambrown11 08867dc72bba22982edce042f8eeabe4 "upsnotiftyslack.sh" >}}
1. Here is the result in Slack<br>![Slack Post](/images/blog/UPS%20Slack%20Post.png)
