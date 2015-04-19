---
layout: post
title: "use virsh change virtual network mode to bridge mode"
date: 2015-04-19 01:23
comments: true
tags: web
categories: english
---
Use virsh change default virtual network mode to bridge mode

First Enable KVM support in BIOS

Second follow Ubuntu’s ServerGuide to install kvm environment

Use default virt-install command in ServerGuide to create a “domain”, but its network is configured to connect to virtual network, while what I want is to use bridge mode. Because in bridge mode the ip address of virtual machine will be in the same subnet as host machine.

Under bridge mode, the virtual machine and host machine connect to the same physical network.

After some experiments, I made it with:

 *   shutdown domain
 *   create a bridge with virsh command “virsh iface-bridge <interface> <bridge>"

>     virsh inface-bridge p2p1 bridge-p2p1

 *   change domain’s configuration with virsh command “virsh edit <domain>"

>     ~$ diff *.xml
>     41c41
>     >     <interface type='network'>
>     ---
>     <     <interface type='bridge'>
>     43c43
>     >       <source network='default'/>
>     ---
>     <       <source bridge='bridge-p2p1'/>

 *   start domain again
