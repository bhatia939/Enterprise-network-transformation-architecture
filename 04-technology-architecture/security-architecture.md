# Security Architecture

## 1. Purpose

This document defines the target enterprise network security architecture for the Enterprise Network Transformation.

The architecture follows a defense-in-depth and Zero Trust approach, combining identity-based access, network segmentation, policy enforcement, secure connectivity, monitoring, and automated security controls.

---

## 2. Security Architecture Objectives

The security architecture aims to:

- Verify users and devices before granting access.
- Apply least-privilege access policies.
- Segment users, devices, applications, and services.
- Protect internal and external network communication.
- Provide centralized identity and policy management.
- Improve security visibility and monitoring.
- Support threat detection and response.
- Enable secure cloud and remote access.
- Support regulatory and compliance requirements.

---

## 3. Security Architecture Overview

```text
                         +------------------+
                         |     Users        |
                         |  Employees/Guest |
                         +--------+---------+
                                  |
                                  v
                         +--------+---------+
                         | Identity Layer   |
                         | Cisco ISE / IdP  |
                         +--------+---------+
                                  |
                                  v
                         +--------+---------+
                         | Access Control   |
                         | 802.1X / MAB     |
                         +--------+---------+
                                  |
                                  v
                    +-------------+-------------+
                    |                           |
             +------+-------+             +------+-------+
             | Campus SDA   |             | Wireless     |
             | Fabric       |             | Infrastructure|
             +------+-------+             +------+-------+
                    |                           |
                    +-------------+-------------+
                                  |
                                  v
                         +--------+---------+
                         | Segmentation     |
                         | VN / VRF / SGT   |
                         +--------+---------+
                                  |
                                  v
                         +--------+---------+
                         | Enforcement      |
                         | Firewall / ACL   |
                         +--------+---------+
                                  |
                    +-------------+-------------+
                    |                           |
                Data Center                  Cloud
````

---

# 4. Security Architecture Principles

The architecture follows these principles:

### 4.1 Zero Trust

No user or device should automatically be trusted based only on network location.

Access decisions should consider:

* User identity
* Device identity
* Device type
* Authentication status
* Security posture
* Application
* Location
* Business policy

---

### 4.2 Least Privilege

Users and devices should receive only the access required to perform their business function.

```text
User / Device
      |
      v
Authentication
      |
      v
Authorization
      |
      v
Minimum Required Access
```

---

### 4.3 Defense in Depth

Multiple security controls should protect enterprise resources.

```text
Identity
   ↓
Authentication
   ↓
Authorization
   ↓
Segmentation
   ↓
Firewall
   ↓
Monitoring
   ↓
Detection & Response
```

---

# 5. Security Architecture Layers

```text
+--------------------------------------+
| Governance & Compliance              |
+--------------------------------------+
| Monitoring & Incident Response       |
+--------------------------------------+
| Security Enforcement                 |
| Firewall / ACL / SGT                 |
+--------------------------------------+
| Network Segmentation                 |
| VN / VRF / VLAN / SGT                |
+--------------------------------------+
| Identity & Access                    |
| ISE / 802.1X / MAB                   |
+--------------------------------------+
| Network Infrastructure               |
| Campus / WAN / Wireless / Cloud      |
+--------------------------------------+
```

---

# 6. Identity and Access Architecture

Cisco ISE provides centralized identity-based access control.

```text
                    +----------------+
                    | Active Directory|
                    +--------+-------+
                             |
                             v
+----------+          +------+-------+
| Endpoint |----------| Cisco ISE    |
+----------+          +------+-------+
                             |
                 +-----------+-----------+
                 |                       |
                 v                       v
          Authentication           Authorization
                 |                       |
                 +-----------+-----------+
                             |
                             v
                      Network Access
```

---

## 6.1 Authentication Methods

The architecture supports:

* 802.1X
* MAB
* EAP-TLS
* PEAP
* Certificate-based authentication
* TACACS+
* RADIUS

---

## 6.2 Endpoint Profiling

ISE identifies endpoints using:

* MAC address
* DHCP information
* CDP
* LLDP
* HTTP attributes
* RADIUS attributes
* Network behavior

Example:

```text
Unknown Device
      |
      v
Endpoint Profiling
      |
      v
Device Classification
      |
      v
Authorization Policy
```

---

# 7. Network Access Control

```text
Endpoint
   |
   v
Access Switch / AP
   |
   | 802.1X / MAB
   v
Cisco ISE
   |
   +--> Authenticate
   |
   +--> Profile
   |
   +--> Authorize
   |
   +--> Assign Policy
   |
   v
Network Access
```

Access decisions may include:

* Permit
* Deny
* Quarantine
* Restricted access
* Guest access

---

# 8. Network Segmentation

Segmentation is implemented at multiple levels.

## Macro-Segmentation

Implemented using:

* Virtual Networks
* VRFs
* VLANs
* Firewalls

## Micro-Segmentation

Implemented using:

* Security Group Tags
* Scalable Group Policies
* Identity-based policies

```text
+------------------+
| Corporate Users  |
+--------+---------+
         |
         v
+--------+---------+
| Corporate VN     |
+------------------+

+------------------+
| IoT Devices      |
+--------+---------+
         |
         v
+--------+---------+
| IoT VN           |
+------------------+

+------------------+
| Guest Users      |
+--------+---------+
         |
         v
+--------+---------+
| Guest VN         |
+------------------+
```

---

# 9. Security Group Tag Architecture

```text
Endpoint
    |
    v
Cisco ISE
    |
    v
SGT Assignment
    |
    v
SDA Fabric
    |
    v
SGT-Based Policy
```

Example:

| Source SGT | Destination SGT  | Action |
| ---------- | ---------------- | ------ |
| Employee   | Application      | Permit |
| Employee   | Database         | Permit |
| Guest      | Internal Server  | Deny   |
| IoT        | Approved Service | Permit |
| Contractor | Sensitive Server | Deny   |
| Admin      | Network Device   | Permit |

---

# 10. Firewall Architecture

Firewalls provide security enforcement between trusted and untrusted zones.

```text
                 Internet
                    |
                    v
             +------+------+
             |  Firewall   |
             +------+------+
                    |
              DMZ / Services
                    |
             +------+------+
             | Internal LAN|
             +-------------+
```

Firewall controls may include:

* Stateful inspection
* Application control
* URL filtering
* IPS/IDS
* NAT
* VPN
* Threat prevention

---

# 11. Network Security Zones

Example security zones:

```text
+-------------------+
| Internet          |
+---------+---------+
          |
          v
+---------+---------+
| DMZ               |
+---------+---------+
          |
          v
+---------+---------+
| Corporate Network |
+---------+---------+
          |
          v
+---------+---------+
| Restricted Zone   |
+-------------------+
```

Typical zones include:

* Internet
* DMZ
* Corporate
* Guest
* IoT
* Management
* Server
* Restricted

---

# 12. Zero Trust Architecture

```text
User / Device
      |
      v
Verify Identity
      |
      v
Verify Device
      |
      v
Evaluate Context
      |
      v
Apply Least Privilege
      |
      v
Monitor Session
      |
      v
Continuous Evaluation
```

The architecture should avoid implicit trust based solely on:

* IP address
* VLAN
* Physical location
* Network segment

---

# 13. Wireless Security

Wireless security includes:

* WPA2-Enterprise
* WPA3-Enterprise
* 802.1X
* EAP-TLS
* Cisco ISE
* Guest isolation
* Rogue AP detection
* Wireless intrusion prevention

```text
Wireless Client
      |
      v
      AP
      |
      v
802.1X / RADIUS
      |
      v
Cisco ISE
      |
      v
Authorization
```

---

# 14. WAN Security

WAN security controls include:

* IPsec encryption
* SD-WAN security policies
* Firewalls
* Secure Internet breakout
* SASE integration
* Application-aware policies

```text
Branch
   |
   v
SD-WAN Edge
   |
   v
Encrypted Overlay
   |
   v
Data Center / Cloud
```

---

# 15. Remote Access Security

Remote users should be authenticated and authorized before accessing enterprise resources.

```text
Remote User
     |
     v
VPN / ZTNA
     |
     v
Identity Provider
     |
     v
Authentication
     |
     v
Policy Evaluation
     |
     v
Authorized Application
```

---

# 16. Management Plane Security

Network management access should be protected using:

* TACACS+
* MFA
* Role-Based Access Control
* SSH
* HTTPS
* Management VRF
* Access Control Lists
* Privileged access management

```text
Administrator
      |
      v
MFA
      |
      v
TACACS+ / ISE
      |
      v
Role-Based Access
      |
      v
Network Device
```

---

# 17. Device Security

Infrastructure devices should implement:

* Secure management protocols
* SSH instead of Telnet
* HTTPS instead of HTTP
* SNMPv3
* Strong authentication
* Secure configuration
* Control Plane Policing
* DHCP Snooping
* Dynamic ARP Inspection
* IP Source Guard

---

# 18. Security Monitoring Architecture

```text
Network Devices
      |
      +--> Syslog
      |
      +--> Telemetry
      |
      +--> NetFlow
      |
      +--> Authentication Logs
      |
      v
+-----+------+
| SIEM / SOC |
+-----+------+
      |
      v
Detection & Response
```

---

# 19. Security Operations

Security monitoring should detect:

* Authentication failures
* Suspicious endpoint behavior
* Unauthorized access
* Malware indicators
* Policy violations
* Network anomalies
* Configuration changes

---

# 20. Incident Response Flow

```text
Detect
  |
  v
Analyze
  |
  v
Contain
  |
  v
Eradicate
  |
  v
Recover
  |
  v
Lessons Learned
```

---

# 21. Security and Automation

Security automation can be used for:

* Quarantining compromised endpoints
* Updating firewall policies
* Blocking malicious IP addresses
* Disabling compromised accounts
* Creating security tickets
* Collecting forensic information

```text
Security Event
      |
      v
SIEM
      |
      v
Automation / SOAR
      |
      v
ISE / Firewall / Network
      |
      v
Automated Response
```

---

# 22. Security Integrations

| Platform         | Integration      | Purpose              |
| ---------------- | ---------------- | -------------------- |
| Cisco ISE        | RADIUS / TACACS+ | Identity and access  |
| Active Directory | LDAP / Kerberos  | User identity        |
| Catalyst Center  | API              | Network policy       |
| Firewall         | API / Syslog     | Security enforcement |
| SIEM             | Syslog / API     | Security monitoring  |
| ServiceNow       | API              | Incident management  |
| SOAR             | API              | Automated response   |

---

# 23. Security High Availability

Security services should avoid single points of failure.

Redundancy should be implemented for:

* ISE PSNs
* Firewalls
* Internet connections
* VPN gateways
* SIEM infrastructure
* Identity services

```text
             +-------------+
             | Firewall 1  |
             +------+------+
                    |
                 HA Link
                    |
             +------+------+
             | Firewall 2  |
             +-------------+
```

---

# 24. Security Failure Scenarios

| Failure              | Expected Behavior                                 |
| -------------------- | ------------------------------------------------- |
| ISE PSN failure      | Authentication uses alternate PSN                 |
| Firewall failure     | HA firewall takes over                            |
| WAN link failure     | Backup path is used                               |
| SIEM failure         | Network services continue; monitoring is impacted |
| Directory failure    | Defined authentication fallback applies           |
| Compromised endpoint | Endpoint is quarantined                           |
| Unauthorized device  | Access is denied or restricted                    |

---

# 25. Security Compliance

The architecture should support applicable security and compliance requirements.

Potential frameworks include:

* ISO 27001
* NIST Cybersecurity Framework
* GDPR
* CIS Controls
* Industry-specific requirements

Security controls should be mapped to business and regulatory requirements.

---

# 26. Security Architecture Checklist

### Identity

* [ ] Identity source defined
* [ ] 802.1X implemented
* [ ] MAB requirements documented
* [ ] MFA requirements defined
* [ ] Administrative access secured

### Segmentation

* [ ] Virtual Networks defined
* [ ] VRFs defined
* [ ] SGT policy matrix created
* [ ] Firewall zones defined

### Security Controls

* [ ] Firewalls deployed
* [ ] IDS/IPS enabled
* [ ] Secure management implemented
* [ ] Endpoint security integrated

### Monitoring

* [ ] SIEM integration completed
* [ ] Authentication logs monitored
* [ ] Network telemetry enabled
* [ ] Incident response process documented

### Operations

* [ ] Security policies reviewed
* [ ] Configuration backup enabled
* [ ] Vulnerability management defined
* [ ] Security incident procedures documented

---

# 27. Architecture Summary

The target security architecture applies a defense-in-depth and Zero Trust approach across the enterprise network.

The architecture integrates:

* Cisco ISE
* 802.1X
* MAB
* Virtual Networks
* VRFs
* Security Group Tags
* Firewalls
* VPN
* SD-WAN security
* SIEM
* Security automation

The security architecture provides identity-based access, least-privilege authorization, network segmentation, centralized monitoring, and automated response capabilities.

This architecture forms the security foundation for the broader Enterprise Network Transformation.


