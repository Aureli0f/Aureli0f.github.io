+++
author = "Corentin Huvelin"
title = "TRACS 2023 : Jeo-Lier"
date = "2023-12-09"
description = "Write Up du challenge Jeo-lier du TRACS édition 2023"
tags = [
    "OSINT",
    "TRACS 2023",
    "write-up"
]
categories = [
    "OSINT",
    "Write-Up",
]
image = "tracs.jpg"
+++

<style>
    article img {
        display: block;
        margin-left :auto;
        margin-right: auto;
    }
</style>


J'ai eu la chance de participer avec mon équipe au TRACS édition 2023 qui se déroulait à CentraleSupélec le samedi 2 décembre. 
Sous le club GCC de l'ENSIBS, notre équipe [GCC] Abracadabrhack a terminé 15ème sur 87 équipes.

Je vais ici présenter mon Write-Up du challenge Joe-lier dont j'ai eu la charge durant le CTF.

Merci à mes coéquipiers Nathan Dunand, Matthieu Breuil, Paul Guennec et  Victor Blanchard et merci à CentraleSupélec, ViaRézo et la DGSE pour l'événement.
<!--more-->

# Le challenge Joe-lier

Ce challenge avait pour but de rassembler des informations sur une personne fictive. Ces informations devaient pouvoir nous aider à exfiltrer un collègue retenu dans le pays malveillant EvilCountry.

La seule information à notre disposition en premier lieu est un pseudonyme : `shadowatch87`

## Découverte du dashboard

La première partie du challenge nous indiquait que cette personne semble utiliser un service de gestion de projet en ligne.
Notre objectif est simple, retrouver précisément la page qui est utilisée.

Nous n'avons qu'un pseudo, mon premier réflexe est donc d'utiliser [WhatsMyName](https://whatsmyname.app/) mais sans trop de résultat.

J'utilise donc Maigret afin d'avoir un listing des comptes existants avec un outil différent : 

```bash
┌──(kali㉿kali)-[~/maigret]
└─$ ./maigret.py shadowatch87
[-] Starting a search on top 500 sites from the Maigret database...
[!] You can run search by full list of sites with flag `-a`
[*] Checking username shadowatch87 on:
[+] Pinterest: https://www.pinterest.com/shadowatch87/
[+] metacritic: https://www.metacritic.com/user/shadowatch87
[+] 9GAG: https://www.9gag.com/u/shadowatch87
[+] CreativeMarket: https://creativemarket.com/users/shadowatch87
[+] Lolchess: https://lolchess.gg/profile/na/shadowatch87
[+] Contently: https://shadowatch87.contently.com/
[+] club.cnews.ru: https://club.cnews.ru/shadowatch87
100%|█████████████████████████████████████████| 500/500 [00:17<00:00, 28.15it/s]
[-] Restarting checks for 2 sites... (1 attempts left)
100%|█████████████████████████████████████████| 2/2 [00:15<00:00,  7.53s/it]
[*] Short text report:
Search by username shadowatch87 returned 7 accounts.
Extended info extracted from 0 accounts.
Countries: us, kr, in, ru
Interests (tags): art, sharing, photo, stock, freelance, blog
```

En vérifiant les différents résultats obtenus, le seul compte probant est celui de [9gag](https://www.9gag.com/u/shadowatch87).
![Profil 9gag obtenu](img/TRACS_9gag.png)

On pivote donc avec ce nouveau pseudo et toujours avec Maigret (il a fait ses preuves 😎) : 

```bash
┌──(kali㉿kali)-[~/maigret]
└─$ ./maigret.py Xx_CRYPTOKILLER87_xX
[-] Starting a search on top 500 sites from the Maigret database...
[!] You can run search by full list of sites with flag `-a`
[*] Checking username Xx_CRYPTOKILLER87_xX on:
[+] Pinterest: https://www.pinterest.com/Xx_CRYPTOKILLER87_xX/
[+] Reddit: https://www.reddit.com/user/Xx_CRYPTOKILLER87_xX
[+] CreativeMarket: https://creativemarket.com/users/Xx_CRYPTOKILLER87_xX
[+] Lolchess: https://lolchess.gg/profile/na/Xx_CRYPTOKILLER87_xX
[+] Contently: https://Xx_CRYPTOKILLER87_xX.contently.com/
[+] club.cnews.ru: https://club.cnews.ru/Xx_CRYPTOKILLER87_xX
100%|█████████████████████████████████████████| 500/500 [00:16<00:00, 29.53it/s]
[-] Restarting checks for 2 sites... (1 attempts left)
100%|█████████████████████████████████████████| 2/2 [00:15<00:00,  7.54s/it]
[*] Short text report:
Search by username Xx_CRYPTOKILLER87_xX returned 6 accounts.
Extended info extracted from 0 accounts.
Countries: kr, in, ru
Interests (tags): art, photo, sharing, discussion, news, stock, freelance, blog
```

Quelques résultats, mais encore une fois un seul nous intéresse, le profil [Reddit](https://www.reddit.com/user/Xx_CRYPTOKILLER87_xX/).
![Profil Reddit obtenu](img/TRACS_reddit.png)

Une nouvelle information est disponible, une adresse mail : `joelier198703@gmail.com`

Cette fois, je me retourne vers mon ami [EPIOS](https://epieos.com/) qui m'indique qu'un compte Google existe bien ainsi qu'un compte Trello, une application de gestion de projet en ligne. Nous approchons du but.

Afin de retrouver le Trello public associé, je dois me tourner vers un autre outil, je ne peux malheureusement pas me payer l'abonnement EPIOS, pauvre étudiant que je suis 🥲.
Je vais donc utiliser [BLACKBIRD](https://blackbird-osint.herokuapp.com/) et l'adresse mail obtenue.Entre quelques résultats intéressants, on retrouve bien un lien vers un Trello publique : [Lien vers l'API Trello](https://trello.com/1/Members/joelier198703@gmail.com?fields=activityBlocked%2CavatarUrl%2Cbio%2CbioData%2Cconfirmed%2CfullName%2CidEnterprise%2CidMemberReferrer%2Cinitials%2CmemberType%2CnonPublic%2Cproducts%2Curl%2Cusername)

On retrouve ensuite le [profil de Joe Lier](https://trello.com/joelier) puis dans cette nouvelle page, on peut observer les activités récentes du compte. On retrouve alors le [Tableau de Xx_CRYPTOKILLER87_xX](https://trello.com/b/xB6a3O2f/tableau-de-xxcryptokiller87xx).

![Dashboard de Joe Lier](img/TRACS_Trello_dashboard.png)

Le flag pour la première partie est donc : `https://trello.com/b/xB6a3O2f/tableau-de-xxcryptokiller87xx`

## Retrouver le badge

La seconde partie du challenge nous demande de retrouver un badge qui aurait été perdu par Joe Lier.
En commençant par fouiller le dashboard Trello, on peut retrouver [une carte avec le texte et l'image suivante](https://trello.com/c/6LpQCP2J/3-copier-le-badge-pro) :  

> On a roulé environ 120 km en partant de là, et y'a un site touristique auquel on s'est arrêtés pour déjeuner. L'après-midi on est allé à quelques kilomètres de là faire de la randonnée, y'a une montagne qui culmine à 1665 mètres, on a réussi à aller au sommet mais j'ai perdu ma sacoche en redescendant, j'avais de l'argent et quelques affaires dedans, notamment mon badge du boulot... Bon du coup il faut que je copie mon badge pour pas me faire toper par les officiers de sécu…

![Image d'un camion stoppé sur un parking à côté d'un cours d'eau, des montagnes son visible en arrière-plan](img/TRACS_montagne.png)

Évidemment pas de donnée [EXIF](https://fr.wikipedia.org/wiki/Exchangeable_image_file_format) sur l'image. Je m'intéresse donc au texte sur le camion. Avec un passage dans Google image, je récupère et traduis directement ce qui me donne à partir du Norvégien :

`K KRAEMER MARITIME Votre partenaire`

Après une courte recherche, K Kraemer est bien une entreprise norvégienne spécialisée dans la livraison de nourritures ou de produits ménagers.

Après avoir passé une bonne heure en essayant de retrouver le lieu précis sur l'image, j'ai changé mon fusil d'épaule pour juste rechercher une montagne de 1 665 m d'altitude située en Norvège. 

Grâce au site [Peakery](https://peakery.com/), je peux rechercher les montagnes avec une altitude comprise entre 5 000 et 5 500 pieds (1 665 mètres correspondent à 5 462 pieds).

Je trouve assez vite un seul résultat probant, le sommet [Alnestinden](https://peakery.com/alnestinden-norway/).
Notre équipe a décidé de tester ce flag, car nous n'avions pas un temps infini lors de l'épreuve et nous devions passer à d'autres challenges.

Heureusement, le flag était bien `Alnestinden`.

## Portrait-robot

Pour le troisième flag, nous devons retrouver la couleur des yeux de Joe Lier afin de réaliser un portrait-robot.
La couleur que nous devons retrouver doit être la manière dont il se décrit lui-même.

Actuellement sur le dashboard, nous n'avons pas d'information se rapportant au physique de notre cible. Cependant, on peut chercher au niveau des tâches archivées sur le Trello et on tombe sur [la carte suivante](https://trello.com/c/pEUrNneI/10-acheter-les-nouvelles-lunettes) : 

>Bon là y’a pas les branches parce que c’est un vieux montage, mais let’s go elles sont trop stylées!

![Une image de Joe Lier avec un photomontage de lunette](img/TRACS_lunettes.png)

On a donc une image de Joe Lier, mais cette piste ne donnera rien. Pas d'information spécifique sur l'image, ni de retour avec des recherches inversées sur Yandex, Google ou Bing.

Je décide donc me pencher sur [une autre carte](https://trello.com/c/JsDgCb4q/11-changer-de-plateforme) :  

> Twitter c’est devenu un enfer, let’s go sur le serveur hosnet !
N.B : penser à changer la photo
N.B2: La crypt0 c’est la vie !

Je décide donc de me lancer à la recherche du serveur Hosnet mentionné dans la carte. Le texte précédant me fait penser aux vagues de départ de Twitter au début de l'année où les utilisateurs partaient vers Mastodon. Avec une recherche google simple, je retrouve l'instance suivante : [mastodon.hosnet.fr](https://mastodon.hosnet.fr/explore)

Sur le flux en direct, nous pouvons observer un compte ayant la photo de profil que nous recherchions avec le compte [crypt0_ki113r87](https://mastodon.hosnet.fr/@crypt0_ki113r87) et nous retrouvons l'information que nous cherchons : 
![Le profil de Joe Lier sur le serveur Mastodon](img/TRACS_sans_lunettes.png)

Le flag est donc `châtaignes`

## Des transactions douteuses

Voici l'énoncé tel qu'il nous était fourni : 

> Il semblerait que Joe Lier organise des transactions. Pouvez-vous trouver la trace d’une transaction qui a été finalisée ? Si oui, indiquez le message exacte qui y est associé.

Au vu du dashboard, je me suis douté que les transactions finalisées étaient les cartes présentes dans la catégorie terminé avec les indicateurs comme BA - C312 - P452317.

![Les cartes terminées du dashboard](img/TRACS_Trello_termine.png) 

N'ayant pas pu terminer cette dernière partie durant l'épreuve, je remercie les copains de [isFred](https://isfred.fr/) pour l'aide après la compétition afin de trouver la solution.

Le détail qu'il me manquait lors de la compétition était l'utilisation de [Wayback Machine](https://archive.org/web/) sur le Trello de Joe Lier. En effet, en passant les url des cartes sur wayback machine, on peut voir qu'[une carte a un détail supplémentaire](https://web.archive.org/web/20231103144708/https://trello.com/c/dCkN4nXj/12-ba-c312-p452317) :

![La carte BA - C312 - P452317 possède une information supplémentaire : 0x6286df9af2fb04e6b8b6e4b4774bbb2824ffa5adb6b94723ff44c5d81999ffdb](img/TRACS_carte_transaction.png)

Au vu du format, cette suite de caractères m'a fait penser à un hash de transaction crypto. Le fait que chaque compte de Joe Lier visité précédemment parlait de crypto renforce cette hypothèse.

Sur le site [Blockchair](https://blockchair.com/fr), on peut retrouver la transaction qui est sur la blockchain BNB. On peut donc aller sur un site spécialisé sur cette blockchain comme [BscScan](https://bscscan.com/) et voir qu'il y a des champs supplémentaires qui contiennent une chaîne Hexadecimal. On peut directement changer la visualisation pour l'afficher en UTF-8 sur le site ou chercher un convertisseur Hexa vers UTF-8. Ce qui nous donne la chaîne suivante : `Bloc A - Cellule 312 - Prisonnier 452317 => 1 tel // 2 clopes`

Le dernier flag était donc `Bloc A - Cellule 312 - Prisonnier 452317 => 1 tel // 2 clopes`

Merci pour votre patience et n'hésitez pas à me contacter sur Linkedin si vous avez des questions.