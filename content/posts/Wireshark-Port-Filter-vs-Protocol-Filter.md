---
title: "Wireshark Port Filter vs Protocol Filter"
date: 2024-03-29
url: /Wireshark-Port-Filter-vs-Protocol-Filter/
description:
categories: [Software]
draft: false
---
## Wireshark Port Filter vs Protocol Filter

When analyzing network traffic using Wireshark, it's crucial to understand the difference between the filters to effectively isolate and examine relevant data.

We will discuss on the basis of port 80 filter and  HTTP filter. Because HTTP itself uses the port 80. So, their will be some key difference when using these two filters.

1. **Port Filter:**  For this filter specifically targets traffic on ports. On this case port 80, which is the standard port for HTTP communication. Use this filter when you want to focus solely on TCP connections established on port 80. It captures the entire TCP communication process, including TCP handshakes, acknowledgments, and data transfers. This filter is useful for gaining insights into low-level TCP interactions.


{{< figure src="/images/WPORT80.png" caption="Applying filter for port 80" align="center" >}}

2. **Protocol Filter:** Unlike Port filter the Protocol filter is higher-level and specifically targets a specific protocol. In this case HTTP traffic, irrespective of the port number. It captures HTTP requests and responses, including the payload data exchanged between the client and the server. However, it does not include TCP handshakes or other lower-level TCP details. Use this filter when you're interested in analyzing HTTP traffic at the application layer, focusing on HTTP headers, contents, and responses.

{{< figure src="/images/WPORT80.png" caption="Applying filter for HTTP protocol" align="center" >}}

**When to Use:**
- Use **"tcp.port==80"** when you need detailed insights into TCP interactions, including handshakes, acknowledgments, and data transfers, specifically on port 80.
- Use **http** when you want to focus on HTTP traffic, examining HTTP requests, responses, and payload data, irrespective of the port number.

Some other protocols and ports are:
FTP (File Transfer Protocol) - Port 21
SSH (Secure Shell) - Port 22
SNMP - Port Number: 161 (SNMP), 162 (SNMP traps)
RDP - Port 3389

Understanding these filters' distinctions enables efficient and targeted analysis of network traffic in Wireshark. Some