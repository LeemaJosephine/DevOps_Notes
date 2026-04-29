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
     - 
## 4. ipconfig/ifconfig
arp
iptables (for Linux)
What is DNS and how does DNS resolution work?
Ping
nslookup/dig
netstat
route
