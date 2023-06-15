# Lab: Domain Controller

## Overview

During deployment of Windows Server one of the first steps is to assign it the correct roles and be promote it to DC (Domain Controller). Once promoted, the DC can not only facilitate centralized identity management with AD (Active Directory), but can also allow the systems administrator to "push" standardized configurations to Windows endpoints using GPOs (Group Policy Objects). Growing companies and enterprises alike will utilize these Windows Server features in order to more effectively administer endpoints at scale.

## Scenario

The GlobeX CEO has requested that endpoint configuration be centrally administered along with other critical services. "I've got sales reps losing customer data to random Windows updates!" he fumes. "This is unacceptable; how does anyone get any work done with these kinds of interruptions? I'm really hoping you can get our computers configured to some kind of standard."

As part of your project to transition GlobeX from Workgroup to Domain, the next step is to configure the new Windows Server so that it can perform these critical roles on the GlobeX network, then start creating users and joining endpoints to the domain.

## Prerequisites

- VMs from Lab12:
  - Windows 2019 Server with DNS enabled
  - pfSense configured to share the Windows Server's static IP as the DNS server along with DHCP lease information
  - Windows 10 endpoint configured with the Windows Server as its DNS

## Objectives

- Add the AD DS role to your Windows Server
- Promote this server to a Domain Controller (DC)
- Add a new forest and create a local domain, `corp.globex.com`, with a NetBIOS of `CORP`
- Join the Windows 10 endpoint to the newly-created domain
- Configure ADAC on the Windows 10 endpoint for use by the systems administrator
- Create user accounts on ADAC
- Create OUs by department
- Sign into the Windows 10 endpoint using each AD profile


## Resources

- [Microsoft Documentation - Install or Uninstall Roles, Role Services, or Features](https://docs.microsoft.com/en-us/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features){:target="_blank"}
- [AD DS Installation and Removal Wizard Page Descriptions](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/deploy/ad-ds-installation-and-removal-wizard-page-descriptions){:target="_blank"}
- [How to create a Windows Domain and AD](https://www.informaticar.net/server-basics-06-how-to-create-windows-domain-active-directory/){:target="_blank"}
- [Microsoft Documentation - Active Directory Administrative Center](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/get-started/adac/active-directory-administrative-center){:target="_blank"}
- [Join Windows 10 to a Domain](https://www.itechguides.com/join-windows-10-to-domain/){:target="_blank"}
- [How to Install And Use Active Directory Administrative Center (ADAC](https://blog.netwrix.com/2023/05/26/how-to-install-active-directory-administrative-center/)

## Tasks

### Part 1: Topology 1

1. In Draw.io, create a copy of your final topology from yesterday's lab to use for today's lab.

2. Then read through the entire lab and use Draw.io to modify the topology of the network to reflect the changes and additions you expect to make. Include details like computer names, OS types, IP Addresses, etc., and also start to include Domain information. Include a screenshot of this initial topology.


### Part 2: Active Directory

1. First, install the Active Directory Domain Services server role on the Windows Server

2. Once installation of AD DS is complete, you'll see an alert in the upper right-hand corner prompting you to promote this server to Domain Controller

    - Select "Add a new forest" and use `corp.globex.com` as the root domain name

    - Set a DSRM password, and record it in your notes

    - Set the NetBIOS name to `CORP`

    - Leave all other setting at their default values, ignore and warnings about DNS, install and reboot

### Part 3: Join Endpoint to Domain

Join your Windows 10 endpoint to the domain. This can be done a number of ways. See this resource for details: [Join Windows 10 to a Domain](https://www.itechguides.com/join-windows-10-to-domain/){:target="_blank"}

- Use the domain name `CORP.GLOBEX.COM`

- Authenticate with the username 'administrator' and the DSRM password you set in Part 2.

### Part 4: AD Profile Creation & Login



1. Optional: in Windows 10, open "Manage optional features" in Settings and install "RSAT: Active Directory Domain Services and LIghtweight Directory Services Tools". This will allow you to manage users and groups remotely from the Windows 10 endpoint instead of from the server itself.

    - Configure ADAC to authenticate into the Windows Server.

2. Using ADAC on either Windows Server or the domain-joined Windows 10 endpoint create the below users with the provided profile information:
  - Francis Hopkins, Sr. Account Executive, Sales Department, GlobeX USA
  - Amanda Williams, HR Specialist, HR, GlobeX USA
  - Jim Sanders, HR Manager, HR, GlobeX USA
  - Rita Morgan, CFO, Finance, GlobeX USA
  - Yourself, Systems Administrator, GlobeX USA

3. Create Organizational Units by department, and move the profiles into the appropriate OU

4. Test that all profiles may login to the Windows 10 endpoint
 
### Part 5: Topology 2

When the other tasks are complete, review the topology and update, revise, extend, or add details as necessary.

Was your initial topology accurate to the finished product? Why or why not?

## Stretch Goals (Optional Objectives)

## Submission Instructions

1. Create a new blank Google Doc. Include above assignment submission text and images within this Google Doc.
1. Name the document according to your course code and assignment.
   - i.e. `seattle-ops-201d1: Reading 01` or `seattle-ops-201d1: Lab 04`.
1. Add your name & date at the top of the Google Doc.
1. Share your Google Doc so that "Anyone with the link can view".
1. Paste the link to your Google Doc in the discussion field below and share an observation from your experience in this lab.
