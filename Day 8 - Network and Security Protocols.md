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
- NACL **(Stateless, subnet level)**

_**Two Scenario:**_
- **SG (allow), NACL (Blocks)**
- **SG (Blocks), NACL (Allows)**

Step 1: Launch an EC2 instance (Include 8080 port)

Step 2: Connect to EC2 instance

Step 3 Connect to webserver

```
python3 -m http.server 8080
```
<img width="514" height="92" alt="image" src="https://github.com/user-attachments/assets/833d2751-4b96-4940-8894-32e2fd4004df" />
</br>

<img width="413" height="254" alt="image" src="https://github.com/user-attachments/assets/4ded5237-5551-4cb9-bd15-fb8e54559d16" />
</br>

Step 4: Identify subnet NACL 
  - Can be found in networkING -> Open subnet id -> Network ACL

**SG (allow), NACL (Blocks)**

Step 5: Add inbound rule to block at NACL leve
  - Open Network ACL in new tab -> Inbound rules -> Edit inbound rules 

<img width="959" height="291" alt="image" src="https://github.com/user-attachments/assets/42e7212b-519b-4765-af8b-3cde3cfba6cb" />

</br>

**SG (Blocks), NACL (Allows)**

Step 5: Remove the inbound rule that block at NACL level

<img width="959" height="281" alt="image" src="https://github.com/user-attachments/assets/ea19185a-321b-4312-a104-4e2624601f44" />
</br>

Step 6: Remove the Security 
  - Go to instance -> Security -> Inbound rules -> Remove 8080 port range if it is allowed already.
    <img width="959" height="362" alt="image" src="https://github.com/user-attachments/assets/7abb4f7e-702e-4bf1-9c3a-3ddded3c906b" />
</br>

After removing:
<img width="959" height="308" alt="image" src="https://github.com/user-attachments/assets/d45b84c9-ab9f-4201-a5f0-9c50578b5bcf" />
</br>

**NACL (Stateless)**
- Works at subnet level
- Need rules for.
    - Inbound
    - Outbound

**Security Group (Stateful)**
- Works at instance level
- Automatically allows return traffic

**Scenario 3: Inbound is allowed but response still fails**

Allow all the inbound rules in SG level and NACL level -> Break the outbound traffic in NACL level

<img width="959" height="305" alt="image" src="https://github.com/user-attachments/assets/39c30fa1-45b7-4516-9964-e358b5b41538" />
</br>  
