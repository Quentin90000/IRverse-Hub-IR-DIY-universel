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

## **Code :**

```
esphome:
  name: esp8266-roblin-ir
  friendly_name: ESP8266-Roblin_IR

esp8266:
  board: d1_mini_pro

logger:

api:
  encryption:
    key: "takeyapi"

ota:
  platform: esphome
  password: "0a1abb4344477f1f0dd6a6e9c7143608"

wifi:
  ssid: "tonwifi"
  password: "tonmotdepasse"
  ap:
    ssid: "Esp8266-Roblin-Ir"
    password: "cvi91SvuVJfn"

captive_portal:

remote_transmitter:
  id: my_remote
  pin: D5
  carrier_duty_percent: 50%

# --- Scripts pour appuis longs ---
script:
  - id: lumiere_min
    then:
      - delay: 3s
      - remote_transmitter.transmit_pronto:
          data: "0000 006D 000B 0000 0021 001A 001E 001A 001E 0019 003C 0034 001E 001A 001F 0019 001F 0019 001F 0019 001E 001B 001E 001A 001D 0181"

  - id: mode_24h_on
    then:
      - delay: 3s
      - remote_transmitter.transmit_pronto:
          data: "0000 006D 0009 0000 003E 0035 001E 0019 003B 0019 001E 0034 001F 001A 001E 001A 003B 0034 001F 001A 001E 0181"

  - id: mode_24h_off
    then:
      - delay: 3s
      - remote_transmitter.transmit_pronto:
          data: "0000 006D 0009 0000 003D 0034 001F 0019 003C 0019 001F 0034 001F 0019 001E 001A 003C 0035 001E 0019 001F 0181"

# --- Tous les boutons ---
button:
  # Lumière
  - platform: template
    name: "Lumière ON (max)"
    on_press:
      - remote_transmitter.transmit_pronto:
          data: "0000 006D 0009 0000 0021 0018 001F 0018 003C 0034 001E 001A 001E 001A 003B 006A 001E 001A 001E 001A 0057 0181"

  - platform: template
    name: "Lumière ON (min) - appui long"
    on_press:
      - script.execute: lumiere_min

  - platform: template
    name: "Lumière OFF"
    on_press:
      - remote_transmitter.transmit_pronto:
          data: "0000 006D 0009 0000 0021 0018 001F 0018 003C 0034 001E 001A 001E 001A 003A 006A 001E 001A 001E 001A 0057 0181"

  # Hotte
  - platform: template
    name: "Hotte ON"
    on_press:
      - remote_transmitter.transmit_pronto:
          data: "0000 006D 0009 0000 0021 0018 001F 0033 003C 001A 001E 001A 001E 0035 003B 004F 001E 0034 001E 001A 003B 0181"

  - platform: template
    name: "Hotte OFF"
    on_press:
      - remote_transmitter.transmit_pronto:
          data: "0000 006D 0009 0000 0021 0019 001F 0034 003C 0019 001F 0019 001F 0034 003B 004E 001F 0033 001F 001A 003B 0181"

  # Aspiration
  - platform: template
    name: "Aspiration +1"
    on_press:
      - remote_transmitter.transmit_pronto:
          data: "0000 006D 0008 0000 0021 0018 0059 0019 001E 001A 001E 001A 0057 001A 001E 004F 0057 0034 003B 0181"

  - platform: template
    name: "Aspiration -1"
    on_press:
      - remote_transmitter.transmit_pronto:
          data: "0000 006D 0008 0000 0021 0033 003C 0018 001F 0019 001E 0035 003B 001A 001E 006A 003B 0034 003B 0181"

  # Boost
  - platform: template
    name: "Boost ON"
    on_press:
      - remote_transmitter.transmit_pronto:
          data: "0000 006D 0008 0000 0021 0018 003C 0033 001F 001A 001E 001A 003B 0035 001E 004F 003B 004F 003B 0181"

  - platform: template
    name: "Boost OFF"
    on_press:
      - remote_transmitter.transmit_pronto:
          data: "0000 006D 0008 0000 0021 0019 003C 0033 001F 001A 001E 001A 003B 0034 001E 004F 003B 004F 003B 0181"

  # Arrêt différé
  - platform: template
    name: "Arrêt différé ON"
    on_press:
      - remote_transmitter.transmit_pronto:
          data: "0000 006D 0006 0000 0020 0034 003B 0034 001E 004F 003C 004F 001D 0034 003B 0181"

  - platform: template
    name: "Arrêt différé OFF"
    on_press:
      - remote_transmitter.transmit_pronto:
          data: "0000 006D 0006 0000 0021 0034 003B 0034 001F 004E 003B 004E 001E 0034 003C 0181"

  # Mode 24H
  - platform: template
    name: "Mode 24H ON - appui long"
    on_press:
      - script.execute: mode_24h_on

  - platform: template
    name: "Mode 24H OFF - appui long"
    on_press:
      - script.execute: mode_24h_off
```

## **Images :**


![Boitier 3D IRverse - Alimentation embarquée](Boitier%203D%20IRverse%20-%20Alimentation%20embarquee.png)
![PCB](pcb.png)




## **Boîtiers 3D :**

- Base commune pour toutes les variantes

- Top interchangeable : LED vers le haut ou sur le côté

- Alimentation intégrée ou externe selon la version

- Les fichiers STL sont fournis dans le dossier 3D/

##**Licence :**

Ce projet est sous MIT License – vous êtes libre de l’utiliser, modifier et partager.
