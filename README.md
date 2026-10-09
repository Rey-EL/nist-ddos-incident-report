# NIST DDoS Incident Report

I wrote this formal incident report as a lab exercise. The scenario: a DDoS attack takes down an organization's internal network for two hours. I worked through the full incident and structured the report around the five functions of the NIST Cybersecurity Framework.

## Executive summary

An ICMP flood overwhelmed the internal network and knocked out file shares, email, and internal web apps for about two hours. The root cause was a firewall rule that was never configured. I contained it by blocking ICMP at the edge and taking non-essential services offline. No data was stolen or altered.

## 1. Identify: attack analysis

- **Attack type:** DDoS using an ICMP packet flood.
- **Root cause:** A missing firewall rule let malicious ICMP traffic straight in.
- **Business impact:** Internal services down for roughly two hours. No evidence of data theft or tampering.
- **Affected systems:** Perimeter firewall, edge router, core switches, application servers, DNS/DHCP servers, VPN concentrator.

## 2. Protect: fixes to prevent a repeat

- Added a firewall rule to rate-limit incoming ICMP.
- Turned on source IP verification (anti-spoofing) on the perimeter firewall.

## 3. Detect: catching it next time

- Network monitoring to baseline normal traffic and flag anomalies.
- IDS/IPS tuned to filter and alert on suspicious ICMP traffic.
- SIEM alerts for sudden ICMP volume spikes and traffic from untrusted sources.

## 4. Respond: what I did during the incident

- **Containment:** Blocked all incoming ICMP at the network edge.
- **Stabilization:** Took non-critical services offline to protect resources.
- **Coordination:** Assigned clear roles: Incident Commander, Network Lead, and the rest.
- **Preservation:** Collected flow records and firewall/IDS logs as evidence.

## 5. Recover: getting services back

- Restored and verified critical services (DNS, DHCP, VPN) first.
- Checked core device configs against known-good backups.
- Brought services back online in stages while watching for instability.

## What this shows

I can take a messy incident and turn it into a clear, structured report. I know how to apply the NIST CSF five functions, pick the right technical controls for a network attack, and lay out containment and recovery in the order they actually happen.

## License

MIT License. See [LICENSE.md](LICENSE.md) for details.
