<h1>Step by Step Configuration</h1>
Objective: Configure a network consisting of two separate LAN’s connected through a router

## Choose Software and Hardware
- In order to complete this lab you will need access to four laptops, a router, 2 switches, and 6 ethernet cables.
- For software, Cisco Packet Tracer is needed for simulation, NAMO will need to be installed to set up the Web Server, and MAMP will be need to be installed to set up the DNS. 

## Add End Devices (PCs/laptops/printers/tablets/etc)
 - Connect laptops to switches using Ethernet cables and select allow them to connect when prompted
   
## IP Assignments
  - Assign IP addresses to laptop
  - On a Mac, navigate to System Settings --> Network --> 

## Connect the End Devices to the Switch
- Use Ethernet cables to connect the end devices to the switch.

## Set IP Address on End Devices
- Configure the IP addresses on all end devices (including mobile devices).

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
