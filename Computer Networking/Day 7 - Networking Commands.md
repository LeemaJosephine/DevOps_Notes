# Day 7 - Networking Commands

## 1. What is an IP address and port?

**IP address**

An **IP address** stands for **Internet Protocol address**, used to uniquely identify the device on network. 

Two Types:
  - **Private IP** : Inside network
  - **Public IP** : Internet facing

Types of IP Address:
  - IPv4 (Internet protocol version 4) - 32-bit numerical IP address (E.g: 192.168.1.1) [when all the IP address are exhausted at one point then we can go for v6)
  - IPv6 (Internet protocol version 6) - 128-bit alphanumerical address (E.g: 2001::db8::1)
---
**Port**

A Port identifies service running on a machine

|Port|Service|
|----|--------|
|22|SSH|
|80|HTTP|
|443|HTTPS|
|3306|MySQL|


**Task 1: Check IP address**
```
ip a
```
<img width="650" height="198" alt="image" src="https://github.com/user-attachments/assets/ff4c54d3-f59f-45ca-a09c-f05b80c797a5" />

</br>

**Explanation:**

**ip** - Modern linux networking tool

**a** - show all interface

**Outpur shows:**

**Lo:** The loopback interface is a virtual interface that a system uses to communicate with itself.

**ens5:** Primary network interface

**Task 2: Check public IP address using command**
```
curl ifconfig.me
```

**Explanation:**

**curl :** Utility that fetch data from internet

**ifcongig.me :** Return the public ip

**Task 3: Run a Wen server on port 8080**

Add inbound rule with port 8080


```
python3 -m http.server 8080
```

**Explanation:**

**python3 :** Python Interpreter

**-m http.server :** built-in web server module (-m)

  - It starts a simple web server using python
  - Servers files from your current directory
  - Runs on port 8080
  - To check, copy the public ip and add 8080 at the end and open in the browser. _E.g: http://15.207.72.212:8080/_

---
## 2. Useful Networking Commands
---
## 3. Traceroute

A network diagnostic tool to discover the path(hops) packets(traffic) source to destination. 

### What is a HOP?

**A hop =** each router between source -> destination

**Example:**

**Your EC2 -> AWS Router -> ISP -> Google Router -> Destination** 

### How Traceroute works:

Tracerount uses the concepts of TTL(Time to Live)

**TTL : Number of hops a packet can travel**

**Internal Working**

  - Send packet with TTL = 1
      - First router drops it
      - Send back "Time exceeded"
  - Send packet with TTL = 2
      - Seconf router responds
      - Continue until destination is reached    

Result: Get a list of all routers in the path.

**Hands-on**

**Step 1:** Install Traceroute
```
  - sudo apt update
  - sudo apt install traceroute -y
```

**Step 2:** Run traceroute
```
traceroute google.com
```
**Step 3:** Understanding the output

<img width="939" height="104" alt="image" src="https://github.com/user-attachments/assets/cbd610c8-bec3-420a-9b2c-dd1a3fc81e79" />
</br>

**Column 1** -> Hop Number (Number of routers in path)

**Column 2** -> IP Address/Hostname (Router handling your packets)

**Column 3 - n** -> Time (Latency) Time taken for wach packet

**Special Symbols (****)** -> Routers didn't respond. Packet dropped. Firewall blocking ICMP.

**Industry Usage:**

  1. Network latency issue
     - Problem : Website is slow
     - Solution: traceout website.com
     - Identify: which hop is slow. Where delay starts

  2. Network Break Detection
      - Problem:  Cannot reach server
      - Output: ****
      - Meaning: Traffic bloacked after hop. Firewall/routing issue.
---
## 4.Ping

Ping is a network diagnostic tool used to: Check if a host is reachable and measure latency(response time)

**Protocol Used: ICMP**

**How Ping works:**
  - Your system sends ICMP Echo(these are message type in ICMP) Request
  - Target system receives it
  - Target replies with ICMP Echo Reply
  - Ping measures round-trip time (RTT)

**Ping Vs Traceroute**

|Feature|Ping|Traceroute|
|-------|-----|----------|
|Purpose| Cheack reachability| Check full path|
|Protocol| ICMP| UDP/ICMP/TCP|
|Output|Simple|Detailed hop|
|Shows route|No|Yes|
|Latency|Overall|Pre hop|

**Ping: "Can I reach you"**

**Traceroute: "How do I reach you"**

### Hands-on

**Basic Command:**

```
ping google.com
```
<img width="623" height="169" alt="image" src="https://github.com/user-attachments/assets/f0c451f0-a64b-4880-add4-a4ae3d9b2abb" />
</br>

**Advanced hands-on**

1. Control the packet size: 
```
ping -c 4 google.com
```
<img width="602" height="136" alt="image" src="https://github.com/user-attachments/assets/2279ecc8-ed7d-4f67-9f94-cba10384ab72" />
</br>

2. Change Interval:
```
ping -i 2 google.com
```
<img width="616" height="252" alt="image" src="https://github.com/user-attachments/assets/d0769641-2681-41dc-8e3f-f3ace9deea17" />
</br>

3. Increase packet size (test large packet handling
```
ping -s 1000 google.com
```
<img width="625" height="128" alt="image" src="https://github.com/user-attachments/assets/3a8db593-0556-4dea-acc1-04c722ec339a" />
</br>

## 5. What is DNS and how does DNS resolution work?
    
**DNS (Domain Name System)**

It is system that converts human readble domain names into IP address.

**Example:** 

For google.com -> 142.250.xx (ip address)

### How does DNS resolution work**

**Example:**

**When you open a website:**
  - Browser checks cache
  - OS checks local DNS cache
  - Query sent to DNS server
  - DNS hierarchy resolves the request:
          - Root server
          - TLD server (.com,.org)
          - Authoritative server
  - IP returned
  - Browser connects to a server

**Types of DNS server:**

|Type|Role|
|-----|----|
|Root server | Starting point|
|TLS server| Top Level Domain server - Handling .com,.org|
|Authorative server|Final Answer|
|Recursive Resolved| Queries on your behalf|

**DNS Record Types**

|Records|Purpose|
|-------|--------|
|A|Domain -> IPv4|
|AAAA|Domain -> IPv6|
|MX|Mail Server|
|TXT|Verification/Security|
|CNAME|Alias|

**Hands-on**

Step 1: Check if DNS is resolving domain name -> IP

Basic DNS lookup

```
nslookup <domain_name>
```
<img width="299" height="170" alt="image" src="https://github.com/user-attachments/assets/c0ce0ec7-ca16-4628-991a-2d6b1c224fbd" />
</br>

Output Explanation:

- Server -> DNS resolver used
- Address -> IP of DNS server
- Name -> Address -> resolution result

Step 2: Detailed DNS
```
dig <domain_name>
```
<img width="467" height="280" alt="image" src="https://github.com/user-attachments/assets/eaa7b9e6-5ba5-4ce2-8d4d-bef0c2d3591e" />
</br>

Usage:
- Debug slow DNS
- Analyse resolution

Step 3: Query Specific Record
```
dig google.com MX
```
Finds mailserver for domain
<img width="476" height="269" alt="image" src="https://github.com/user-attachments/assets/4373e528-2636-4910-b68f-968742b8c04c" />
</br>

**Real world scenario:**

**Scenario 1: Website not opening**

**Step 1:** nslookup website.com

If fails -> DNS issue

**Step 2:** dig website.com

Check
- Query time
- Response

**Step 3:** cat/etc/resolv.conf

Verify DNS Server

---
## 6. Route

Decides where network traffic should go.

Each system has a routing table that acts like a map for sending packets to the correcr destination.

**Example:**

Destination: google.com -> go via gateway 172.31.0.1

### What is route command?

The route command is used to
- View routing table
- Add route
- Delete route

It helps how you control how your system communicates with network.

**Hands-on** - View Routing table

Install net-tools: sudo apt install net-tools -y

```
route -n
```
<img width="536" height="92" alt="image" src="https://github.com/user-attachments/assets/d82a570b-26b2-4995-b305-743bcfb929a5" />
</br>

**Explanation:**

Destination:
- 0.0.0.0 -> default route (internet traffic)

Gateway
- 172.31.32.1 -> router (AWS VPC Gateway)

Genmask
- Subnet mask


Flags
- U ->  route is up
- G -> uses gateway

Iface
- ens5 -> network card


### ipcongig/ifcongif

**ifcongig**

- Install net-tools
- 
<img width="518" height="245" alt="image" src="https://github.com/user-attachments/assets/0788a7c7-6bf4-462f-a698-6b85362d7e2d" />
<br>

### arp

Address resolution protocol - Used to map an IP address to MAC address. It's like a bridge between

**Why arp needed?**

In an network, devices communicates using IP address (Logical communication) , bur the actual data transfer happens using MAC address (physical communication)

Example:

System wants to send 

```
arp -a
```
<img width="645" height="34" alt="image" src="https://github.com/user-attachments/assets/b5defcba-80bb-4086-8f20-bf1ff0eed8cf" />
</br>

Mordern alternative: 
```
ip neigh
```
<img width="395" height="28" alt="image" src="https://github.com/user-attachments/assets/d289dd05-579e-43f3-ad19-f9618366a85c" />
</br>

### netstat

Show all listening port
```
netstat -tuln
```
<img width="548" height="158" alt="image" src="https://github.com/user-attachments/assets/610ca5db-a29c-46a7-b4c3-506dc37be50c" />
</br?

Show all process using port
```
netstat -tulp
```
<img width="659" height="170" alt="image" src="https://github.com/user-attachments/assets/d8f83d3c-8ac5-415c-ba27-d0b060b8c5ee" />
</br>

