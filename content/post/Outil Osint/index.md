+++
author = "Corentin Huvelin"
title = "Outil Osint"
date = "2024-01-24"
description = "Liste de quelques outils d'OSINT et leur usage"
tags = [
    "osint",
    "tool",
    "list"
]
categories = [
    "OSINT",
    "Outil",
]
+++

<style>
    article img {
        display: block;
        margin-left :auto;
        margin-right: auto;
    }
</style>

Petit liste des outils d'OSINT que j'ai rencontré.
<!--more-->


## Catégorie

* [Image](#image)
* [Compte](#compte)
* [Lieux](#lieux)
* [Trafic maritime ou aérien](#trafic)
* [Recherche web](#recherche)
* [Forum, tuto, CTF](#forum-tuto-ctf)


# Image

* [Yandex](https://yandex.com/images/) : Recherche inversé d'image, performant pour les textes et voiture
* [Bing](https://www.bing.com/images/details/%7B0%7D) : Recherche inversé aussi, performant pour les visages
* [Google image](https://www.google.com/imghp?hl=en) : Recherche inversé encore

Merci Krzysztof Wosiński pour [la comparaison des moteurs de recherche](https://www.linkedin.com/pulse/comparison-reverse-image-searching-popular-search-engines-osint/)

* [Forensically](https://29a.ch/photo-forensics/) : Analyse d'image avec divers outils en ligne
* [Pimeyes](https://pimeyes.com/en) : Reconnaissance faciale
* [Face Check](https://facecheck.id/fr) : Reconnaissance faciale
* [Exif data](https://exifdata.com/) : Extracteur de données EXIF

# Compte

* [Blackbird](https://blackbird-osint.herokuapp.com/) : Recherche sur base de pseudo
* [WhatsMyName](https://whatsmyname.app/) : Même chose que Blackbird, avec GoogleSearch
* [Map Snapchat](https://map.snapchat.com/) : Live map Snapchat
* [Hunter.io](https://hunter.io/) : Recherche d'adresse mail professionel
* [';--have i been pwned?](https://haveibeenpwned.com/) : Vérification de présence dans des leaks et breachs de données
* [Twint](https://github.com/twintproject/twint) : Scrapping Twitter sans utiliser l'API
* [Maigret](https://github.com/soxoj/maigret) : Recherche de pseudo sur une base de site
* [Epios](https://epieos.com/) : Recherche inversé autour des email et numéro de téléphone

# Lieux

* [Geoint localisator](https://github.com/Th0rr/GeoInt-Localisator) : Outil de scrapping pour retrouver la distance entre deux lieux 
* [Overpass Turbo](https://overpass-turbo.eu/) : Recherche de lieu avec des query spécifique
* [Suncalc](https://www.suncalc.org/#/27.6936,-97.5195,3/2024.01.25/13:18/1/3) : Carte solaire 
* [Windy](https://www.windy.com/) : Carte météo en temps réelle
* [Annuaire mairie](https://www.annuaire-mairie.fr/jumelage.html) : Annuaire des villes jumellees
* [GPS visualizer](https://www.gpsvisualizer.com/calculators) : Calculer distance entre deux coordonnées géographique, afficher des cercles sur une cartes, triangularisation ...
* [Cachesleuth](https://www.cachesleuth.com/) : Outil de manipulation de carte, comme avant, tracé de cercle ...
* [PeakVisor](https://peakvisor.com/) : Visualisation de montagne et de la vue à leur sommet
* [I know where your cat lives](https://iknowwhereyourcatlives.com/) : Retrouver la localisation de chat
* [OpenStreetMap](https://www.openstreetmap.org/) : Cartographie bénévole pour des données en tout genre
* [Geoportail](https://www.geoportail.gouv.fr/carte) : Carte des reliefs de France
* [Phozagora](http://phozagora.free.fr/) : Liste des luminaires en France, description des luminaire et société et position géographique à la ville près
* [World map osint](http://cybdetective.com/osintmap/) : Carte de lieu d'intêret dans le monde
* [What3words](https://what3words.com/) :  Protocole pour désigner chaque 3m² du monde spécifiquement

# Trafic

* [Marine traffic](https://www.marinetraffic.com/) : Trafic maritime en temps réel
* [Vessel finder](https://www.vesselfinder.com/) : Ressemble a Marine trafic avec un onglet info
* [Flight radar](https://www.flightradar24.com/) : Trafic aérien en temps réel
* [Flightera](https://www.flightera.net/) : Recherche sur les vols, aéroports ...
* [Airfleets](https://www.airfleets.fr/home/) : Recherche de vol, ...

# Recherche

* [Occamm](https://www.occamm.com/) : Moteur de recherche avec des propositions de sujets liés
* [Studybyte](https://light-lens.github.io/Studybyte/) : Similaire à Googlescholar, recherche autour sujet d'étude
* [Google Scholar](https://scholar.google.com/) : Moteur de recherche publication et article scientifique
* [Memegine](https://memegine.com/) : Moteur de recherche pour reddit, recherche de meme (on sait jamais ça peut servir 😂)
* [Onyphe](https://www.onyphe.io/) : A partir d'un nom de domaine, qu'est ce que je peut obtenir
* [OCCRP Aleph](https://data.occrp.org/) : Recherche sur des documents gouvernementaux
* [Wayback Machine](https://archive.org/web/) : Les archives d'internet
* [Pappers](https://www.pappers.fr/) : Recherche d'information sur les entreprises, données fiscales, signature, ...
* [Family Search](https://www.familysearch.org/) : Recherche généalogique
* [sundowndev/GoogleDorking.md](https://gist.github.com/sundowndev/283efaddbcf896ab405488330d1bbc06) : Cheatsheet google dork

# Forum, tuto, CTF

A suivre, y'a souvent des infos sympa

* [Bellingcat](https://www.bellingcat.com/) : Lié souvent politique, crime contre humanité, trafic drogue, conflit ...
* [Authentic8](https://www.authentic8.com/blog) : Sujets variés, outils, IA, methodo
* [Open Facto](https://openfacto.fr/articles/) : Article d'investigation Osint sur sujets variés
* [Trace Labs](https://www.tracelabs.org/) : CTF de recherche de personne disparu, attention cas réel
* [GIJN](https://gijn.org/newsletter/) : Réseau de journaliste, source internationale
* [Tuto OSINT Benjamin Strick](https://www.youtube.com/playlist?list=PLrFPX1Vfqk3ehZKSFeb9pVIHqxqrNW8Sy) : Tuto OSINT d'un ancien de Belligcat
* [Osint US](https://start.me/p/GEQXv7/osint-us) : Liste de tool Osint spécialisé USA
