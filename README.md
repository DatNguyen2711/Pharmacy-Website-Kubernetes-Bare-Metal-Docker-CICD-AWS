## Getting Started

First, run the development server:

```bash
docker compose up -d
```

Open [http://localhost:8900](http://localhost:8900) with your browser to see the result.

You can start editing the page by modifying `Medicine-Web-FE/src/component/auth/login`. The page auto-updates as you edit the file.

This project uses [`next/font`](https://dotnet.microsoft.com/en-us/download/dotnet/8.0) to write API and also ReactJS for client

## Learn More


## Deploy on EC2 Instance 

The easiest way to deploy this app is to use the AWS EC2 [AWS Platform](https://ap-southeast-1.console.aws.amazon.com/ec2/home?region=ap-southeast-1#Home:) 

Step 1: Register a EC2 (T2 medium above because SQL server need 2000MB to run) instance using Ubuntu ( Remember you open Inbound Rules of Instance before run the application [AWS Platform](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DAX.create-cluster.console.configure-inbound-rules.html) )

Step 2: Download Docker (lastest version is best)
```bash
mkdir -p /tools/docker

touch docker-install.sh && chmod +x docker-install.sh && nano docker-install.sh

#!/bin/bash
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update -y
sudo apt install docker-ce -y
sudo systemctl start docker
sudo systemctl enable docker
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker -v
docker-compose -v


sh docker-install.sh


sudo usermod -aG docker $(whoami)

```
Step 3 : Clone this Repo and cd path/to/the repo

Step 4 : 
```bash
docker compose up -d
```
Step 5:
Go to the address:
```bash
http://{instance_public_IP_address}:8900
```