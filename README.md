# Robot de bureau interactif (Deskmate) - Animo

| Author | Ivan Eduard-Iulian |
| :--- | :--- |

## Description

Robot de bureau (Deskmate) interactif capable de modéliser des comportements émotionnels. Le système intègre l'interprétation spatiale des gestes et de la proximité de l'utilisateur en temps réel, couplée à la reconnaissance d'objets pour déclencher des scénarios d'interaction spécifiques. Le robot simule l'attention visuelle grâce à un mouvement mécanique fluide sur deux axes de rotation. L'interaction est complétée par un feedback visuel dynamique, affichant des expressions faciales animées qui reflètent son état émotionnel, et par un retour audio restituant des signaux sonores complexes ou des réactions vocales.

## Motivation

L'objectif de ce projet est d'explorer l'interaction homme-machine (HMI) en créant une entité robotique qui semble "vivante". En synchronisant des mouvements mécaniques de précision avec des capteurs de proximité et une interface visuelle, le projet permet de mettre en pratique des notions techniques avancées (communication SPI/I2C, contrôle PWM) tout en concevant un gadget interactif et attachant pour le bureau.

## Architecture

Le système est structuré en quatre sous-systèmes principaux : l'unité centrale de contrôle, le sous-système de mouvement, le sous-système de perception et le sous-système de feedback.

L'unité centrale, basée sur la carte de développement **ESP32**, coordonne l'ensemble des opérations. Grâce à son processeur dual-core, elle gère simultanément les calculs logiques, la lecture des capteurs et le contrôle des moteurs.

Le sous-système de mouvement utilise deux **servomoteurs SG90** montés sur un support Pan-Tilt. Contrôlés via des signaux PWM générés par l'ESP32, ils permettent au robot d'orienter sa "tête" sur deux axes (horizontal et vertical) de manière fluide.

Le sous-système de perception repose sur un **capteur ultrasonique HC-SR04P** (alimenté en 3.3V) pour mesurer la distance des objets ou de l'utilisateur via des impulsions sonores. Il intègre également un **module RFID RC522** communicant via le bus SPI, permettant la reconnaissance de badges ou d'objets spécifiques pour déclencher des réactions ciblées.

Le sous-système de feedback comprend un **écran OLED de 0.96 pouces** communicant via le bus I2C, utilisé pour afficher les expressions faciales animées (yeux du robot). Un **buzzer passif**, contrôlé par PWM, complète l'interaction en émettant des tonalités variées selon l'état émotionnel du robot.

## Block diagram

<img width="1536" height="1024" alt="schematicsblock_diagram" src="https://github.com/user-attachments/assets/7edfe6a1-ede9-40e6-b431-691ed6f0411c" />

## Components


| Device | Usage | Price |
| :--- | :--- | :--- |
| ESP32 CH340C 30P | Microcontrôleur principal (Cerveau) | [41.19 RON](#) |
| Servomoteur SG90 (x2) | Mouvement mécanique Pan-Tilt (axes X/Y) | [18.98 RON](#) |
| Support Pan-Tilt | Structure mécanique articulée | [8.46 RON](#) |
| HC-SR04P (3-5.5V) | Capteur ultrasonique pour la détection de proximité | [10.14 RON](#) |
| Écran OLED 0.96" | Affichage I2C des expressions faciales | [16.96 RON](#) |
| Kit RFID RC522 | Module SPI pour la lecture des cartes/badges | [9.53 RON](#) |
| Buzzer passif | Retour audio (signaux sonores émotionnels) | [1.45 RON](#) |
| Breadboard 400 pts | Plaque d'essai pour le prototypage initial | [6.62 RON](#) |
| Carte PCB FR4 7x9 | Assemblage final par soudure | [5.76 RON](#) |

## Libraries

| Library | Description | Usage |
| :--- | :--- | :--- |
| `ESP32Servo` | Bibliothèque optimisée pour les signaux PWM sur ESP32 | Utilisée pour contrôler précisément la position des deux servomoteurs SG90. |
| `Adafruit_SSD1306` | Pilote pour les écrans OLED basés sur SSD1306 | Utilisée pour gérer l'affichage I2C et dessiner les expressions du visage. |
| `MFRC522` | Bibliothèque de communication pour lecteur RFID | Utilisée pour initialiser le bus SPI et lire l'UID des cartes détectées. |
