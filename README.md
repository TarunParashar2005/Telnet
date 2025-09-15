# Telnet
  Telnet Lab: This project demonstrates how to configure remote router access via Telnet using local authentication. A PC connects to the router over LAN, and administrators can log in with a username and password to manage the device remotely.

#Objective
To configure and verify Telnet remote access on a Cisco Router so that administrators can manage the router from a remote PC.

 Topology Description

Router: Cisco 2911
End Device: 1 PC (Client)
Network: 192.168.1.0/24
Connection: Router (G0/0) ↔ PC (Fa0)

Step-by-Step Procedure:-

🔹 Step 1: Configure IP Address on Router
Router> enable
Router# configure terminal
Router(config)# interface g0/0
Router(config-if)# ip address 192.168.1.1 255.255.255.0
Router(config-if)# no shutdown

🔹 Step 2: Set Router Login Credentials
Router(config)# enable secret cisco123
Router(config)# username admin password admin123

🔹 Step 3: Configure VTY Lines for Telnet
Router(config)# line vty 0 4
Router(config-line)# login local
Router(config-line)# transport input telnet
Router(config-line)# exit

🔹 Step 4: Configure IP on PC
Assign IP 192.168.1.2/24
Default Gateway: 192.168.1.1

🔹 Step 5: Verify Connectivity
From PC, ping the router:
C:\> ping 192.168.1.1

Step 6: Access Router via Telnet
On the PC, open the command prompt:
C:\> telnet 192.168.1.1

Enter username: admin
Password: admin123
Enter enable password: cisco123

Now you have remote CLI access to the router!

#Key Learnings

>How to configure Telnet access on a Cisco router.
>Importance of using local login with usernames for better security.
>Steps to access and manage a router remotely.
>How Telnet enables network administrators to manage devices without physical access.
>Understanding the need for SSH over Telnet in production for encryption.
