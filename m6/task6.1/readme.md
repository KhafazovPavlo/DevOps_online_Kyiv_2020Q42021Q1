## Task6.1

## Creating connection between virtual machines VM1 and VM2 on Ubuntu 16.04 Server

VM1 has 2 network interfaces (NAT, Internal), VM2 has Internal network interface. VM2 will have access to the Internet using VM1 Internal interface as a gateway.

![Image101](screenshots/101.jpg "Image101")

![Image102](screenshots/102.jpg "102")

![Image103](screenshots/103.jpg "Image103")

Configuring VM2 ( changing hostname, configuring the network):

![Image16-1](screenshots/16-1.jpg "Image1")

![Image16-2](screenshots/16-2.jpg "Image2")

Editing /etc/network/interfaces to add static ip, mask, gateway

![Image16-3](screenshots/16-3.jpg "Image3")

I had difficulties with restarting netwoks service using `service restart networking`, so I've used `sudo /etc/init.d/networking restart`.

![Image16-4](screenshots/16-4.jpg "Image4")

Configuring VM1

![Image17-1](screenshots/17-1.jpg "Image1")

![Image17-2](screenshots/17-2.jpg "Image2")

![Image17-3](screenshots/17-3.jpg "Image3")

![Image17-4](screenshots/17-4.jpg "Image4")

![Image17-5](screenshots/17-5.jpg "Image5")
  
 _After I had connectivity troubles because I didn't remove '#' before this string net.ipv4.ip_forward=1 in /etc/sysctl.conf file. So I fixed this._
 
 Checking the access to the Internet from VM2:
 
![Image18-1](screenshots/18-1.jpg "Image18-1")
 
 I 've used `nslookup` determine which resource has an IP address 8.8.8.8:
 
![Image18-2](screenshots/18-2.jpg "Image18-2")
 
 To determine IP belongs to epam.com we can use `ping` or `nslookup`:
 
![Image18-3](screenshots/18-3.jpg "Image18-3") 

_To be able to do this we have to add dns-nameserver in /etc/network/interfaces file.

![Image18-4](screenshots/18-4.jpg "Image18-4")

To display routing table:

![Image18-5](screenshots/18-5.jpg "Image18-5")

To trace the route is used `tracerout`. By default traceroute uses UDP packets and sometimes it's not working correctly (because of routers and firewalls), so -I key is used to send ICMP:

![Image18-6](screenshots/18-6.jpg "Image18-6")

_Host default gateway is 192.168.1.1 (my TP-Link router)._ 

## Creating connection between virtual machines VM1 and VM2 on Ubuntu 20.04

In this case to configure network setting was used netplan and changed /etc/netplan/01-network-manager-all.yaml file.
To restart network service was used `service network-manager restart`, iptables configuration was saved by using `iptables-save > /etc/iptables/rules.v4`, iptable configs were the same.

![Image1](screenshots/1.jpg "Image1")

![Image2](screenshots/2.jpg "Image2")
   
![Image3](screenshots/3.jpg "Image3")

![Image4](screenshots/4.jpg "Image4")

![Image5](screenshots/5.jpg "Image5")