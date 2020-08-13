---
title: "Créer un VPN site-à-site pour un VPC"
slug: creer-vpn-site-a-site-pour-un-vpc
---


Un VPN site-à-site est utile pour interconnecter un VPC à un bureau à distance, à un autre centre de données, ou à un autre VPC.  Pour plus de détails, consultez [Gestion des VPCs](../compute-service/working-with-vpcs.md).

L'exemple suivant illustre comment à connecter deux VPCs avec un site-à-site VPN.  Les détails varient selon vos appareils.

#### Détails pour les VPCs d'exemple
| Nom du VPC | Nom de l'environnement | CIDR du VPC | IP NAT source |
| --- | --- | --- | --- |
| dmz | env-dmz | 10.0.0.0/22 | 172.30.200.106 |
| gestion | env-gest | 10.0.4.0/22 | 172.30.200.107 |

#### Configuration du VPN site-à-site
1. Aller à l'environnement **dmz**.
1. Cliquer sur l'onglet *Réseautique*.
1. Cliquer sur l'icône d'engrenage pour *VPNs site-à-site*.
1. Cliquer sur *Ajouter VPN site-à-site*.
1. Saisir les détails du tunnel de **dmz** vers **gestion**.
   - **Nom :** Tunnel vers gestion
   - **Adresse IP distant :** 172.30.200.107
   - **CIDR distant :** 10.0.4.0/22
   - **Clé pré-partagée IPSec :** Uj2nzrTQ7xkbgun3ZqVFPbyxr9wfQzXZG5ZJ
   - **Détection de pair mort :** Activée
   - **Forcer l'encapsulation :** Désactivée
   - **Connexion passive :** Activée
   - Laisser les valeurs par défaut pour les autres options.
1. Cliquer *Valider*.
1. Aller à l'environnement **gestion** et répéter les étapes 2 à 4.
1. Saisir les détails du tunnel de **gestion** vers **dmz**:
   - **Nom :** Tunnel vers **dmz**
   - **Adresse IP distant :** 172.30.200.106
   - **CIDR distant :** 10.0.0.0/22
   - **Clé pré-partagée IPSec :** Uj2nzrTQ7xkbgun3ZqVFPbyxr9wfQzXZG5ZJ
   - **Détection de pair mort :** Activée
   - **Forcer l'encapsulation :** Désactivée
   - **Connexion passive :** Désactivée
   - Laisser les valeurs par défaut pour les autres options.
1. Cliquer *Valider*.
1. La liste des VPNs site-à-site maintenant énumère **Tunnel à dmz**.  L'état va dire **Connecté**.  De l'autre côté du VPN, la liste des VPNs site-à-site dans **dmz-env** aura une entrée,**Tunnel vers gestion**, et va dire **Connecté**.
