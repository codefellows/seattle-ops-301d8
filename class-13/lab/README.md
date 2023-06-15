# Lab: Group Policy

## Overview

Systems administrations can use OUs (Organizational Units) and GPOs (Group Policy Objects) to apply computer configurations to specific departments or teams in the organization. Group policy can be used to protect user data by applying folder redirection to the Windows user files.

## Scenario

After a junior IT support technician accidentally deleted user data yesterday afternoon on a marketing executive's computer, management at GlobeX wishes to know how you intend to backup user profile data on Windows 10 endpoints to prevent such incidents in the future. 

## Prerequisites

- VMs configured in Lab 12:
  - pfSense
    - Configured to assign Windows Server a static IP
    - Configured to share the Windows Server's static IP as the DNS server along with DHCP lease information
   

- VMs configured in Lab 13:
  - Windows Server 2019, promoted to Domain Controller of `corp.globex.com`
    - Users and OUs created in ADAC
  - A Windows 10 endpoint joined to the domain, with a domain user logged in

## Objectives

- Create a GPO that redirects user's Pictures folder to a shared folder on the Windows Server
- Validate the GPO works as expected to replicate a picture file to your Windows Server file share

## Resources

- [Group Policy Planning and Deployment Guide](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754948(v=ws.10)){:target="_blank"}
- [Back to Basics: Groups vs Organizational Units in Active Directory](http://techgenix.com/back-basics-groups-vs-organizational-units-active-directory/){:target="_blank"}
- [Configuring Folder Redirection through Group Policy](https://medium.com/tech-jobs-academy/configuring-folder-redirection-through-group-policy-b38d1faeb833)
- [Video: Folder Redirection with Group Policy](https://www.youtube.com/watch?v=UY2l1uEGGbM){:target="_blank"}

## Tasks

> There are no topology tasks in this lab, since there are no changes to the network configuration or domain status of any of our VMs.

> If you would like to follow along with a video, chekc out [Video: Folder Redirection with Group Policy](https://www.youtube.com/watch?v=UY2l1uEGGbM), linked above in the resources.

### Part 1: File Share

First you'll need to create a file share on Windows Server:

1. In C:\ on the Windows Server, create a folder caller 'GlobexShare' (file path should be `C:\GlobexShare`)

2. To share this folder, go to Properties > Sharing > Advanced Sharing > Permissions, select 'Everyone' and check the 'Full Control' box, then apply the changes

3. Confirm that the share address of this folder is `\\server-name\GlobexShare`, where `server-name` is the computer name of your Windows Server
  
4. Test this file share by accessing `\\server-name\GlobexShare` from the Windows 10 endpoint

### Part 2: GPO Creation

This part uses Group Policy Management Console (GPMC) to create a Group Policy Object (GPO) which will redirect all domain user's Pictures folders to the shared folder on the Windows Server. We will initially test this on users in only one OU before we roll it out to all employees.

1. Open GPMC in the Windows Server and create a new GPO linked to only one of the Organizational Units you created in Lab12 in the `corp.globex.com` domain

2. Open the Group Policy Editor for that new GPO and configure the User's Pictures folder to redirect to the network address of the shared folder you created in Part 1


### Part 2: Policy Push & Testing

Now we will test that our GPO is working as intended, and that it only applies to the users in the OU we link it to. Once we are successful, we will link the GPO to all users in the domain.

1. On your Windows 10 endpoint, run `gpupdate` to apply the the new Group Policy, then log out and log back in as a user from the associated OU for the GPO to take effect

    - Confirm that a folder for that user has appeared in the GlobexShare folder on the Windows Server (you should also see a little green badge on the Pictures folder for that user on the Windows 10 endpoint)

> Note: Group Policies are not applied instantly, but only update periodically, usually every 60-90 minutes. If you're having trouble, trying running `gpupdate /force` on the endpoint, and/or try rebooting instead of just logging in and out.

2. Now try logging in as a user from a different OU -- is a folder created on the Server? Why or why not?

3. If everything else has been successful, link the GPO to the whole domain so that it will apply to all domain users

4. Update the Group Policy on the endpoint and log in to different users until you are satisfied that it is working for users of all OUs

## Submission Instructions

1. Create a new blank Google Doc. Include above assignment submission text and images within this Google Doc.
1. Name the document according to your course code and assignment.
   - i.e. `seattle-ops-201d1: Reading 01` or `seattle-ops-201d1: Lab 04`.
1. Add your name & date at the top of the Google Doc.
1. Share your Google Doc so that "Anyone with the link can view".
1. Paste the link to your Google Doc in the discussion field below and share an observation from your experience in this lab.
