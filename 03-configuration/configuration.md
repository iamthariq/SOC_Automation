# Configuration

This section contains the core configuration used to build the SOC automation environment.

## Configuration Components

### Sysmon

Sysmon is configured on the Windows systems to generate detailed endpoint telemetry for security monitoring and detection.
### Install Sysmon

```powershell
sysmon.exe -accepteula -i sysmon-config.xml
```
### Update Sysmon Configuration
```
sysmon.exe -c sysmon-config.xml
```
### Uninstall
```
sysmon.exe -u
```
### Wazuh Agent

The Wazuh Agent is configured to collect Sysmon Operational events from the Windows endpoint.

### Wazuh Manager

Custom detection rules and the Wazuh-to-Shuffle integration are configured at the Wazuh Manager level.

## Configuration Files

- Sysmon configuration
- Wazuh Agent Sysmon event collection
- Wazuh Manager to Shuffle integration

All configuration examples are documented with comments and can be adapted for another lab environment by replacing environment-specific values where required.


