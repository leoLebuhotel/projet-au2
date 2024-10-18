# Projet Automatique AU2 2023 S2

## Trains à Sustentation Électromagnétique

### Introduction
Un train à sustentation magnétique utilise les forces magnétiques pour léviter au-dessus de la voie, sans contact avec des rails. Ce procédé permet de supprimer la résistance au roulement et d'atteindre des vitesses élevées.

### Transrapid (Sustentation électromagnétique)
Le Transrapid est le seul exemple commercial de train à sustentation électromagnétique, avec une ligne de 30 km en service depuis 2004 à Shanghai. Le train peut atteindre une vitesse de 430 km/h avec une accélération de 0 à 350 km/h en 2 minutes.

### Objectif du Projet
Le projet consiste à étudier le système de sustentation électromagnétique du Transrapid, avec une modélisation précise du circuit magnétique et un asservissement pour maintenir une position verticale stable du train.

## Modélisation du Système

### Équation du Mouvement
La force électromagnétique sur le train est exprimée comme suit :

\[
m\ddot{z} = \frac{N^2 S \mu_0 i^2}{2z^2} - mg
\]

Avec :
- \( N \) : Nombre de spires (1000)
- \( S \) : Surface du circuit magnétique (0,50 m²)
- \( z \) : Position du train par rapport au rail
- \( i \) : Intensité du courant dans la bobine

### Linéarisation autour du point d'équilibre
L'équation de mouvement est linéarisée autour de la position d'équilibre \( z_0 = 10 \, \text{mm} \).

La fonction de transfert linéarisée devient :

\[
\frac{\Delta z(p)}{\Delta i(p)} = -\frac{k_1 k_2 K_z}{p^2 + K_z}
\]

### Paramètres Système
- Perméabilité magnétique \( \mu_0 = 4\pi \times 10^{-7} \, \text{H⋅m}^{-1} \)
- Masse du train \( m = 180 \, \text{tonnes} \)
- Gain de capteur de position \( k_2 = 145 \, \text{V/m} \)
- Gain de boucle de courant \( k_1 = 10 \, \text{A/V} \)

## Synthèse des Correcteurs

### Analyse du Système
Le système est instable sans asservissement de la position. Une commande numérique est nécessaire pour stabiliser la position du train en ajustant le courant dans la bobine en fonction de la position mesurée.

### Commande RST
Une commande **RST** est conçue pour respecter les spécifications suivantes :
1. Pas de dépassement dans la réponse temporelle.
2. Rejet d'une perturbation de sortie (échelon de 2 mm).
3. Pas d'erreur statique.

La robustesse de la commande est évaluée, et l'implémentation est testée en simulation.

### Commande par Modèle Interne
Une deuxième approche de commande est réalisée avec un **modèle interne**, où un pré-bouclage est utilisé pour améliorer la stabilité et la performance face aux perturbations.

## Bonus: Rejet de Perturbation à 50 Hz
Un objectif supplémentaire est l'atténuation d'une perturbation sinusoïdale à 50 Hz avec une atténuation minimale de 40 dB. Une analyse est effectuée pour déterminer si cette spécification est atteignable.

## Conclusion
Ce projet a permis d'explorer différentes stratégies de commande pour stabiliser un système de sustentation électromagnétique, en particulier à travers la synthèse des correcteurs RST et par modèle interne. La robustesse des commandes et leur implémentation pratique sont également abordées.
