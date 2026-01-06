# Wireshark Lab Notes — UW Info Assurance (2022)

## Goal
Capture & understand normal HTTP traffic vs. signs of trouble.

## What I Did
1. Opened Wireshark → started capture on Wi-Fi interface  
2. Visited http://example.com (no HTTPS — to see raw traffic!)  
3. Stopped capture, filtered: `http`

## Key Observations
- ✅ **3-way handshake**: SYN → SYN-ACK → ACK (before data flows)  
  → If missing, connection fails → user sees "site not loading"
- ✅ **HTTP GET request**: Shows full URL, user-agent (e.g., Chrome version)  
- ✅ **TCP Retransmission** (red in Wireshark) = packet loss → could be Wi-Fi interference

## Real-World Takeaway
When a user says “some sites load, some don’t,” check:
- Is it *only* HTTPS sites? → Could be system clock wrong (breaks TLS)  
- Do `ping 8.8.8.8` — if that works, it’s likely DNS or browser, not network

> Lab done on home network, Ubuntu 20.04 VM. No sensitive data captured.
