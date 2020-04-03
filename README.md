![alt tag](https://github.com/GoVanguard/legion/blob/master/images/LegionBanner.png)
[![Build Status](https://travis-ci.com/GoVanguard/legion.svg?branch=master)](https://travis-ci.com/GoVanguard/legion)
[![Known Vulnerabilities](https://snyk.io/test/github/GoVanguard/legion/badge.svg?targetFile=requirements.txt)](https://snyk.io/test/github/GoVanguard/legion?targetFile=requirements.txt)
[![Maintainability](https://api.codeclimate.com/v1/badges/4e33e52aab8f49cdcd02/maintainability)](https://codeclimate.com/github/GoVanguard/legion/maintainability)
![Linter](https://img.shields.io/badge/linter-flake8-brightgreen)
[![Analytics](https://ga-beacon-gvit.appspot.com/UA-126307374-3/legion/readme)](https://github.com/GoVanguard/legion)



## ABOUT
Legion, une branche de Sparta de SECFORCE, est un réseau open source, facile à utiliser, super-extensible et semi-automatisé
cadre de tests de pénétration qui facilite la découverte, la reconnaissance et l'exploitation des systèmes d'information.
[Legion](https://govanguard.com/legion) est développé et maintenu par[GoVanguard](https://govanguard.com). 
Plus d'informations sur Legion, y compris le[roadmap](https://govanguard.com/legion), peut être trouvé sur son projet
sur [https://GoVanguard.com/legion](https://govanguard.com/legion).
Si vous souhaitez contribuer à la Légion, rejoignez notre [Legion Keybase Team](https://keybase.io/team/govanguard.dev.legion).

### FEATURES

* Reconnaissance et numérisation automatiques avec NMAP, whataweb, nikto, Vulners, Hydra, SMBenum, dirbuster, sslyzer, webslayer
et plus (avec près de 100 scripts auto-programmés)
* Interface graphique facile à utiliser avec des menus contextuels et des panneaux riches qui permettent aux pentesters de              trouver et exploiter les vecteurs d'attaque sur les hôtes
* La fonctionnalité modulaire permet aux utilisateurs de personnaliser facilement Legion et d'appeler automatiquement leurs propres scripts / outils
* Balayage de scène hautement personnalisable pour une évasion IPS de type ninja
* Détection automatique des CPE (Common Platform Enumeration) et des CVE (Common Vulnerabilities and Exposures)
* Lie les CVE aux exploits comme détaillé dans Exploit-Database
* Enregistrement automatique en temps réel des résultats et des tâches du projet

### CHANGEMENTS NOTABLES DE SPARTA

* Refactorisé de Python 2.7 à Python 3.6 et l'élimination des bibliothèques obsolètes et non entretenues
* Mise à niveau vers PyQT5, réactivité accrue, moins de bugs, interface graphique plus intuitive qui comprend des fonctionnalités telles que:
   * Estimations de fin de tâche
   * Listes de scan en 1 clic des sous-réseaux ips, hostnames et CIDR
   * Possibilité de purger les résultats, de réanalyser les hôtes et de supprimer les hôtes
   * Options de numérisation NMAP granulaire
* Prise en charge de la résolution du nom d'hôte et de l'analyse des hôtes vhosts / sni
* Révisez les routines de mise en file d'attente et d'exécution des processus pour améliorer la fiabilité et les performances des applications
* Simplification de l'installation avec résolution des dépendances et routines d'installation
* Sauvegarde automatique du projet en temps réel donc en cas de problème, vous ne perdrez aucun progrès!
* Option de déploiement de conteneur Docker
* Soutenu par une équipe de développement très active

### GIF DEMO 
![](https://govanguard.com/wp-content/uploads/2019/02/LegionDemo.gif)

## INSTALLATION

Il est préférable d'utiliser l'image docker par rapport à une installation traditionnelle. C'est à cause de toute la dépendance
exigences et les complications qui se produisent dans des environnements qui diffèrent d'une installation propre et non par défaut.

REMARQUE: les versions Docker de Legion sont * peu susceptibles * de fonctionner lorsqu'elles sont exécutées en tant que root ou sous un root X!

### Distributions prises en charge
#### Docker runIt script

runIt prend en charge Ubuntu 18, Fedora 30, Parrot et Kali pour le moment. Il est possible d'exécuter l'image docker sur n'importe quel
La distribution Linux, cependant, différentes distributions ont des cercles différents à parcourir pour obtenir une application docker
pouvoir se connecter au serveur X. Tout le monde est le bienvenu pour essayer de comprendre ces cerceaux et créer un PR pour runIt. 

#### Installation traditionnelle

Nous ne pouvons pas promettre un fonctionnement correct sur Ubuntu 18 en utilisant l'installation traditionnelle pour le moment. Alors qu'il devrait
travailler sur ParrotOS, Kali et autres, jusqu'à ce que Legion soit emballé et placé dans les dépôts pour chacune de ces distributions
ce sont des chaises musicales en ce qui concerne les mises à jour de plate-forme changeant et brisant les dépendances.

### DOCKER METHOD
------

Linux with Local X11:

 - Suppose que Docker et X11 sont installés et configurés (y compris l'exécution de commandes Docker en tant qu'utilisateur non root)
 - Il est essentiel de suivre toutes les instructions pour fonctionner en tant qu'utilisateur non root. Sauter l'un d'eux entraînera des complications pour que docker communique avec le serveur X
 - Voir les instructions détaillées pour configurer docker [içi](#docker-setup) et activer l'exécution de conteneurs en tant qu'utilisateurs non root et octroi de droits ssh à un groupe de dockers [içi](#docker-setup-non-root)

 - avec le Terminal:
   ```
   git clone https://github.com/GoVanguard/legion.git
   cd legion/docker
   chmod +x runIt.sh
   ./runIt.sh
   ```
Linux avec Remote X11:
 - Suppose que Docker et X11 sont installés et configurés
 - Remplacez X.X.X.X par l'IP de la télécommande exécutant X11.
 - Dans le terminal:
   ```
   git clone https://github.com/GoVanguard/legion.git
   cd legion/docker
   chmod +x runIt.sh
   ./runIt.sh X.X.X.X
   ```

Windows sous WSL utilisant Xming et Docker Desktop:
 - Suppose que Xming est installé dans Windows
 - Suppose que Docker Desktop est installé sous Windows, Docker Desktop s'exécute en mode conteneurs Linux et
 Docker Desktop est connecté à WSL
 - Voir les instructions détaillées [içi](# docker-setup-wsl)
 - Remplacez X.X.X.X par l'adresse IP avec laquelle Xming s'est enregistré.
   - Cliquez avec le bouton droit sur Xming dans la barre d'état système -> Afficher le journal et voir IP à côté de "XdmcpRegisterConnection: newAddress"
 - Dans le terminal:
   ```
   git clone https://github.com/GoVanguard/legion.git
   cd legion/docker
   sudo chmod +x runIt.sh
   sudo ./runIt.sh X.X.X.X
   ```

Windows utilisant Xming et Docker Desktop sans WSL:
 - Pourquoi? Ne fais pas ça. :)


OSX utilisant XQuartz:
 - Pas encore dans le script runIt.sh.
 - Possibilité de configuration à l'aide de socat. Voir les instructions [ici](https://kartoza.com/en/blog/how-to-run-a-linux-gui-application-on-osx-using-docker/)


<a name="docker-setup"></a>
Configuration de Docker sous Linux:
 - Pour installer les composants de docker généralement nécessaires et ajouter la configuration de l'environnement pour docker, sous un terme, exécutez:

   ```
   sudo apt-get update
   sudo apt-get install -y docker.io python-pip -y
   sudo groupadd docker
   pip install --user docker-compose
   ```

<a name="docker-setup-non-root"></a>
Configurez Docker pour autoriser les utilisateurs non root:
 - Pour permettre aux utilisateurs non root d'exécuter des commandes docker, sous un terme, exécutez:
   ```
   sudo usermod -aG docker $USER
   sudo chmod 666 /var/run/docker.sock
   sudo xhost +local:docker
   ```

<a name="docker-setup-wsl"></a>
Setup Hyper-V, Docker Desktop, Xming and WSL:
 - The order is important for port reservation reasons. If you have WSL, HyperV or Docker Desktop installed then 
 please uninstall those features before proceeding.
 - Cortana / Search -> cmd -> Right click -> Run as Administrator
 - To reserve the docker port, under CMD, run:
   ```
   netsh int ipv4 add excludedportrange protocol=tcp startport=2375 numberofports=1
   ```
   - This will likely fail if you have Hyper-V already enabled or Docker Desktop installed
 - To install Hyper-V, under CMD, run:
   ```
   dism.exe /Online /Enable-Feature:Microsoft-Hyper-V /All
   ```
 - Reboot
 - Cortana / Search -> cmd -> Right click -> Run as Administrator
 - To install WSL, under CMD, run:
   ```
   dism.exe /Online /Enable-Feature /FeatureName:Microsoft-Windows-Subsystem-Linux
   ```
 - Reboot
 - Download from https://hub.docker.com/editions/community/docker-ce-desktop-windows (Free account required)
 - Run installer
 - Optionally input your docker hub login
 - Right click Docker Desktop in system tray -> Switch to Linux containers
   - If it says Switch to Windows containers then skip this step, it's already using Linux containers
 - Right click Docker Desktop in system tray -> Settings
 - General -> Expose on localhost without TLS
 - Download https://sourceforge.net/projects/xming/files/Xming/6.9.0.31/Xming-6-9-0-31-setup.exe/download
 - Run installer and select multi window mode
 - Open Microsoft Store
 - Install Kali, Ubuntu or one of the other WSL Linux Distributions
 - Open the distribution, let it bootstrap and fill in the user creation details
 - To install docker components typically needed and add setup the environment for docker redirection, 
 under the WSL window, run:
   ```
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
   sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
   sudo apt-get update
   sudo apt-get install -y docker-ce python-pip -y
   sudo apt autoremove
   sudo usermod -aG docker $USER
   pip install --user docker-compose
   echo "export DOCKER_HOST=tcp://localhost:2375" >> ~/.bashrc && source ~/.bashrc
   ```
 - Test docker is reachable with:
   ```
   docker images
   ```

### TRADITIONAL METHOD
 - Veuillez utiliser l'image docker si possible! Il devient très difficile de prendre en charge toutes les différentes plates-formes
 et leurs propres caprices
 - Suppose qu'Ubuntu, Kali ou Parrot Linux est utilisé avec Python 3.6 installé.
 - Dans le terminal:
   ```
   git clone https://github.com/GoVanguard/legion.git
   cd legion
   sudo chmod +x startLegion.sh
   sudo ./startLegion.sh
   ```

## Development

### Executing test cases

To run all test cases, execute the following in root directory:

```bash
python -m unittest
```

## LICENSE

Legion is licensed under the GNU General Public License v3.0. Take a look at the 
[LICENSE](https://github.com/GoVanguard/legion/blob/master/LICENSE) for more information.

## ATTRIBUTION
* Refactored Python 3.6+ codebase, added feature set and ongoing development of Legion is credited to [GoVanguard](https://govanguard.com)
* The initial Sparta Python 2.7 codebase and application design is credited SECFORCE.
* Several additional PortActions, PortTerminalActions and SchedulerSettings are credited to batmancrew.
* The nmap XML output parsing engine was largely based on code by yunshu, modified by ketchup and modified SECFORCE.
* ms08-067_check script used by smbenum.sh is credited to Bernardo Damele A.G.
* Legion relies heavily on nmap, hydra, python, PyQt, SQLAlchemy and many other tools and technologies so we 
would like to thank all of the people involved in the creation of those.
* Special thanks to Dmitriy Dubson for his continued contributions to the project!
