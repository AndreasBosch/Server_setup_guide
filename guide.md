# SETUP AF SERVER 
## Droplet
vi starter ud med at gå ind på DigitalOcean og navigerer ind under droplets menuen. Derfra laver vi en server med følgende indstillinger:

### Distribution:
```
CentOS - 6.9 x32
```
### Size:

|Memory       |vCPUs   |SSD DISK       | TRANSFER | PRICE |
|:----------|:----------|:----------------|:------------|:-------|
|`1GB` |`1vCPU`   |`25GB` | `1TB` | `$5/mo  / $0.007/hr`

### Datacenter:
En af disse er anbefalet
```
Frankfurt | 1
Amsterdam | 2 / 3
```

### Hostname:
```
Angiv til sidst et relevant navn til din droplet
```

## PuTTY
Åbn dit PuTTY program og angiv din ip adresse på din Droplet, denne kan findes inde på DigitalOcean hvis man hover over navnet på din droplet. Det kan anbefales at gemme dine indstillinger så det er nemmere at åbne serveren op en anden gang.
* Når PuTTY åbner første gang kommer der en advarsel om manglen på et cached password, dette skal der bare svares "yes" til.

* Når du kommer videre og åbner command prompt'en igennem PuTTY skal du til at logge ind, som standard har nye servere altid brugernavnet "root" og et tilfældigt genereret kodeord (kodeordet bliver sendt til din mail når du opretter din droplet).

*  PuTTY vil tvinge dig til at ændre dit kodeord med det samme, kodeordet kan ikke indeholde et ord fra ordbogen, så det er en meget god idé at lave et "kludder" kodeord du kan huske.

* Nu er serveren klar til at få installeret diverse moduler, modulerne der skal installeres er som følgende:
## Nano
### Syntax:
```
yum install nano
```
## MySQL
### Syntax:
```
yum install mysql-server
```
### Start/Stop/restart:
```
service mysqld start/stop/restart
```
### Konfiguration af MySQL:
```
sudo /usr/bin/mysql_secure_installation
```

## Node.js
### Syntax:
```
yum install epel-release
yum install nodejs
yum install npm
npm install -g n
```
### Opdatering af Node.js:
```
n lts
n
```
### Herefter vil det være nødvendigt at genstarte din PuTTY linux box

## PM2
### Syntax:
```
npm install -g pm2
```
### Kør PM2 ved startup:
```
pm2 startup
```
## Git
### Syntax: 
```
yum install git
```
### Konfiguration af Git:
```
git config --global user.name "Dit navn"
git config --global user.email "din@email.dk"
```
### Tjek konfigurationen:
```
nano ~/.gitconfig
```
* Efter alle disse moduler er blevet installeres skal der oprettes et nøglesæt for at kunne forbinde din Server til Github.
### Opret nøglesæt
```
ssh-keygen -t rsa
```
* Herefter skal den offentlige nøgle åbnes
```
nano ~/.ssh/id_rsa.pub
```
* Kopier indholdet som bliver sendt tilbage til dig og gør som følgende:

GitHub.com -> Settings -> SSH and GPG keys -> New SSH key -> Paste indholdet du fik fra PuTTY og opret din nøgle.

* Herfter skal der oprettes en mappe til din applikation:
```
mkdir ~/www
```
### Naviger ind i mappen:
```
cd ~/www
```
## Kloning
* til sidst skal der klones noget indhold ind på serveren fra github fra en af dine repositories, det bliver gjort på følgende måde.
### Kloning:
```
git clone git@github.com:brugernavn/repository
```
### Opdatering/pull:
```
git pull git@github.com:brugernavn/repository
```