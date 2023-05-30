# Lab: Traffic Mirroring

## Overview

Configuring the network for optimal visibility by security tools is essential in the modern era. One method involves duplicating or "mirroring" network traffic to a sniffing tool. This allows the tool to monitor all traffic passing through the mirrored interface.

## Scenario

After the network intrusion incident, the GlobeX MSSP, Secutronix, performed and in-depth review of GlobeX's primary LAN subnet and determined additional security measures would be necessary to detect such a threat in the future. Secutronix is about to deploy a new IDS (Intrusion Detection System) on the GlobeX network, but they're requesting that a "span port" be created that will mirror all traffic on the primary subnet interface.

## Objectives

- Create a span port on pfSense that mirrors the traffic from the LAN network interface
- Configure Kali Linux so that it can capture traffic on a dedicated sniffing port
- Live-capture LAN traffic using Wireshark on Kali Linux

## Resources

- [pfSense Docs - Interface Bridges](https://docs.netgate.com/pfsense/en/latest/bridges/index.html){:target="_blank"}

## Tasks

### Part 1: Setup

First, we need to configure network devices on pfSense and Kali so that they have a sort of 'back door' between each other.

- On both pfSense and Kali, enable an extra network interface
  - Set the interface to Internal Network
  - Change the name of the Internal Network to `span`
  - Set Promiscuous Mode to Allow All
- We will also need another VM on pfSense's LAN (we will need this machine to generate traffic for us to capture)

### Part 2: Prepare a Span Port on pfSense

We want pfSense to mirror all LAN traffic to this connection

- In Interfaces > Assignments, add a new interface
- Configure the new interface
  - Enable the interface and give it an appropriate name
- In Interfaces > Assignments, move to the Bridges tab and add a bridge with the following configuration:
  - Member Interfaces: LAN
  - Span Port: whatever interface you just created (neither WAN no LAN)


### Part 3: Capture Packets with Kali

Now we will use Wireshark on Kali to sniff for network traffic on the `span` connection.

- Make sure another VM is connected on the LAN, and use it to ping `scanme.nmap.org`
  > Hint: you can make Windows 10 ping continuously by adding a `-t` flag, as in `ping scanme.nmap.org -t`
- On Kali, set Wireshark to capture traffic on the interface associated with the `span` connection we set up earlier
- Include a screenshot of pings out to `scanme.nmap.org` captured in Wireshark

### Part 4: Questions

- On pfSense, navigate to the Dashboard, and locate the list of active interfaces
  - Does the interface you created have an IP address?
- Disable all network devices on Kali *except* the `span` port connection
  - Does the traffic capture still work?
  - Why might you want to disconnect a sniffing machine in this way?
- On Kali, run
  ```
  sudo dhclient -r
  sudo dhclient
  ip a
  ```
  - Does Kali have any IP addresses?
- If niether Kali nor pfSense have an IP address on the `span` port connecting them, how is traffic being sent from pfSense and reaching Kali?

## Submission Instructions

1. Create a new blank Google Doc. Include above assignment submission text and images within this Google Doc.
1. Name the document according to your course code and assignment.
   - i.e. `seattle-ops-201d1: Reading 01` or `seattle-ops-201d1: Lab 04`.
1. Add your name & date at the top of the Google Doc.
1. Share your Google Doc so that "Anyone with the link can view".
1. Paste the link to your Google Doc in the discussion field below and share an observation from your experience in this lab.
