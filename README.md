# Mise en place d'un environnement sous Kali :

## VPN *global*

En cliquant sur l'icône du wifi en haut à droite de l'écran, puis sur "Connexions VPN"->"Configurer le VPN...".
![confVPNglob1](https://github.com/davdu31/BugBounty/assets/35230152/a182811d-ab30-4cd4-bd1a-88173f3f23eb)
Ensuite vous cliquez sur le + en bas à gauche de la fenêtre puis "Importer une configuration VPN enregistrée".
![confVPNglob2](https://github.com/davdu31/BugBounty/assets/35230152/43deffb4-88ae-4d5e-891c-6673a9545311)
Là vous sélectionnez le fichier client.ovpn télécharger sur la page du bug bounty de YesWeHack et vous rentrez vos identifiants de connections à YesWeHack.
Ensuite lorsque vous cochez "client" dans vos connections VPN vous y serez connectez.
![confVPNglob3](https://github.com/davdu31/BugBounty/assets/35230152/6d85eef8-599c-439e-8ab2-356065f8d844)
A noter, l'utilisation du VPN peut vous limiter sur l'ensemble de vos connections (comme aller sur google par exemple) suivant sa configuration.

## VPN *via* un proxy

### Installation

Une autre manière de procéder et d'utiliser le VPN via un proxy. Ceci vous permet de choisir lorsque vous passez ou non par ce VPN (que lors de vos recherche sur les sites du Bug Bounty).
1. `git clone https://github.com/davdu31/BugBounty.git`
2. `cd BugBounty`
3. Modifier le fichier `.env` avec vos identifiants YesWeHack
4. `docker-compose up`

### SOCKS5

Maintenant, le proxy socks5 est disponible sur `localhost:1080`
Vous pouvez utiliser différents outils en passant par ce proxy :
```bash
ffuf -x socks5://username:password@localhost:1080
curl -x socks5://username:password@localhost:1080
```

### Burp Suite
Pour utiliser Burp Suite, il faut rediriger le traffic par le proxy SOCKS à partir des options du projet :
![burp](https://github.com/davdu31/BugBounty/assets/35230152/1aa85a04-c946-4256-aaa9-de23c4f120a5)
