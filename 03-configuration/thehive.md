# TheHive 5 — SOC Case Management Server in docker (ubuntu)
## Update Ubuntu
```
sudo apt update && sudo apt upgrade -y
```
## Install Required Packages
```
sudo apt install -y ca-certificates curl gnupg git
```
## Install Docker
```
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
## Update Package Repository
```
sudo apt update
```
## Install Docker Engine and Compose
```
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
## Enable Docker
```
sudo systemctl enable --now docker
```
# Verify Docker
```
docker --version
docker compose version
```
## Download TheHive Docker Deployment
```
git clone https://github.com/StrangeBeeCorp/docker.git
```
## Enter the TheHive Production Directory
```
cd docker/prod1-thehive
```
## Initialize TheHive

> Run the initialization script provided by the official deployment:
```
bash ./scripts/init.sh
```
> Follow the prompts and provide the IP address/hostname of your TheHive server when requested.

## Start TheHive
```
docker compose up -d
```
## Check TheHive Containers
```
docker compose ps
```
> You should see the required services running, including TheHive, Cassandra, Elasticsearch, and Nginx.

## Check TheHive Logs
```
docker compose logs --tail=100 thehive
```
## Check All Services
```
docker compose logs --tail=100
```
## Find TheHive Server IP
```
ip addr
```
> Identify the IP address of your Ubuntu TheHive server.

## Open TheHive

> Open this in your browser:

```
https://YOUR_THEHIVE_SERVER_IP
```
