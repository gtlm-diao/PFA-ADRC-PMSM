# Introduction
La première utilisation pratique d'un moteur électrique a été réalisée en 1834 par Thomas Davenport pour alimenter un wagon sur une courte 
section de voie de chemin de fer. Aujourd'hui, les moteurs constituent l’élément principal pour les transports électrifiés, l'automatisation 
industrielle, et les produits commerciaux et de consommation. Selon une étude de l'Agence internationale de l'énergie (AIE), 40 à 45 % de 
l'électricité produite dans le monde est consommée par des systèmes entraînés par des moteurs.

Au cours des dernières décennies, les moteurs brushless ont gagné en popularité en raison de leur performance supérieure sur les critères 
d'efficacité, de densité de puissance et de fiabilité. Parallèlement à la popularité croissante des moteurs brushless, des techniques de 
contrôle ont été mises au point pour assurer un contrôle précis de ces moteurs et améliorer davantage leur efficacité.

La commande vectorielle (Field-oriented control ou FOC) est l'une de ces techniques offrant un contrôle précis sur l'ensemble de la plage de 
couple et de vitesse pour les moteurs brushless.
Comme le montre le schéma précédent, la commande vectorielle s'appuie sur des contrôleurs PI pour les boucles de contrôle de la vitesse ainsi que 
des courants Iq et Id. Les contrôleurs PI sont simples et faciles à implémenter, mais ils peuvent être difficiles à ajuster dans les situations où 
il existe des incertitudes et des perturbations externes. En voici quelques exemples :

- Incertitudes sur les paramètres du moteur et la dynamique du système
- Changements dans les paramètres du moteur (résistance, inductance, force contre-électromotrice, etc.) liés à l'usure, au vieillissement et à la température de fonctionnement
- Fluctuations du couple de charge et de la tension d'entrée
- Changement de la zone de fonctionnement et hystérésis dans le comportement du moteur

Outre ces facteurs, il faut également tenir compte de la nécessité de réajuster les contrôleurs si les moteurs sont redimensionnés pour votre application. Ce processus implique des efforts considérables. Afin de relever ces défis, des algorithmes de contrôle avancés peuvent être utilisés pour concevoir des commandes vectorielles capables de prendre en compte ces facteurs tout en améliorant la précision, le temps de réponse et l'efficacité du contrôle moteur, même dans des environnements difficiles.

La lecture de ce livre blanc vous donnera une bonne compréhension du design des commandes vectorielles. Ce document détaille les outils qu'il convient d'utiliser dans MATLAB® et Simulink® pour travailler avec les techniques de contrôle suivantes :

Commande par rejet actif de perturbations (Active Disturbance Rejection Control ou ADRC)


La commande par rejet actif de perturbations étend le contrôle PID et offre l'avantage significatif de gérer une gamme d'incertitudes élargie, notamment 
des dynamiques et des perturbations inconnues, tout en maintenant la performance du contrôleur.

L'algorithme utilise une approximation du modèle de la dynamique connue du système et regroupe la dynamique et les perturbations inconnues sous la forme 
d'un état étendu du système physique. Un observateur d'état étendu est utilisé pour estimer cet état et implémenter un contrôle par rejet des 
perturbations. Celui-ci est obtenu en réduisant l'effet sur le système de la perturbation estimée et en amenant le système vers le comportement souhaité.

Dans les applications à grande vitesse des bras robotiques industriels, un contrôle précis des moteurs brushless qui entraînent les articulations et 
les liaisons du robot est crucial pour l'exactitude des mouvements et du positionnement. Cependant, les éléments structurels de nombreux robots
présentent une légère flexion, ce qui introduit des dynamiques supplémentaires à l'origine d'oscillations ou de vibrations indésirables.

Les contrôleurs PID peuvent avoir des difficultés à gérer ces dynamiques de flexion, et nécessiter une modélisation et un réglage complexes pour 
maintenir la stabilité et les performances. En revanche, l'ADRC est une solution efficace pour gérer les dynamiques des articulations et des 
liaisons flexibles. Cette solution consiste à estimer et compenser les perturbations causées par les dynamiques additionnelles en temps réel, 
sans s'appuyer sur un modèle explicite du système.

