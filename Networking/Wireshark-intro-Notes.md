# TryHackMe – Wireshark: The Basics (Learning Notes)

These notes document my learning and hands-on practice from the **TryHackMe – Wireshark: The Basics** room.  
The focus of this room was understanding Wireshark’s interface, packet structure, navigation, filtering, and basic investigation techniques using PCAP files.

---

## Task 1: Introduction

Wireshark is an **open-source, cross-platform network packet analyser** used to capture and inspect live traffic and PCAP files.  
It is widely used for **network troubleshooting, security analysis, and protocol investigation**.

### Files Used
- **Screenshot simulation file:** `http1.pcapng`
- **Question & exercise file:** `Exercise.pcapng`

---

## Task 2: Tool Overview

### Use Cases of Wireshark
- Troubleshooting network issues (latency, congestion, failures)
- Detecting security anomalies (rogue hosts, suspicious traffic)
- Learning protocol behavior (headers, response codes, payloads)

> Wireshark is **not an IDS**. It does not block or modify traffic — analysis depends on the analyst’s skills.

---

### Wireshark GUI Overview

Key interface components:
- **Toolbar** – Packet capture, filtering, exporting, and statistics
- **Display Filter Bar** – Apply display filters
- **Recent Files** – Quickly open previously analysed captures
- **Capture Interfaces** – Select network interfaces for sniffing
- **Status Bar** – Packet count, profile, and interface details

---

### Packet Panes
- **Packet List Pane** – Summary of packets (IP, protocol, info)
- **Packet Details Pane** – Layer-by-layer protocol breakdown
- **Packet Bytes Pane** – Hex and ASCII representation

---

### Colouring Packets
Wireshark uses colouring rules to quickly identify protocols and anomalies.
- **Temporary rules** – Active only during the session
- **Permanent rules** – Saved in the user profile

---

### Traffic Sniffing
- **Blue shark icon** → Start capture
- **Red button** → Stop capture
- **Green button** → Restart capture

---

### Merge PCAP Files
- Combine multiple capture files using  
  `File → Merge`
- A new merged PCAP file must be saved before analysis

---

### Capture File Details

Using `Statistics → Capture File Properties`:
- File comments
- Capture time
- Interface details
- Hash values

#### Answers
- **Capture file comment flag:** `TryHackMe_Wireshark_Demo`
- **Total packets:** `58620`
- **SHA256 hash:**  
  `f446de335565fb0b0ee5e5a3266703c778b2f3dfad7efeaeccb2da5641a6d6eb`

---

## Task 3: Packet Dissection

Packet dissection (protocol dissection) breaks packets into OSI layers.

### Packet Layers Observed
1. Frame (Physical)
2. Source & Destination MAC (Data Link)
3. Source & Destination IP (Network)
4. Transport Protocol (TCP/UDP)
5. Application Protocol (HTTP, FTP, etc.)
6. Application Data

---

### Exercise Answers
- **Packet 38 markup language:** eXtensible Markup Language (XML)
- **Packet arrival date:** `05/13/2004`
- **TTL value:** `47`
- **TCP payload size:** `424`
- **HTTP e-tag value:** `9a01a-4696-7e354b00`

---

## Task 4: Packet Navigation

### Key Features
- **Go To Packet** – Navigate using packet numbers
- **Find Packet** – Search by string, hex, regex, or display filter
- **Mark Packets** – Highlight packets of interest
- **Packet Comments** – Persistent notes inside PCAP files
- **Export Packets** – Extract scoped traffic
- **Export Objects** – Extract files transferred over protocols
- **Time Display Format** – Change timestamp format
- **Expert Info** – Highlights warnings, errors, and anomalies

---

### Exercise Answers
- **Artist name (search string `r4w`):** `r4w8173`
- **MD5 hash of extracted JPEG:**  
  `911cd574a42865a956ccde2d04495ebf`
- **Alien’s name in `.txt` file:** `PACKETMASTER`
- **Number of warnings (Expert Info):** `1636`

---

## Task 5: Packet Filtering

Wireshark supports two filtering methods:
- **Capture Filters** – Applied during capture
- **Display Filters** – Applied after capture

### Filtering Techniques
- **Apply as Filter** – Filter based on selected field
- **Conversation Filter** – View all packets in a conversation
- **Colourise Conversation** – Highlight related packets
- **Prepare as Filter** – Build filter without applying it
- **Apply as Column** – Add packet fields as columns
- **Follow Stream** – Reconstruct application-level data

---

### Exercise Answers
- **Filter query applied:** `http`
- **Displayed packets:** `1089`
- **Total artists in stream:** `3`
- **Second artist name:** `Blad3`

---

## Task 6: Conclusion

This room provided a strong foundation in:
- Wireshark interface navigation
- Packet dissection using OSI layers
- Packet searching, marking, and commenting
- Filtering and stream reconstruction
- Extracting files and analysing anomalies

This hands-on practice strengthened my **network traffic analysis and cybersecurity investigation skills**.

---

📌 **Next Step:** Wireshark – Packet Operations  
⚠️ Notes created for educational and learning purposes only.
