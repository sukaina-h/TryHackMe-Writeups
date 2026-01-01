# 🛠️ Tcpdump Mastery: Network Analysis & Filtering

A comprehensive reference guide for capturing and analyzing network traffic using `tcpdump`. This documentation covers everything from basic syntax to advanced bitwise operations on TCP flags.

---

## 📌 1. Basic Operations
The foundation of packet capture.

| Command | Description |
| :--- | :--- |
| `tcpdump -i [interface]` | Capture on a specific interface (e.g., `eth0`, `any`). |
| `tcpdump -n` | **Numeric format:** Disables DNS resolution for speed. |
| `tcpdump -nn` | Disables both DNS and port name resolution. |
| `tcpdump -w file.pcap` | Saves the capture to a file for later analysis. |
| `tcpdump -r file.pcap` | Reads and displays packets from a saved `.pcap` file. |
| `tcpdump -c [count]` | Stops after capturing a specific number of packets. |

---

## 🔍 2. Filtering Expressions
Use filters to isolate specific traffic and reduce "noise."

### Host & Port Filtering
* **Specific Host:** `tcpdump host 1.1.1.1`
* **Directional:** `tcpdump src host 10.10.1.1` or `tcpdump dst host 10.10.1.2`
* **Port Specific:** `tcpdump port 80` (or `src port` / `dst port`)

### Protocol Filtering
Filter by the protocol name directly:
* `tcpdump icmp`
* `tcpdump udp`
* `tcpdump arp`

### Logical Operators
* **AND:** `tcpdump host 192.168.1.1 and port 443`
* **OR:** `tcpdump udp or icmp`
* **NOT:** `tcpdump not tcp`

---

## ⚡ 3. Advanced Header & Bitwise Filtering
To find specific packet states (like TCP flags), we use header byte offsets: `proto[offset:size]`.



### TCP Flag Filtering
| Goal | Filter Syntax |
| :--- | :--- |
| **Only SYN set** | `tcpdump "tcp[tcpflags] == tcp-syn"` |
| **Only RST set** | `tcpdump "tcp[tcpflags] == tcp-rst"` |
| **At least SYN set** | `tcpdump "tcp[tcpflags] & tcp-syn != 0"` |
| **SYN or ACK set** | `tcpdump "tcp[tcpflags] & (tcp-syn\|tcp-ack) != 0"` |

### Packet Length
Find anomalies or data transfers based on size:
* `tcpdump greater 15000` (Packets larger than 15,000 bytes)
* `tcpdump less 64` (Small packets, often used in scanning/heartbeats)

---

## 👁️ 4. Data Display & Inspection
Customize how packet data is rendered on your screen.

* `-e`: Show **MAC addresses** (Ethernet layer).
* `-A`: Display payload in **ASCII** (useful for reading HTTP/cleartext).
* `-xx`: Display data in **Hexadecimal**.
* `-X`: Display data in **both Hex and ASCII**.
* `-v`, `-vv`, `-vvv`: Increase the **verbosity** (detail) of the output.

---

## 🛠️ 5. Practical Lab Findings
Examples of troubleshooting and analysis performed during the learning process:

**Identifying ARP Requests:**
To find the MAC address of a host requesting an IP:
`tcpdump -r traffic.pcap arp -e`
*Result: 52:54:00:7c:d3:5b*

**Extracting DNS Queries:**
To see what hostnames are being looked up:
`tcpdump -r traffic.pcap port 53 -A`
*Result: mirrors.rockylinux.org*

**Counting Specific Traffic:**
Using `wc -l` to count instances:
`tcpdump -r traffic.pcap 'tcp[tcpflags] == tcp-rst' | wc -l`
*Result: 57 Reset packets found*

---
*Generated as part of a Network Security learning path.*
