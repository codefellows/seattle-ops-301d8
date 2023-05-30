# Lab: Web Server Deployment

## Overview

Infrastructure deployment is an important role for the systems administrator. Public-facing infrastructure such as web servers present unique security and operational challenges compared to endpoints. Configuring a web server requires an understanding of firewall, networking design, network protocols, and security practices.

## Scenario

GlobeX HR division wants to launch a new employee information website. This website will be public-facing, as it does not contain sensitive information, but rather helpful information about the various services available to employees. You've joined the project team and are tasked with standing up some prototype infrastructure for the web developer to work with. "All I know is Wordpress!" the web developer exclaims. "If you can get me a web server and remote access to it, I'll be all set to begin front-end development."

## Objectives

- Deploy an NGINX web server on Linux Server behind pfSense
- On pfSense, setup port forwarding to route traffic on ports 8000 to the web server
- Create firewall rule exceptions for port 8000 and 22
- Add SSH and open up port 22 for administration purposes
- Deploy UFW firewall and activate it
- Allow correct traffic through pfSense
- Test and validate access using a computer on the other side of the pfSense firewall
- Submit an updated network topology

## Resources

- [Ubuntu Server Download](https://ubuntu.com/download/server){:target="_blank"}
- [Ubuntu Official Documentation - Install NGINX](https://ubuntu.com/tutorials/install-and-configure-nginx#1-overview){:target="_blank"}
- [PfSense Port Forwarding](https://serverspace.io/support/help/routing-in-pfsense-port-forwarding/){:target="_blank"}

## Tasks

### Part 1: Ubuntu Server VM Deployment

First you'll need to create a new VM behind pfSense. This will be a Linux system hosting NGINX.

- Download the Ubuntu Server ISO.
- Create a new VM in VirtualBox.
  - Specify the network adapter to connect to your pfSense using the "Internal Network" option.
- Install the latest version of Ubuntu Server.
  - Install OpenSSH during the OS installation process.
- Reboot when installation is complete.
- Connect to the server's CLI, either by shelling in from Kali or another VM on the same network as the server, or by using the VirtualBox display.

### Part 2: NGINX Web Server Setup

In this step, you'll deploy an NGINX web server on Linux Server behind pfSense.

Complete the following steps:

1. Install NGINX:

     ```
     sudo apt update
     sudo apt install nginx
     ```

2. Creating our own website:

     ```
     cd /var/www
     sudo mkdir globex
     cd globex
     sudo touch index.html
     ```

3. Code the new web page:
  
     - Open the html file for editing using nano (`sudo nano index.html`) and copy the following to the `index.html` file:

     ```
     <!doctype html>
     <html>
     <head>
         <meta charset="utf-8">
         <title>Hello via Nginx!</title>
     </head>
     <body>
         <h1>Hello via Nginx!</h1>
         <p>We have just configured our Nginx web server to serve HTML on Ubuntu Server!</p>
     </body>
     </html>
     ```

 4. Set up virtual host:
  
     ```
     cd /etc/nginx/sites-enabled
     sudo touch globex
     sudo nano globex
     ```
     
     - Once you've opened the `globex` file, copy in the following:

     ```
     server {
            listen 8000;
            listen [::]:8000;

            server_name employees.globex.com;

            root /var/www/globex;
            index index.html;

            location / {
                     try_files $uri $uri/ =404;
            }
      }
     ```

  5. Activate virtual host and test results:

     - Check to see that nginx is running 
      `sudo systemctl status nginx`
     - If it is not running, start it with:
      `sudo systemctl start nginx`
     - Open up ports 22, 8000 on UFW.
       - Activate the Ubuntu Server's UFW.
       - Include a screenshot of UFW settings while you're shelled into Ubuntu Server.
     - Test that your webpage is available by navigating to `http://<ip of NGINX server>:8000` on a VM on the same subnet as the webserver.
       - It should should show "Hello via Nginx!" as its headline. Include a screenshot.
     
  6. Load the Globex website files:

     - Clone the class repo to the home directory of your Ubuntu Server.
     - Recursively copy the assets from class-07/starter-code folder to `/var/www/globex`.
       - This will overwrite the `index.html` file you created in step 3.
     - Access the web page using a browser (remember we used port 8000) and include a screenshot.

### Part 3: Configuring pfSense

Now that the web server is deployed, you'll need to configure the pfSense perimeter to redirect inbound HTTP requests to the new VM's IP address.

- Set your pfSense's WAN interface to NAT Network on VirtualBox.
- Login to pfSense web UI and navigate to Interfaces > WAN. Scroll to the bottom and set *Block private networks and loopback addresses* and *Block bogon networks* to disabled. These default firewall rules clash with our VirtualBox NAT Network configuration.
- Determine the web server's MAC address and add a static DHCP mapping to pfSense for the NGINX web server.
- In Firewall > NAT, configure pfSense to route incoming HTTP requests on WAN port 80 to the NGINX web server port 8000.
- Now that the web server has been deployed we can access the web server from outside the network on a device that's also set to NAT Network.

### Part 4: Testing

- Identify your pfSense's WAN address on its main dashboard screen towards the bottom right. You'll need it for the upcoming step.
- Move Kali Linux outside the LAN by setting its network adapter to NAT Network.
- Test and validate that your web page is accessible from outside the LAN by querying pfSense's WAN interface using a browser.
  - > You can explicitly specify the port using `http://<WAN ip of pfSense>:80` or, because http traffic uses port 80 by default, you can use `http://<WAN ip of pfSense>` and your browser should automatically connect to port 80.
- Include a screenshot of the successful browser test.

Congratulations! You've set up your first web server properly behind a firewall.

### Part 5: Topology

- Update your network topology in draw.io and include in your submission.

## Stretch Goals (Optional Objectives)

Pursue these stretch goals if you have remaining lab time.

- Update the NGINX configuration to activate a second website on port 8080.
  - Use the same HTML and CSS assets.
  - Publish it to the WAN on port 8000 (to be accessed by `http://<WAN ip of pfSense>:8000`).

## Submission Instructions

1. Create a new blank Google Doc. Include above assignment submission text and images within this Google Doc.
1. Name the document according to your course code and assignment.
   - i.e. `seattle-ops-201d1: Reading 01` or `seattle-ops-201d1: Lab 04`.
1. Add your name & date at the top of the Google Doc.
1. Share your Google Doc so that "Anyone with the link can view".
1. Paste the link to your Google Doc in the discussion field below and share an observation from your experience in this lab.
