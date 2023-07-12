---
title: "CloudStack: Forcer l'arrêt d'une instance"
slug: cloudstack-forcer-le-redemarrage-d-une-instance
---


Si une instance ne répond plus, utilisez ces étapes pour forcer l'arrêt de l'instance :

   - Notez l'**ID** de l'instance que vous trouverez dans la vue "Détails" de cette instance
   - Configurer l'environnement CloudMonkey : [procédure](../cloudstack-compute-service/install-and-config-cloudmonkey.md)
   - Dans CloudMonkey, exécutez : `stop virtualmachine id = ID forcé = true`

Pour démarrer l'instance, utilisez CloudMonkey et exécutez : `start virtualmachine id = ID`
