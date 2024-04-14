# Networking Concepts. Assignment 2
## About
The following documentation contains a guide on how to set up an (File Transfer Protocol) FTP server using a docker. This guide also focuses on network configuration, iptables filtering, and access control via IP whitelisting.

`setup_node.sh`
Automates the initial setup of the Docker container by installing ifconfig and nmap, 
setting up an FTP server (vsftpd), configuring iptables rules to disable ping via ICMP from any host, 
allowing FTP access only from specified IP addresses, creating a new user (jp_user) with FTP access, 
and adding two files in the user's home directory. 

The script runs silently, without any ser interaction.

`setup_iptables.sh`
The script is running as an authentication service to control access to the FTP server. 
It asks the user to enter the authorization key for an IP address that is connecting to the server. 
The script then checks if the authorization key matches any entry in a credentials.txt file:
- If a match is found, the script adds the IP address to the allow list for FTP access using iptables. 
- If no match is found, the script removes any existing allow rules for the IP address related to FTP in iptables, effectively denying access.


`credentials.txt`
This file stores all authorization keys for IP addresses that are allowed to access the server. 