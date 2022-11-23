---
title: "Déployer une machine virtuelle à l'aide de Terraform"
slug: deployer-une-machine-virtuelle-a-l-aide-de-terraform
---


[Terraform](https://www.terraform.io/) est un outil largement utilisé pour automatiser la création et la maintenance d'une infrastructure virtuelle. En utilisant un langage déclaratif pour décrire les ressources souhaitées dans un déploiement, Terraform exécute les tâches nécessaires pour amener l'infrastructure à l'état décrit. Ce modèle de *infrastructure-as-code* permet des déploiements basés sur le cloud qui sont plus faciles à construire et, si nécessaire, plus faciles à reconstruire rapidement.

Un exemple simple présenté ici est l'utilisation de Terraform pour créer des instances basées sur la plate-forme Hypertec Cloud à l'aide de ressources de calcul de taille personnalisées.

### Prérequis

- [Terraform](https://www.terraform.io/downloads.html) doit être installé localement
- Le [provider de Terraform pour Hypertec Cloud](https://github.com/hypertec-cloud/terraform-provider-hci) doit être installé
- Une clé d'API pour Hypertec Cloud valide
    - Vous pouvez générer une clé d'API pour votre compte Hypertec Cloud en vous connectant à Hypertec Cloud, en allant dans *Mon profil* (dans le menu **Utilisateur** en haut à droite de la page), et en cliquant sur *Identifiants d'API* dans la barre latérale.
- L'ID de l'environnement cible
    - L'ID de l'environnement peut être trouvé en allant sur la page *Environnements* du service approprié, en cliquant sur le menu *Action* à l'extrême droite de l'environnement souhaité, et en cliquant sur *Copier l'ID de l'environnement*.
- L'ID du réseau cible
    - L'ID du réseau peut être trouvé en accédant à la page *Réseautique* de l'environnement cible, en cliquant sur le réseau souhaité dans la section **Réseaux** du VPC approprié, et l'ID du réseau sera le premier attribut répertorié. Cliquez sur l'ID du réseau pour le copier dans votre presse-papiers.

### Déployer une machine virtuelle

Se référer à la [documentation du provider de Terraform pour Hypertec Cloud](https://github.com/hypertec-cloud/terraform-provider-hci/tree/master/docs) pour les derniers attributs.

Ici, nous définissons les attributs que nous voulons pour notre nouvelle instance, *prod-app01*:

```
resource "hci_instance" "prod-app01" {
  environment_id = "4cad744d-bf1f-423d-887b-bbb34f4d1b5b"
  name = "prod-app01"
  network_id = "672016ef-05ee-4e88-b68f-ac9cc462300b"
  template = "centos 7"
  compute_offering = "nvme flash"
  ssh_key_name = "my_ssh_key"
  root_volume_size_in_gb = 100
  cpu_count = 1
  memory_in_mb = 1024
}
```

Ici, nous créons 10 instances du même type en utilisant les attributs définis ci-dessus, et elles seront nommées séquentiellement *prod-appXX* :

```
resource "hci_instance" "prod-app" {
  count = "10"
  environment_id = "4cad744d-bf1f-423d-887b-bbb34f4d1b5b"
  name = "prod-app${count.index}"
  network_id = "672016ef-05ee-4e88-b68f-ac9cc462300b"
  template = "centos 7"
  compute_offering = "nvme flash"
  ssh_key_name = "my_ssh_key"
  root_volume_size_in_gb = 100
  cpu_count = 1
  memory_in_mb = 1024
}
```

### Liens externes

- [Terraform](https://www.terraform.io/)
- [Le provider de Terraform pour Hypertec Cloud](https://github.com/hypertec-cloud/terraform-provider-hci)
