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

4. 
