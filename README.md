# nist-ddos-incident-report

This project demonstrates my ability to analyze a security incident and structure a formal report using the five functions of the **NIST Cybersecurity Framework**. The scenario involves a Distributed Denial-of-Service (DDoS) attack that disrupted an organization's network.

---

## Executive Summary

The organization experienced a DDoS attack that flooded the internal network with ICMP packets, causing a two-hour network outage. The root cause was an unconfigured firewall rule. The incident was mitigated by blocking ICMP traffic and taking non-essential services offline. This report breaks down the incident and response according to the NIST Cybersecurity Framework.

---

### 1. Identify: Attack Analysis

*   **Attack Type:** DDoS attack using an ICMP packet flood.
*   **Root Cause:** An unconfigured firewall rule allowed malicious ICMP packets into the network.
*   **Business Impact:** Internal network services (file shares, email, internal web apps) were unresponsive for approximately two hours. No evidence of data exfiltration or integrity loss was found.
*   **Affected Systems:** Perimeter firewall, edge router, core switches, application servers, DNS/DHCP servers, and VPN concentrator.

### 2. Protect: Vulnerability Remediation

To prevent a recurrence, the following protective controls were implemented:
*   A new firewall rule was deployed to rate-limit incoming ICMP packets.
*   Source IP address verification (anti-spoofing) was enabled on the perimeter firewall.

### 3. Detect: Future Detection Capabilities

To improve the timely detection of similar attacks, the following systems were implemented:
*   Network monitoring software to baseline traffic patterns and detect anomalies.
*   An Intrusion Detection and Prevention System (IDS/IPS) configured to filter and alert on suspicious ICMP traffic.
*   SIEM alerts tuned to trigger on sudden ICMP volume spikes and traffic from untrusted sources.

### 4. Respond: Incident Response Actions

During the incident, the team took the following immediate actions:
*   **Containment:** Blocked all incoming ICMP packets at the network edge.
*   **Stabilization:** Took non-critical services offline to preserve system resources.
*   **Coordination:** Assigned formal incident response roles (Incident Commander, Network Lead, etc.).
*   **Preservation:** Collected and preserved evidence, including network flow records and firewall/IDS logs.

### 5. Recover: Service Restoration Process

After containing the threat, the recovery process involved:
*   Restoring and verifying critical network services (DNS, DHCP, VPN).
*   Validating core network device configurations against known-good backups.
*   Performing a staged re-enabling of all services while monitoring for instability.

---

## Summary of Skills Demonstrated

This exercise showcases understanding and application of:
*   **Incident Analysis:** Deconstructing a security incident to identify the attack vector, root cause, and business impact.
*   **NIST Cybersecurity Framework:** Structuring an incident report and response plan according to the five core functions (Identify, Protect, Detect, Respond, Recover).
*   **Network Security:** Recommending specific technical controls like firewall rules, rate-limiting, and IDS/IPS configurations.
*   **Incident Response & Recovery:** Outlining the formal steps required to contain a threat, respond effectively, and restore services.

---

## Security Context

This incident report underscores the critical importance of maintaining system availability, a core component of the CIA (Confidentiality, Integrity, Availability) triad. DDoS attacks, while primarily impacting availability, can also serve as a smokescreen for more sophisticated attacks aimed at exploiting other vulnerabilities, including those found in the OWASP Top 10 (e.g., data exfiltration facilitated by a distracted security team). Effective incident response, as outlined by the NIST framework, is crucial for mitigating the immediate impact of such attacks and preventing further compromise.

---

## License

This project is licensed under the [MIT License](./LICENSE.md) - see the LICENSE.md file for details.

---

## Contributing

Contributions are welcome! If you have suggestions for improvements or want to enhance the report, please feel free to open an issue or submit a pull request.
