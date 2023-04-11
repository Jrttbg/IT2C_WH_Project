# IT2C_WH_Project
**Dokumentace k WH stránce**

**Updatování systému**

sudo apt update \
sudo apt upgrade 

**Instalace Dockeru** 

sudo apt install docker.io \
sudo systemctl enable docker \
sudo systemctl start docker \
sudo systemctl status docker 

**Instalace Portaineru** 

sudo docker run -d \
--name="portainer" \
--restart on-failure \
-p 9000:9000 \
-p 8000:8000 \
-v /var/run/docker.sock:/var/run/docker.sock \
-v portainer_data:/data \
portainer/portainer-ce:latest

**Instalace SSH**
Je potřeba nainstalovat snapd a ujistit se pomocí příkazu "sudo snap install core; sudo snap refresh core", že je updatován
**Vymázání certbot-auto a jakékoliv Certbot OS balíčky**
Pokud máte nějaké balíčky Certbot nainstalované pomocí správce balíčků operačního systému, jako je apt, dnf nebo yum, měli byste je před instalací modulu snap-out Certbot odstranit, abyste zajistili, že při spuštění příkazu certbot bude použit snap spíše než instalace ze správce balíčků operačního systému. Přesný příkaz k tomu závisí na vašem operačním systému, ale běžné příklady jsou sudo apt-get remove certbot, sudo dnf remove certbot, or sudo yum remove

**Instalace Certbota**
sudo apt-get remove certbot, sudo dnf remove certbot, or sudo yum remove

