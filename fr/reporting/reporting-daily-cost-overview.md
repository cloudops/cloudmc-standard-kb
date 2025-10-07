---
title: "Aperçu des coûts quotidiens"
slug: rapports-apercu-des-couts-quotidiens
---


Cet article fournit des détails sur l'utilisation de l'aperçu des coûts quotidiens et ses différentes options.

## Description générale

L'aperçu des coûts quotidiens est un rapport interactif destiné aux professionnels de la finance, de la comptabilité et aux cadres, afin de leur permettre de comprendre l'évolution de leurs coûts d'utilisation au fil du temps. Le rapport par défaut offre un aperçu de tous les coûts d'un cycle de facturation. L'utilisateur peut ensuite sélectionner différents critères de filtrage pour se concentrer sur les aspects intéressants des données de coûts. Si nécessaire, le rapport peut être comparé aux données de coûts d'un autre cycle de facturation ou approfondir le sujet pour obtenir plus de détails.

La première section du rapport présente l'agrégation des données de coûts pour un mois complet (cycle de facturation) dans un graphique en anneau accompagné d'une légende. Toutes les données du cycle de facturation sélectionné sont agrégées selon le regroupement sélectionné. La deuxième section du rapport présente un graphique à barres empilées présentant l'agrégation quotidienne des données de coûts selon le même regroupement, pour chaque jour du cycle de facturation. Ces deux graphiques permettent d'explorer des catégories, des types de plan ou des journées spécifiques afin d'isoler les données cibles.

La dernière section du rapport énumère les événements qui se sont produits pendant la période sélectionnée. Cela permet à un utilisateur de potentiellement faire correspondre les événements et les changements de dépenses, et de trouver les causes profondes des tendances.

![Une capture d'écran de l'aperçu des coûts quotidiens](/assets/reporting-daily-cost-overview.png)

1. **Regrouper par**

    Détermine la méthode d'agrégation des graphiques des première et deuxième sections du rapport.

    - Catégorie de produit :  Les données de coût de tous les produits sont regroupées selon la catégorie (et par extension, le catalogue de produits) dans laquelle chaque produit se trouve.
    - Type de plan :  Les données de coût de tous les produits sont regroupées en fonction de l'utilisation sur demande ou des engagements. Sur le graphique d'agrégation quotidien, les coûts attribuables aux engagements sont répartis uniformément sur chaque jour du mois.
    Notez que le regroupement par défaut pour un revendeur peut être défini dans **Admin.** > **Rapports**.

2. **Organisation**

    Ce champ n'est disponible que si votre compte d'utilisateur a accès à d'autres organisations que la vôtre. Il contient une liste alphabétique des organisations auxquelles vous avez accès. Sélectionnez une organisation pour afficher ses données de coût.

3.  **Connexion de service**

    Par défaut, l'aperçu des coûts quotidiens affiche les données de coûts pour toutes les connexions de service de l'organisation sélectionnée. Pour limiter l'affichage à un seul service, sélectionnez-le dans le champ **Connexion de service**.

    Sélectionner **Autres** affichera les données de coûts qui ne peuvent être associées à aucune connexion, comme les engagements limités à l'organisation sélectionnée.

    Cliquez sur l'icône **X** pour effacer le contenu du champ. Une fois effacé, les données de toutes les connexions de service et de tous les environnements s'afficheront.

4.  **Environnement**

    Par défaut, l'aperçu des coûts quotidiens affiche les données de tous les environnements de l'organisation sélectionnée. Cependant, lorsqu'un service spécifique a été sélectionné dans le champ de connexion au service, vous pouvez raffiner les données à un seul environnement du service sélectionné grâce au champ **Environnement**.

    Cliquez sur l'icône **X** pour effacer le contenu du champ et afficher les données de tous les environnements du service sélectionné.

5.  **Période sélectionnée**

    Utilisez ce filtre pour sélectionner le cycle de facturation souhaité pour le rapport. La période en cours est sélectionnée par défaut.

6. **Par rapport à**

    Utilisez ce champ pour sélectionner un cycle de facturation à comparer au cycle du filtre **Période sélectionnée**. Les données de comparaison apparaîtront dans une colonne supplémentaire du tableau d'agrégation mensuelle pour indiquer la différence de valeur, et apparaîtront également sous forme de marqueur horizontal dans les barres empilées pour chaque jour de l'agrégation quotidienne.

7. **Agrégation mensuelle**

    Cette section du rapport contient un graphique en anneau et un tableau affichant les données de coûts ciblées par organisation, connexion de service, environnement et filtres de période sélectionnés. Les données seront regroupées par catégorie de produit ou par l'utilisation sur demande ou engagement, comme spécifié dans l'option **Regrouper par**.

    Cliquer sur une catégorie ou un type de plan activera sa visibilité sur l'agrégation mensuelle et l'agrégation quotidienne, ce qui facilitera la concentration sur des éléments spécifiques.

    Lors de la comparaison avec un autre cycle de facturation, chaque élément du tableau comportera une colonne indiquant la différence de totaux entre les deux cycles de facturation sélectionnés.

8. **Agrégation quotidienne**

    Cette section du rapport présente un graphique à barres empilées présentant les données ciblées par les filtres d'organisation, de connexion de service, d'environnement et de période sélectionnée. Chaque barre empilée indique les données de coût pour un jour de la période sélectionnée, et chaque zone de la barre représente la part relative du coût attribuable soit à l'utilisation sur demande ou aux engagements, ou à chaque catégorie de produit.

    Lors d'une comparaison avec un autre cycle de facturation, le coût total pour un jour donné du mois de comparaison apparaît sous la forme d'une ligne horizontale superposée à la barre empilée.

    Cliquer sur une barre actualise la section « Activités des utilisateurs » et affiche uniquement les activités dont l'horodatage correspond à ce jour. Cliquer de nouveau sur la barre agrandit la section « Activités des utilisateurs » à toute la période sélectionnée.

9. **Activités des utilisateurs**

    Cette section du rapport fournit la liste des activités survenues au cours du cycle de facturation sélectionné dans le filtre « Période sélectionnée ». Ces activités sont tirées du journal d'activité. Le rapport affiche seulement les événements liés aux connexions de service comprises dans le rapport. Si vous cliquez sur une barre empilée de l'agrégation quotidienne, cette section affichera uniquement l'activité de ce jour. Pour étendre la vue à l'ensemble de la période sélectionnée, cliquez de nouveau sur la barre.


