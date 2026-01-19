# TASK3

### 1. ifconfig
- Understood ifconfig to get ip addresses related to the system
- Look for an interface like eth0 or wlan0.The number next to inet is your Private IP (e.g., 192.168.1.15).
- The /24 you might see (e.g., 192.168.1.15/24) is CIDR notation. It tells you that the first 24 bits are the "Street Name" (Network) and the last 8 bits are your "House Number" (Host).

### 2. Ping
- Understood the usage of ping.
- It is used to check the connectivity to a site or domain via transfering packets
- if packet loss is 0% then the site or domain is reachable.
- If you can ping 8.8.8.8 (an IP) but you cannot ping google.com (a name), your internet is fine, but your DNS is broken.

| Command | Function |
| ------- | -------- |
| ping <domain/ip address> | ping continuosly |
| cntrl + c | stop ping |
| ping -c 5 google.com | Set no. of pings |

### 3. netstat or ss
- Both ss and netstat are command-line utilities used to investigate network sockets—the connections your computer makes to other devices or services.
- command: ss -tuln
- -t: TCP connections
- -u: UDP connections
- -l: Listening sockets only
- -n: Show numerical addresses (don't waste time looking up domain names)
- sudo ss -lptn 'sport = :8080': Find which program is using a specific port
- If you see *:22 listening, your machine is ready to accept SSH remote logins.

### 4. nslookup and dig
- nslookup and dig are both tools used to query the Domain Name System (DNS). They act like a "phonebook lookup" for the internet, translating human-friendly names (google.com) into computer-friendly IP addresses ($142.250.190.206$).
- nslookup (Name Server Lookup)
- dig (Domain Information Groper)
- Each "hop" represents a router. If the trace stops at hop #1, the problem is your local router. If it stops at hop #10, the problem is deep in the Internet Service Provider's (ISP) network.


### 5. traceroutes
- While ping tells you if a destination is alive, traceroute tells you exactly which path the data took to get there. It is essentially a "map" of the internet's infrastructure between your computer and a target server.
- ### How Traceroute Works (The "Hop" System)
  When you connect to a website, your data doesn't go there in one straight line. It "hops" through several routers (gateways). Traceroute works by sending a series of packets with an increasing TTL (Time to Live):
- First Packet (TTL=1): It hits the first router (your home router), which "kills" the packet and sends back an error message. Traceroute records this router's name and speed.
- Second Packet (TTL=2): It passes your router and dies at the second router (your ISP). Traceroute records that one.
- Repeat: It continues increasing the TTL until the packet finally reaches the destination.
- The Asterisk (* * *): This means a "Request Timed Out."
- Hop Count: How many routers are between you and the target.
If it happens for one hop but the next one works, the router is likely just configured to ignore traceroute requests for security.
If it happens for every hop until the end, you have hit a "dead end" or a firewall.


### 6. Simulate network failure by disabling interfaces.
- ip link show : This command will show a list of numbered items.
- sudo ip link set enp0s3 down : this command will stop the enp0s3 inerface
- After disabling the interface there was no success for commands like ping, traceroute.
- In high-end servers, we use Bonding or Teaming. If eth0 goes down, eth1 takes over so fast that the user never notices the "failure."

