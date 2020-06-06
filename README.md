# GazIOT
## Table of contents
+ [Matériel](#Matériel)
+ [Étape 1](#Étape 1)
+ [Étape 2](#Étape 2)
## Matériel :
+ 1 Arduino BT
+ 1 mini breadboard
+ 1 capteur de gaz
+ 1 moteur vibrateur
+ 1 LED
+ 1 module Bluetooth
+ 1 batterie
+ 25 cables
+ 3 résistances


## Étape 1 : Connecter votre Arduino à votre ordinateur
Tout d’abord il va falloir charger le code dans le microcontrôleur via USB et au logiciel “Arduino IDE”.
```C++
#define LED_PIN 2
#define VIBRATOR 3
#define GAZ_PIN A0

void setup()
{
  pinMode(LED_PIN, OUTPUT);
  pinMode(VIBRATOR, OUTPUT);
  pinMode(GAZ_PIN, INPUT);
  Serial.begin(9600);
}

void loop()
{
  delay(10); // for simulation performance
  int gazValue = analogRead(GAZ_PIN);
 
  if (Serial.available() > 0) {
	Serial.println(Serial.read(), DEC);
  }

  if (gazValue > 600) {
	digitalWrite(LED_PIN, HIGH);
	digitalWrite(VIBRATOR, HIGH);
	Serial.println("GAZ_DETECTED");
	delay(2000);
  } else {
	digitalWrite(LED_PIN, LOW);
	digitalWrite(VIBRATOR, LOW);
  }
}
```

Ouvrir le logiciel Arduino
Dans outils -> type de carte: sélectionner "Arduino Uno”
Dans outils -> Port: sélectionner le port USB correspondant au port que vous avez utilisé pour brancher votre Arduino (sur windows allez sur Paramètres -> Appareils Bluetooth et autres pour voir sur quel port se trouve votre Arduino)
Dans Fichier -> Exemples ->  Basics: sélectionner le programme
Une fois le programme ouvert, appuyer sur le bouton Vérifier puis sur le bouton Téléverser.
Si tout se passe bien, la LED "L" sur votre Arduino va se mettre à clignoter.
Vous avez chargé votre premier programme sur votre microcontrôleur Arduino, bravo! 

## Étape 2 : Brancher les composants à l’Arduino
Nous allons maintenant brancher les composants entre eux pour les relier à l’arduino.

| Composant1       | pin     | Composant2       | pin              |
|------------------|---------|------------------|------------------|
| Arduino          | 5V      | Breadboard       | +                |
| Arduino          | GND     | Breadboard       | -                |
| Breadboard       | +       | Breadboard       | 27.a             |
| Breadboard       | -       | Breadboard       | 28.a             |
| Capteur de Gaz   | A2      | Breadboard       | 27.b             |
| Capteur de Gaz   | H1      | Breadboard       | 27.b             |
| Capteur de Gaz   | A1      | Breadboard       | 27.b             |
| Capteur de Gaz   | B1      | Arduino          | A0               |
| Capteur de Gaz   | B2      | Resistance2      | borne1           |
| Capteur de Gaz   | H2      | Breadboard       | 28.d             |
| Resistance2      | borne2  | Breadboard       | 28.c             |
| Arduino          | D2      | Breadboard       | 19.a             |
| Arduino          | D3      | Breadboard       | 15.a             |
| Arduino          | D1      | Resistance8      | borne2           |
| Arduino          | D0      | Module bluetooth | TX               |
| Resistance1      | borne1  | Breadboard       | 19.d             |
| Resistance1      | borne2  | Breadboard       | 19.f             |
| Moteur vibrateur | négatif | Breadboard       | 14.a             |
| Moteur vibrateur | positif | Breadboard       | 15.a             |
| Breadboard       | 14.a    | Breadboard       | -                |
| LED              | Anode   | Breadboard       | 19.g             |
| LED              | Cathode | Breadboard       | 18.g             |
| Breadboard       | 18.f    | Breadboard       | -                |
| Resistance8      | borne1  | Module bluetooth | RX               |
| Resistance4      | borne1  | Module bluetooth | RX               |
| Resistance4      | borne2  | Module bluetooth | Terre            |
| Breadboard       | 1.e     | Module bluetooth | Terre            |
| Module bluetooth | Activer | Resistance7      | borne2           |
| Resistance7      | borne1  | Resistance6      | borne1           |
| Resistance6      | borne1  | Module bluetooth | Alimentation     |
| Resistance6      | borne2  | Module bluetooth | Réinitialisation |
| Arduino          | 3.3V    | Module bluetooth | Alimentation     |
| Batterie         | positif | Arduino          |                  |
| Batterie         | négatif | Arduino          |                  |

