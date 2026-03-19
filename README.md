# 📦 GLPI Monitoring Stack (Docker + Traefik + CI/CD)

## 🚀 Description

Ce projet met en place une infrastructure complète de supervision et gestion IT basée sur :

- **GLPI** → gestion de parc IT  
- **MariaDB** → base de données  
- **Traefik** → reverse proxy + HTTPS automatique (Let's Encrypt)  
- **Uptime Kuma** → monitoring des services  
- **CI/CD GitHub Actions** → déploiement automatique  
- **Trivy** → scan de sécurité (secrets)  

---

## 🧱 Architecture

```
                🌍 Internet
                     │
                     ▼
        🔐 Traefik (Reverse Proxy + HTTPS)
                     │
        ┌────────────┼────────────┐
        ▼            ▼            ▼
     🖥 GLPI     📊 Uptime Kuma   ⚙️ Dashboard Traefik
        │
        ▼
     🗄 MariaDB (réseau interne sécurisé)
```

---

## ⚙️ Stack technique

- Docker & Docker Compose  
- Traefik v3 (reverse proxy)  
- MariaDB 11  
- GLPI (latest)  
- Uptime Kuma  
- GitHub Actions (CI/CD)  
- Trivy (security scan)  

---

## 📁 Structure du projet

```
.
├── docker-compose.yml
├── .env
├── .github/
│   └── workflows/
│       ├── deploy.yml
│       └── trivy-secrets.yml
```

---

## 🔐 Configuration (.env)

Créer un fichier `.env` :

```
LETSENCRYPT_EMAIL=ton.email@exemple.com

TRAEFIK_DOMAIN=traefik.tondomaine.fr
GLPI_DOMAIN=glpi.tondomaine.fr
KUMA_DOMAIN=status.tondomaine.fr

TRAEFIK_BASIC_AUTH=admin:hash_htpasswd

DB_ROOT_PASSWORD=motdepasse_root
DB_NAME=glpi
DB_USER=glpi
DB_PASSWORD=motdepasse_glpi

GLPI_ADMIN_USER=admin
GLPI_ADMIN_PASSWORD=motdepasse_admin
```

---

## 🌐 Accès aux services

| Service        | URL |
|----------------|-----|
| GLPI           | https://glpi1.daryu.xyz |
| Uptime Kuma    | https://status1.daryu.xyz |
| Traefik        | https://traefik1.daryu.xyz |

---

## 🐳 Lancement du projet

```bash
git clone https://github.com/LuquyPest/devops_cours.git
docker compose up -d
```

---

## 🔁 CI/CD (Déploiement automatique)

Le déploiement se fait automatiquement via GitHub Actions.

### Étapes :

```
1. Récupération du code
2. Vérification docker-compose
3. Pull des images Docker
4. Redémarrage des containers
```

---

## 🔍 Sécurité (Trivy)

```bash
trivy fs --scanners secret --exit-code 1 .
```

---

## 🔒 Sécurité mise en place

- HTTPS automatique (Let's Encrypt)  
- Dashboard Traefik protégé (Basic Auth)  
- Réseau Docker interne  
- Variables sensibles externalisées (.env)  
- Scan de sécurité avec Trivy  

---

## 👨‍💻 Auteur

Daryu / Jimmy / Marie / Bastien
