# Phonegap_developper_app
Solution to resolve connection timeout when using  Phonegap developper app.

PhoneGap is a development tool that allows web developers to take advantage of the core features in mobiles with a unified JavaScript API. The PhoneGap Developer App allows users to develop locally then see the changes instantly on your mobile device.

# Issue
WHen trying to use he PhoneGap Developer App, on Linux kali running on my Chromebook, I received timeout error (on a browser) and downloading error ( on my mobile). There is connectivity between the Phonegap server and the mobile. This was tested using ping. I did not have any firewall on.

# Solution

I tried most of the solutions I could find online, but none of them worked for me. So I decided to use SSH port forwarding between my mobile and the phonegap server. This solution works for my issue.

# Implementation

On the computer,

      1- Install ssh server if it is not already installed
      
      2- Open /etc/ssh/sshd_config and add the following line somewhere in that config file:
      
         GatewayPorts yes
         
      3- Restart SSH: sudo service ssh restart
      
      4- Launch phonegap server by running 'phonegap serve' inside your application repository

On the mobile,

      1- Install SSH Tunnel App
      
      2- Launch SSH Tunnel and configure it:
      
               Host: phonegap server ip, 
               
               User: username on phonegap server, 
               
               Password: password on phonegap server, 
               
               Local Port 3000, 
               
               Remote Address: 127.0.0.1, 
               
               Remote Port: 3000
         
      3- Launch The PhoneGap Developer App and use your mobile IP address
