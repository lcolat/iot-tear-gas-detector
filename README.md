# GazIOT

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

| Composant1     | pin   | Composant2  | pin   |
|----------------|-------|-------------|-------|
| Arduino        | 5V    | Breadboard  | +     |
| Arduino        | GND   | Breadboard  | -     |
| Breadboard     | +     | Breadboard  | 27.1  |
| Breadboard     | -     | Breadboard  | 28.1  |
| Capteur de Gaz | A2    | Breadboard  | 27.2  |
| Capteur de Gaz | H1    | Breadboard  | 27.2  |
| Capteur de Gaz | A1    | Breadboard  | 27.2  |
| Capteur de Gaz | B1    | Arduino     | A0    |
| Capteur de Gaz | B2    | Resistance2 | borne1|
| Capteur de Gaz | H2    | Breadboard  | 28.4  |
| Resistance2    | borne2| Breadboard  | 28.3  |
| Arduino        | D2    | Breadboard  | 19.1  |
| Arduino        | D3    | Breadboard  | 15.1  |
| Arduino        | D1    | Breadboard  | +     |
| Arduino        | D0    | Breadboard  | +     |
| Resistance1    | borne1| Breadboard  | 19.d  |
| Arduino        | 5V    | Breadboard  | +     |
| Arduino        | 5V    | Breadboard  | +     |
| Arduino        | 5V    | Breadboard  | +     |
|----------------|-------|-------------|-------|













































	
Capteur de gaz
Arduino
A1 
5V
A2 
5V
H1
5V
B2
GND
H2
GND
B1
A0

Attention: le pin B2 sera connecté à une résistance avant d’attendre le GND de l’arduino.



