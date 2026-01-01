# 🛡️ Nmap Mastery: Network Discovery & Port Scanning

A comprehensive guide to host discovery, port scanning, and service enumeration using **Nmap**. This repository documents practical learning from the TryHackMe Nmap modules, focusing on real-world application and packet-level behavior.

---

## 📡 1. Host Discovery (Finding Online Systems)
Before scanning for ports, we must identify which hosts are alive.

| Target Type | Example Syntax |
| :--- | :--- |
| **IP Range** | `192.168.0.1-10` |
| **Subnet (CIDR)** | `192.168.0.0/24` |
| **Hostname** | `example.thm` |

### Key Discovery Flags:
* `-sn`: **Ping Scan**. Disables port scanning.
  * **Local Network:** Uses ARP requests to find hosts.
  * **Remote Network:** Uses ICMP Echo, TCP SYN (port 443), and TCP ACK (port 80).
* `-sL`: **List Scan**. Simply lists targets without sending any packets to them.
* `-Pn`: **No Ping**. Skips host discovery and treats all hosts as online (useful for bypassing firewalls that block ICMP).

---

## 🔍 2. Port Scanning Techniques
Once a host is found, we scan it to find open services.



### TCP Scanning
* **`-sT` (Connect Scan):** Completes the full TCP 3-way handshake. Used by default for users without root/sudo privileges.
* **`-sS` (SYN/Stealth Scan):** Sends a SYN but resets the connection (`RST`) after receiving a `SYN-ACK`. Faster and less likely to be logged. Requires root privileges.

### UDP Scanning
* **`-sU` (UDP Scan):** Scans for services like DNS (53) or SNMP (161). Since UDP is connectionless, Nmap identifies "open" ports by the *absence* of an `ICMP Port Unreachable` response.

### Port Selection
* `-F`: Fast mode (scans the top 100 most common ports).
* `-p-`: Scans all 65,535 ports.
* `-p80,443,8008`: Scans specific ports.

---

## ⚙️ 3. Version & OS Detection
Moving beyond just "open" or "closed," we identify what is actually running.

* **`-sV` (Service Version):** Probes open ports to determine software versions (e.g., `OpenSSH 8.9p1`).
* **`-O` (OS Detection):** Fingerprints the TCP/IP stack to guess the Operating System.
* **`-A` (Aggressive):** Enables OS detection, version detection, script scanning, and traceroute in one command.

---

## ⏱️ 4. Timing & Performance
Control the speed of your scan to manage network load or avoid detection.

| Template | Name | Use Case |
| :--- | :--- | :--- |
| **-T0 / -T1** | Paranoid / Sneaky | Avoiding IDS/Firewall detection. |
| **-T2 / -T3** | Polite / Normal | Default behavior. |
| **-T4** | **Aggressive** | Recommended for fast, reliable networks. |
| **-T5** | Insane | Extremely fast; may miss ports or crash services. |

* **Rate Limiting:** Use `--min-rate <number>` to force Nmap to send packets at a specific speed.

---

## 💾 5. Output Formats
Always save your results for documentation and reporting.

* `-oN`: **Normal** output (human-readable).
* `-oX`: **XML** output (best for importing into other tools).
* `-oG`: **Grepable** output (best for command-line filtering).
* `-oA`: **All formats**. Saves results in all three major formats simultaneously.
* `-v / -vv`: Increase **Verbosity** to see open ports in real-time.
* `-d`: Enable **Debugging** for deep troubleshooting.

---

## 🛠️ Lab Examples & Answers
* **Target Range:** `192.168.0.1/27` scans up to `.31`.
* **Detected Web Server:** `lighttpd 1.4.74` on port `8008`.
* **Privilege Impact:** If run without `sudo`, Nmap defaults to a **Connect Scan (`-sT`)** because raw socket creation (for SYN scans) requires root access.

---
*Authored by a Security Learner | Guided by TryHackMe*
