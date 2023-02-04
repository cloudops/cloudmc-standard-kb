---
title: "Groupes d'affinité"
slug: groupes-d-affinite
---


## Résumé

Cet article présente le concept de groupes d'affinité et les cas d'utilisation des différents types de groupes.

Un groupe d'affinités est un ensemble d'instances liées par une règle d'affinité. Les groupes d'affinité vous permettent de définir des relations entre les instances spécifiées et de contrôler la façon dont ces instances seront lancées dans votre environnement Hypertec Cloud. Ils jouent un rôle important dans la mise en œuvre des politiques de la haute disponibilité \(HA, en anglais\) et des règles métier.

## Anti-affinité

Afin de mettre en œuvre des politiques HA, plusieurs instances exécutant la même application doivent être déployées. Lorsqu'un hôte de calcul physique tombe en panne, toutes les instances exécutées sur cet hôte s'arrêtent immédiatement et sont perdues. Pour s'assurer que l'application continue de fonctionner en cas de panne, l'environnement Hypertec Cloud doit être informé de la manière de lancer correctement chacune des instances de votre application.

L'objectif est d'exclure un ensemble spécifique d'instances de l'exécution sur un seul hôte physique. Utilisez une règle `anti-affinité` pour définir votre groupe d'affinité, et l'environnement Hypertec Cloud tentera automatiquement de lancer chaque instance spécifiée sur un hôte unique. Le système tentera également de respecter cette règle dans le cas où une instance individuelle est arrêtée puis lancée.

**Remarque :** Il incombe au développeur de l'application de créer la logique de basculement dans votre application pour gérer la perte d'instances d'application individuelles.

## Affinité

Les groupes d'affinités peuvent également être utilisés pour implémenter des règles métier là où l'inverse est nécessaire : s'assurer qu'un ensemble d'instances est lancé sur le même serveur physique. Cela peut être nécessaire pour améliorer les performances ou la sécurité entre les composants de l'application, ou pour répondre à d'autres exigences métier.

L'objectif est d'inclure un ensemble spécifique d'instances sur un seul hôte physique. Utilisez une règle de `affinité` pour définir votre groupe d'affinité, et l'environnement Hypertec Cloud tentera automatiquement de lancer chaque instance spécifiée sur le même hôte. Le système tentera également de respecter cette règle dans le cas où une instance individuelle est arrêtée puis lancée.
