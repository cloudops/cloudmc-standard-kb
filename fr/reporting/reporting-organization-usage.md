---
title: "Rapport d'utilisation d'organisation"
slug: rapports-utilisation-organisation
---


Cet article explique en détail comment utiliser le rapport d'utilisation d'organisation et ses différentes options.

## Aperçu

Le rapport d'utilisation de l'organisation est le premier document à consulter pour visualiser précisément les ressources consommées par votre organisation et comprendre vos dépenses. Pour la période sélectionnée, le rapport fournit une liste détaillée de chaque produit utilisé, la quantité consommée et le coût associé. Le rapport complet comprend les données de l'utilisation utilitaire et les engagements pour toutes les connexions de services de l'organisation.

Si votre compte utilisateur vous donne accès à plusieurs organisations, le rapport d'utilisation affichera la consommation de toutes les organisations auxquelles vous avez accès. Ce rapport est visible uniquement avec le rôle **Administrateur** ou avec un rôle personnalisé avec autorisation **Utilisation : Voir**.

![Capture d'écran du rapport d'utilisation d'organisation](/assets/reporting-organization-usage.png)

Le rapport d'utilisation de l'organisation est divisé en sections :

-   **Filtres**
-   **Utilisation de l'engagement**
-   **Utilisation utilitaire**

Consultez les sections correspondantes ci-dessous pour plus de détails.

Lorsque plusieurs devises sont configurées pour une ou plusieurs connexions de service sélectionnées :

-   L'utilisation utilitaire sera affichée dans des sous-sections distinctes.
-   Chaque sous-section affichera un total correspondant à la devise.
-   Chaque devise aura ses propres filtres de catégories de produits.

Lorsqu'une seule devise est configurée, le total des coûts de consommation pour la période sélectionnée apparaît au bas du rapport. Il est important de noter que le rapport de consommation de l'organisation n'est pas une facture et n'inclut ni les remises, ni les crédits, ni les taxes. De plus, les frais facturés au cours du cycle de facturation actuel sont des estimations et peuvent être modifiés jusqu'à l'émission de la facture finale.

## Filtres

![Capture d'écran des filtres disponibles pour le rapport d'utilisation d'organisation, avec l'onglet Où et quoi? sélectionné.](/assets/reporting-organization-usage-filters.png)

1.  **Liste des filtres actuellement sélectionnés**

    La liste contient tous les critères sélectionnés pour le rapport affiché. Cliquez sur le bouton **×** pour supprimer un critère, ou sur **Effacer tous les filtres** pour supprimer tous les critères.

2.  **Filtre de dates**

    Cliquez sur l'onglet **Quand?** pour afficher un sélecteur de dates et choisir la période désirée pour le rapport. Utilisez les boutons prédéfinis ou cliquez sur **Personnalisé** pour sélectionner une plage exacte.

3.  **Filtres de données**

    Cliquez sur l'onglet **Où et quoi?** pour afficher les filtres permettant de choisir la source des données :

    -   Le menu contextuel **Organisation** permet de choisir l'organisation dont les données d'utilisation figureront dans le rapport. Ce menu affiche l'organisation actuelle et les sous-organisations auxquelles votre compte utilisateur a accès. Vous ne pouvez sélectionner qu'une seule organisation à la fois.
    -   Le menu contextuel **Connexion de service** répertorie toutes les connexions de service de l'organisation sélectionnée. Vous pouvez sélectionner une connexion pour afficher uniquement les données d'utilisation de cette connexion. Une seule connexion peut être sélectionnée à la fois. Si aucune connexion n'est sélectionnée, les données d'utilisation de toutes les connexions seront affichées.
    -   Si une connexion de service est sélectionnée, un menu contextuel **Environnement** s'affiche, vous permettant d'affiner les données à un environnement spécifique. Un seul environnement peut être sélectionné. Si aucun environnement n'est sélectionné, les données d'utilisation de tous les environnements de la connexion de service sélectionnée sont affichées.

![Capture d'écran du sélecteur permettant d'afficher ou de masquer les catégories de produits dans le rapport](/assets/reporting-organization-usage-categories.png)

1.  **En-tête du rapport**

    L'en-tête indique la plage de dates et l'organisation sélectionnées, ainsi que la ou les devises qui apparaissent dans le rapport actuellement configuré.

2.  **La devise pour cette sous-section**

    Ceci n'apparaît que lorsqu'un rapport contient des données d'utilisation pour plusieurs devises, afin d'indiquer la devise des frais jusqu'à la sous-section de devise suivante.

3.  **Sélecteur de catégorie de produits**

    Une liste de boutons s'affiche, chacun correspondant à une catégorie de produits et au total des frais associés. Cliquez sur un bouton pour afficher uniquement les données d'utilisation liées à cette catégorie. Dans la capture d'écran, la catégorie **Compute** est sélectionnée. Vous pouvez sélectionner plusieurs catégories simultanément. Le premier bouton, **Total**, permet de réinitialiser le sélecteur de catégories de produits afin d'afficher toutes les catégories.

    Notez que lorsqu'un rapport comporte plusieurs devises, chaque sous-section de devise possède son propre sélecteur de catégories de produits.


## Utilisation de l'engagement

![Utilisation de l'engagement](/assets/reporting-organization-usage-commitment.png)

Tous les engagements configurés pour l'organisation sélectionnée et actifs pendant la période choisie seront affichés ici. Le nom de l'engagement, le nom du produit, la référence, la quantité utilisée, le tarif et le coût s'afficheront, ainsi que le total pour chaque engagement. Si plusieurs cycles de facturation sont sélectionnés pour la période, les quantités engagées pour chaque cycle de facturation, au sein de la période sélectionnée, seront indiquées pour chaque produit et chaque engagement.

## Utilisation utilitaire

![Utilisation utilitaire](/assets/reporting-organization-usage-utility.png)

Cette section affiche le total de la consommation enregistrée sur la période sélectionnée. Chaque produit apparaît sur une ligne distincte, indiquant la quantité utilisée, le tarif et le coût. Les données sont regroupées par catégorie de produits, avec un sous-total pour chaque catégorie.


