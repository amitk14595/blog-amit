---
layout: post
title: Hotspot Setup in Mikrotik Router
comments: true
description: My views on why digital presence matters the most for your career
keywords: omkar pathak, blog, digital presence, why is digital presence important today, importance of digital presene, importance of digital presence for career, career
image: /public/img/blog-images/python.png
tags: [jekyll, python]
---



## Hotspot Setup in Mikrotik Router

**Reset**
❖ Remove all files from FILE menu
❖ Remove default configuration:- Checked No default configuration and Do not backup
After reset or New router configuration:-
Username :- Admin
Password:- #blank#
Note:- Its always good to change default username and password before starting configuration
because of security reasons. You can change username and password from SYSTEM - Users menu.

**Index:**

* TOC
{:toc}

Once you have completed above steps in case of new router and configured router too then you are
ready to configure router for hotspot services.
Basic Mikrotik router setting:-
WAN IP:- 192.168.1.10/24 (Airtel) in our case and it can be change according to requirement.
Bridge IP:- 172.16.0.1/16 (in our case this IP is bridge IP on which we configure our hotspot services).
Gateway IP:- 192.168.1.1 (Gateway to reach the internet)

## Lets start step by step process:-
**Step 1.** IP – Addresses :- provide WAN IP (192.168.1.10/24) on ether1 (interface can be change
according to your network).

**Step 2.** Interface – Create a bridge and include remaining interfaces as a bridge interface (For ex-
ether2, ether3, ether4, wlan) and allow all 4 basic firewall in Setting tab inside interface.

**Step 3.** IP – Addresses:- provide Bridge IP (172.16.0.1/16) on bridge 1.
**Step 4.** IP – Route:- provide gateway address to 0.0.0.0/0 network 192.168.1.1 (can be change).
Note:- Now you can ping (for ex- 8.8.8.8) google server IP but you can’t ping google.com because
DNS would not configured for resolving name to ip. So now we need to configure DNS.
**Step 5.** IP - DNS:- provide DNS address 8.8.8.8, 8.8.4.4 and 4.2.2.2 and unchecked allow remote
request .
Note:- Now you can ping both IP and Name of domains because of DNS address has been
configured.
## Advance Mikrotik router setting:-
Before starting advance setting we can download updates of router SYSTEM – Packages.
**Step 6**. Radius:- Add Radius server(+)

❖ Address – x.x.x.x (Server IP)
❖ Secret - ********
❖ Time – 60000ms (default-300ms) depends on router model
❖ Authentication port – 1812 (default)
❖ Accounting port – 1813 (default)

## Mikrotik Router configuration for Hotspot Service
Incoming
❖ Check Accept
❖ Port no. – 1700 (Radius server port no.)

**Step 7.** IP – Services:- Enable services
❖ Winbox – 8291
❖ Api_ssl – 8728
❖ ftp – 21
❖ ssh – 22

**Step 8.** IP – Cloud :- DDNS Enabled checked.
Force update.
**Step 9.** System

❖ Identity – Change identity for future identification(for ex- cosmodata)
❖ SNTP Client – Time protocol - ______ (server ip)
❖ Scheduler –
a) time interval – 5 min and put command /ip cloud force-update
(purpose of this scheduler command is to update dydns ) .
b) start time – 03:00:00 , time interval – 24 hrs and put command
/system reboot

**Step 10.** Queues:- General:-

a) Target address:- 172.16.0.0 (Hotspot address or Bridge address)
b) You can also restrict target upload and target download limit.

## Limiting upload and Download Speed:- Target upload:-

a) Queue type:- pcq upload default
Target download:-
b) Queue type:- pcq download default
**Step 11.** System – Watchdog:- Auto supout unchecked
Hotspot configuration:-
**Step 12.** IP – Hotspot:- Click on Hotspot setup (Automatic configures):- Only you have to
provide basic configuration (for ex:- Interface on which you want to configure your
hotspot services (in our case:- bridge1), DHCP pool- 172.16.1.2-172.16.255.254), Ip
address of smtp server:- 0.0.0.0(default), DNS name, user information etc)

## Hotspot Server Config-
a) Hotspot server name will be replaced by 15 digit code of Location

domain in Dashboard – Properties.
b) DNS Name:- hotspot.cosmodata.co.in
c) Idle time:- 1d 00:00:00
d) Keep alive time:- 1d 00:00:00
e) Address per mac:- Optional
❖ Server profile:- General – checked hotspot
Login – HTTP PAP, Mac Cookie, Cookie, SSL – none
RADIUS – use radius checked
❖ Users – default user (admin) – delete(recommended)

✓

## Mikrotik Router configuration for Hotspot Service
❖ User Profile:-
a) Address pool- hspool (select address pool that configured during
hotspot setup )
b) Idle time:- 1d 00:00:00
c) Keep alive time:- 1d 00:00:00
d) Transparent proxy – Checked

❖ Walled garden IP list:-
a) Address Destination server:- _________ (Server IP)
b) Address Destination host:- cosmodata.co.in
**Step 13.** IP – DHCP Server:- Note:- If hotspot server created by using hotspot
setup(automatically) then dhcp server will create automatically or if we configure
hotspot manually then we need to create DHCP server and DHCP pool manually and
include into Hotspot server option.
In our case mostly we use Hotspot Setup(Automatically) therefore only we need to
change in few options.

a) Lease time:- 2d 00:00:00
b) ARP:- Enable arp for lease (checked)

**Step 14.** Replace files in Hotspot directory in their respective directories inside Files menu:-
\hotspot
a) login
b) alogin
c) rlogin
d) redirect
e) error
f) status
g) logout

**Step 15.** IP – Firewall:- Layer 7 protocol allow.
**Step 16.** Dashboard – Properties – Location Name should be replaced by IP – Identity .
**Step 17.** IP – Hotspot – Server – Hotspot server name should be replaced by 15 digit code
generated in Dashboard – Properties – Location domain.
**Step 18.** *System – Loging:- changes at the place of IDENTITY in loging script file
(Connection log ):- 2 files

Note:- Configuration might be changes according to requirement and premises.