# IT2C_WH_Project
**Dokumentace k WH stránce**

**Updatování systému**

sudo apt update \
sudo apt upgrade 

**Instalace Dockeru** \

sudo apt install docker.io \
sudo systemctl enable docker 
sudo systemctl start docker \
sudo systemctl status docker 

**Instalace Portaineru** \

sudo docker run -d \
--name="portainer" \
--restart on-failure \
-p 9000:9000 \
-p 8000:8000 \
-v /var/run/docker.sock:/var/run/docker.sock \
-v portainer_data:/data \
portainer/portainer-ce:latest
