---
title: AWS (writing in progress...)
layout: single
header:
    teaser: /assets/images/aws_windows.png
author_profile: true
categories: projects
read_time: true
comments : true
toc: true
toc_sticky: true
sidebar:
    nav: sidebar-sample
---

Here, the purpose has been to create a Windows virtual machine on AWS and to have
access to its desktop from a remote workstation. It is different from what I did
with Linux where the remote control was via SSH and only using the terminal.

Like with Linux, I choosed an Amazon machine image and I follow the same steps,
here it is a Windows server 2019 image. I had to specify the rules in the security
group in order to allow the desktop remote control. And for this purpose, I used
RDP protocol of TCP with port 3389 which is suited for that, as illustrated in the following figure.

![Image](/assets/images/aws_ec2_windows_inbound_rules.jpg#center)

Once launched the Windows instance on AWS, I used a RDP client to connect it from
a remote desktop. As indicated in the following figure, I have entered the DNS
address or the IP address of the instance both available on AWS, and I created a
password to enable remote access. It is also possible to download the remote
desktop file and directly enter the user name and password related to the instance.

![Image](/assets/images/aws_ec2_windows_remote_client.jpg#center)

Once completed, there is a confirmation message indicating the remote connection
and you need to approve to enable the remote desktop control. After about 3 seconds,
the remote desktop appears to the screen of the local machine (as shown in the
following figure), you may use Windows, configure and install what you want.

![Image](/assets/images/aws_ec2_windows_remote_desktop.jpg#center)
