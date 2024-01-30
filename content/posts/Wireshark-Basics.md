---
title: "Wireshark Basics"
date: 2023-10-10
url: /Wireshark-Basics/
description:
categories: [Software]
draft: true
---

## What is wireshark!

Wireshark is an open-source network protocol analyzer that may be used to monitor and analyze network traffic. It enables users to collect and analyse data packets as they transit across a network, providing vital insights into network behavior and assisting with network problems.

Wireshark allows users to study packet headers and payloads, assisting in the identification of communication issues, security concerns, and performance bottlenecks. The tool is versatile for both wired and wireless networks because it supports a wide range of network protocols. Furthermore, Wireshark provides a variety of filtering and visualization options, making it easy to concentrate on specific network segments or categories of information.

## Important commands for wiresharks to remember

1. `ip.addr==1.1.1.1`
	This will filter the network and only show result containing that ip address. Whether it is on source or destination it will show the result.
2. `ip.scr==1.1.1.1`
	This will show results when the mentioned ip is only found in source.
3. `ip.dst==1.1.1.1`
	This will show results when the mentioned ip is only found in destination.

*If you want to do the same but for ipv6 all you need to do is ipv6.scr/addr/dst*
Same can be acheived if you drag and drop the ip into the field.