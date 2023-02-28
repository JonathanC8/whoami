+++
author = "Jonathan Cammack"
title = "Securing 333Cloud"
date = "2023-02-28"
description = "Security Update for 333Cloud"
tags = [
    "linode",
    "security",
    "ubuntu",
    "linux",
    "iptables",
    "ssh"
]
categories = [
    "Self Hosted",
    "333Cloud",
]
series = ["Security"]
image = ""
draft = false
+++
# Preface

Recently, I have secured my servers using Linode. If you didn't know all of my servers run through a proxy I created in Linode, the Ubuntu server I run on Linode is a small single cpu vm routes all of my server traffic between the internet and my front-facing servers. I use a wireguard tunnel which my servers connect to and route their services to such as Minecraft and my website. This for one, is a major improvement to security since my port-forwarding on my home internet days, however, that's not the focus of this article. Until recently my Linode server was kind of neglected as far as security configuration goes, I always thought the threat level to my small scale of services was too low to worry about so I always pushed off the extra security my server should have. Of course I used a strong password and closed ports that shouldn't be accessed but that's not enought in my opinion so here is what I did.

# SSH Hardening
First, I began hardening the SSH connection, generally speaking SSH is pretty secure it has encryption and requires knowledge of the username and password to connect. That's not enough in this day in age with the advent of extremely powerful consumer graphics cards password cracking is a real threat especially if you use the root account for your SSH management(my first major mistake). Luckily I haven't been hacked before but generally speaking that was a bad idea so I went ahead and created a new user for myself in which I will keep the details undisclosed, that should in theory be almost the same level as a double password however if the root account can still be used its useless. So I configured SSH to where you cannot login using the root account and you must have the private key in order to connect. Now that second part is really important and practically makes your server impenetrable as long as your private key doesn't get leaked. 

# Blocking ports and leaving UFW 
Usually in most cases UFW for Ubuntu is enough for a server however since my server acts as a proxy/router for my self-hosted services UFW can be troublesome with the currect iptables I have configured. So to solve this problem I have taught myself iptables which wasn't too complicated but it has a lot of content that I have not perfected just yet. So using iptables I blocked all access to my server except through ports 443(HTTPS) and 51820(Wireguard). With that I have locked down the Ubuntu server, as there are no possible ways for the user to run unauthorized code or commands because the services that are running will not accept user input.

# Conclusion
Having secured 333Cloud I will now continue to work on the major projects to come such as "cloud computing service", calculators, and much more services designed, built, and deployed by me.