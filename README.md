#  Projet DevOps — Stack GLPI

---

##  A faire

* Pipe line: git push --> ssh vm : restart docker compose
* Ansible : provisionne la vm Ubuntu serveur --> install docker --> créa dossier --> clone repo (si possible)
* tache cron : dump DB + save fichier GLPI --> envoie si possible stockage externe  ( Mais mieux utiliser proxmox backup )
* Peut être mise en place de Traefik ( déjà commencer à finir if good )

---

##  Déjà réalisé

###  Docker compose : NPM + GLPI + MARIADB + UPTIME-KUMA

---

###  NPM

* UI simple et sécu possible OTP
* Reverse Proxy
* Domaine utilisé daryu.xyz : glpi.daryu.xyz ----- status.daryu.xyz

---

###  GLPI

* bah c'est GLPI quoi

---

###  MARIADB

* bah c'est la DB pour GLPI

---

###  UPTIME-KUMA

* UI simple et sécu possible OTP
* Permet de superviser l'uptime des service, avec Dashboard pour les clients et envoie de log uptime sur (Discord, sms, mail…)

---

##  Docker compos

```bash
sudo docker compose -f GLPI.yml up -d
```

* une commande pour tous lancer
* Tous les services dans le même
* network divisé ( pour mieux Reigner ),
* .env ( possibilité de faire des secret, mais franchement inutilisé dans le monde de l'entreprise actuellement)
* service en unless-stop
* des Dependance de service

---

##  Network

* internal : DB + GLPI
* Proxy : NPM + GLPI
* Monitoring : Full

---
