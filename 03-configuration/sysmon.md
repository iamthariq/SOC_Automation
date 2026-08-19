# Sysmon

Sysmon is configured on the Windows systems to generate detailed endpoint telemetry for security monitoring and detection.
## Install Sysmon

```powershell
sysmon.exe -accepteula -i sysmon-config.xml
```
## Update Sysmon Configuration
```
sysmon.exe -c sysmon-config.xml
```
## Uninstall
```
sysmon.exe -u
```
