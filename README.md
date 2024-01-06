# Automatic-watering

# **Objectif du projet**

L’objectif est d’élaborer un système permettant de capter l’humidité d’une plante puis, en fonction de cette valeur, d’activer une pompe électrique acheminant de l’eau vers elle.

Vidéo du projet : <https://www.tiktok.com/@__hakii__/video/7245607361170181403>

# I- **Conception électronique**

Pour concevoir le projet, j’ai opté pour l’utilisation d’une carte Nodemcu afin de manipuler l’irrigation comme je le souhaitais avec mon téléphone et ainsi tester le bon fonctionnement du système.

## a) Capteur de niveau d’eau

Le capteur d’humidité est branché au GND, 5V et à un pin analogique de la Nodemcu.

Nous l’enfonçons à l’intérieur du pot en terre afin de connaitre le taux d’humidité de la plante à arroser.

Enfin dans la partie informatique, nous le programmerons pour connaitre les valeurs transmises à la carte.


## b) Affichage des données du capteur

Pour afficher l’humidité de la plante nous utilisons un petit écran OLED branché aux pins suivants : VCC, GND, SDA, SCK.


## c) Pompe électrique

L’irrigation est réalisée grâce à une pompe électrique. Celle-ci fonctionnant en 12V, nous allons devoir utiliser une batterie supplémentaire et un relais pour contrôler le passage du courant grâce à la carte.

Le pôle positif des piles est branché à la porte NO du relais, puis le COM est branché à l’un des pins du moteur éléctrique. L’autre pin de ce moteur est ensuite connecté au pôle négatif de la batterie.

Le relais est ensuite connecté au 5V, GND et à un pin digital de la Nodemcu pour pouvoir le contrôler.

Nous avons désormais une pompe dont l’un de ses embouts aspire l’eau dans un réservoir et dont l’autre la rejette dans la plante.

# II- **Conception Informatique**

Nous devons maintenant programmer notre système pour qu’il soit autonome ou contrôlable par Blynk.

## a) Capteur et OLED

Le capteur renvoie donc les valeurs d’humidité à la carte par simple utilisation d’un `ananolgRead()` puis nous utilisons la bibliothèque **`Wire` **pour manipuler l’écran OLED et afficher les données reçues.

## b) Irrigation de l’eau

Pour activer l’eau, nous avons deux possibilités :

### Utilisation de blynk

La carte étant une Nodemcu nous pouvons utiliser l’application Blynk pour simuler virtuellement l’appuie sur un bouton.

Sur l’application nous créons un bouton virtuel. Sur l’IDE Arduino, nous déclarons comme pour tout projet Blynk le nom du réseau, le mot de passe, le token, et nous lançons le démarrage.

Nous rajoutons une fonction lisant la valeur du bouton virtuel à chaque appuie sur l’application.

Lorsque le bouton renvoie la valeur 1, alors nous activons le relais pour qu’il puisse laisser passer le courant et ainsi laisser le moteur fonctionner.

### **Utilisation des valeurs du capteurs**

Grâce aux données renvoyées par le capteur, nous pouvons relever une valeur seuil où la plante est trop sèche et doit être hydratée.

Si les valeurs lues sont inférieures au seuil limite alors le relais s’active et la plante est arrosée jusqu’à rétablir une bonne humidité.

# III- **Conception 3D**

L’unique pièce réalisée en 3D est un support permettant de placer une bouteille faisant office de réservoir d’eau.

Il aurait été possible de rajouter des soudures ou un rangement pour cacher les modules électroniques pour rendre le projet plus propre.

![Image1](https://user-images.githubusercontent.com/92324336/147491361-f02368aa-e9ba-4ee0-9e8a-8d06d40c260f.png)

# **Rendu final**

![ezgif com-gif-maker (2)](https://user-images.githubusercontent.com/92324336/147491552-00b94b63-7aef-4b81-89e5-23f57f6cb0fe.gif)
