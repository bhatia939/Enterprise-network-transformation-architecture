# Wireless Architecture

## 1. Purpose

This document defines the target enterprise wireless architecture for the Enterprise Network Transformation.

The architecture provides secure, scalable, high-performance wireless connectivity for corporate users, guests, IoT devices, and business-critical applications.

---

## 2. Architecture Objectives

The wireless architecture aims to:

- Provide reliable enterprise Wi-Fi connectivity.
- Support Wi-Fi 6 and Wi-Fi 6E.
- Provide secure identity-based access.
- Integrate with Cisco ISE.
- Support Cisco SD-Access.
- Provide centralized management and assurance.
- Optimize RF performance.
- Support seamless roaming.
- Provide high availability.
- Support IoT and guest connectivity.

---

## 3. Wireless Architecture Overview

```text
                         +------------------+
                         | Catalyst Center  |
                         | Management       |
                         +--------+---------+
                                  |
                                  v
                         +--------+---------+
                         | Wireless         |
                         | Controller       |
                         | Catalyst 9800    |
                         +--------+---------+
                                  |
                         +--------+---------+
                         | Cisco ISE        |
                         | Identity & Policy |
                         +--------+---------+
                                  |
                    +-------------+-------------+
                    |                           |
             +------+-------+            +------+-------+
             | Wireless APs |            | Wireless APs |
             |   Site A     |            |   Site B     |
             +------+-------+            +------+-------+
                    |                           |
              Wireless Clients              Wireless Clients
````

---

# 4. Wireless Architecture Components

The wireless architecture consists of:

* Wireless access points
* Wireless LAN controllers
* Cisco Catalyst Center
* Cisco ISE
* RF management
* Authentication services
* Network infrastructure
* Monitoring and assurance platforms

---

# 5. Wireless Network Design Model

```text
Wireless Client
      |
      v
Access Point
      |
      v
Access Switch
      |
      v
Wireless Controller
      |
      v
Campus / SDA Fabric
      |
      +--> Data Center
      |
      +--> Internet
      |
      +--> Cloud
```

---

# 6. Wireless LAN Controller Architecture

The wireless controller provides centralized WLAN control and management.

### Responsibilities

* AP management
* WLAN configuration
* RF management
* Client roaming
* Authentication integration
* Mobility services
* Wireless policy enforcement
* Monitoring and troubleshooting

---

## 6.1 High-Availability Controller Design

```text
                  +----------------+
                  |   Catalyst     |
                  |   9800 WLC 1   |
                  +--------+-------+
                           |
                     HA / SSO
                           |
                  +--------+-------+
                  |   Catalyst     |
                  |   9800 WLC 2   |
                  +----------------+
```

The design should provide:

* Stateful switchover
* Redundant control-plane functions
* Redundant network connectivity
* Controller redundancy

---

# 7. Wireless Access Point Architecture

Access Points should be deployed according to:

* Coverage requirements
* Capacity requirements
* User density
* Application requirements
* RF characteristics
* Building construction
* Interference levels

```text
                  +-------------+
                  | Wireless AP |
                  +------+------+ 
                         |
                  Wired Network
                         |
                  +------+------+
                  | Access Switch|
                  +-------------+
```

---

# 8. Wi-Fi Standards

The architecture should support modern wireless standards.

| Standard | Frequency       | Use                    |
| -------- | --------------- | ---------------------- |
| 802.11n  | 2.4 / 5 GHz     | Legacy compatibility   |
| 802.11ac | 5 GHz           | High-performance Wi-Fi |
| 802.11ax | 2.4 / 5 / 6 GHz | Wi-Fi 6 / 6E           |

---

# 9. Wi-Fi 6 and Wi-Fi 6E

Wi-Fi 6 provides:

* OFDMA
* MU-MIMO
* BSS Coloring
* Target Wake Time
* Improved high-density performance

Wi-Fi 6E extends Wi-Fi 6 capabilities into the 6 GHz spectrum.

### Wi-Fi 6E Benefits

* Additional spectrum
* Less congestion
* Wider channels
* Lower interference
* Improved capacity

---

# 10. RF Architecture

RF design should consider:

* Coverage
* Capacity
* Channel utilization
* Co-channel interference
* Adjacent-channel interference
* Transmit power
* Channel width
* Client density

```text
        AP-1                  AP-2
         ))                     ((
          ))                   ((
           ))                 ((
              Wireless Area
           ((                 ))
          ((                   ))
        Client              Client
```

---

# 11. Wireless Survey

Wireless surveys should be performed to validate RF design.

### Survey Types

* Predictive survey
* AP-on-a-stick survey
* Passive survey
* Active survey
* Spectrum analysis
* Post-deployment validation

### Survey Objectives

* Validate coverage
* Identify interference
* Validate capacity
* Optimize AP placement
* Validate roaming

---

# 12. Frequency Planning

## 2.4 GHz

The 2.4 GHz band has limited non-overlapping channels.

Use:

* 20 MHz channel width
* Carefully planned channel reuse
* Reduced reliance in high-density environments

---

## 5 GHz

Provides:

* More available channels
* Higher capacity
* Wider channel options

Channel widths should be selected based on:

* Client density
* Application requirements
* RF environment

---

## 6 GHz

Wi-Fi 6E provides additional spectrum for compatible clients.

Use cases include:

* High-density environments
* High-throughput applications
* Low-interference wireless networks

---

# 13. WLAN / SSID Architecture

Example SSID design:

```text
+----------------------+
| Corporate-WiFi       |
| Employee Access      |
+----------------------+

+----------------------+
| Guest-WiFi           |
| Internet Access      |
+----------------------+

+----------------------+
| IoT-WiFi             |
| IoT Devices          |
+----------------------+

+----------------------+
| Voice-WiFi           |
| Voice Applications   |
+----------------------+
```

---

# 14. SSID Design Principles

The number of SSIDs should be minimized.

Each SSID may represent:

* A business requirement
* An identity requirement
* A security requirement
* A device type

Excessive SSIDs increase:

* Beacon overhead
* RF utilization
* Management complexity

---

# 15. Wireless Authentication

```text
Wireless Client
      |
      v
     AP
      |
      v
Wireless Controller
      |
      | RADIUS
      v
    Cisco ISE
      |
      v
Identity Directory
```

Supported methods may include:

* WPA2-Enterprise
* WPA3-Enterprise
* 802.1X
* EAP-TLS
* PEAP
* MAB for compatible IoT devices

---

# 16. Identity-Based Wireless Access

```text
User / Device
      |
      v
802.1X Authentication
      |
      v
Cisco ISE
      |
      +--> User Identity
      |
      +--> Device Profile
      |
      +--> Authorization
      |
      +--> SGT Assignment
      |
      v
Wireless Network Access
```

---

# 17. Wireless Segmentation

Wireless networks can be segmented using:

* VLANs
* VRFs
* Virtual Networks
* Security Group Tags
* Firewall policies

```text
Corporate Wi-Fi
       |
       v
Corporate VN

Guest Wi-Fi
       |
       v
Guest VN

IoT Wi-Fi
       |
       v
IoT VN
```

---

# 18. Wireless and SD-Access Integration

```text
                 +----------------+
                 | Cisco ISE      |
                 | Identity       |
                 +--------+-------+
                          |
                          v
                 +--------+-------+
                 | Catalyst       |
                 | Center         |
                 +--------+-------+
                          |
                          v
                 +--------+-------+
                 | Wireless       |
                 | Controller     |
                 +--------+-------+
                          |
                          v
                 +--------+-------+
                 | SDA Fabric     |
                 +----------------+
```

The integration provides:

* Identity-based access
* Virtual Network assignment
* SGT assignment
* Centralized policy
* Wireless assurance

---

# 19. Wireless Roaming

The architecture should support seamless roaming where required.

Roaming depends on:

* RF design
* AP placement
* WLAN configuration
* Mobility architecture
* Authentication design

```text
       AP-1                    AP-2
        |                        |
        |     Roaming Client     |
        +----------->------------+
```

Applications requiring roaming include:

* Voice
* Healthcare applications
* Warehouse applications
* Industrial applications

---

# 20. Voice over Wi-Fi

Voice WLAN design should consider:

* Low latency
* Low jitter
* Packet loss
* Fast roaming
* QoS
* Coverage

```text
Voice Client
     |
     v
Wireless AP
     |
     v
Wireless Controller
     |
     v
Voice Network
```

---

# 21. Wireless QoS

Wireless QoS should prioritize traffic based on application requirements.

Example:

| Traffic               | Priority   |
| --------------------- | ---------- |
| Voice                 | Highest    |
| Video                 | High       |
| Business Applications | Medium     |
| Standard Data         | Normal     |
| Guest Traffic         | Controlled |

QoS design should include:

* Classification
* Marking
* Queuing
* WMM
* DSCP

---

# 22. Guest Wireless Architecture

```text
Guest Client
     |
     v
Guest SSID
     |
     v
Wireless Infrastructure
     |
     v
Firewall / Internet
     |
     v
Internet
```

Guest users should be isolated from internal enterprise resources.

Security controls may include:

* Captive portal
* Guest authentication
* Internet-only access
* Client isolation
* Firewall policies

---

# 23. IoT Wireless Architecture

IoT devices may use:

* 802.1X
* MAB
* PSK
* Device profiling

```text
IoT Device
    |
    v
IoT SSID
    |
    v
Cisco ISE
    |
    v
Device Profiling
    |
    v
IoT Policy
```

IoT devices should receive only the access required for their business function.

---

# 24. Wireless Security

Security controls include:

* WPA2-Enterprise
* WPA3-Enterprise
* 802.1X
* EAP-TLS
* Cisco ISE
* Rogue AP detection
* Wireless intrusion prevention
* Client isolation
* Segmentation

---

# 25. Wireless Management

Catalyst Center may provide:

* AP provisioning
* Configuration management
* Software management
* RF visibility
* Client health
* Wireless assurance
* Fault monitoring

```text
Engineer
    |
    v
Catalyst Center
    |
    v
Wireless Controller
    |
    v
Access Points
```

---

# 26. Wireless Monitoring

Monitor:

* AP availability
* Client health
* Channel utilization
* Noise floor
* Interference
* Signal strength
* SNR
* Retries
* Authentication failures
* Roaming events

---

# 27. Wireless Performance Metrics

Important metrics include:

| Metric              | Purpose                 |
| ------------------- | ----------------------- |
| RSSI                | Signal strength         |
| SNR                 | Signal quality          |
| Channel Utilization | RF congestion           |
| Noise Floor         | Interference level      |
| Retry Rate          | Transmission quality    |
| Client Health       | User experience         |
| Data Rate           | Performance             |
| Latency             | Application performance |

---

# 28. Wireless High Availability

High availability should be implemented at:

* Wireless controller level
* Network connectivity level
* Access switch level
* Power level
* WAN level

```text
                 +-------------+
                 | WLC-1       |
                 +------+------+ 
                        |
                     HA / SSO
                        |
                 +------+------+ 
                 | WLC-2       |
                 +-------------+
                        |
                   Access Points
```

---

# 29. Wireless Failure Scenarios

| Failure                    | Expected Behavior                               |
| -------------------------- | ----------------------------------------------- |
| AP failure                 | Clients roam to neighboring AP                  |
| WLC failure                | Standby controller takes over                   |
| Access link failure        | Redundant network path is used                  |
| Authentication PSN failure | Alternate PSN processes authentication          |
| WAN failure                | Local wireless services continue where designed |
| High RF interference       | RF optimization adjusts channels/power          |

---

# 30. Wireless Automation

```text
GitHub
   |
   v
CI/CD Pipeline
   |
   v
Automation Platform
   |
   v
Catalyst Center API
   |
   v
Wireless Infrastructure
```

Automation use cases:

* WLAN provisioning
* AP configuration
* Compliance validation
* Configuration backup
* Monitoring integration

---

# 31. Wireless Design Checklist

### RF Design

* [ ] Predictive survey completed
* [ ] AP placement validated
* [ ] Capacity requirements defined
* [ ] Channel plan defined
* [ ] Power plan defined
* [ ] Interference analyzed

### Security

* [ ] 802.1X configured
* [ ] ISE integration completed
* [ ] Guest access secured
* [ ] IoT access defined
* [ ] Encryption standards defined

### Architecture

* [ ] WLC high availability designed
* [ ] SSID strategy defined
* [ ] SDA integration designed
* [ ] Segmentation defined
* [ ] Roaming requirements documented

### Operations

* [ ] Monitoring configured
* [ ] Assurance enabled
* [ ] Automation defined
* [ ] Troubleshooting procedures documented

---

# 32. Architecture Summary

The target wireless architecture provides secure, scalable, high-performance wireless connectivity across the enterprise.

The architecture integrates:

* Wi-Fi 6 and Wi-Fi 6E
* Cisco Catalyst Wireless Controllers
* Enterprise Access Points
* Cisco ISE
* Catalyst Center
* Cisco SD-Access
* Identity-based authentication
* RF optimization
* Wireless assurance
* Network automation

This architecture provides a modern wireless foundation for corporate users, guests, IoT devices, voice applications, and future enterprise services.

Trust, segmentation, and security controls** into one enterprise security architecture.

