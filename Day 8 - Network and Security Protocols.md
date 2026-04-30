# Day 8 - Network and Security Protocols

### Common Network Security Attacks (e.g., DDoS, Man-in-the-Middle)

### DDoS (Distributed Denial of Service)

Flood a server with massive traffic -> make it unavailable. 

**How it works:**
- Thousands of compromised machine (bonet)
- Send requests simultaneously
- Server resources exhausted

**Detection:**
- Sudden spike in traffic
- High CPU/Memory usage
- Many requests from different Ips

**Prevention:**
- Load balancer
- AWS Shield
- Use Cloudflare **(CDN (Content Delivery Network service)  + Security layer)** this is block un legimitic traffic
- Rate limiting **(Restricts number request per user/IP in a time window)**

### MITM (Man-In-The-Middle)

Attacker secretly intercepts communication.

**Example**

User -> Attacker -> Server

**Detection:**

- Unexpected certificate warnings
- Suspicious network behavior

**Prevention:**
- HTTPS(SSL/TLS)
- VPN
- Secure Wi-fi

**Malware/Ransomware**

Malicious software infects system

**Effect**

- Data theft
- File encryption

**Prevention**
  - Antivirus
  - Regular updates
  - Backup
 
**Phishing**

  Fake emails/websites to steal credentials

**Detection**

  - Suspicious
  - Fake domain

**Prevention**
- Use awareness
- Email filtering
---

### ACL - Access Control List

A set of rules that allow or deny traffic based in IP, protocol, port

Where ACLSs are used
- Network devices (router,switches)
- Cloud (AWS Network ACLs)
- Operating System (file ACLs also exist)

Example Rule:

ALLOW: 192.168.1.0/24
DENY: 0.0.0.0/0

Note: 
- Allow internal network
- Deny everything else

How ACL works
- Rules are checked from **Top - Bottom**
- First match is applied
- If no match -> default action (allow/deny)

### What are Firewall Rules?

Firewall rules are instruction that controls incoming and outgoing traffic

**Example:**
```
sudo iptables -A INPUT -p tcp -dport22 -j ACCEPT
```

### ACL Vs Firewall rules

|Feature|ACL|Firewall|
|--------|-----|------|
|Level| Network| OS/Cloud|
|Type|Stateless (Authorization at Inbound and outbound) |Stateful (Remembers the inbound authorization)|
|Rule Order|Strict order|Can be flexible|
|Complexity|Basic|Advanced|

**Hands-on-Demo:**

Allow in one layer and block in another layer and obser real behaviour in EC2

How traffic is controlled by multiple layers
- Security Group **(Stateful, instance-level)**
- NACL **(Stateless, submit level)**
  
---
### 
