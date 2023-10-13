I just tried to access my Linux computer while it was shut down.  It wouldn’t connect via RDP.  I want to be able to access it from anywhere so I am trying to configure Wake-on-Lan (WoL) which will power on my Linux computer even when it is shut down when I attempt to connect to it.

It was kind of a long process but here is the gist of it:

Hit up your BIOS menu and find the Wake On Lan settings.  Enable them, but just the normal boot sequence, not the PXE startup or whatever the other option is.
Save those settings and return to startup.

Once your lab computer is started you can remote into it and do the next steps.

First identify the IP address and Mac address of your lab computer.  I won't use my real ones here but I'll use fillers.  Make note of these and keep them handy.  Do this in terminal via the command 'ip a' and look for the 'eno1' 'inet 192.168.9.xxx' (that's the IP addy) and 'link/ether 91:a7:4d:98:t9:4e" (that's the mac address)

next you need to enter the command 'ls /etc/netplan/' which will return something like 01-network-manager-all.yaml

Then you are going to want the full file path for that so enter
realpath /etc/netplan/01-network-manager-all.yaml
Result: /home/your name here/01-network-manager-all.yaml

next up you are going to enter sudo nano /home/your name here/01-network-manager-all.yaml 

this is going to take you to what is most likely a blank file.  It will ask you something I don't remember.  Just say yes.  Then you are going to code the following

```
network:
   version: 2
   renderer: networkd
   ethernets:
     eno1:
       dhcp4: no
       addresses: [192.168.0.198/13] # Replace with your lab computer's  IP address
       gateway4: 192.168.0.1  # Replace with your router's IP address
       nameservers:
         addresses: [192.168.0.1]  # Replace with your DNS server addresses
```
        

This will set your Linux machine to a static IP address

Next you are going to login to the TP-Link router
open a browser and enter 192.168.0.1 or tplinkwifi.net and then put in the password
Go to Network > DHCP Server
Click the + in the Address Reservation table
Here you will add the name of your lab computer from the DHCP Client List
You will enter the MAC Address, Static IP Address, and Description
Go to NAT Forwarding > Virtual Servers
Click the + to add a new Virtual Server
Service Type: WakeOnLan
External Port: 9
Internal IP: [Enter your static IP address]
Internal Port: 9
Protocol:  I used UDP because that is what most of the reading and research said but I can't explain why that is
Go to Security > IP & MAC Binding
Click the little link chains on the device with the proper MAC and IP addresses in the ARP List table.
This should populate a new item in the Binding List table

You can now leave your router.

So, finally, if you are on a MAC open a terminal and enter "brew install wakeonlan" and you should see it download.

cross your fingers, shut off your Linux machine, and try to RDP.  

The RDP should fail and say it can't connect.

Now go to your MAC terminal and do a "wakeonlan [your desired MAC address here]"

if it works you will get a dope message that says "Sending magic packet to xxx.xxx.xxx.xxx:X with payload [mac address here]

I let out a legit giggle when I heard my linux computer boot up and was even more delighted when my RDP connected.

Check it out.  It's a good time!

Enjoy!!

