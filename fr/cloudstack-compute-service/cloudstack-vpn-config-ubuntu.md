---
title: "Configuration Client :  Ubuntu 24.04"
slug: cca-config-client-ubuntu
---


Ce guide va vous aider à configurer l'accès VPN à distance sur Ubuntu en utilisant le *network manager*, qui est installé par défaut dans la version desktop.

1. Installer les paquets requises :
   - `apt-get install strongswan network-manager-strongswan libcharon-extra-plugins`
1. Dans la section *VPN*, cliquez sur le bouton **+** à l'extrême droite.
1. Sélectionner **IPsec/IKEv2 (strongswan)** comme type de VPN.

![Sélection de VPN](/assets/Lx-1-Strongswan.png)

5. Naviguer à l'onglet *Identity*.
5. Donnez un nom au VPN dans le champ **Name**, par exemple : **Hypertec VPN**
5. Sous la section *Server*, le champ *Address* correspond à l'IP publique affichée dans la page de configuration du VPN et *Certificate* correspond au fichier de certificat que vous avez créé lors de [l'activation du VPN](cca-using-remote-access.md).
5. Dans la section *Client*, définissez *Authentication* sur **EAP (Username/Password)**.
5. Saisissez le nom d'utilisateur VPN dans les champs *Identity* et *Username*.
5. Dans la section *Options*, cochez la case **Request an inner IP address**.

![Page de configuration du VPN](/assets/Lx-2-Request-internal.png)

11. Si vous le souhaitez, vous pouvez naviguer sur l'onglet *IPv4*, et cocher **Use this connection only for resources on its network**.
11. Cliquer sur *Add* en haut à droite de la fenêtre pour sauvegarder la configuration.


Vous pouvez maintenant activer le VPN depuis la page *Network* ou depuis le widget en haut à droit de l'écran.
