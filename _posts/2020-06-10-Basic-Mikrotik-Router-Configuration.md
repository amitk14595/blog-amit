---
layout: post
title: Basic Mikrotik Router Configuration
comments: true
keywords: Mikrotik, DNS, LAN, WAN, IP
image: /public/img/blog-images/linux.jpg
tags: [website, life]
author: Amit Kumar
---

**Basic Mikrotik Configuration**

Mikrotik is one of the most popular routers. Mikrotik Router has a lot of networking
services that help to build a stable and smooth network so easily. It is said that any ISP
Company or any Enterprise Office cannot go a single day without Mikrotik Router. So,
the system administrators who are not using Mikrotik Router yet, they will soon start
using Mikrotik Router, I think. As a system administrator, I am also using Mikrotik
Router about 3 years in my network and really I have got a very stable and smooth
network. Mikrotik Router is mainly famous for bandwidth control service and packet
filtering functionalities as well as cheap price. Mikrotik Router is also favorite to any
system administrator because of having graphical user interface (GUI) software
named Winbox which helps to manage Mikrotik Router so easily. As the usage of
Mikrotik Router is growing rapidly, this article is designed to show the basic
configuration of a Mikrotik Router from very beginning using Winbox software so that
a new Mikrotik Router user can easily configure his/her router from very starting and
can operate his network smoothly.
Prerequisites to Configure a Mikrotik Router
Before going to start basic configuration of a Mikrotik Router you should have below
information.
1. Basic knowledge about IP Addressing.
2. A Mikrotik RouterBoard or Mikrotik RouterOS installed on a PC.
3. Winbox Software.
4. PC with windows operating system installed and RJ45 cables.

**4 Easy Steps to Configure a Mikrotik Router**

Mikrotik router basic configuration includes assigning IP addresses and enabling NAT
for accessing internet. Mikrotik router basic configuration can be divided into 4 steps.
1. Assigning WAN and LAN IP addresses
2. Gateway configuration
3. NAT configuration and
4. DNS configuration
To configure a Mikrotik Router properly according to the above 4 steps, I’m using
below information and a simple office network diagram where three users are
connected to Mikrotik router through a network switch and one interface of the router
is connected to internet for accessing internet information.
1. Mikrotik RouterBoard 1100 AHX2
2. WAN IP: 172.22.3.99/25 (ISP provided)
3. Gateway: 172.22.3.1 (ISP provided)
4. Public DNS: 8.8.8.8 and 8.8.4.4
5. LAN IP Network: 192.168.10.0/24 (Private IP block chosen by me)


According to our simple office network diagram, first interface (ether1 port) is
connected to ISP internet and this interface is our WAN port. We will set our WAN
IP (provided by ISP) in this interface. Second interface (ether2 port) is our LAN
interface and we will set our LAN Gateway in this interface. The users of this network
are connected to MikroTik router trough a switch for accessing internet. In practical,
your network will not be simple like this network diagram. You may have to main a
large network where there may be hundred or thousand of users. But the basic
configuration is same for all networks. However, we will now start our MikroTik
router basic configuration according to the above 4 steps with our simple office
network diagram.
**Step 1. Assigning WAN and LAN IP Addresses**
First step to configure a MikroTik router is to assign WAN and LAN IP addresses in
WAN and LAN interface accordingly. So, follow below steps to set WAN and LAN IP
addresses in your new MikroTik router.
❖ Download winbox from this link or collect winbox from any source.
❖ Connect your PC with MikroTik Router by a RJ45 cable.
❖ Open winbox software in your operating system and click on search button located
after Connect To: input box. Connected Ethernet’s MAC will appear now. Click on
the MAC address. MikroTik router default username is admin and password is
blank. So, type admin in the login input box and password field left blank and
then click on Connectbutton. MikroTik graphical user interface (GUI) will appear
now. If you face any confusion to open MikroTik GUI using winbox software,
watch my below video tutorial carefully. Hope, it will reduce your confusion.
❖ Now click on Remove Configuration button if prompted.
❖ Go to IP > Addresses menu. Address List window will appear now. Click on add
new button (PLUS sign) from Address List window. New Address window will
appear. Put your WAN IP address (In this article: 172.22.3.99/25) which is
provided to you by your ISP into the Address input box and then select interface

(In this article: ether1) on which you want to set WAN IP from the Interface drop-
down menu and click Apply and then OK button.

❖ Click on add new button (+) again and put your LAN Gateway IP address (In this
article: 192.168.10.1/24) into the Address input box and choose your LAN
interface (In this article: ether2) from Interface drop-down menu and
click Applyand OK button.
Assigning WAN and LAN IP addresses has been completed. Now we will assign our
MikroTik gateway which is provided by our ISP so that our MikroTik router can
communicate to internet with this gateway.

**Step 2. Gateway Configuration**
After completing WAN and LAN IP setup, you should now configure your MikroTik
gateway which is provided by your ISP. So, follow below simple steps to assign gateway
IP in your MikroTik router.
▪ Go to IP > Routes menu. Route List window will appear now. You can see two
dynamic routes are already added in this Route List. Click on add new button (+).
New Route window will appear as soon as you click the button. Now put gateway
address (in this article: 172.22.3.1) which is provided by your ISP in Gateway input
field.
▪ Now click Apply and OK button.
Gateway configuration of your MikroTik router has been completed. Now we will
create NAT rule so that our MikroTik router can masquerade our LAN user IP to access
internet.

**Step 3. NAT Configuration**
After completing gateway configuration, you have to create a NAT firewall rule to
masquerade your LAN IP. Otherwise, your LAN user cannot access internet through
your MikroTik router. So, follow below steps to create the masquerade firewall rule in
your MikroTik router.
▪ Go to IP > Firewall menu and click on NAT tab and then click on add new
button (+) button. New NAT Rule window will appear now.
▪ Choose Chain: srcnat and Src. Address: 192.168.10.0/24 under General tab and
choose Action: masquerade from Action tab and then click Apply and OK button.
NAT configuration in your MikroTik router has been completed. if you do not create
this NAT rule, your LAN user cannot access internet through your router.
Three mandatory steps for configuring a new MikroTik router to access internet has
been completed. Your LAN user are now able to access internet through your router if
they use custom DNS server IP. But we shall now configure DNS in MikroTik router
so that it can resolve DNS request as well as it can work as a DNS server.

**Step 4. DNS Configuration**
After completing three mandatory configuration, you need to configure DNS in
MikroTik router so that it can resolve DNS request from the LAN user as well as itself.
So, follow bellow steps to configure DNS in your MikroTik router.
▪ Go to IP > DNS menu. DNS Settings window will appear now. In this window, put
DNS server address that you have got from ISP company or you can use public
DNS IP (8.8.8.8) in Servers input box. You can put secondary DNS server IP by
clicking add new value button (drop down button) located after the Servers input
box. Optionally, you can turn your MikroTik router as a DNS server. Turning your
MikroTik router as a DNS server is a better idea, I think. Because if you use public
DNS server in your network, every DNS request of your user will consume your
paid bandwidth. But if you turn MikroTik router as a DNS sever, your user will
get DNS solution from MikroTik router without consuming paid bandwidth. So,
if you want to turn MikroTik into a DNS server, click the Allow Remote
Requests check box and click Apply and OK button.
▪ If you turn your MikroTik router into a DNS server, all your MikroTik IP address
can be used as a DNS server IP including WAN IP which is a public IP and problem
will arise here. If anyone outside of your LAN use your WAN IP as a DNS IP, your
MikroTik will be happy by serving him/her DNS solution consuming your paid
bandwidth. So, you must stop DNS request from outside of your LAN. For
stopping DNS request from outside of your LAN, you should apply firewall rules
which will drop all DNS requests coming from your WAN interface (in this article:
ether1). For this, go to IP > Firewall menu and click on add new button (PLUS
Sign). New Firewall Rule window will appear now. Under General tab,
choose Chain: input, Protocol: udp, Dst. Port: 53 and In. Interface: ether1. Now
choose Action: drop from under Action Tab and click Apply and OK button. You
must create another similar rule for TCP connection. For this, click on add new
button (PLUS Sign) again and choose Chain: input, Protocol: tcp, Dst.Port:
53 and In. Interface: ether1 and then choose Action: drop under Action tab and
click Apply and OK button. Now your MikroTik DNS server is safe from outside
of your LAN.
DNS configuration in your MikroTik router has been completed. Now your MikroTik
router is able to resolve DNS request for the LAN user as well as itself.

Your MikroTik router is completely ready if you follow the above 4 steps carefully.
Connect a switch to MikroTik LAN interface with RJ45 cable and connect all PCs to
this switch. Also connect ISP cable to WAN interface. Now assign IP to all your LAN
PC according to your LAN IP network series. If you face any problem to set IP address
in windows PC, follow my another article about how to assign static IP address in
windows operating system which will guide you the proper way to assign IP address in
any windows PC. Now browse any website or ping google.com from your LAN PC. If
your ISP is OK, you will now be able to browse any website successfully.