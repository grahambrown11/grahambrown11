---
title: "Business Continuity in the COVID-19 pandemic"
date: 2020-03-18
draft: false
menu: blog
weight: 1
---
COVID-19 has forced many businesses to act on their continuity plans. Fortunately, as we operate mostly online we were able to execute a plan with relative ease. 
<!--more-->
Ramaphosa addressed South Africa this weekend announcing a "National State of Disaster" due to "Internal Transmission" of the virus occurring. Although the rules put in place don’t specifically require businesses to close their doors, there are concerned employees so many businesses are exercising some sort of continuity plan to allow them to work from home. Not only will this help reduce the anxiety of the concerned employees, it will limit contact with others and hopefully reduce the infection rate curve.

Most of our computers at Different Life are Google Chromebooks as everything we do is “web” based. However not all our systems are available on the Internet for security reasons. Our continuity plan catered for accessing those internal systems but did not specifically address a scenario where all staff are isolated, but we’ve managed to find a solution for them to work from home - here’s how:
Installing a VPN Server at the office
Setting up VPN Clients on their computers

VPN is an acronym for Virtual Private Network it creates a secure connection from the users computer to the company network so you can continue to work as if you were located at the office. There are many software and hardware options available for creating a VPN. We use [Pritunl](https://pritunl.com/) (pronounced pri-tunnel), which is a nicely wrapped version of OpenVPN, with both a free or paid option. We use the free version to access servers for remote support which has worked well for that. The office VPN for all the staff remote is not an ongoing requirement, so we opted to use the free version for that too. Setting up the VPN Server was a breeze, however there was a hurdle setting up the Chromebooks.

Chromebooks come with a built-in OpenVPN client, but setup is complex requiring certificates and other details and also lacks an import function. Fortunately there is a hidden option to import an [Open Network Configuration](https://chromium.googlesource.com/chromium/src/+/master/components/onc/docs/onc_spec.md) in ChromeOS and caters for VPN configuration. So I wrote a bash script that can download the profile from the temporary links Pritnul generates and creates an ONC file. This file can be imported at the special URL chrome://net-internals/#chromeos, which made setting up the Chromebooks easier.

{{< gist grahambrown11 cee9cfeb53ea2d76eb000bef1014c8b4 "convertvpn.sh" >}}

Our continuity is now in place with the majority of our staff working from home. I hope my experience can help your continuity plan.
