# Detection-Lab

This detection lab is a homelab that was designed to give me hands on experience
with the type of tools I would likely be using in a future
soc analyst role.


<h2>Description</h2>
This project was a long one. With help from a write up and guide from Cyberwox on youtube, I was able to build my own virtual detection lab. Complete with a firewall, SIEM, Domain controller, Splunk and a few other nice additions. The goal of this project was to give me hands on experience with a few tools that I’d be working with as a soc analyst. 

The first thing I did was install pfsense. An open source firewall that would be used for the detection lab. This would be the main thing allowing connections between all 6 of my machines when they’re all up and running in the future. So to make sure everything goes well, I set the ip addresses for the 6 machines that I'll be using on the pf sense configuration. Afterwards, I set up my 2nd machine, Kali Linux, which would be used to interact with and configure the pfsense desktop page. From there, I created a few firewall rules to allow certain connections and ones that would eventually generate alerts based on certain tasks. 

Next on the list (well, it actually came before the pfsense desktop) was downloading and installing security onion. This was another multi step task that saw a command line based system installed first, and then another ubuntu machine created specifically to manage the security onion desktop page. This is where the majority of the fun will be taking place. For those that don't know, Security Onion (I’ll be calling it SO from now on) is an all in one SIEM that comes prepackaged with many different tools. One of the more standout additions includes the entire ELK stack (Elasticsearch, Logstash and Kibana). It is here that I will be reviewing logs, checking out alerts and monitoring for any possible intrusions or attacks. That’s where Kali Linux will come in down the line. Unfortunately, at the time of writing and installing, there seems to be a problem with the SO server which has made it difficult for me to access alerts and other configuration settings. ELK still runs but it comes with a few hiccups. But, we got the gist of things so it's time to move on to the rest of the set up.

Now, we set up our domain controller for the lab. For this, we’ll be using Windows Server 2019 which will then have Active Directory installed. This is my 5th time setting up Active directory so I don’t have much more to say about the configuration. I did experience an issue with accessing the internet through my DC’s web browser. I fixed it by going back to pfsense and changing a few firewall rules that would then allow my DC to access the internet. To go with my new AD server, I created another machine. This machine would house a windows 10 client which would act as an additional user in the domain and to generate more alerts down the line. In a past lab, I modified and ran a script that added 1000 users to my Organizational Unit.  This time, I just created 5 extra users and went from there.

The final thing I would be installing for my detection lab would be Splunk. Splunk is used to centralize the data, logs, and telemetry from other software and operating systems. Splunk would be installed on another Ubuntu, this time, the server version because it handles splunk better. I would still have to install the desktop version on top of it though and that process took over an hour. I love how helpful youtube comments and reddit can be during my time of need. With splunk installed, there would only be one task left. Installing a universal splunk forwarder on my domain controller so that events from the windows machines could be forwarded to the splunk machine.  Downloading and installing programs on a DC is pretty different than doing it on a regular windows client. There are security restrictions automatically put in place to prevent downloads of external applications.  You can temporarily bypass those restrictions or you can just turn them off completely. I chose the latter. Which reminds me, I need to go turn those settings back on before I progress any further. After successfully configuring port forwarding in Splunk, my detection lab was officially complete.

This took over a week to set up. Youtube tutorials don’t really show you how long things will take, especially when you run into problems that don’t show up in their video. For example, on the latest version of VMWare when setting up an Ubuntu machine, if you use the recommended pathway you will run into many problems and be unable to continue. I had to find a separate guide just to set up and install Ubuntu, then reference that guide each time it was time to set up a new machine. I also want to discuss the hardware limitations of my host device that greatly impacted the performance of my virtual machines at times. This project recommends 16gb, but in reality, you really need about 32. When your system only has 16, like mine, about 4gb is already reserved for system processes and services. I was unable to run more than 4 machines at once and when I tried to, I got a message that basically told me to upgrade my machine. If I sat here and listed every issue I came across, this write would be 5 pages long. So, to conclude this, I’m really proud of myself for being able to build my 4th homelab. I’ll be exploring my lab a lot more over the coming weeks to really learn about all the tools that come with it.

<br />


<h2>Languages and Utilities Used</h2>

- <b>Hypervisor</b> 
- <b>Active Directory</b>
- <b>Splunk</b>
- <b>Security Onion</b>
- <b>Pf sense</b>

<h2>Environments Used </h2>

- <b>VMWare</b>
- <b>Ubuntu</b>
- <b>Kali Linux</b>

<h2>Project overview:</h2>

<p align="center">
Configuring and installing pfsense: <br/>
<img src="https://i.imgur.com/3A7c0k5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Installing Security Onion:  <br/>
<img src="https://i.imgur.com/VvFW7r5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Installing Kali Linux: <br/>
<img src=https://i.imgur.com/91In5Ug.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Creating firewall rules in pfsense:  <br/>  
<img src="https://i.imgur.com/Vs4oTS6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Reveiwing security onion dashboard:  <br/>
<img src=https://i.imgur.com/F20HGFY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Configuring Active Directory on Windows Server 2019: <br/>
<img src=https://i.imgur.com/ho5zoJN.png height="80%" width="80%"/>
<br />
<br />
Creating and adding users to domain: <br/>
<img src=https://i.imgur.com/fsLmXpi.png height="80%" width="80%"/>
<br />
<br />
Installing Splunk on Ubuntu: <br/>
<img src=https://i.imgur.com/Lqk9sHx.png height="80%" width="80%"/>
<br />
<br />
Installing Universal Forwarder on Domain Controller: <br/>
<img src=https://i.imgur.com/2ovXCVc.png height="80%" width="80%"/>
<br />
<br />
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
