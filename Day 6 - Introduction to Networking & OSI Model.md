# Day 6 - Introduction to Networking & OSI Model

## 1. Computer Networking Overview

**What it is:** A system of connected devices that share data and resources using agreed rules called *protocols*.

**Examples:**
- Home Wi-Fi connecting your phone, laptop, and smart TV
- A company's internal network (intranet) linking all office computers
- The internet — the largest network of all networks

**Key terms:**

| Term | What it means | Example |
|------|--------------|---------|
| IP Address | Unique label for every device on a network | `192.168.1.1` |
| Protocol | Agreed rules for communication | HTTP, TCP/IP |
| Router | Device that directs traffic between networks | Home Wi-Fi router |
| DNS | Translates domain names to IP addresses | `google.com` → `142.250.72.46` |
| LAN | Local Area Network — devices in one location | Your home network |
| WAN | Wide Area Network — spans large distances | The internet |

---

## 2. How Computer Networks Work

**What it is:** Data is broken into small *packets*, each travels independently across the network, and they're reassembled at the destination.

**Step-by-step example — loading a webpage:**

1. You type `google.com` → your browser asks DNS for the IP address
2. DNS replies with e.g. `142.250.72.46`
3. Your browser sends an HTTP request to that IP via the internet
4. Google's server sends back the HTML in packets
5. Your browser reassembles the packets and renders the page

**The OSI model (simplified to 4 key layers):**

| Layer | Name | What it does | Example |
|-------|------|-------------|---------|
| 1 | Physical | Hardware signals and cables | Ethernet cable, Wi-Fi radio |
| 3 | Network | IP addressing and routing | IP addresses, routers |
| 4 | Transport | Reliable (TCP) or fast (UDP) delivery | TCP for web, UDP for video calls |
| 7 | Application | What your apps use to communicate | HTTP, FTP, SMTP |

> **TCP vs UDP:** TCP guarantees delivery (slower). UDP is faster but can drop packets — used for live video and gaming.

---

## 3. Cloud Networking

**What it is:** Networking infrastructure hosted by cloud providers (AWS, Azure, GCP) instead of physical hardware you own. You define and manage networks in software.

**Examples:**

- **VPC (Virtual Private Cloud)** — your own isolated network inside AWS, like a private data centre in the cloud
- **Load Balancer** — distributes incoming traffic across multiple servers so no single one is overloaded  
  *e.g. AWS ELB, Azure Load Balancer*
- **CDN (Content Delivery Network)** — caches content at edge servers worldwide so users get it from the nearest location  
  *e.g. Cloudflare, AWS CloudFront*
- **VPN / Peering** — securely connects your office network to your cloud VPC

**Key concepts:**

- **Subnets** — split a VPC into public (internet-facing) and private (internal) zones
- **Security Groups** — act as firewalls; control which traffic is allowed in and out
- **Pay for bandwidth** — you pay for data transfer rather than owning physical cables

---

## 4. Microservices Networking

**What it is:** When an app is split into many small independent services, those services need to discover each other, communicate, and handle failures — that's microservices networking.

**Examples:**

- **REST / HTTP calls** — Order service calls Payment service via an HTTP API endpoint
- **Message queues** — Order service publishes an event to Kafka; Inventory service consumes it asynchronously
- **Service discovery** — services register themselves with Consul or Kubernetes DNS so others can find them without hardcoded IPs
- **API Gateway** — a single entry point that routes external requests to the right internal service  
  *e.g. AWS API Gateway, Kong*
- **Service mesh** — automatically handles retries, timeouts, and encryption between services  
  *e.g. Istio, Linkerd*

**Key challenges:**

| Challenge | What it means | Solution |
|-----------|--------------|----------|
| Latency | A single user request may fan out to 5–10 internal service calls | Async messaging, caching |
| Failures | One slow service can cascade and bring down others | Circuit breaker pattern |
| Security | Traffic between services inside the cluster needs to be encrypted | mTLS (mutual TLS) |

> **Circuit breaker:** If the Payment service is down, stop hammering it — return a fallback response instead and retry later.

---
## 5. What is LAN, Switch, Router, Subnet, Firewall, Gateway

**LAN - Local Area Network**

A network that connects devices in small area.
- Home
- Office
- School

**Example: Laptop/Mobile/Printer connected to Wi-Fi**

**Switch:**

Connect multiple device within LAN
Sends data to the correct device only
Use MAC address

**Example: Office network connecting multiple computers**

**Routers:**

Connects different networks
Routes data between LAN <-> Internet
Uses IP address

**Example: Home Wi-Fi router**

**Subnet:**

A subnet is a small network inside a large network. 

_Analogy: You house have partitions like hall, dining, bedroom out of which Hall and dining will be public access but bedroom will be private access. So in large network we have smaller network where through large network, we can connect to small ones._ 

- Organize network
- Improve performance
- Increase security

**Firewall:**

Protects a network from unauthorised access
Allows or blocks traffic

**Examples:**

**Allow, Port 80 (HTTP) and Port 443(HTTPS)
Block, Unknown traffic**

**Gateway:**

Is the entry/exit point of a network
Your router acts as gateway

### How these components work together?

- Your laptop(LAN) sends a request
- Switch forwards within network
- Router sends request to internet
- Gateway acts as exit points
- Firewall checks traffic
- Response comes back

---
## 6. OSI Model 

OSI Model is the (**Open System Interconnection Model**) is a way to understand how data travels from one device to another over a network.

_Analogy:_

_Sending a package:_
_- You write a messsage -> Pack it -> Send it -> Transport -> Deliver -> Open_

### The 7 Layers (Top <-> Bottom)

**7. Application Layer(User Level)**

 What you see and use (Browser,apps,email)
 Example: Opening a chrome, YouTube

 **6. Presentation Layer(Formatting)**

 Makes data readable 
 - Encryption/Decryption
 - Compression 

**Example: HTTPS encryption**

**5. Session Layer (Connection Manager)**

Starts and ends communication
**Example: Logic ssession on a website**

**4. Transport Layer(Delivery Control)**

Ensures data is delivered properly
- TCP(reliable)
- UDP(Fast)
  
**Example: Video call vs File download**

**3. Network Layer(Routing)**

Finds the path
- Uses IP addresses
**Example: Sending data from India -> USA**

**2. Data Link Layer(Local delivery)**

Works inside your network
  - Uses MAC address
**Examples: Laptop -> Router**

**1. Physical Layer(Hardware)**

Actual transmission
- Cables, signals,Wi-Fi
**Example: Wi-Fi signals, Ethernet cable**

**Memory Trick**

**All people seems to need data processing**

|Word|Meaning|
|----|--------|
|All|Application|
|People|Presentation|
|Seems| Session Layer|
|To| Transport|
|Need|Network|
|Data|Data link|
|Processing|Physical|
