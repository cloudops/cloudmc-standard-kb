---
title: "Politique d'authentification native"
slug: politique-d-authentification-native
---


## Aperçu

Les revendeurs peuvent contrôler quels domaines peuvent être utilisés pour les comptes d'utilisateurs CloudOps natifs et également définir certaines exigences minimales pour les mots de passe. Cette fonctionnalité est appelée "politique d'authentification native", et chaque organisation peut configurer sa propre politique ou utiliser la politique par défaut. Une sous-organisation héritera la politique de son parent, et elle ne peut pas être remplacée.

Pour gérer ces fonctionnalités pour une organisation spécifique, accédez à **Administration** \> **Organisations**, cliquez sur l'organisation cible, puis accédez à **Règles d'authentification** \> **Native**.

![Capture d'écran de la page Politiques d'authentification natives](/assets/native-authentication-policy-fr.png)

## Domaines prohibés

Les comptes natifs CloudOps utilisent une adresse e-mail comme nom d'utilisateur. La fonctionnalité "Domaines prohibés" permet à un revendeur de spécifier des noms de domaine qui ne sont pas autorisés. Il accepte une liste de noms de domaine séparés par des virgules. Les utilisateurs qui tentent de définir un mot de passe ou de se connecter en utilisant une adresse e-mail avec ce nom de domaine seront refusés.

## Politique de complexité des mots de passe

Les revendeurs peuvent définir une politique de complexité des mots de passe pour une organisation. La stratégie s'applique uniquement aux mots de passe des comptes CloudOps natifs créés dans cette organisation. Cela n'a pas d'incidence sur les comptes gérés par LDAP ou OIDC. Les exigences minimales pour les mots de passe peuvent inclure :

-   Longueur
- Caractères minuscules ou majuscules
-   Nombres
- Caractères spéciaux tels que les astérisques, les perluètes et autres
