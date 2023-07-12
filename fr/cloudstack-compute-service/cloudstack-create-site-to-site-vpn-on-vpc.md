---
title: "CloudStack: Créer un VPN site-à-site pour un VPC"
slug: cloudstack-creer-vpn-site-a-site-pour-un-vpc
---


Un VPN site-à-site est utile pour interconnecter un VPC à un bureau à distance, à un autre centre de données, ou à un autre VPC.  Pour plus de détails, consultez [Gestion des VPCs](../cloudstack-compute-service/working-with-vpcs.md).

L'exemple suivant illustre comment à connecter deux VPCs avec un site-à-site VPN.  Les détails varient selon vos appareils.

#### Détails pour les VPCs d'exemple
| Nom du VPC | Nom de l'environnement | CIDR du VPC | IP NAT source |
| --- | --- | --- | --- |
| dmz | env-dmz | 10.0.0.0/22 | 172.30.200.106 |
| gestion | env-gest | 10.0.4.0/22 | 172.30.200.107 |

#### Configuration du VPN site-à-site
1. Aller à l'environnement **env-dmz**.
1. Cliquer sur l'onglet *Réseautique*.
1. Cliquer sur l'icône d'engrenage pour *VPNs site-à-site*.
1. Cliquer sur *Ajouter VPN site-à-site*.
1. Entrez les détails du tunnel de **dmz** à **gestion** :
    - **Nom de la connexion :** tunnel-vers-gestion
    - **Adresse IP distant (si un autre VPC, saisir Source NAT) :** 172.30.200.107
    - **Liste de CIDR distants (séparés par une virgule) :** 10.0.4.0/22
    - **Clé pré-partagée IPSec :** Uj2nzrTQ7xkbgun3ZqVFPbyxr9wfQzXZG5ZJ
    - **Chiffrement IKE :** AES128
    - **Empreinte IKE :** SHA1
    - **Groupe Diffie-Hellman IKE :** modp1536 (Groupe-5)
    - **Durée de vie IKE (en secondes) :** 86400
    - **Chiffrement ESP :** AES128
    - **Empreinte ESP :** SHA1
    - **Confidentialité persistante ESP :** modp1536 (Groupe-5)
    - **Durée de vie ESP (en secondes) :** 3600
    - **Détection de pair mort :** activée
    - **Forcer l'encapsulation pour NAT :** Désactivé
    - **Connexion passive (si le réseau distant n'est pas configuré):** activée
1. Cliquer *Valider*.
1. Aller à l'environnement **env-gest** et répéter les étapes 2 à 4.
1. Saisir les détails du tunnel de **gestion** vers **dmz**:
   - **Nom de la connexion :** tunnel-vers-dmz
   - **Adresse IP distant (si un autre VPC, saisir Source NAT) :** 172.30.200.106
   - **Liste de CIDR distants (séparés par une virgule) :** 10.0.0.0/22
   - **Clé pré-partagée IPSec :** Uj2nzrTQ7xkbgun3ZqVFPbyxr9wfQzXZG5ZJ
   - **Chiffrement IKE :** AES128
   - **Empreinte IKE :** SHA1
   - **Groupe Diffie-Hellman IKE :** modp1536 (Groupe-5)
   - **Durée de vie IKE (en secondes) :** 86400
   - **Chiffrement ESP :** AES128
   - **Empreinte ESP :** SHA1
   - **Confidentialité persistante ESP :** modp1536 (Groupe-5)
   - **Durée de vie ESP (en secondes) :** 3600
   - **Détection de pair mort :** activée
   - **Forcer l'encapsulation pour NAT :** désactivé
   - **Connexion passive (si le réseau distant n'est pas configuré):** désactivé
1. Cliquer *Valider*.
1. La liste des VPNs site-à-site maintenant énumère **tunnel-vers-dmz**.  L'état va dire **Connecté**.  De l'autre côté du VPN, la liste des VPNs site-à-site dans **env-dmz** aura une entrée, **tunnel-vers-gestion**, et va dire **Connecté**.
