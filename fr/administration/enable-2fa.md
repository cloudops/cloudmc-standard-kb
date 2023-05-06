---
title: "Activer l'authentification à deux facteurs"
slug: activer-2fa
---


Cet article présente le concept d'authentification à deux facteurs et décrit comment activer et désactiver cette fonctionnalité pour votre compte.

## Aperçu détaillé

L'authentification à deux facteurs, également connue sous le nom d'authentification multifacteur, 2FA ou MFA, permet d'identifier sans ambiguïté un utilisateur au moyen de deux pièces d'identité distinctes. Le premier composant est quelque chose que l'utilisateur doit connaître, comme un mot de passe ou une phrase de passe. Le deuxième composant est quelque chose que l'utilisateur doit avoir, par exemple, un jeton à usage unique. Ce mécanisme permet de prouver au système que vous êtes bien celui que vous prétendez être.

Il est généralement recommandé de toujours activer 2FA pour votre compte Hypertec Cloud. Une fois 2FA est configuré, lors de la connexion, vous serez invité à saisir le jeton à usage unique :

![Capture d'écran de la page de connexion Hypertec Cloud demandant un jeton à usage unique](/assets/enable-2fa-login-fr.png)

Pour générer un jeton à usage unique, vous devrez installer une application de génération de jetons, soit sur votre smartphone, soit sur votre poste de travail. De nombreuses applications peuvent fonctionner avec le système 2FA de Hypertec Cloud, telles que LastPass, 1Password, Google Authenticator, Microsoft Authenticator et autres. Veuillez vous reporter à la documentation fournie par le fournisseur de votre logiciel pour obtenir des informations sur l'installation et la configuration.

## Activer l'authentification à deux facteurs

### Avant que tu commences

- Vous devez avoir un générateur de jetons installé et configuré

### Procédure

1. Cliquez sur le **Menu utilisateur** \> **Mon profil** \> **Sécurité**. Le menu utilisateur se trouve dans le coin supérieur droit de la barre de menu Hypertec Cloud.

2. Faites défiler la page jusqu'en bas et cliquez sur le bouton intitulé **Activer l'authentification à deux facteurs \(2FA\)**.

     ![Capture d'écran de la page Sécurité, centrée sur le bouton Activer l'authentification à deux facteurs](/assets/enable-2fa-enablebutton-fr.png)

3. Vous serez invité à saisir votre mot de passe, saisissez-le puis cliquez sur **Confirmer**.

4. Utilisez votre générateur de jetons pour scanner le code QR qui apparaît à l'écran.

     Vérifiez que votre générateur de jetons a accepté le code QC et génère un jeton à usage unique.

5. Entrez le jeton à usage unique de votre générateur de jetons dans le champ de texte fourni.

     ![Capture d'écran de la page Sécurité, centrée sur le code QR et la saisie du jeton](/assets/enable-2fa-qrcode-fr.png)

6. Cliquez sur **Activer**.

     Une liste de codes de secours s'affichera. Rangez-les dans un endroit sûr. Si vous perdez l'accès à votre générateur de jetons, utilisez l'un de ces codes pour vous connecter au système et réactivez 2FA avec un nouveau générateur de jetons.

     ![Capture d'écran de la page Sécurité, centrée sur les codes de secours](/assets/enable-2fa-codes-fr.png)


### Résultats

- L'authentification à deux facteurs est maintenant activée sur votre compte Hypertec Cloud
- Lors de votre prochaine connexion, après avoir vérifié votre nom d'utilisateur et votre mot de passe, le système vous demandera d'entrer le jeton à usage unique de votre générateur de jetons

### Régénérez vos codes de secours

Si vous perdez vos codes de sauvegarde, vos codes peuvent être régénérés.

#### Procédure

1. Cliquez sur le **Menu utilisateur** \> **Mon profil** \> **Sécurité**. Le menu utilisateur se trouve dans le coin supérieur droit de la barre de menus Hypertec Cloud.

2. Faites défiler la page jusqu'en bas et cliquez sur le bouton intitulé **Gérer l'authentification à deux facteurs \(2FA\)**.

3. Vous serez invité à saisir votre mot de passe, saisissez-le puis cliquez sur **Confirmer**.

4. Cliquez sur le bouton intitulé **Régénérer des codes de secours**.

     Une liste des nouveaux codes de secours s'affichera. Rangez-les dans un endroit sûr.


### Désactiver l'authentification à deux facteurs

#### Procédure

1. Cliquez sur le **Menu utilisateur** \> **Mon profil** \> **Sécurité**. Le menu utilisateur se trouve dans le coin supérieur droit de la barre de menus Hypertec Cloud.

2. Faites défiler la page jusqu'en bas et cliquez sur le bouton intitulé **Gérer l'authentification à deux facteurs \(2FA\)**.

3. Vous serez invité à saisir votre mot de passe, saisissez-le puis cliquez sur **Confirmer**.

4. Cliquez sur le bouton intitulé **Désactiver l'authentification à deux facteurs**.

     L'authentification à deux facteurs est désormais désactivée sur votre compte. Lors de votre prochaine connexion, seuls votre nom d'utilisateur et votre mot de passe vous seront demandés.


