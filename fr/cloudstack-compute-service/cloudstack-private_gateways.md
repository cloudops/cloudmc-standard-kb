---
title: "CloudStack: Passerelles privées"
slug: cloudstack-passerelles-privees
---


Cet article présente le concept de passerelle privée et inclut des détails sur la gestion de leurs ACL et routes statiques.

## Aperçu détaillé

Les instances dans des VPC distincts sont isolées les unes des autres. Souvent, la configuration d'un [VPN site-à-site](create-site-to-site-vpn-on-vpc.md) est un moyen pratique d'établir une connexion entre deux VPC, permettant à leurs instances de communiquer entre elles . Il y a cependant des limites à cette approche. Un VPN crypte le trafic réseau, ce qui peut réduire les performances. De plus, les connexions VPN peuvent se terminer de manière inattendue et doivent être réinitialisées, ce qui affecte la disponibilité et les performances.

Pour résoudre ces problèmes, les fournisseurs de services peuvent proposer une infrastructure de réseau privé dédiée pour permettre l'appairage de deux VPC. Le trafic réseau entre les VPC traverse un chemin interne au lieu du réseau public. Ceci est utile lorsqu'une connexion fiable et rapide est nécessaire, comme pour les applications en temps réel ou pour la surveillance et la gestion. Dans un tel scénario, CloudMC est en mesure de tirer parti du chemin interne en créant une passerelle privée entre les VPC.

![Illustration simplifiée de deux VPC appairés par une passerelle privée sur une connexion réseau interne](/assets/private-gateways-diagram-fr.jpg)

Le diagramme ci-dessus illustre une topologie possible, où deux VPC sont appairés et chaque côté peut communiquer avec l'autre. Un routeur virtuel dans le VPC 1 se connecte à la passerelle privée via une interface réseau dédiée. Les cases rouges contiennent l'adresse IP qui pourrait être attribuée à chaque interface. Les adresses IP sont fournies à titre indicatif uniquement. Une passerelle privée est configurée dans les deux VPC et est identifiée de chaque côté par l'adresse IP de l'interface de terminaison sur le routeur virtuel. Dans cette illustration, la passerelle privée du VPC 1 serait répertoriée comme 10.0.5.2 et la passerelle privée du VPC 2 serait 10.0.2.2. Le diagramme n'inclut pas des détails du réseau physique sous-jacent, et il omet également les réseaux au sein de chaque VPC.

Étant donné que la configuration d'une passerelle privée nécessite une connaissance spécifique de la configuration du réseau physique, seul un compte CloudMC avec des privilèges de niveau revendeur peut configurer cette fonctionnalité. Cependant, les utilisateurs et les administrateurs ont l'autorisation de voir les passerelles privées dans leurs environnements et ils peuvent configurer l'accès et le routage. La configuration de la passerelle privée de chaque côté possède son propre ensemble de routes statiques. Celles-ci définissent, en fonction de l'IP de destination, le trafic qui sera acheminé via la passerelle privée. Le contrôle d'accès est établi via les ACL réseau que vous avez définies, voir [Sécuriser votre réseau](securing-your-network.md) pour plus d'informations.

Les passerelles privées sont visibles en accédant à l'environnement de votre choix, puis sur **Réseau** \> **Passerelles privées**.

![Une capture d'écran de la page de présentation du VPC, avec des points numérotés indiquant les fonctionnalités de la passerelle privée](/assets/private-gateways-vpc-fr.png)

1. **Liste des passerelles privées**

     Une liste de toutes les passerelles privées de ce VPC, ainsi que leur état, apparaît dans cette section. Chaque passerelle est identifiée par l'adresse IP de l'interface de terminaison \(l'autre extrémité de la connexion\).

2. **Icône d'engrenage**

     Cliquez sur l'icône d'engrenage pour accéder à la page **Passerelles privées** de ce VPC.


## Passerelles privées et ACL

![Capture d'écran de la page des détails des passerelles privées, avec des points numérotés sur les principales fonctionnalités](/assets/private-gateways-list-fr.png)

1. **Liste des passerelles privées**

     Dans la zone principale de l'espace de travail, une liste de toutes les passerelles privées du VPC sélectionné s'affiche.

2. **Zone de recherche**

     Tapez dans la zone de recherche pour filtrer la liste des passerelles privées. Le système recherche dans tous les champs de la passerelle privée, y compris le nom, l'adresse IP de la passerelle, les noms ACL et les chaînes UUID internes, et renvoie toute passerelle privée correspondant à la chaîne dans la zone de recherche.

3. **Ligne de passerelle privée**

     Chaque ligne comprend l'adresse IP et le masque de sous-réseau de l'interface du routeur virtuel connecté à la passerelle privée, l'adresse IP de la passerelle privée elle-même, son état et l'ACL actuellement appliquée.

     Cliquez sur une passerelle privée pour voir ses détails, y compris les routes statiques.

4. **Menu Actions cachées**

     Chaque entrée de la liste des passerelles privées possède un menu Actions cachées. Cliquez sur le menu Actions cachées pour accéder à la commande **Remplacer ACL**.

     Pour appliquer une autre ACL à une passerelle privée, cliquez sur la commande **Remplacer ACL**. Une boîte de dialogue s'affiche, dans laquelle vous pouvez en sélectionner une à appliquer dans une liste d'ACL réseau qui ont été définies pour votre VPC.


## Routes statiques

![Une capture d'écran de la page routes statiques, avec des points numérotés sur les principales fonctionnalités](/assets/private-gateways-static-routes-fr.png)

1. **Liste des routes statiques**

     Dans la zone principale de l'espace de travail, une liste apparaît de toutes les routes statiques qui ont été définies pour la passerelle privée sélectionnée.

2. **Zone de recherche**

     Tapez dans la zone de recherche pour filtrer la liste des routes statiques. Le système recherche dans le champ CIDR et renvoie toute route statique correspondant à la chaîne dans la zone de recherche.

3. **Ajouter une route statique**

     Cliquez sur ce bouton pour ouvrir une boîte de dialogue dans laquelle vous pouvez ajouter une nouvelle route statique à la passerelle privée. Entrez le CIDR du réseau ou de l'hôte de destination, et le trafic vers cette destination sera acheminé via la passerelle privée.

4. **Ligne de route statique**

     Chaque ligne comprend le CIDR de la route de destination, son état et un menu Actions cachées avec la commande **Supprimer** pour supprimer cette route statique.


