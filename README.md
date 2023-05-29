# IT2C_WH_Project
**Dokumentace k WH stránce**

**Updatování systému**
````console
sudo apt upgrade 
````
- "sudo apt upgrade" aktualizuje nainstalované balíčky na nejnovější verze.
````console
sudo apt update
````
- "sudo apt update" aktualizuje seznam dostupných balíčků z repositářů

**Instalace Dockeru**
````console
sudo apt install docker.io
````
- Tento příkaz nainstaluje balíček Docker.io, který obsahuje všechny potřebné závislosti a soubory pro spuštění Dockeru.
````console
sudo systemctl enable docker
````
- Tento příkaz nastaví Docker jako službu, která se spouští při startu systému.
````console
sudo systemctl start docker
````
- Tento příkaz spustí Docker službu na systému.
````console
sudo systemctl status docker 
````
- Tento příkaz ověřuje stav Docker služby a vypisuje informace o aktuálním stavu (spuštěná / zastavená).

**Instalace Portaineru** 
````console
sudo docker run -d
````
-d spustí kontejner v pozadí (detached mode)
````console
--name="portainer"
--restart on-failure
-p 9000:9000
-p 8000:8000
-v /var/run/docker.sock:/var/run/docker.sock
-v portainer_data:/data
portainer/portainer-ce:latest
````
- pojmenuje kontejner jako "portainer"
- automaticky restartuje kontejner v případě chyby
- propojí port 9000 hostitelského počítače s portem 9000 v kontejneru
- propojí port 8000 hostitelského počítače s portem 8000 v kontejneru
- sdílí socket Dockeru mezi hostitelským počítačem a kontejnerem
- vytvoří oddíl pro ukládání dat Portaineru
- použije nejnovější verzi Portaineru z oficiálního registru Docker.
**Instalace SSH**
````console
sudo snap install core; sudo snap refresh core
````
- Je potřeba nainstalovat snapd a ujistit se pomocí příkazu "sudo snap install core; sudo snap refresh core", že je updatován

**Vymázání certbot-auto a jakékoliv Certbot OS balíčky**
Odstraňte balíčky Certbot nainstalované pomocí správce balíčků (apt, dnf nebo yum) před instalací Certbotu ze snapu. To zajistí, že při spuštění příkazu certbot bude použit Certbot ze snapu. Přesný příkaz závisí na vašem operačním systému, ale běžné příklady jsou sudo apt-get remove certbot, sudo dnf remove certbot nebo sudo yum remove.
**Instalace Certbota**
můžete použít příkazy - sudo apt-get remove certbot, sudo dnf remove certbot, nebo sudo yum remove

**Příprava Certbot příkazu**
````console
sudo ln -s /snap/bin/certbot /usr/bin/certbot
````
- Vytvoří symbolický odkaz mezi umístěním souboru certbot v systému snap a umístěním souboru certbot v umístění /usr/bin. To umožní použití příkazu certbot z příkazové řádky bez nutnosti uvádět plnou cestu k souboru certbot.

**Najěte certifkát**
````console
sudo certbot certonly --apache
````
- Používá Certbot k získání SSL certifikátu pro webovou aplikaci, která běží na apache serveru. Tento příkaz se používá, pokud chcete získat certifikát bez automatické konfigurace serveru

**Otestujte automatické obnovení**
````console
sudo certbot renew --dry-run
````
- Tento příkaz se používá pro testování, zda je nastaven automatický obnovovací proces.
Příkaz pro obnovení certbot je nainstalován v jednom z následujících umístění:
````console
/etc/crontab/
/etc/cron.*/*
systemctl list-timers
````
- /etc/crontab/ a /etc/cron.*/*: Tyto adresáře obsahují skripty cronu, které se používají k plánování periodických úloh v operačním systému Linux.
- systemctl list-timers: Zobrazuje seznam plánovaných úloh, které spouští systémový démon timer.
- sudo ufw enable: Povoluje firewall Uncomplicated Firewall (ufw) v operačním systému Linux.

**Na konec je důležité se ujistit, že vše funguje jak má.** 

**Instalace firewalu**
````console
sudo ufw enable
sudo ufw allow 22
sudo ufw allow 80
sudo ufw allow 443
sudo ufw reload
````
- sudo ufw enable: povoluje firewall Uncomplicated Firewall (ufw) v operačním systému Linux.
- sudo ufw allow 22: Povoluje komunikaci na portu 22 (SSH) pro vzdálený přístup k serveru.
- sudo ufw allow 80: Povoluje komunikaci na portu 80 (HTTP) pro webovou aplikaci.
- sudo ufw allow 443: Povoluje komunikaci na portu 443 (HTTPS) pro zabezpečenou webovou aplikaci.
- sudo ufw reload: Aktualizuje konfiguraci firewallu, aby se změny projevily okamžitě.\
\
\
**Zabezpečení**
````console
sudo nano /etc/ssh/sshd_config
````
- Nejdříve si otevřeme soubor obsahující konfiguraci
````console
PasswordAuthentication no
````
- Upravíme řádek
- Příkaz "PasswordAuthentication no" vypne možnost přihlašování pomocí hesla na SSH serveru.
````console
PermitRootLogin no
````
- Upravíme řádek
- Zakáže přihlašování přes root
````console
Port 489
AddressFamily inet
````
- Přenastaví port na 465535 z důvodu zvýšení bezpečnosti
````console
sudo systemctl restart sshd
````
- Restartování ssh
- Pro opětovné přihlášení použijeme:
````console
ssh -i .ssh/server_key sysadmin@192.168.56.10 -p 65535
````
````console
sudo ufw deny 22
````
- Zakázání portu 22
````console
sudo ufw reload
````
Aktualizuje konfiguraci firewallu, aby se změny projevily okamžitě.\
\
\
**##############\
  ##Web Content##\
  ##############**
 ````console
 -i C:.......
 ````
 - Příkaz zkopiruje složku d
zkopiruje slozku dojmena(unity hra) z meho pc do domovskeho adresare uzivatele ubuntu na serveru ( "-i C:......." pouzije klice, aby se ty soubory vubec mohli poslat na server)
````console
scp -i C:\Users\*nazevuzivatele*\Downloads\ssh-key.key 
-r "C:\Users\*nazevuzivatele*\Desktop\dojmena" ubuntu@dojmena.ssibrno.cz:~
````
- Smaže starou stránku
````console
sudo rm /var/www/html/index.html
````

- Přemístí složky z **dojmena** 
````console
sudo mv /home/dojmena/* /var/www/html
````

- Restartuje apache
````console
sudo systemctl restart apache2
````
