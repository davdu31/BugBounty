# Mise en place d'un environnement sous Kali :

## VPN *global*

En cliquant sur l'icône du wifi en haut à droite de l'écran, puis sur "Connexions VPN"->"Configurer le VPN...".

![confVPNglob1](https://github.com/davdu31/BugBounty/assets/35230152/e9276118-f104-4f30-a212-b86507a2be02)

Ensuite vous cliquez sur le + en bas à gauche de la fenêtre puis "Importer une configuration VPN enregistrée".

![confVPNglob2](https://github.com/davdu31/BugBounty/assets/35230152/14982205-c064-4723-bc9a-0f9a1d290ad5)

Là vous sélectionnez le fichier client.ovpn télécharger sur la page du bug bounty de YesWeHack et vous rentrez vos identifiants de connections à YesWeHack.
Ensuite lorsque vous cochez "client" dans vos connections VPN vous y serez connectez.

![confVPNglob3](https://github.com/davdu31/BugBounty/assets/35230152/b51f4176-6d28-4d9e-9fd4-623abb9d100d)

A noter, l'utilisation du VPN peut vous limiter sur l'ensemble de vos connections (comme aller sur google par exemple) suivant sa configuration.

## VPN *via* un proxy

### Installation

Une autre manière de procéder et d'utiliser le VPN via un proxy. Ceci vous permet de choisir lorsque vous passez ou non par ce VPN (que lors de vos recherche sur les sites du Bug Bounty).
Il faudra néanmoins que `docker` et `docker-compose` soit installé sur votre machine (https://computingforgeeks.com/install-docker-and-docker-compose-on-kali-linux/)
1. `git clone https://github.com/davdu31/BugBounty.git`
2. `cd BugBounty`
3. Modifier le fichier `.env` avec vos identifiants YesWeHack
4. `docker-compose up`

### SOCKS5

Maintenant, le proxy socks5 est disponible sur `localhost:1080`
Vous pouvez utiliser différents outils en passant par ce proxy :
```bash
ffuf -x socks5://username:password@localhost:1080 -H "User-Agent: BB23"
curl -x socks5://username:password@localhost:1080 -H "User-Agent: BB23"
```

### Burp Suite
Pour utiliser Burp Suite, il faut rediriger le traffic par le proxy SOCKS à partir des options du projet :
![burp](https://github.com/davdu31/BugBounty/assets/35230152/6fede2f0-d925-43a8-895d-434aea7c1f04)

Maintenant, le navigateur par default de Burp étant chromium, je peux naviguer sur firefox sans être connecté au VPN alors que je le suis lorsque j'utilise Burp.
