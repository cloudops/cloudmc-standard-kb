---
title: "AWS: Sous-réseaux"
slug: aws-sousreseaux
---


Un sous-réseau est une partie d'un VPC AWS qui peut être utilisée pour déployer des instances. Un seul sous-réseau peut utiliser une partie de la plage IP de son VPC, ou il peut utiliser la plage IP complète du VPC.

Comme un VPC, un sous-réseau est défini à l'aide d'un CIDR. Le CIDR du sous-réseau doit exister entièrement dans le CIDR du VPC, et il ne doit pas chevaucher le CIDR de tout autre sous-réseau au sein du même VPC. Un sous-réseau existe dans une seule zone de disponibilité AWS.

Le choix du sous-réseau déterminera la zone de disponibilité d'une instance. Cela a un impact sur les volumes disponibles à attacher à une instance.

Les sous-réseaux se trouvent dans l'onglet **Réseautique** de votre environnement AWS. Recherchez le VPC souhaité et cliquez sur la fonctionnalité **Sous-réseaux** pour afficher une liste complète.

**Sujet parent :** [AWS : Réseautage](aws-networking.md)

