## Wazuh Server — Ubuntu

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

This is the official all-in-one installation method. It installs the Wazuh server/manager, Wazuh indexer and Wazuh dashboard on the same host.

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
```
ip addr
```
To Open dashboard - Use this format in your browser:
```
https://YOUR_WAZUH_SERVER_IP
```

The installer displays the admin password when installation finishes. Wazuh also stores the generated passwords in wazuh-passwords.txt inside the installation archive.


## Wazuh Agent — Windows

Download the Wazuh Agent

wazuh-agent-4.14.7-1.msi

Open PowerShell as Administrator & Go to the directory containing the MSI:
```
cd $env:USERPROFILE\Downloads
```
Install the Agent and point it to your Wazuh Server by replace xxx.xxx.xxx with your actual Wazuh Server IP.
```

msiexec.exe /i .\wazuh-agent-4.14.7-1.msi /q WAZUH_MANAGER="xxx.xxx.xxx.xxx"
```
Start the Wazuh Agent
```
Start-Service wazuhsvc
```
Verify the Agent service
```
Get-Service wazuhsvc
```



