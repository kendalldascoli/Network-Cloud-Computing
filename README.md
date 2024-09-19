<h1>System Architecture Guide</h1>

![System_Architecture_Diagram](https://github.com/user-attachments/assets/e3de59c3-ad75-4975-922a-17c5a70675b3)

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
- At this point MAMP should be installed already, open MAMP from the Applications folder and select "Nginx"
<img width="537" alt="Screenshot 2024-09-18 at 4 42 51 PM" src="https://github.com/user-attachments/assets/681d937b-fa4b-43c9-8361-2141e394c808">

- Navigate to system preferences in the upper left hand corner of MAMP and then select Ports, in the Nginx Port, change out 8000 for 80
<img width="537" alt="Screenshot 2024-09-18 at 4 45 26 PM" src="https://github.com/user-attachments/assets/00e13266-161c-4ec8-9802-270e2d04aaea">

- Navigate back to the home of MAMP by pressing Ok and closing out of System Preferences and press start, if it says stop just stop it and press start. MAMP should look like the below image
<img width="537" alt="Screenshot 2024-09-18 at 4 50 53 PM" src="https://github.com/user-attachments/assets/f61410b3-49b7-407c-94a3-14e77a6eb8c5">

- Next, navigate to the Terminal and enter (for Mac users) /Applications/MAMP/htdocs/index.html
    - This will create an index.html in the directory for your operating system
- Once that is complete, go to Virtual Studio Code or a text/code editor and add/replace "Welcome to Capstone Consulting"
- Test that this is working by first having the computer hosting the Web Server navigate to a browser and input its own IP, if it goes through to a screen that says "Welcome to Capstone Consulting" then it was a success. If it doesnt, please refer to the FAQ section.

## Setting up the DNS Server
- On the computer that was not used for the Web Server, open NAMO and hit create record, the screen should now show as follows.
  <img width="585" alt="Screenshot 2024-09-18 at 5 26 34 PM" src="https://github.com/user-attachments/assets/99211c1e-57b4-479f-8885-862997fbbfe5">

- Add a Host Name called "capstoneconsulting.com" and set the IP address to individual
- In IPv4, input the address of the laptop designated as the DNS Server, in other words the one not used for the Web Server. It should look like the below and then save your work.
  <img width="585" alt="Screenshot 2024-09-18 at 5 45 39 PM" src="https://github.com/user-attachments/assets/89d81ee5-a2f6-4d16-afac-8163fe921e94">

- Next,set the DNS server on each laptop to the IP address of that laptop that is assigned to act as the DNS server
    - Go to system settings --> network --> select the connected ethernet interface --> details --> DNS --> Remove and existing DNS Servers -> Add the IP address of the laptop that is assigned to act as the DNS server (192.168.0.65)
 - Confirm DNS Server recognition by navigating to the Terminal or CLI and type in networksetup -listallnetworkservices
networksetup -getdnsservers {NETWORK INTERFACE}
- Confirm that the laptop hosting the DNS server can access the website by navigating to google.com and searching "capstoneconsulting.com", if it goes through and the page says "Welcome to Capstone Consulting" then it was a success and you can move on.
## Follow the previous instructions for the other LAN as well with the other two computers prior to connecting via the Router,(use IP range of 172.16.0.0/24) once this is completed, proceed to the next step

## Add a Router to Connect Networks
- Insert a router to enable communication between different networks
- In order to prepare the router for connection, add a power cable to the router and turn it on

## Connect the Switches to the Router
- Use Ethernet cables to connect the switches from each LAN that we just configured to the router.

## Establish communication from the switches to the router
- Once communication is established by following the next steps, you can receive data,commands, or configurations with the router.
- Install driver for serial adapter onto your computer on each LAN
- Open terminal and type ls/dev/*usb*
- screen /dev/USB-SERIAL-CONNECTION BAUD-RATE - this is searching for all devices connected to the system that have usb in their names
- Enter this 2x
- When exiting the session Ctrl+a then Ctrl+\
## Configure IPs on the Router
- Assign IP addresses to the router interfaces.
- Access the router's CLI and input the following
    - Router> enable
    - Router# configure terminal
    - Router(config)# interface (ex. GigabitEthernet 0/1 - or whever you want to set the IP address)
    - Router(config-if)# ip address 192.168.0.1 255.255.255.0

## Set Port Status to ON on the Router
- Enable the ports on the router for communication by following these commands in the CLI of the router
  - Router(config-if)# no shutdown
  - Router# write memory
  - Router# copy running-config startup-config
  - Router# show ip interface brief

## Getting into the correct mode
- Enter User Exec mode and have access to all status and configuration commands by typing
  - Router>enable in Terminal
  - Router#
- The password will be LMU
- You will then enter the hostname (ex. router01)
## Viewing a summary of router interfaces
- In Terminal type
  - do show ip interface brief
## Configure Router Interfaces
- In terminal type
  - interface gigabitEthernet 0/0
  - ip address 15.255.255.1 255.255.255.0
  - description ## to switch01 ##
  - no shutdown
- View the running config in RAM by typing
  - show running-config
- Save the configuration to NVRAM by typing
  - write memory
- Confirm the config was permanently saved by typing
  - show startup-config
## Set Default Gateway on All End Devices
- Set the default gateway on each end device to the router’s `GigabitEthernet` interface it is connected to.
- Navigate to System Preferences --> Network --> TCP/IP tab --> Select Manually for Configure IPv4
   - Enter the IP address, Subnet Mask, and the Router's IP address (as the default gateway)
   - Click OK and then Apply to save the settings


<h1>FAQ</h1>

# Network Troubleshooting Guide

## Common Networking Issues and Steps to Resolve Them

### 1. PC1 is Not Pinging PC2:
- **Ensure IP addresses are set for both PCs:**
  - Verify that both PCs are on the same network segment (e.g., same subnet).
  - Check IP configuration on each PC using:
    ```bash
    ifconfig (Linux/Mac)
    ```
  - Ensure the IP addresses are not in conflict (i.e., no two devices on the network should have the same IP address).

- **Ensure ethernet cables are secured:**
  - Check the physical connection between both PCs and the network (switch/router).
  - Look for link lights (green/orange LEDs) on the network interface card (NIC) to confirm proper connectivity.
  - Test the cables on another device to rule out any cable issues.

### 2. No Connection:
- **Ping test a website to verify internet connectivity:**
  - Open a terminal and run the following command to ping an external website (Google, in this case):
    ```bash
    ping google.com
    ```
  - If you receive no response or timeouts:
    - Ensure your DNS settings are configured correctly.
    - Verify your network interface is up and running (`ipconfig /all` on Windows, `ifconfig` or `ip a` on Linux/Mac).
    - Restart the network adapter or try reconnecting to the network.

### 3. Router is Not Connecting to Switch:
- **Check if the port status is on:**
  - Inspect the switch and router to ensure the appropriate port is enabled.
  - Use switch management tools (CLI, web interface) to check port status and activity.
  - Try swapping to a different port on the switch or router to isolate potential hardware issues.

- **Ensure the default gateway is set:**
  - Verify the default gateway IP is configured properly on all devices in the network.
  - On most systems, this can be checked using:
    ```bash
    ipconfig (Windows) or route -n (Linux/Mac)
    ```
  - If the default gateway is not set, configure it manually through the network settings or command line.

### 4. Website is Not Accessible:
- **Check that there is no firewall blocking traffic on the web server host computer:**
  - Ensure the firewall on the web server is not blocking HTTP/HTTPS traffic (ports 80 and 443).
  - On Windows, check the Windows Firewall settings; on Linux, check `iptables` or `ufw` rules:
    ```bash
    sudo ufw status (for Ubuntu/Debian)
    sudo iptables -L
    ```
  - Temporarily disable the firewall to test connectivity, then re-enable it with appropriate rules.
  - Ensure any security groups or policies (for cloud-hosted servers) allow inbound traffic.

### 5. PC1 Cannot Ping the DNS Server:
- **Ensure the default gateway is set on PC1:**
  - Verify that PC1 has the correct gateway configured, as this is required to route traffic outside the local network.
  - Check for DNS configuration issues as well:
    - Ensure PC1 is using the correct DNS server IP.
    - Test by using an external DNS server, such as Google's DNS (`8.8.8.8`), to see if it's a local DNS issue.

- **Additional Steps to Consider:**
  - Try resetting the network adapter on PC1:
    ```bash
    ipconfig /release && ipconfig /renew (Windows)
    sudo dhclient -r && sudo dhclient (Linux)
    ```
  - Use `tracert` (Windows) or `traceroute` (Linux/Mac) to identify where the connection is breaking down between PC1 and the DNS server.

---

### Additional Ideas:
- **Check for IP Conflicts:**
  - If multiple devices are assigned the same IP address, communication may fail. Use the command below to identify devices with conflicting IPs:
    ```bash
    arp -a
    ```

- **Verify Subnet Mask:**
  - Incorrect subnet masks can prevent devices on the same network from communicating. Double-check the subnet configuration on each device.

- **Test with Another Device:**
  - If pinging between PC1 and PC2 fails, try pinging another known working device to isolate whether the issue is with the PC or network hardware.

- **Update Drivers/Firmware:**
  - Ensure that the network drivers on PCs and the firmware on the router/switch are up to date. Outdated software can cause connectivity issues.

- **Check for VLAN Issues:**
  - If VLANs (Virtual Local Area Networks) are configured, ensure both PCs are on the same VLAN or that inter-VLAN routing is enabled.

---


<h1>Retrospective</h1>
Throughout this project, I configured a network using Cisco Packet Tracer, created a step by step configuration guide, and created an FAQ section addressing different issues that are commonly encountered. This journey was not without challenges, but each obstacle provided a learning opportunity and deepened my understanding of networking concepts. 

Initially, I ran into some issues with Packet Tracer itself, it wouldn’t open from my Applications leading to some early frustrations. After troubleshooting and reaching out for help, I learned it was running in the background of my computer, the solution was the open my Activity Monitor, select Cisco Packet Tracer, and fore quit it.This situation highlighted the importance of understanding the tools at my disposal and not being discouraged by technical glitches.

Once the software issue was resolved and I was able to use Packet Tracer as a simulation guide, I got started on configuring the network. I gathered my hardware  which and begain configuring IP addresses for the end devices. At first, understanding how IP addresses function in both Local Area Networks (LAN) and Wide Area Networks (WAN) was confusing, especially since different ranges were used for the two LANs in the project. I came across a few issues when testing the IP addresses via ping in my Terminal, most were easy fixes. For example, me and my group member had accidentally set the same IP for our computers and our Ethernet cables were not fully secured. These were simple issues, but they underscored the importance of verifying both physical connections and configurations before jumping to more complicated conclusions. It taught me to break problems down into smaller components and address the most basic potential issues first. Through these setbacks, I gained a deeper understanding of IP addresses and how they connect different devices to one another within a LAN and within a WAN. It became evident that attention to detail in IP configuration is critical because even a minor mistake could lead to connectivity failure.

As we progressed through the network configuration, I also encountered a more complex issue when setting up the Web Server using MAMP. The Web Server seemed to be unreachable from other devices even though I had selected Nginx but, I quickly realized attention to detail in the port settings is critical and after I ensured that Nginx was set to 80 instead of 8000, the isssues were resolved. 

Another larger issue we encountered was when we tried to access the Web Server from the DNS Server. The webpage wouldnt go through however when the computer hosting the Web Server attempted to access the website, it would go through. We re-traced our configuration steps to ensure the DNS server and Web server were set up correctly however the issue still persisted. This led us to explore the posibility of a system specific issue or an error in computer settings. After some troubleshooting, we realized that the computer hosting the Web server had a Firewall enabled in the settings of their computer which was blocking traffic from the DNS Server. Once this was deactivated, the DNS Server was able to connect to the Web Server and access the website. 

This project enhanced my understanding of network functions at both the hardware and software levels. It also tested my ability to continue to maintain attention to detail at every step because if one step is overlooked, the whole system may not work. I gained valuable perspective on how each piece of a network interesects as well.
