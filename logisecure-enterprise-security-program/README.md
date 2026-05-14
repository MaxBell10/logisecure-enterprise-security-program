# LogiSecure Enterprise Security Program

[![Hub](https://img.shields.io/badge/LogiSecure-Enterprise%20Security%20Program-1F3864?style=flat-square)](https://github.com/MaxBell10/logisecure-enterprise-security-program)
[![ISO 27001](https://img.shields.io/badge/ISO%2027001-2022-EF7730?style=flat-square)](https://www.iso.org)
[![IEC 62443](https://img.shields.io/badge/IEC%2062443-OT%20Security-8B5CF6?style=flat-square)](https://www.iec.ch)
[![NIS2](https://img.shields.io/badge/NIS2-Compliant%20Programme-3B8ADB?style=flat-square)](https://digital-strategy.ec.europa.eu)
[![EBIOS RM](https://img.shields.io/badge/EBIOS%20RM-Risk%20Assessment-F59E0B?style=flat-square)](https://www.ssi.gouv.fr)
[![MITRE ATT&CK](https://img.shields.io/badge/MITRE-ATT%26CK%20Mapped-E05252?style=flat-square)](https://attack.mitre.org)

> **This is the central hub of a 16-project cybersecurity portfolio simulating a full enterprise security programme for LogiSecure SA — a fictional Belgian logistics operator.**
> The programme covers identity management, network segmentation, OT security, cloud, GRC, and incident response — built end-to-end as a CISO-level portfolio.

---

## LogiSecure SA — Fictional Enterprise Context

| Attribute | Detail |
|---|---|
| **Sector** | Automated logistics operator — conveyors, WMS, B2B e-commerce |
| **Size** | 500 employees · HQ Brussels, Belgium |
| **Regulatory scope** | NIS2 (Jan 2025) · ISO 27001 · IEC 62443 (OT) |
| **IT infrastructure** | Active Directory `lab.local` · pfSense · Wazuh SIEM · AWS `eu-west-1` |
| **OT infrastructure** | Legacy conveyor HMI (Windows 7) · PLC · WMS · Historian SCADA |
| **Suppliers** | TechLogix BVBA (WMS) · ConveyorPro GmbH (OT) · DataAPI SAS (API) |
| **Key risks** | Ransomware · IT→OT lateral movement · API data leak · Supply chain compromise |

---

## Global Architecture

```
LOGISECURE SA — INFRASTRUCTURE

INTERNET/WAN
    │
[pfSense CE — Firewall/Router]                          P2
    │
    ├── [LAN IT — 192.168.1.x]
    │       Active Directory (lab.local)                P1
    │       Wazuh SIEM                                  P1, P8, P11, P12
    │       PKI / KMS                                   P7
    │
    ├── [DMZ — 192.168.2.x]
    │       Cowrie Honeypot                             P8
    │       Web server (supplier-facing)                P8
    │
    ├── [OT Control VLAN 20]                            P6, P13
    │       HMI legacy (Windows 7) · Historian SCADA
    │
    └── [OT Field VLAN 30]                              P6
            PLC · Sensors · Conveyors

[AWS Cloud — eu-west-1]                                 P10
    IAM · S3 · CloudTrail · GuardDuty · Terraform

[Third-party VPN]                                       P14
    TechLogix · ConveyorPro · DataAPI
```

---

## Programme Overview

| Part | Name | Projects |
|---|---|---|
| 0 | Hub — Enterprise Security Program | P0 |
| 1 | Build the Lab | P1 → P5 |
| 2 | Expand the Skills | P6 → P12 |
| 3 | Govern the Risk | P13 → P15 |

### Part 1 — Build the Lab

| # | Repository | Status | Description |
|---|---|---|---|
| P1 | [logisecure-active-directory](https://github.com/MaxBell10/logisecure-active-directory) | 🔄 In progress | AD hardening · GPO · Wazuh SIEM · MITRE ATT&CK |
| P2 | [logisecure-pfsense-segmentation](https://github.com/MaxBell10/logisecure-pfsense-segmentation) | 🔄 In progress | pfSense · Suricata IDS/IPS · DMZ · OpenVAS |
| P3 | [logisecure-ebios-rm-assessment](https://github.com/MaxBell10/logisecure-ebios-rm-assessment) | 📋 Planned | EBIOS RM 5 workshops · NIS2 · strategic scenarios |
| P4 | [logisecure-bash-automation](https://github.com/MaxBell10/logisecure-bash-automation) | 📋 Planned | Bash & PowerShell · GPG-signed · GitHub Actions CI |
| P5 | [logisecure-attack-simulation](https://github.com/MaxBell10/logisecure-attack-simulation) | 📋 Planned | Kill chain · password spray · Wazuh correlation |

### Part 2 — Expand the Skills

| # | Repository | Status | Description |
|---|---|---|---|
| P6 | [logisecure-ot-network-security](https://github.com/MaxBell10/logisecure-ot-network-security) | 📋 Planned | Purdue Model · VLAN · ACL · IEC 62443 |
| P7 | [logisecure-pki-kms](https://github.com/MaxBell10/logisecure-pki-kms) | 📋 Planned | 2-tier PKI · Root CA offline · CRL · GPG |
| P8 | [logisecure-honeypot-threat-intel](https://github.com/MaxBell10/logisecure-honeypot-threat-intel) | 📋 Planned | Cowrie · STIX IOC export · Threat Intel |
| P9 | [logisecure-container-security](https://github.com/MaxBell10/logisecure-container-security) | 📋 Planned | Docker hardening · Trivy · kube-bench · SBOM |
| P10 | [logisecure-cloud-security](https://github.com/MaxBell10/logisecure-cloud-security) | 📋 Planned | AWS · Terraform IaC · GuardDuty · CloudTrail |
| P11 | [logisecure-forensics-ir](https://github.com/MaxBell10/logisecure-forensics-ir) | 📋 Planned | PICERL · TheHive · memory & disk forensics |
| P12 | [logisecure-redteam-blueteam](https://github.com/MaxBell10/logisecure-redteam-blueteam) | 📋 Planned | Purple Team · MTTD · 13 MITRE techniques |

### Part 3 — Govern the Risk

| # | Repository | Status | Description |
|---|---|---|---|
| P13 | [logisecure-legacy-ot-security](https://github.com/MaxBell10/logisecure-legacy-ot-security) | 📋 Planned | Legacy HMI · virtual patching · risk treatment |
| P14 | [logisecure-supply-chain-risk](https://github.com/MaxBell10/logisecure-supply-chain-risk) | 📋 Planned | Vendor assessment · SBOM Syft/Grype · MFA VPN |
| P15 | [logisecure-iso27001-audit](https://github.com/MaxBell10/logisecure-iso27001-audit) | 📋 Planned | SoA · Annex A audit · NC report · action plan |

---

## CISO Dashboard — Consolidated KPIs

> **Reading guide:** `Target` = objective defined in the programme · `Actual` = measured value after project completion

| KPI | Target | Actual | Project |
|---|---|---|---|
| Purple Team MTTD | < 120s | `TBD after P12` | P12 |
| MITRE techniques detected | ≥ 11 / 13 tested | `TBD after P12` | P12 |
| Critical Docker CVEs reduction | > 90% | `TBD after P9` | P9 |
| Custom Wazuh rules | ≥ 15 | `TBD after P12` | P1, P8, P11, P12 |
| Network segments | 5 | `TBD after P6` | P2, P6 |
| Legacy OT risk level | CRITICAL → MEDIUM | `TBD after P13` | P13 |
| ISO 27001 Annex A controls audited | ≥ 20 | `TBD after P15` | P15 |
| Major NCs identified | documented | `TBD after P15` | P15 |
| Suppliers assessed | 3 | `TBD after P14` | P14 |
| PingCastle AD score improvement | significant reduction | `TBD after P1` | P1 |
| OpenVAS critical vulns (DC) | 0 after remediation | `TBD after P2` | P2 |

---

## Security Posture — Executive Summary

| Domain | Maturity | Projects |
|---|---|---|
| Identity & Access Management | `TBD after P1` | P1 — AD + GPO + Wazuh |
| Network Segmentation | `TBD after P2` | P2 — pfSense + Suricata |
| Cryptography & PKI | `TBD after P7` | P7 — PKI/KMS Lab |
| Threat Detection | `TBD after P12` | P1, P8, P12 — Wazuh + Cowrie |
| Cloud Security | `TBD after P10` | P10 — AWS + Terraform |
| OT / ICS Security | `TBD after P13` | P6, P13 — Packet Tracer + Legacy |
| Incident Response | `TBD after P11` | P11 — PICERL + TheHive |
| Supplier Risk | `TBD after P14` | P14 — Supply Chain + SBOM |
| GRC & Compliance | `TBD after P15` | P3, P15 — EBIOS RM + ISO 27001 |
| Security Awareness | Gap identified | P15 — A.6.3 NC majeure |

---

## Risk Register

| Risk | Impact | Likelihood | Mitigation | Project |
|---|---|---|---|---|
| AD compromise — password spray | CRITICAL | MEDIUM | Account lockout · Wazuh rule · MFA | P1, P5, P12 |
| Lateral movement IT → OT | CRITICAL | MEDIUM | VLAN · pfSense ACL · Suricata IPS | P2, P6, P12 |
| Ransomware via phishing (WMS) | CRITICAL | HIGH | Email filtering · backup · IR playbook | P3, P11 |
| Unsecured third-party VPN (OT) | HIGH | HIGH | MFA VPN · ACL · session timeout · logs | P14 |
| API partner data leak | HIGH | MEDIUM | TLS · vendor assessment · SBOM | P14 |
| Legacy OT unpatched exploit | HIGH | MEDIUM | Virtual patching Suricata · VLAN Zeek | P13 |
| S3 cloud exfiltration | HIGH | LOW | Public access block · GuardDuty | P10 |
| Software supply chain compromise | HIGH | LOW | SBOM Syft/Grype · image scanning | P14, P9 |

---

## Regulatory & Framework Coverage

| Framework | Coverage |
|---|---|
| **ISO 27001:2022** | Annex A — A.5 Policies · A.6 People · A.7 Physical · A.8 Technological |
| **NIS2 Art. 21** | Risk management · Supply chain · Access control · Incident handling · Continuity |
| **IEC 62443** | SL1–SL2 · SR 1.1–1.3 · SR 5.1–5.4 · Purdue Model · IT/OT segmentation |
| **EBIOS RM** | 5 workshops · Strategic & operational scenarios · Residual risk treatment |
| **MITRE ATT&CK Enterprise** | T1078 · T1110 · T1484 · T1566 · T1195 · T1562 · T1021 · T1133 |
| **MITRE ATT&CK for ICS** | T0862 · T0859 · T0814 · T0813 · T0849 · T0822 |
| **CIS Controls** | Control 5 — Account Mgmt · Control 8 — Audit Logs · Control 12 — Network Infra |

---

## Flagship Projects

| # | Repository | Why flagship | Key metric |
|---|---|---|---|
| P12 | [logisecure-redteam-blueteam](https://github.com/MaxBell10/logisecure-redteam-blueteam) | Purple Team — full system vision | MTTD · 11/13 techniques detected |
| P15 | [logisecure-iso27001-audit](https://github.com/MaxBell10/logisecure-iso27001-audit) | SoA + audit report — rare GRC profile | 2 major NCs documented |
| P5 | [logisecure-attack-simulation](https://github.com/MaxBell10/logisecure-attack-simulation) | AD + pfSense + detection + incident report | Complete kill chain |
| P1 | [logisecure-active-directory](https://github.com/MaxBell10/logisecure-active-directory) | IAM + SIEM foundation — base of everything | PingCastle score before/after |
| P10 | [logisecure-cloud-security](https://github.com/MaxBell10/logisecure-cloud-security) | Terraform IaC + AWS — highly in demand | GuardDuty + compliance |

---

## Certification Coverage

| Project | Security+ | CCNA | SecOT+ | CISSP |
|---|---|---|---|---|
| P0 Hub | — | — | — | D1 |
| P1 AD | IAM, SIEM | — | — | D5 |
| P2 pfSense | Network | ACL, VLAN | — | D4 |
| P3 EBIOS | Risk | — | Risk OT | D1 |
| P4 Bash | Automation | — | — | D7 |
| P5 Attack | Threats | Routing | — | D7 |
| P6 OT | ICS/SCADA | VLANs | OT Net | D7 |
| P7 PKI | Crypto | — | — | D3 |
| P8 Honeypot | Threat Intel | — | — | D7 |
| P9 Docker | Virtualisation | — | — | D7 |
| P10 Cloud | Cloud Sec | — | — | D3/D7 |
| P11 Forensics | IR | — | — | D7 |
| P12 Red/Blue | Pentest | CCNA | OT threats | D7 |
| P13 Legacy OT | ICS | — | Legacy | D7 |
| P14 Supply Chain | Supply | — | OT vendors | D1 |
| P15 ISO 27001 | Risk Mgmt | — | — | D1 |

---

<div align="center">

*All environments simulate the fictional enterprise LogiSecure SA, used solely for educational and portfolio purposes.*

*Built by [Maxime Belliard](https://github.com/MaxBell10) — Cybersecurity Analyst · Technical & GRC · End-to-End Implementation*

</div>
