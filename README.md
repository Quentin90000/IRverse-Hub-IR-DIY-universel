# IRverse – Hub IR DIY universel

IRverse est un hub IR DIY basé sur ESP8266, capable de piloter tous vos appareils à télécommande infrarouge : TV, ampli, clim, hotte, sèche-serviettes, lumières IR, et plus.
Il apprend et reproduit vos codes IR, avec boîtiers modulables (LED haut/côté) et alimentation 5 V ou 230 V. Universel, flexible et 100 % DIY.

## **Fonctionnalités :**

- Apprentissage et reproduction de codes IR

- Pilotage de multiples appareils dans la même pièce

- Alimentation modulable : 5 V USB ou 230 V embarquée

- Boîtier modulable : LED pointant vers le haut ou sur le côté

- Compatible avec différents projets DIY et makers

## **Matériel nécessaire :**
**Microcontrôleur**

1 × **D1 Mini Pro 16 Mb avec antenne externe** – Gère l’émission IR et alimente tous les composants

### **Émission IR**

1 × **LED IR TSAL6400** – Pour émettre la lumière IR

1 × **Résistance 220 Ω** – Montage en série sur l’anode pour protéger la LED

### **Réception IR**

1 × **Résistance 10 kΩ** – Pull-up pour le TSOP38238

1 × **Récepteur IR TSOP38238** (ou équivalent)

### **Alimentation & découplage**

1 × **Condensateur 100 nF céramique** – Découplage et filtrage des hautes fréquences

1 × **Condensateur 100 µF électrolytique** – Stabilisation de l’alimentation

1 × **Module HLK-PM01** – Convertit 230 V AC en 5 V DC pour la version alimentation embarquée

### **Connectique & boîtier**

2 × **Borniers 2P 5.08 mm**

Câble 2G1.5 ou câble USB selon version

Presse-étoupe : PG9 pour alimentation embarquée, PG7 pour alimentation séparée

PCB sur mesure pour monter tous les composants proprement

## **Contenu du dépôt :**
IRverse/
 ├─ firmware/           # Code ESP8266 (Arduino ou PlatformIO)
 │   └─ main.ino
 ├─ PCB/                # Schémas PCB
 │   └─ esquisse.kicad_pcb
 ├─ 3D/                 # Boîtiers 3D
 │   ├─ boitier_top.stl
 │   └─ boitier_base.stl
 ├─ assets/             # Images et photos du projet
 │   ├─ prototype.jpg
 │   └─ pcb.png
 └─ README.md           # Ce fichier
## **Images :**

## Images

![Prototype IRverse](Boitier 3D IRverse - Alimentation embarquée.png)
![PCB](pcb.png)




## **Boîtiers 3D :**

- Base commune pour toutes les variantes

- Top interchangeable : LED vers le haut ou sur le côté

- Alimentation intégrée ou externe selon la version

- Les fichiers STL sont fournis dans le dossier 3D/

##**Licence :**

Ce projet est sous MIT License – vous êtes libre de l’utiliser, modifier et partager.
