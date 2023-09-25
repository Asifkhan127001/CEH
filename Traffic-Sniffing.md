# Tracffick Sniphink

Wireshark > Pcap File Analysis


1. Pcap(pacture Capture) File Structure
2. Filtering Packets
3. Follo up Streams
4. Finding Files
5. Search Strings

## Dos Attack DDos Attack

1. How Dos and DDos Attack perform
2. 3-way handshake, is a protocol for establishing a connection between a server and a client in a TCP/IP network
3. How TCP Work
4. Clinct sand server Request clincket like SYN request and server sand SYN-ACK Respotion and clinte sand ACK packet, This is Three Handshack work
5. How Dos And DDOS Attack 
6. Clint sand a SYN packet, Server is response SYN-ACK but clint never sand the Act Clicket agen again sand a SYN Packet this is Dos Attack

## Find Dos and DDos Attack 

1. Filtring the packet

     tcp.flags.syn==1
   
2. select the packet file click-back tab button, select follow sand to tcp strem, and manuwal check request and respotion

3. Extracking Files

        Open File option, option Expkrt-Objects, HTTP open, Tubble tabe Contect Type here show file

4. Filtring Comment select left bottom file logo selecte, file logo touch show message like (Open the Capture File Properties dialog

5. Finding Strings, Enter clt+f show search string option

6. Find Dos and DDos Attck, select the Statistics, Conversations, tabe 1pv4, check Bytes which IP Sand Many packets this is Attack Dos DDos attack
