# Shuffle SOAR Server Installation in docker (Ubuntu)
## Update & Upgrade Ubuntu
```
sudo apt update && sudo apt upgrade -y
```
## Install Git
```
sudo apt install git -y
```
## Install Docker
```
sudo apt install docker.io -y
```
## Enable and Start Docker
```
sudo systemctl enable --now docker
```
## Verify Docker
```
sudo systemctl status docker
```
> You should see active (running).

## Install Docker Compose

> Check whether the Docker Compose plugin is already available:

> docker compose version

> If it is not available, install it:
```
sudo apt install docker-compose-plugin -y
```
> Then verify:
> docker compose version
## Clone the Official Shuffle Repository
```
git clone https://github.com/Shuffle/Shuffle.git
```
## Enter the Shuffle Directory
```
cd Shuffle
```
> Configure OpenSearch Permissions
> Shuffle's official installation guide requires the shuffle-database directory to have the appropriate ownership.
```
sudo chown -R 1000:1000 shuffle-database
```
> Disable Swap
> Shuffle's installation documentation recommends disabling swap for the OpenSearch database.
```
sudo swapoff -a
```
> To make the change persistent after reboot:
```
sudo sed -i '/\sswap\s/s/^/#/' /etc/fstab
```
## Configure OpenSearch Memory Mapping
```
sudo sysctl -w vm.max_map_count=262144
```
## Make it persistent:
```
echo "vm.max_map_count=262144" | sudo tee /etc/sysctl.d/99-shuffle.conf
```
## Apply it:
```
sudo sysctl --system
```
Shuffle specifically recommends vm.max_map_count=262144 for OpenSearch.

> Check Shuffle Configuration
> The Shuffle repository contains the .env file used by the Docker Compose deployment. Shuffle's documentation states that configuration such as database locations, ports and host information can be controlled through .env.

## Open it:
```
nano .env
```
> For a lab installation, you should at minimum verify the OUTER_HOSTNAME value and set it to your Shuffle server's IP address if the supplied configuration requires it.
> For example:
> OUTER_HOSTNAME=192.168.1.60
> Replace 192.168.1.60 with the actual IP of your Shuffle Ubuntu VM.
> Save:
```
CTRL + O → Enter → CTRL + X
```
## Start Shuffle
> From inside the Shuffle directory:
```
sudo docker compose up -d
```
> This starts the Shuffle components in the background. The official installation guide uses Docker Compose for the standard deployment.

## Check Running Containers
```
sudo docker compose ps
```
> You should see the Shuffle services running, including components such as:
> Shuffle frontend
> Shuffle backend
> Shuffle Orborus
> OpenSearch

## Open Shuffle Dashboard from another computer on the same network, open:

http://xxx.xxx.xxx:3001

> Replace the IP with your actual Shuffle server IP.

> Shuffle's official installation documentation specifies port 3001 for the HTTP web interface; HTTPS is available on port 3443 in the standard setup.

> Create the Shuffle Administrator Account

> On the first visit, Shuffle will ask you to create the administrator account.

> There is no default username/password. You create the credentials during the initial setup.
