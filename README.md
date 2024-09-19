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
    - This will create an index.html in the directory for your     operating system
- Once that is complete, go to Virtual Studio Code or a text/code editor and add/replace "Welcome to Capstone Consulting"
- Test that this is working by having the alternate computer navigate to a browser and input the IP of the laptop that set up the Web Server, if it goes through to a screen that says "Welcome to Capstone Consulting" then it was a success. If it doesnt, please refer to the FAQ section.

## Setting up the DNS Server
- On the computer that was not used for the Web Server, open NAMO and hit create record
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


<h1>FAQ</h1>

PC 1 is not pinging PC 2
 - Ensure IPs are set for both PCs
 - Ensure ethernet cables are secured
No connection
 - Ping test a website by opening the terminal and # ping google.com
Router is not connecting to switch
 - Port status is not on
 - Default gateway not set
Website is not accessible
 - Make sure there is no Firewall up on Web Server host computer
PC1 cannot ping the DNS Server
 - Ensure default gateway is set


<h1>Retrospective</h1>
Throughout this project, I configured a network using Cisco Packet Tracer, created a step by step configuration guide, and created an FAQ section addressing different issues that are commonly encountered. Initially, I ran into some issues with Packet Tracer itself, it wouldn’t open from my Applications however I learned to go into my Activity Monitor and force quit it because it was running in the background of my computer. Once I got started on configuring the network, I gained a deeper understanding of IP addresses

