<h1>Step by Step Configuration</h1>
Objective: Configure a network consisting of two separate LAN’s connected through a router

## Choose Software and Hardware
- In order to complete this lab you will need access to four laptops, a router, 2 switches, and 6 ethernet cables.
- For software, Cisco Packet Tracer is needed for simulation, NAMO will need to be installed to set up the Web Server, and MAMP will be need to be installed to set up the DNS. 

## Add End Devices (PCs/laptops/printers/tablets/etc) and Connect the End Devices to the Switch
 - Connect laptops to switches using Ethernet cables and select allow them to connect when prompted
   
## IP Assignments/ Set IP Addresses on End Devices
  - Assign IP addresses to laptop
  - On a Mac, navigate to System Settings --> Network --> Select "10/100/1000" --> Details --> TCP/IP 
<img width="716" alt="Screenshot 2024-09-18 at 2 02 42 PM" src="https://github.com/user-attachments/assets/2a7204d4-0776-4246-b815-81416a325649">
<img width="668" alt="Screenshot 2024-09-18 at 2 11 15 PM" src="https://github.com/user-attachments/assets/58767253-e0f2-45fa-88e4-22f482036896">

  - Next, set IP address on the laptops in one LAN to an IP in the range 192.168.0.0/26 and in the other LAN that will be connected later via Router, set the IP to one in the range 172.16.0.0/24 and set the subnet masks to 255.255.255.192
<img width="668" alt="Screenshot 2024-09-18 at 2 04 29 PM" src="https://github.com/user-attachments/assets/8988f26b-ec90-4d5a-9ee8-6d74670a7ca4">

 - Once IPs are in place ensure connectivity by opening Terminal on the Mac and type # ping "IP address used"
 - There should be 0% packet loss, if there is packet loss refer to FAQ section
 - Once IPs are configured on all end devices and you are able to successfully ping within your LAN, you are ready to move on.

## Set up a Network Web Server
- Choose a laptop in your LAN that will be the Web Server, the other will be the DNS server in later steps
- At this point MAMP should be installed already, open MAMP from the Applications folder
- 

## Add a Router to Connect Networks
- Insert a router to enable communication between different networks.

## Connect the Switches to the Router
- Use Ethernet cables to connect the switches to the router.

## Configure IPs on the Router
- Assign IP addresses to the router interfaces.

## Set Port Status to ON on the Router
- Enable the ports on the router for communication.

## Set Default Gateway on All End Devices
- Set the default gateway on each end device to the router’s `GigabitEthernet` interface it is connected to.

## Configure the Web Server
1. Open MAMP.
2. Select Nginx as the web server.
3. Update Nginx port from `8888` to `80` in **Preferences -> Ports -> Nginx Port: 80 -> OK**.
4. Click `Start`. If only `Stop` is available, press `Stop` first, then click `Start`.

<h1>FAQ</h1>

PC 1 is not pinging PC 2
 - Ensure IPs are set for both PCs
 - Ensure ethernet cables are secured
No connection
 - Ping test a website by opening the terminal and # ping google.com
Router is not connecting to switch
 - Port status is not on
 - Default gateway not set
PC1 cannot ping the DNS Server
 - Ensure default gateway is set

<h1>Retrospective</h1>
Throughout this project, I configured a network using Cisco Packet Tracer, created a step by step configuration guide, and created an FAQ section addressing different issues that are commonly encountered. Initially, I ran into some issues with Packet Tracer itself, it wouldn’t open from my Applications however I learned to go into my Activity Monitor and force quit it because it was running in the background of my computer. Once I got started on configuring the network, I gained a deeper understanding of IP addresses

