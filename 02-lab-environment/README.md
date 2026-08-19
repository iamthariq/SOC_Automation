# Lab Environment

This section documents the infrastructure used to build and test the SOC automation environment.

The lab combines a local VirtualBox environment with cloud-hosted AWS infrastructure.

---

## Environment Overview

The SOC automation lab consists of:

- Local VirtualBox Lab
- AWS Cloud Infrastructure
- Windows-based security event sources
- Wazuh SIEM
- Shuffle SOAR
- TheHive Case Management

---

## 01. Local Virtual Lab

The local security environment is hosted using Oracle VirtualBox.

### Domain Controller

| Specification | Details |
|---|---|
| Operating System | Windows Server 2022 (64-bit) |
| CPU | 2 vCPU |
| RAM | 4.5 GB |
| Storage | 80 GB |
| Role | Active Directory Domain Controller |

### Windows Endpoint

| Specification | Details |
|---|---|
| Operating System | Windows 11 (64-bit) |
| CPU | 2 vCPU |
| RAM | 4 GB |
| Storage | 80 GB |
| Role | Monitored Windows Endpoint |

### Wazuh Server

| Specification | Details |
|---|---|
| Operating System | Ubuntu Server 25.04 (64-bit) |
| CPU | 4 vCPU |
| RAM | 4.5 GB |
| Storage | 80 GB |
| Role | Wazuh Manager / SIEM |

---

## 02. Cloud Infrastructure

The cloud-based security components are hosted on Amazon Web Services (AWS) EC2.

### Shuffle SOAR

| Specification | Details |
|---|---|
| Platform | AWS EC2 |
| Instance Type | t3.xlarge |
| RAM | 16 GB |
| Storage | 50 GB |
| Region | US East (N. Virginia) |
| Availability Zone | us-east-1d |
| Role | Security Orchestration and Automated Response |

Shuffle SOAR receives security alerts from Wazuh and executes automated workflows.

### TheHive

| Specification | Details |
|---|---|
| Platform | AWS EC2 |
| Instance Type | t2.xlarge |
| RAM | 16 GB |
| Storage | 50 GB |
| Region | US East (N. Virginia) |
| Availability Zone | us-east-1c |
| Role | Security Case Management |

TheHive is used for security case creation and incident management.

---

## 03. Network Environment

The local virtual machines use VirtualBox networking for communication within the lab.

The environment uses:

- NAT Network
- Host-Only Adapter
- AWS VPC networking

---

## 04. Environment Architecture

```text
                 LOCAL VIRTUAL LAB
┌──────────────────────────────────────────────┐
│                                              │
│  Windows Server 2022                         │
│  Domain Controller                           │
│          │                                   │
│          │ Windows Events / Sysmon           │
│          ▼                                   │
│  Windows 11 Endpoint                         │
│          │                                   │
│          │ Wazuh Agent                       │
│          ▼                                   │
│  Ubuntu Wazuh Server                         │
│  Wazuh Manager / SIEM                        │
│                                              │
└────────────────────┬─────────────────────────┘
                     │
                     │ Alert / Webhook
                     ▼
              ┌───────────────┐
              │  Shuffle SOAR │
              │    AWS EC2    │
              └───────┬───────┘
                      │
             ┌────────┼─────────┐
             ▼        ▼         ▼
        VirusTotal  TheHive   Gmail
        Enrichment  Case Mgmt Notification
