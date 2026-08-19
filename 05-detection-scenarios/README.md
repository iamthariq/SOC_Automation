# Detection Scenarios

This section documents the security scenarios simulated in the SOC lab and their detection through Wazuh.

---

## 01. Mimikatz Execution

![Mimikatz Detection 01](01-mimikatz-detection.png)

Mimikatz execution is detected using Sysmon process telemetry and a custom Wazuh detection rule.

## Mimikatz Detection

### Evidence

![Mimikatz Detection 02](02-mimikatz-detection.png)

![Mimikatz Detection 03](03-mimikatz-detection.png)

![Mimikatz Detection 04](04-mimikatz-detection.png)

![Mimikatz Detection 05](05-mimikatz-detection.png)

---

## 02. RDP Brute Force

Multiple failed RDP authentication attempts are generated against the Windows system and detected through Windows Security Event ID 4625.

### Evidence

![RDP Brute Force 01](01-rdp-brute-force.png)

![RDP Brute Force 02](02-rdp-brute-force.png)

![RDP Brute Force 03](03-rdp-brute-force.png)

![RDP Brute Force 04](04-rdp-brute-force.png)


---

## 03. Active Directory Group Modification/Privilege Escalation

A domain user is added to a privileged Active Directory group, generating Windows Security Event ID 4728.

### Evidence

![Active Directory Group Modification 01](01-ad-group-modification.png)

![Active Directory Group Modification 02](02-ad-group-modification.png)

![Active Directory Group Modification 03](03-ad-group-modification.png)

![Active Directory Group Modification 04](04-ad-group-modification.png)
