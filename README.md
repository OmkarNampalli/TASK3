# TASK3

### ifconfig
- Understood ifconfig to get ip addresses related to the system

### Ping
- Understood the usage of ping.
- It is used to check the connectivity to a site or domain via transfering packets
- if packet loss is 0% then the site or domain is reachable.

| Command | Function |
| ------- | -------- |
| ping <domain/ip address> | ping continuosly |
| cntrl + c | stop ping |
| ping -c 5 google.com | Set no. of pings |

### netstat or ss
- Both ss and netstat are command-line utilities used to investigate network sockets—the connections your computer makes to other devices or services.
- command: ss -tuln
- -t: TCP connections
- -u: UDP connections
- -l: Listening sockets only
- -n: Show numerical addresses (don't waste time looking up domain names)
- sudo ss -lptn 'sport = :8080': Find which program is using a specific port

###  nslookup and dig
- nslookup and dig are both tools used to query the Domain Name System (DNS). They act like a "phonebook lookup" for the internet, translating human-friendly names (google.com) into computer-friendly IP addresses ($142.250.190.206$).
- nslookup (Name Server Lookup)
- dig (Domain Information Groper)


### traceroutes
- While ping tells you if a destination is alive, traceroute tells you exactly which path the data took to get there. It is essentially a "map" of the internet's infrastructure between your computer and a target server.
- ### How Traceroute Works (The "Hop" System)
  When you connect to a website, your data doesn't go there in one straight line. It "hops" through several routers (gateways). Traceroute works by sending a series of packets with an increasing TTL (Time to Live):
- First Packet (TTL=1): It hits the first router (your home router), which "kills" the packet and sends back an error message. Traceroute records this router's name and speed.
- Second Packet (TTL=2): It passes your router and dies at the second router (your ISP). Traceroute records that one.
- Repeat: It continues increasing the TTL until the packet finally reaches the destination.
- The Asterisk (* * *): This means a "Request Timed Out."
If it happens for one hop but the next one works, the router is likely just configured to ignore traceroute requests for security.
If it happens for every hop until the end, you have hit a "dead end" or a firewall.

