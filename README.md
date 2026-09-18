# SBT-DF203 Lab 3 - SYN Flood Pattern Investigation Using TShark

## Overview
This lab investigates TCP SYN flood activity against a training Apache web service. The investigation establishes a normal handshake baseline, performs a bounded 4-packet loopback simulation using Scapy, analyses the supplied training PCAP and identifies incomplete-handshake indicators using TShark.

## Investigator
- **Name:** Adeleye Ademiluyi Timilehin
- **Registration:** 2025/FWSD/11459
- **Course:** SBT-DF203 Basic Networking Skills for Digital Forensics
- **Lab:** Lab 3 — SYN Flood Pattern Investigation Using TShark
- **Deadline:** 11 September 2026

## Evidence Files
- **mySYNFloodCapture.pcap** — Supplied training PCAP (255KB, 4 packets)
- **normal_http.pcapng** — Normal HTTP baseline capture (10 packets)
- **bounded_syn_activity.pcapng** — Bounded 4-packet simulation (12 packets)

## Evidence Hashes
| File | SHA-256 |
|---|---|
| mySYNFloodCapture.pcap | 14765b029a72e9c41dd8b4d32f5b1d2c7d9efee0f084949151f183a39baa55f5 |
| bounded_syn_activity.pcapng | ac88da9466647ae3576017387ef975b05204fab38e0636093cec7b4957166937 |

## Tools Used
- **tshark** — Packet capture and analysis
- **Scapy** — Bounded 4-packet SYN simulation
- **Apache2** — Target service for baseline capture
- **sha256sum** — Evidence integrity verification

## Safety Declaration
The bounded simulation was limited to exactly 4 SYN packets sent to 127.0.0.1:80 only. No external systems were targeted. The simulation was stopped immediately after the required evidence was captured.

## Key Findings
- Normal handshake: SYN → SYN-ACK → ACK → HTTP data → FIN-ACK closure
- SYN flood pattern: Multiple SYNs from random ports → SYN-ACK → no final ACK
- 4 unique source ports identified: 10980, 12538, 15770, 16211
- RST packets confirm OS had no record of Scapy-initiated connections
- Supplied PCAP contained 65,054-byte SYN packets — 877x larger than normal
- Expert analysis: 4 RST warnings + 4 SYN-without-SACK-PERM notes

## Parts Completed
- **Part A** — Normal HTTP baseline captured and analysed
- **Part B** — Bounded 4-packet Scapy simulation performed
- **Part C** — Initial SYNs, SYN-ACKs and RSTs identified
- **Part D** — Quantitative analysis — counts, unique ports, expert info
- **Part E** — Normal vs suspicious comparison table completed

## Submission Package
- PDF Report: SBT-DF203-Lab3_2025FWSD11459_AdeleyelAdemiluyi.pdf
- ZIP Package: SBT-DF203-Lab3_2025FWSD11459_AdeleyelAdemiluyi.zip

## GitHub Repository
https://github.com/Adeleye001/SBT-DF203-Lab3-SYNFlood-Investigation
