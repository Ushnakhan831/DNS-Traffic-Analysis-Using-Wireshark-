DNS Traffic Analysis Using Wireshark
Overview


This type of analysis is commonly used in SOC (Security Operations Center) environments for threat detection, incident response, and network monitoring.

Objectives
Capture live network traffic using Wireshark
Analyze DNS queries and responses
Identify active domains visited during browsing
Detect DNS errors and failed queries
Investigate suspicious or unusual domains
Understand DNS behavior in real-world browsing activity
Tools Used
Wireshark
Web browser (Chrome/Edge/Firefox)
Internet connectivity for traffic generation
Methodology
1. Traffic Generation

To generate DNS traffic, multiple websites were visited for a few minutes, including:

google.com
youtube.com
facebook.com
github.com
tryhackme.com
microsoft.com

This browsing activity created real DNS queries and responses that were captured in Wireshark.

2. Packet Capture

Wireshark was started before browsing to capture all network traffic. After browsing, the capture file was saved for analysis.

3. DNS Analysis Filters Used

The following Wireshark filters were applied during analysis:

All DNS traffic:

dns

DNS Queries only:

dns.flags.response == 0

DNS Responses only:

dns.flags.response == 1

Specific domain search:

dns.qry.name contains "google"

DNS errors:

dns.flags.rcode != 0
IPv4 conversations and endpoints:
Statistics → Conversations / Endpoints
Findings
Total DNS Queries

Example: 120 queries observed during browsing session

Unique Domains Observed
google.com
youtube.com
github.com
microsoft.com
Most Active DNS Servers
8.8.8.8 (Google DNS)
1.1.1.1 (Cloudflare DNS)
DNS Errors

Example: 2–3 failed DNS queries detected during capture

Suspicious Domain Investigation

During analysis, DNS traffic was reviewed manually to identify any unusual or suspicious domains.

Suspicious Domain Record Format

If any suspicious domain is found, it should be documented like this:

Domain Name: abc123xyz.ru
Date Found: 30-May-2026
Tool Used: Wireshark
Protocol: DNS
Type: Suspicious / Unrecognized Domain
Notes: Domain does not match normal browsing activity and appears randomly generated. Requires further investigation.

How Suspicious Domains Are Identified

A domain is considered suspicious if it shows patterns like:

Random or meaningless characters
Unusual TLDs (e.g., .ru, .xyz in random contexts)
Not related to user browsing activity
Frequent failed requests
Repeated connection attempts
Skills Learned
DNS traffic analysis
Packet inspection using Wireshark
Network troubleshooting
Threat hunting basics
Identifying unusual domain behavior
SOC-style investigation workflow
Conclusion

This project demonstrates how DNS traffic can be analyzed to understand network activity and detect abnormal behavior. The analysis helped in identifying normal browsing patterns, DNS resolution flow, and potential suspicious domain activity. It provides a strong foundation for SOC and cybersecurity monitoring tasks.
