# 🔐 Mise en place d’une PKI avec IIS et Audit Wireshark

> **Projet Académique - Master 1 Sécurité des Systèmes d’Information (ESMT)**  
> **Membres :** Kasongo Mashika Samuel Evariste, Sokhna Sylla, HOUNTONDJI Geoffroy  
> **Encadreur :** Pr. Demba SOW

## 📌 Contexte & Objectif
Ce projet vise à sécuriser les communications Web en mettant en place une **Infrastructure à Clé Publique (PKI)** sous Windows Server. L'objectif est de démontrer concrètement l'apport du chiffrement TLS en comparant le trafic HTTP (non sécurisé) et HTTPS (sécurisé) via une analyse réseau avec **Wireshark**.

## 🏗️ Architecture du Laboratoire
L'environnement est virtualisé sous VMware Workstation avec un réseau isolé (Host-Only).

| Machine | Rôle | OS | IP Statique |
| :--- | :--- | :--- | :--- |
| **SRV-DC** | AD DS, DNS, Autorité de Certification (AD CS) | Windows Server 2022 | `192.168.100.10` |
| **SRV-IIS** | Serveur Web (IIS), URL Rewrite | Windows Server 2022 | `192.168.100.20` |
| **CLIENT-WIN** | Poste utilisateur de test | Windows 10/11 | `192.168.100.30` |
| **Hôte Ubuntu** | Analyseur de trafic (Sniffer) | Ubuntu 24.04 | N/A |

## 🚀 Fonctionnalités Implémentées
- ✅ Déploiement d'**Active Directory Domain Services (AD DS)** et création du domaine `lab.local`.
- ✅ Installation et configuration d'une **Autorité de Certification Entreprise (Enterprise Root CA)**.
- ✅ Génération de demande de certificat (CSR) et délivrance par la CA.
- ✅ Configuration d'**IIS** avec binding HTTPS (Port 443).
- ✅ Mise en place de la redirection automatique **HTTP → HTTPS** via URL Rewrite.
- ✅ Importation du certificat racine sur le client pour établir la chaîne de confiance.

## 🦈 Audit de Sécurité (Wireshark)
Une analyse comparative du trafic a été réalisée pour prouver l'efficacité du chiffrement :

### 1. Trafic HTTP (Non Sécurisé)
Les données applicatives (identifiants, mots de passe) circulent en **clair**.
![Audit HTTP](Docs/Captures_Ecrans/wireshark_http_clear.png)

### 2. Trafic HTTPS (Sécurisé)
Les mêmes données sont chiffrées via **TLS**. Seul le métadata (IP, Ports) reste visible.
![Audit HTTPS](Docs/Captures_Ecrans/wireshark_https_encrypted.png)

## 🛠️ Prérequis Techniques
- VMware Workstation
- Windows Server 2022 ISO
- Windows 10/11 ISO
- Ubuntu 24.04 (Hôte)
- Wireshark

## 📂 Contenu du Repository
- `Rapport_Projet.pdf` : Documentation complète du projet.
- `WebContent/index.html` : Code source de la page de test utilisée pour l'audit.
- `Scripts/` : Exemples de commandes PowerShell utilisées pour l'automatisation.

## 🎓 Compétences Développées
- Administration Windows Server (AD DS, AD CS, IIS)
- Cryptographie appliquée (PKI, Certificats X.509, TLS)
- Analyse Réseau (Wireshark, Filtrage TCP/HTTP/TLS)
- Gestion des incidents de sécurité (Configuration SAN, Chaîne de confiance)

---
*Pour plus de détails, consultez le [Rapport Complet](Rapport_Projet.pdf).*
