# Projet 3

Ce projet a été développé dans le cadre du cours de Robotique Mobile à l'École de Technologie Supérieure (ÉTS). Il consiste en un système de téléopération assistée pour un robot mobile (Clearpath Dingo) équipé d'un bras manipulateur (Kinova Gen3 Lite).

L'objectif principal est de permettre au robot de naviguer dans un environnement inconnu, de détecter des objets marqués par des balises AprilTag, et d'interagir avec ces objets à l'aide de son bras robotisé.  

## Fonctionnalités principales

* **Interface utilisateur interactive :** Créée avec `ipywidgets` pour les notebooks Jupyter. Elle propose un flux vidéo en temps réel de la caméra frontale, un tableau de bord manuel, une carte interactive et un journal des événements.  
* **Deux modes de contrôle :**
  * **Mode Manuel :** Pilotage du robot via des boutons directionnels et un curseur de vitesse.  
  * **Mode Autonome :** L'utilisateur clique sur une destination sur la carte interactive. Le robot calcule alors une trajectoire optimisée en vert et s'y rend tout seul.  
* **Planification de trajectoire :** Utilisation de l'algorithme A* pour naviguer en évitant les obstacles cartographiés.  
* **Évitement d'obstacles réactif :** Le robot s'arrête automatiquement si la caméra détecte un obstacle imprévu à moins de 0,1 mètre dans un cône de 60 degrés.  
* **Interaction avec les AprilTags :** Lorsqu'un tag est détecté, le système convertit ses coordonnées du repère de la caméra vers le repère monde. Le robot s'en approche, puis déploie son bras pour l'atteindre. Pendant la navigation autonome, le bras est maintenu en position "verticale" de sécurité.  

## Technologies utilisées

* **ROS :** Architecture globale, gestion des nœuds et des services.  
* **Python :** Logique de contrôle, algorithme A* et interface.  
* **Gazebo :** Utilisé pour la simulation avant le passage sur le robot physique.  

## Évaluation et limites actuelles

Une étude ergonomique a été menée sur ce système, montrant une satisfaction globale élevée pour le contrôle manuel. Cependant, le passage de la simulation à la réalité a mis en évidence quelques limites :  

* La détection de tags à distance génère parfois des erreurs de positionnement dans le repère monde.  
* L'algorithme A* peine parfois à trouver un chemin vers un tag, même si la zone semble dégagée.  
* La précision du bras physique est impactée par les erreurs de localisation du robot par rapport au tag.
