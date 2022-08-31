---
title: "Déployer un cluster Kubernetes avec Rancher 2.x"
slug:  deployer-un-cluster-kubernetes-avec-rancher-2-x
---


1. Créez une nouvelle instance.
   1. Choisissez CentOS comme image.
   1. Assurez-vous que la machine virtuelle dispose d'au moins 4 Go de RAM
   1. Ajoutez un volume à la machine virtuelle.(Optionnel)
   1. Ajoutez une clé ssh pour pouvoir accéder à la machine virtuelle.
   1. Ajoutez les éléments suivants sous Automation:
   **user-data**
   ```
   #cloud-config
   package_upgrade: true
   yum_repos:
     docker-main:
       name: Docker Repository
       baseurl: https://yum.dockerproject.org/repo/main/centos/7/
       enabled: true
       gpgcheck: true
       gpgkey: https://yum.dockerproject.org/gpg
   fs_setup:
     - label: data
       filesystem: 'btrfs'
       device: '/dev/xvdb'
   mounts:
     - [ xvdb, /var/lib/docker, "auto", "defaults", "0", "0" ]
   runcmd:
     - systemctl stop firewalld
     - setenforce 0
     - "sed -i 's/^SELINUX=.*/SELINUX=disabled/g' /etc/selinux/config"
     - yum install -y docker-engine
     - systemctl start docker
     - systemctl enable docker
     - "docker run -d --restart=unless-stopped -p 80:80 -p 443:443 rancher/rancher"
   ```
1. Configurez les règles de redirection de port pour la nouvelle instance. Reliez-les directement aux ports 80 et 443. Lorsque vous créez la deuxième règle, assurez-vous d'utiliser l'adresse IP publique créée par la première règle. Vous pouvez également éventuellement ajouter une redirection de port pour le port 22 si vous souhaitez vous connecter à la machine virtuelle.
![Détails de l'instance](/assets/deploy-kubernetes-with-rancher-en-1.png) <br><br>
![Redirection de ports](/assets/deploy-kubernetes-with-rancher-en-2.png)
1. Entrez l'adresse IP publique de votre navigateur dans un onglet séparé.  Ajoutez une exception de sécurité pour le certificat.
1. Vous verrez une boîte de dialogue pour un mot de passe administrateur.  Définissez-le et cliquez sur Suivant.
1. Vous verrez une invite pour l'URL du serveur Rancher.  Copiez l'adresse IP privée de l'instance que vous avez créée et utilisez-la.  Vous pouvez recevoir un avertissement qu'il s'agit d'une adresse IP privée, mais il faut l'utiliser.
![Détails de l'instance avec les règles de redirection de ports](/assets/deploy-kubernetes-with-rancher-en-3.png)
1. Selectionnez "Node Drivers" dans la barre de navigation. Dépendemment de votre version de Rancher, il est possible que Hypertec Cloud ne soit pas accessible comme fournisseur par défaut. S'il est présent, il suffit de cliquer sur ce dernier. Si toutefois il n'est pas présent, cliquerz sur "Add Node Driver" et ajoutez le avec les informations suivantes :
   1. "Download URL" : [https://github.com/cloud-ca/docker-machine-driver-cloudca/files/2446837/docker-machine-driver-cloudca_v2.0.0_linux-amd64.zip](https://github.com/cloud-ca/docker-machine-driver-cloudca/files/2446837/docker-machine-driver-cloudca_v2.0.0_linux-amd64.zip)
   1. "Custom UI URL" : [https://objects-east.cloud.ca/v1/5ef827605f884961b94881e928e7a250/ui-driver-cloudca/component.js](https://objects-east.cloud.ca/v1/5ef827605f884961b94881e928e7a250/ui-driver-cloudca/component.js)
   1. Checksum : 2a55efd6d62d5f7fd27ce877d49596f4
   1. Cliquez sur  "Add Whitelist Domain"
   1. "Whitelist Domain" : objects-east.cloud.ca
   ![Ajouter le pilote de nœuds](/assets/deploy-kubernetes-with-rancher-en-4.png)
1. Sélectionnez "Clusters" dans la barre de navigation.  Sous "Nodes from an Infrastructure Provider", choisissez Hypertec Cloud.
1. Faites défiler jusqu'à "Nodes from an Infrastructure Provider", puis ajoutez au moins un "Node Pool".  Cochez les cases pour que vous ayez rempli le nombre requis pour "etcd", "Control plane" et "workers". Si vous souhaitez économiser de l'espace, le "Control Plane" et "etcd" peuvent partager un seul serveur.
1. Cliquez sur "Node Template" pour l'un des serveurs. Vous serez invité à saisir votre clé d'API Hypertec Cloud.
1. Si vous ne disposez pas de votre clé API, vous pouvez en générer une sur Hypertec Cloud en cliquant sur votre nom dans le coin inférieur gauche de l'interface Hypertec Cloud pour afficher votre profil.
   1. ![Barre latérale de Hypertec Cloud](/assets/deploy-kubernetes-with-rancher-en-5.png)
   1. Sélectionnez les informations d'identification de l'API dans le menu Paramètres, puis cliquez sur "Générer une clé API".
   1. Entrez un nom, puis cliquez sur Générer. Un pop-up sera affiché avec la clé API. La clé API ici doit être copiée et stockée de manière sécurisée, car elle ne sera plus affichée.
   1. Entrez votre nouvelle clé dans l'invite de Rancher.
1. Sélectionnez l'environnement dans lequel déployer ces nodes. Assurez-vous de choisir le même environnement sur lequel votre VM Rancher a été créé.
1. Entrez les spécifications (CPU, RAM) de vos instances. La configuration de Hypertec Cloud créera un volume supplémentaire d'au moins 10 Go pour traiter les données liés à Docker sans impacter la machine virtuelle elle-même.
   1. Assurez-vous que le type de disque pour le volume supplémentaire est défini sur une option fournie par Hypertec Cloud. "Performance, No QoS" peut ne pas être disponible dans votre région.
   1. Assurez-vous que vous utilisez le même réseau que la VM Rancher.
1. Nommez le l'instance, puis ajoutez les étiquettes de votre choix pour la planification (par exemple, une étiquette pour différencier les "workers" et "etcd"). Vous pouvez également ajouter toutes les modifications requises de Docker, telles que les registres non sécurisés et les miroirs de registre. Une fois cela fait, créez le l'instance.
1. Assurez-vous que tous les pools de nœuds ont les modèles souhaités.  Au besoin, créez des modèles supplémentaires pour les appliquer, puis sélectionnez Créer.
   ![Rancher templates](/assets/deploy-kubernetes-with-rancher-en-6.png)
1. Après cela, vos nœuds devraient démarrer et vous devriez pouvoir les voir approvisionnés sous "Nodes" dans la barre de navigation.  Si vous recevez que ces nœuds reçoivent une erreur HTTP 400, consultez les détails de calcul de votre Node Template.  Il est possible que vous ayez sélectionné une offre qui n'est pas disponible dans votre région. Vous devrez resélectionner toutes les options et enregistrer le Node Template pour qu'il soit appliqué. Le Node Template ne sera pas appliqué immédiatement, mais Rancher essaiera de générer à nouveau ces nœuds à intervalles réguliers.
1. Attendez que Rancher démarre vos nœuds. Cela prendra probablement plusieurs minutes, car les nœuds doivent être créés, provisionnés et importés dans le cluster Kubernetes.
