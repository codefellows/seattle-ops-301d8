# Lab: Windows Server and Domain Controller

## Overview

Microsoft Windows Server is an OS that facilitates the hosting of critical authoritative Windows services on the network, including Active Directory, DNS, DHCP, and Domain Controller roles. Microsoft's Evaluation Center allows for the use of Windows Server for 180 days free with full functionality. When deployed in tandem with Windows 10 Pro endpoints, once can establish a domained LAN with little more than VirtualBox and some relevant Microsoft documentation.

## Scenario

After performing your initial survey of GlobeX systems, you gather that the company mostly runs virtual Windows 10 Professional 64-bit endpoints. However, GlobeX computer systems are inconsistently configured, resulting in a high rate of data loss, regulatory compliance violations and operational dissatisfaction. Your task is to deploy Windows Server to the LAN so that the process of migrating from Workgroup to Domain can begin.

## Prerequisites

- A pfSense VM in VirtualBox, free from configuration settings from previous labs
- A user endpoint VM in VirtualBox (any existing Windows 10 or Linux VM)

## Objectives

- Deploy Windows Server 2019 as a VM to your local VirtualBox Manager and add it to your network
- Assign the VM a static IP using DHCP reservation on your pfSense VM
- Verify connectivity from Windows Server to Windows 10 and to the internet
- 
- Create a professional network topology diagram that reflects your current deployments

## Resources

- [Windows Server 2019 ISO Download](https://www.microsoft.com/en-US/evalcenter/evaluate-windows-server-2019?filetype=ISO){:target="_blank"}
- [Windows 10 ISO Download](https://www.icloud.com/iclouddrive/01azgWsJOfzZaBbAj-G3sLWTg#Windows10){:target="_blank"}
- [AD DS Installation and Removal Wizard Page Descriptions](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/deploy/ad-ds-installation-and-removal-wizard-page-descriptions){:target="_blank"}
- [Microsoft Documentation - Install or Uninstall Roles, Role Services, or Features](https://docs.microsoft.com/en-us/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features){:target="_blank"}
- [How to create a Windows Domain and AD](https://www.informaticar.net/server-basics-06-how-to-create-windows-domain-active-directory/){:target="_blank"}

## Tasks

Today you'll be deploying Windows Server 2019 as part of the project to transition GlobeX from Workgroup to Domain on its network.

### Part 1: Topology 1

Read through the entire lab and use Draw.io to create an appropriate topology of the network you expect to construct. Include as many details as you can such as computer names, OS types, IP addresses, etc. Include a screenshot of this initial topology.

### Part 2: Staging

Submit detailed documentation regarding all of the configurations in this section.

1. First you will need a fresh pfSense VM, free from configuration settings from previous labs. You can reset an existing instance to factory settings (Diagnostics / Factory Defaults), revert to a baseline snapshot, import a fresh instance from a baseline OVA backup, or by installing pfSense on a new VM. However you achieve this, it is important to start from a clean baseline to avoid complications.

    - On the pfSense VM, configure the WAN network adapter to NAT Network and the LAN adapter to Internal Network.

2. Second you will need a Windows 10 endpoint VM.

    - On the Windows 10 VM, configure the network adapter to match the LAN adapter of pfSense (should be set to the same Internal Network).
    
3. Third, deploy a new Windows Server 2019 VM.

    - Create a new VM. Document the CPU, RAM, and storage allocations you've made to this VM.

        - Configure the network adapter to match the LAN adapter of pfSense (should be set to the same Internal Network).

    - Download the [Windows Server 2019 ISO](https://www.microsoft.com/en-US/evalcenter/evaluate-windows-server-2019?filetype=ISO) to your lab computer and install the OS on the VM.

        - During installation, select "Windows Server 2019 Standard Evaluation (Desktop Experience)"

### Part 3: Network Connectivity, Configuration, and updates

Now we are going to configure our Windows Server 2019 VM on the Network.

1. Connect to pfSense from your Windows 10 VM and confirm that the Windows Server has been assigned an IP address by checking Status / DHCP Leases. Document both the DHCP range in pfSense and the current leases.

2. Next, assign the Windows Server 2019 VM a static IP using DHCP reservation on your pfSense VM. Document the reserved IP you've allocated to the server.

    - Why did you choose this IP, and what are your plans for future reserved IPs on this subnet?

3. Verify connectivity from Windows Server to Windows 10.

4. Disable enhanced security feature on Internet Explorer in Windows Server.

5. Verify internet connectivity on Windows Server using its Internet Explorer/Edge browser.

6. Perform Windows Update on the server until it is fully patched to latest possible version.

7. At this point, take a snapshot of your VM and export an OVA backup. Document where you have saved this backup and what you have named it.

### Part 4: DNS

Activate roles:
- DNS
- AD DC



In order for AD and DC to function properly, we'll need to configure Windows Server to act as the DNS server for this LAN instead of pfSense. Ideally, pfSense should be configured to be aware that Windows Server's IP address is the DNS of this network.

- First, activate the DNS role on Windows Server using Server Manager.
- Next, you'll need to point your network hosts to it as their DNS server. Configure pfSense to assign the DNS server for LAN hosts to use this Windows Server's IP address if possible; otherwise, you can manually assign DNS server IP via the Windows Server/Windows 10 network adapter settings.
- Verify that all devices have working DNS through Windows Server and can browse the internet.
- Test your DNS is working by applying a forward lookup zone. Create a new forward lookup that causes http://admin.globexpower.com to resolve as the IP address of pfSense.

### Part 5: Active Directory

Activate AD DS role on Windows Server.

- Install server roles:
  - Active Directory Domain Services.
- Promote this server to a Domain Controller.
- Add a new forest. It's OK if your forest only has one tree.
  - Create a local domain using `corp.globexpower.com` as the root domain name.
- Set a DSRM password.
- Set the NetBIOS name to `CORP`.

### Part 6: Topology 2

When the other tasks are complete, review the topology and update, revise, extend, or add details as necessary.

Was your initial topology accurate to the finished product? Why or why not?

## Submission Instructions

1. Create a new blank Google Doc. Include above assignment submission text and images within this Google Doc.
1. Name the document according to your course code and assignment.
   - i.e. `seattle-ops-201d1: Lab 04`.
1. Add your name & date at the top of the Google Doc.
1. Share your Google Doc so that "Anyone with the link can view".
1. Paste the link to your Google Doc in the discussion field below and share an observation from your experience in this lab.
