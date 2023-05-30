# Lab: Network Address Translation

## Overview

NAT (Network address translation) is a technique performed by routers whereby the IP address in a packet header is altered in transit so that the destination interprets the packet as coming from the new IP instead of the actual originating IP. One-to-many NAT has played a vital role globally in delaying [IPv4 address exhaustion](https://en.wikipedia.org/wiki/IPv4_address_exhaustion){:target="_blank"}, greatly reducing the need to transition at a large scale to IPv6.

In network administration, you may encounter sub-optimal situations where two LANs share the same network addressing scheme. For example, the 192.168.1.1/24 network address is extremely common amongst consumer grade routers. 1:1 NAT can offer a workaround for this kind of issue.

## Scenario

GlobeX has made a strategic acquisition and needs to share resources over a VPN tunnel. However, your manager wishes to obfuscate the corporate network architecture for security reasons. You've been tasked with working up a proof of concept as to how GlobeX can conceal the IP addresses of critical resources such as Windows Server.

## Prerequisites

- Two networks with pfSense at the edge, connected via IPsec VPN
- Windows Server in the corporate network
- Windows 10 in the corporate network
- Windows 10 in the external network

## Objectives

- Share a folder from Windows Server and test normal accessibility both from same LAN and from external network
- Create a 1:1 NAT rule that alters the IP address of the Windows Server for hosts accessing it from over the VPN tunnel
- Use 1:1 NAT to access the Windows Server shared folder from Windows 10 (external) without using Windows Server's real local IP address

## Resources

- [Netgate Docs - 1:1 NAT](https://docs.netgate.com/pfsense/en/latest/nat/1-1.html){:target="_blank"}
- [Troubleshooting NAT](https://docs.netgate.com/pfsense/en/latest/troubleshooting/nat.html){:target="_blank"}
- [Troubleshooting NAT 1:1](https://docs.netgate.com/pfsense/en/latest/troubleshooting/nat-1-1.html){:target="_blank"}
- [Troubleshooting NAT Port Forwards](https://docs.netgate.com/pfsense/en/latest/troubleshooting/nat-port-forwards.html){:target="_blank"}

## Tasks

### Part 1: Staging the Networks

This lab requires that you've established a VPN tunnel between two pfSense networks in VirtualBox.

- Share a folder on Windows Server.
- From Windows 10 (internal), access the shared folder. Create a file. Include a screenshot of this operation.
- From Windows 10 (external), access the shared folder via VPN. Create a file. Include a screenshot of this operation.

### Part 2: Configuring the Networks

Now that we have established normal comms between the networks, and know that the file share is working, let's start experimenting with NAT. We can use a 1:1 NAT rule in pfSense to convert the IP address of our Windows Server for VPN users.

- In pfSense, utilize 1:1 NAT to convert the file server IP to a different IP if accessed via VPN tunnel.
- To accomplish this, you may need to configure other areas of pfSense such as Advanced Outbound NAT. Read up on documentation to explore how this can be achieved.
- Include a screenshot of your configuration.

### Part 3: Testing

Now let's test and verify that the NAT is translating the IP address correctly and that we can access the shared folder from Windows 10 (external).

- Mount the file share on Windows 10 (external).
- Include a screenshot of successfully accessing the file share in Windows Explorer.

### Part 4: Topology

Update your network topology diagram with any changes made to your network.

## Submission Instructions

1. Create a new blank Google Doc. Include above assignment submission text and images within this Google Doc.
1. Name the document according to your course code and assignment.
   - i.e. `seattle-ops-201d1: Lab 04`.
1. Add your name & date at the top of the Google Doc.
1. Share your Google Doc so that "Anyone with the link can view".
1. Paste the link to your Google Doc in the discussion field below and share an observation from your experience in this lab.
