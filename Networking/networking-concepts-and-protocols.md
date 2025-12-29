# TryHackMe – Networking Concepts & Protocols Notes

These notes document **what I learned and practiced** while completing the **Networking rooms on TryHackMe**.  
They cover core networking models, IP addressing, transport protocols, packet flow, and hands-on interaction with common network services using the command line.

---

## 1. Networking Models

### OSI Model (7 Layers)

The OSI model is a conceptual framework that explains how data moves through a network.

| Layer | Name | Responsibility |
|------|------|---------------|
| 7 | Application | User interaction (HTTP, FTP) |
| 6 | Presentation | Encoding, encryption, compression |
| 5 | Session | Session management |
| 4 | Transport | Reliable/unreliable delivery (TCP/UDP) |
| 3 | Network | Routing using IP addresses |
| 2 | Data Link | MAC addressing, local delivery |
| 1 | Physical | Cables, signals, hardware |

**Key Answers I Learned**
- Application-to-application communication → **Layer 4**
- Packet routing → **Layer 3**
- Encoding application data → **Layer 6**
- Same network segment delivery → **Layer 2**

---

### TCP/IP Model (4 Layers)

| TCP/IP Layer | OSI Mapping |
|-------------|-------------|
| Application | OSI Layers 5–7 |
| Transport | OSI Layer 4 |
| Internet | OSI Layer 3 |
| Link | OSI Layers 1–2 |

- HTTP belongs to the **Application Layer**
- TCP/IP Application layer covers **3 OSI layers**

---

## 2. IP Addresses & Subnetting

### IPv4 Basics
- IPv4 = **32-bit address**
- Written as four octets (e.g., `192.168.66.89`)

### Subnet Masks
- `255.255.255.0` = `/24`
- Network range: `192.168.66.1 – 192.168.66.254`
- Network address: `.0`
- Broadcast address: `.255`

### Private IP Ranges (RFC 1918)
- `10.0.0.0/8`
- `172.16.0.0/12`
- `192.168.0.0/16`

✔ **Not private:** `49.69.147.197`  
❌ **Invalid IP:** `192.168.305.19`

---

## 3. Routing

- Routers operate at **Layer 3**
- They inspect **destination IP addresses**
- Forward packets toward the best next hop

---

## 4. Transport Layer Protocols

### UDP vs TCP

| Protocol | 특징 |
|--------|------|
| UDP | Fast, unreliable (streaming, VoIP) |
| TCP | Reliable, ordered, error-checked |

### TCP Three-Way Handshake
1. SYN
2. SYN-ACK
3. ACK

- Valid ports range: **1–65535**
- Approximate number of ports: **65 thousand**

---

## 5. Encapsulation

Encapsulation is the process of wrapping data with headers at each layer:

1. Application Data
2. TCP Segment / UDP Datagram
3. IP Packet
4. Ethernet/WiFi Frame

**Key Answers**
- IP packet is encapsulated in a **Frame**
- UDP unit → **Datagram**
- TCP unit → **Segment**

---

## 6. DHCP (Dynamic Host Configuration Protocol)

Automatically assigns:
- IP Address
- Subnet Mask
- Gateway
- DNS

### DHCP Process (DORA)
1. Discover
2. Offer
3. Request
4. Acknowledge

**Important Details**
- Source IP: `0.0.0.0`
- Destination IP: `255.255.255.255`
- Total steps: **4**

---

## 7. ARP (Address Resolution Protocol)

Maps **IP addresses → MAC addresses**

- ARP Request → Broadcast (`ff:ff:ff:ff:ff:ff`)
- ARP Reply → Unicast with MAC address

✔ MAC of `192.168.66.1`: `44:df:65:d8:fe:6c`

---

## 8. ICMP (Ping & Traceroute)

### Ping
- ICMP Type 8 (Echo Request)
- ICMP Type 0 (Echo Reply)
- Used for connectivity testing

### Traceroute
- Uses **TTL**
- Routers decrement TTL
- When TTL = 0 → ICMP Time Exceeded

✔ Bytes sent in ping request: **40**  
✔ Header field used by traceroute: **TTL**

---

## 9. Telnet (Hands-On Practice)

Used Telnet to manually interact with services.

### Echo Server (Port 7)

telnet 10.10.63.37 7

### Daytime Server (Port 13)

Returns current date & time.

### HTTP via Telnet (Port 80)

GET / HTTP/1.1
Host: telnet.thm

## 10. DNS

- Resolves domain names to IP addresses
- Uses UDP port 53
- Runs at Application Layer

### DNS Records
- A → IPv4
- AAAA → IPv6
- MX → Mail server
- CNAME → Alias

## 11. HTTP & HTTPS

- Protocol	Port	Security
- HTTP	80	Plaintext
- HTTPS	443	Encrypted (TLS)

### HTTPS Flow
- TCP Handshake
- TLS Handshake
- HTTP over TLS

## 12. FTP

- FTP uses TCP port 21
- Anonymous login possible
- Separate control & data channels

## 13. Email Protocols

### SMTP (Send Mail)
- Port 25
- Key command: DATA
- End of message: .

### POP3 (Retrieve Mail)
- Port 110
- Server: Dovecot

### IMAP (Sync Mail)
- Port 143
- Retrieve command: FETCH <num> body[]

## 14. Securing Protocols with TLS
- TLS is the upgraded and more secure version of SSL.

| Insecure Protocol (Port) | Secure Protocol (Port) |
|--------------------------|------------------------|
| HTTP (80)                | HTTPS (443)            |
| FTP (21)                 | FTPS (990)             |
| Telnet (23)              | SSH (22)               |
| SMTP (25)                | SMTPS (465 / 587)      |
| POP3 (110)               | POP3S (995)            |
| IMAP (143)               | IMAPS (993)            |

### 15. SSH, SFTP & VPN

### SSH
- Secure remote login
- Port 22
- Open-source implementation: OpenSSH

### SFTP
- Secure file transfer over SSH

### VPN
- Creates encrypted tunnel
- Hides real IP
- Used for remote access between offices
