# Wazuh Server — Ubuntu

Update the Ubuntu system
```
sudo apt update && sudo apt upgrade -y
```
Download the Wazuh installation assistant
```
curl -sO https://packages.wazuh.com/4.14/wazuh-install.sh
```
Install Wazuh Server, Indexer and Dashboard
```
sudo bash ./wazuh-install.sh -a
```

> This is the official all-in-one installation method. It installs the Wazuh server/manager, Wazuh indexer and Wazuh dashboard on the same host.

Check Wazuh Manager
```
sudo systemctl status wazuh-manager
```
Check Wazuh Indexer
```
sudo systemctl status wazuh-indexer
```
Check Wazuh Dashboard
```
sudo systemctl status wazuh-dashboard
```
Find the server IP
`ip addr`

To Open dashboard - Use this format in your browser:
```
https://YOUR_WAZUH_SERVER_IP
```

> The installer displays the admin password when installation finishes. Wazuh also stores the generated passwords in wazuh-passwords.txt inside the installation archive.

# Wazuh Agent — Windows

## Download and install:

`wazuh-agent-4.14.7-1.msi`

## Open PowerShell as Administrator

> Go to the directory containing the MSI:

```powershell
cd $env:USERPROFILE\Downloads
```
> Configure Wazuh Manager
## Add the Wazuh Manager IP address to the Wazuh Agent configuration:
```
<client>
    <server>
        <address>WAZUH_MANAGER_IP</address>
    </server>
</client>
```
## Replace:
`WAZUH_MANAGER_IP`
> with the Wazuh Manager IP address used in the lab.
> Restart Wazuh Agent
> Restart-Service -Name Wazuh
## Start Wazuh Agent
```
Start-Service wazuhsvc
```
## Verify Wazuh Agent
```
Get-Service wazuhsvc
```
