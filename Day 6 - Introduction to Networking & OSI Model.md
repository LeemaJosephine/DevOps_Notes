# Day 6 - Introduction to Networking & OSI Model

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

## OSI Model 

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
