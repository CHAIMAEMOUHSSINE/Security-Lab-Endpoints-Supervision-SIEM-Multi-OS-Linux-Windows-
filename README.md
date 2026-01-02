# Atelier Sécurité SIEM & EDR Multi-OS (Linux & Windows)

**Atelier pratique de déploiement et de supervision de la sécurité des endpoints Linux et Windows à l’aide de Wazuh (SIEM & EDR) dans un environnement Cloud AWS.**

---

## Project Overview

Ce projet illustre la mise en place d’une plateforme complète de cybersécurité combinant les technologies **SIEM (Security Information and Event Management)** et **EDR (Endpoint Detection and Response)**.  
L’environnement déployé couvre des systèmes **Linux (Ubuntu)** et **Windows Server**, avec une supervision centralisée, une détection avancée des menaces et des scénarios réalistes de sécurité.

L’objectif est de reproduire le fonctionnement d’un **SOC moderne** dans un contexte Cloud réel.

---

## Concepts Covered

### 1. SIEM (Security Information and Event Management)
- **Purpose:** Centraliser, corréler et analyser les événements de sécurité en temps réel.
- **Role:** Fournir une visibilité globale sur les incidents et générer des alertes de sécurité.

### 2. EDR (Endpoint Detection and Response)
- **Purpose:** Surveiller les endpoints pour détecter et répondre aux comportements malveillants.
- **Role:** Collecter des données détaillées sur les processus, connexions et activités suspectes (Sysmon sous Windows).

### 3. IAM (Identity and Access Management)
- **Purpose:** Gérer les accès et privilèges utilisateurs.
- **Role:** Réduire les risques liés aux accès non autorisés.

### 4. Threat Hunting
- **Purpose:** Recherche proactive de menaces avancées.
- **Role:** Identifier des attaques non détectées automatiquement via des requêtes Wazuh.

---

## Tools & Technologies Used

- AWS EC2 (Learner Lab)
- Wazuh (SIEM & EDR)
- Ubuntu 22.04 LTS
- Windows Server 2025
- Sysmon (Windows)
- Bash & PowerShell
- Git & GitHub

---

## Lab Architecture

| Instance Name  | OS                | Role                                      | Type        |
|----------------|------------------|-------------------------------------------|-------------|
| Wazuh-Server   | Ubuntu 22.04 LTS | Wazuh Manager + Indexer + Dashboard       | t3.large    |
| Linux-Client   | Ubuntu 22.04     | Wazuh Agent                               | t2/t3.micro |
| Windows-Client | Windows Server   | Wazuh Agent + Sysmon                      | t2.medium   |

---

## Network Configuration

### Required Ports

| Port | Protocol | Usage |
|------|----------|-------|
| 22   | TCP      | SSH (Linux) |
| 3389 | TCP      | RDP (Windows) |
| 443  | TCP      | Wazuh Dashboard |
| 1514 | TCP      | Agent Communication |
| 1515 | TCP      | Agent Enrollment |

---

## Deployment Steps

### Step 1: Install Wazuh Server (Ubuntu)

```bash
sudo apt update && sudo apt -y upgrade
curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh
sudo bash wazuh-install.sh -a
