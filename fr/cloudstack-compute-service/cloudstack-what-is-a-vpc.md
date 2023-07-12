---
title: "CloudStack: Qu’est-ce qu’un VPC?"
slug: cloudstack-qu-est-ce-qu-un-vpc
---

Un nuage virtuel privé (VPC) est une section logiquement isolée dans un environnement où vous pouvez construire une architecture applicative multi-tiers.

Typiquement, dans la plupart des nuages publiques sur le marché, vous déployez vos instances dans ce qu'on aime appeler un *réseau simple*. Dans d'autres mots, vos instances ainsi que celles des autres clients sont connectées sur le même réseau.

![Réseau simple](/assets/what-is-a-vpc-1.png)

Le contrôle d'accès réseau est accompli avec l'utilisation de groupes de sécurité ou ACL au niveau de l'hyperviseur. Nous sommes conscients que ce modèle est beaucoup plus simple à mettre en place par un fournisseur de services et pour les clients, mais la sécurité et l'isolation entre les clients est un problème.

Dans un modèle VPC, vous ferez face à une plus grande complexité de gestion. Toutefois, vous gagnerez énormément en contrôle et en isolation. Pour cette raison, nous avons sélectionné ce modèle plutôt qu'une approche plus traditionnelle.

![Réseau modèle VPC](/assets/what-is-a-vpc-2.png)

### Considérations réseaux d’un VPC
Un VPC est composé des éléments suivants:

- **VPC :** Un VPC contient un ou plusieurs réseaux isolés qui peuvent communiquer entre eux via un routeur virtuel.
- **Tiers :** Chaque tier agit comme un réseau isolé avec son propre VLAN et son sous-réseau où l’on peut grouper logiquement les resources (ex. instances). Chaque tier est connecté au routeur virtuel qui agit comme passerelle vers les autres tiers.
- **Routeur Virtuel :** Un router virtuel est automatiquement créé et démarré lors de la création d’un VPC. Le routeur virtuel inter-connecte les tiers et dirige le trafic vers la passerelle publique, les passerelles VPN et fait la translation d’adresses (NAT) pour les instances. Pour chaque tier, une interface correspondante et une adresse IP existe sur le routeur virtuel. Le routeur virtuel fournit les services DNS et DHCP grâce à cette IP.
- **Passerelle publique :** Le trafic à destination et provenant de l’Internet est aiguillé dans le VPC à travers la passerelle publique. Dans un VPC, la passerelle publique n’est pas exposée à l’utilisateur, donc impossible d’ajouter ou modifier les routes.
- **Passerelle Privée :** Tout trafic qui provient ou se dirige vers un réseau privé est aiguillé vers le VPC à travers la passerelle privée.
- **Passerelle VPN :** L’interface du VPC lors d’une connection VPN.
- **VPN Site-à-Site :** Une connection VPN vers un centre de donnée et votre VPC.
- **Passerelle client :** Le côté du client lors d’une connection VPN.
- **Traduction d'adresse réseau :** Traduction d'adresse réseau (NAT) pour les instances afin de donner accès à l’Internet via la passerelle publique.
- **ACL Réseau :** Règles ordonnées qui déterminent si le trafic sera permis en entrée ou en sortie de chacun des tiers associés à la règle ACL.

### Architecture réseau dans un VPC
Dans un VPC, les types d’architectures suivantes sont disponibles:

- VPC avec une passerelle publique seulement
- VPC avec passerelle publique et privée
- VPC avec passerelle publique et privée, avec connection VPN site-à-site
- VPC avec passerelle privée et seulement un VPN site-à-site

### Options de connectivité pour un VPC
Vous pouvez connecter votre VPC à:

- Internet via la passerelle publique
- Un centre de données d’entreprise en utilisant une connection VPN site-à-site
- À la fois Internet et un centre de données

### Considérations réseaux d’un VPC
Considérez les items suivants lors de la création d’un VPC:

- Le nombre maximal de tiers que vous pouvez créer est 4.
- Chaque tier doit avoir un réseau CIDR unique dans le VPC. L’interface web s’assure de cette dernière condition.
- Un tier appartient à un seul VPC.
- Lorsqu’un VPC est créé, une IP de “Source NAT” est allouée par défaut. Cette adresse est libérée lors de la destruction du VPC.
- Une IP publique ne peut être utilisée que pour une seule tâche à la fois. Par exemple, si une adresse est utilisée pour le “Source NAT”, elle ne peut être utilisée pour la redirection de port.
- Le **NAT statique** est un mappage un-à-un entre une adresse IP publique et une instance dans un VPC. Tout le trafic envoyé à l'IP publique sera envoyé à l'instance désignée, et tout le trafic de l'instance sera envoyé à partir de l'IP publique.
- **La redirection de port** est un mappage d'un port sur une adresse IP publique vers un port sur une IP privée dans un VPC. Différents ports sur l'adresse IP publique peuvent être redirigé vers des ports sur des instances distinctes, tant que les instances se trouvent dans le même VPC. Tout le trafic des instances utilisera l'adresse IP NAT source du VPC pour le trafic de sortie.
- Les instances ne peuvent qu’avoir une seule adresse IP, donc elles ne peuvent qu’être connectées sur un tier à la fois.
- Le service de répartition de charge public ne peut s'appliquer qu'à un seul tier du VPC.
- Si une adresse IP est assignée à un tier:
   - Cette IP ne peut pas être utilisée par plus d’un tier du même VPC. Par exemple, si vous avez un tier A et B et une adresse IP publique, vous pouvez créer une règle de redirection de port soit pour le tier A ou le tier B, mais pas les deux à la fois.
   - Cette IP ne peut plus être utilisée pour effectuer de la répartition de charge, de la traduction d'adressse réseau ou de la redirection de port sur un autre tier du même VPC.
