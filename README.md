# DDoS Incident Report: ICMP Flood Attack

## Executive Summary

The organization experienced a Distributed Denial of Service (DDoS) attack that flooded the internal network with Internet Control Message Protocol (ICMP) packets. As a result, the network was out of service for approximately two hours. The incident was mitigated by blocking incoming `ICMP` packets, taking nonessential services offline, and restoring critical network services. A later investigation found that the `ICMP` flood entered through an unconfigured firewall.

## 1. Identify (The Attack)

*   **Attack Type:** `DDoS` attack using an `ICMP` packet flood.
*   **Cause:** An unconfigured `firewall rule` allowed malicious `ICMP` packets into the network.
*   **Impact:** Internal network services (file shares, email, internal web apps) became unresponsive for approximately two hours. No evidence of data integrity loss.
*   **Affected Systems:** Perimeter firewall, edge router, core/distribution switches (high CPU), on-prem application servers, DNS/DHCP, and VPN concentrator.

## 2. Protect (Vulnerability Remediation)

To address this vulnerability and strengthen network protection, the team implemented:

*   A new `firewall rule` to limit the rate of incoming `ICMP` packets.
*   Source `IP address verification` on the firewall to check for spoofed `IP addresses`.

## 3. Detect (Future Detection Improvements)

To improve detection of similar attacks in the future, the organization implemented:

*   Network monitoring software to detect abnormal traffic patterns.
*   An `Intrusion Detection and Prevention System (IDS/IPS)` to filter suspicious `ICMP` traffic.
*   `SIEM alerts` configured for sudden `ICMP volume spikes` and traffic from non-trusted sources.

## 4. Respond (Incident Response Actions)

During the incident, the team responded by:

*   Blocking incoming `ICMP` packets to stop the traffic flood.
*   Taking non-critical services offline to preserve system stability.
*   Assigning roles: Incident Commander, Network Lead, Comms Lead, and Scribe.
*   Preserving evidence, including flow records and `firewall/IDS logs`.

## 5. Recover (Recovery Process)

After containing the attack, the organization:

*   Restored affected critical network services to normal operation.
*   Verified that network services were functioning properly.
*   Restored core network devices from verified configuration backups.
*   Re-enabled critical services (`DNS`, `DHCP`, `VPN`, etc.) in a staged manner.

## Reflections / Key Takeaways

This incident demonstrated how a single unconfigured firewall can lead to major network disruption. Implementing proper `firewall configurations`, consistent monitoring, and periodic audits are essential. The organization should develop a formal `incident response playbook` and conduct periodic tabletop exercises to practice a coordinated response.