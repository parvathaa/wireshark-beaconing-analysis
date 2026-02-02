# wireshark-beaconing-analysis
Detecting Command-and-Control Beaconing via Network Traffic Analysis

Overview

This project documents a network traffic investigation conducted using a public PCAP file.
The objective was to identify **command-and-control (C2) beaconing behavior** originating from an internal host by analyzing outbound traffic patterns, timing regularity, and protocol structure using Wireshark.

The analysis follows a **host-centric detection approach**, mirroring how SOC analysts investigate suspicious outbound activity in real environments.

Objective

* Analyze a packet capture from a Windows enterprise network
* Identify suspicious outbound communication indicative of beaconing
* Isolate the affected internal host
* Extract defensible Indicators of Compromise (IOCs)
* Document findings in an incident-report style format

Skills Demonstrated

* Network traffic analysis (Wireshark)
* Host-centric investigation methodology
* Beaconing & C2 behavior detection
* Timing and pattern analysis
* IOC extraction and validation
* Incident reporting fundamentals (blue team)

Tools & Environment

Wireshark
Public PCAP dataset from *malware-traffic-analysis.net*

Methodology

1. Scoping Outbound Traffic

The analysis began by filtering traffic to focus exclusively on **internal-to-external communication**, removing:

* Broadcast traffic
* Multicast traffic
* Internal-only LAN chatter

This step reduced noise and enforced a clear trust-boundary perspective.

2. Host-Centric Analysis

Instead of focusing on “suspicious destinations,” traffic was evaluated **per internal host**.

Using conversation statistics, one internal host consistently appeared across outbound communications, making it a strong candidate for deeper inspection.

Outbound conversation dominance
![Conversations view](images/conversations.png)

3. Timing & Periodicity Analysis

Traffic from the suspected host was graphed over time to evaluate **regularity and automation**.

The I/O graph revealed **evenly spaced outbound activity**, a strong indicator of machine-driven behavior rather than human interaction.

Consistent outbound timing**
![I/O Graph](images/io-graph.png)

4. Protocol & Structure Validation

Outbound HTTP traffic from the host was isolated and examined for structural consistency.

Findings included:

* Repeated HTTP requests
* Same destination endpoint
* Similar request size and structure
* Fixed timing intervals (~4 seconds)

Repeated outbound HTTP requests**
![HTTP pattern](images/http-pattern.png)

5. Flow Direction Confirmation

A TCP flow graph was used to confirm **who initiates communication** and whether the interaction follows a predictable request-response loop.

The internal host consistently initiated outbound connections, reinforcing the beaconing hypothesis.

Automated request-response flow
![Flow graph](images/flow-graph.png)

Indicators of Compromise (IOCs)

Indicators listed are limited to those directly observable and relevant to the identified behavior.

* **Internal Host:** `10.8.15.133`
* **External IP:** `72.5.43.29`
* **Protocol:** HTTP
* **Behavior:** Repeated outbound requests at fixed intervals
* **Characteristic:** Automated, low-variance request structure

