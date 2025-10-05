# IRverse / IRfinity – Hub IR DIY universel

**IRverse / IRfinity** est un hub IR DIY basé sur ESP8266, capable de piloter tous vos appareils à télécommande infrarouge : TV, ampli, clim, hotte, sèche-serviettes, lumières IR, et bien plus.  
Il apprend et reproduit vos codes IR, avec boîtiers modulables (LED haut/côté) et alimentation 5 V ou 230 V. Universel, flexible et 100 % DIY.

---

## Fonctionnalités
- Apprentissage et reproduction de codes IR
- Pilotage de multiples appareils dans la même pièce
- Alimentation modulable : 5 V USB ou 230 V embarquée
- Boîtier modulable : LED pointant vers le haut ou sur le côté
- Compatible avec différents projets DIY et makers

---

## Contenu du dépôt
IRverse/
├─ firmware/ # Code ESP8266 (Arduino ou PlatformIO)
│ └─ main.ino
├─ PCB/ # Schémas PCB
│ └─ esquisse.kicad_pcb
├─ 3D/ # Boîtiers 3D
│ ├─ boitier_top.stl
│ └─ boitier_base.stl
├─ assets/ # Images et photos du projet
│ ├─ prototype.jpg
│ └─ pcb.png
└─ README.md # Ce fichier
Ouvrez le firmware dans Arduino IDE ou PlatformIO.

Configurez votre réseau Wi-Fi et compilez.

Téléversez le firmware sur l’ESP8266.

Montez la LED IR dans le boîtier choisi (haut ou côté) et branchez l’alimentation.

Testez l’apprentissage et l’envoi des codes IR.

Images


__________________________________________________________________________________

Boîtiers 3D :

- Base commune pour toutes les variantes

- Top interchangeable : LED vers le haut ou sur le côté

- Alimentation intégrée ou externe selon la version

- Les fichiers STL sont fournis dans le dossier 3D/


__________________________________________________________________________________

Licence :

Ce projet est sous MIT License – vous êtes libre de l’utiliser, modifier et partager.
