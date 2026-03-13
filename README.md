# Projet Prolog - Tournoi de Stratégie Numérique (L2 MIASHS 2025)

Ce dépôt contient l'implémentation d'un agent intelligent en **Prolog** conçu pour participer à un tournoi de jeu de stratégie à deux joueurs. L'objectif est de maximiser son score sur plusieurs tours en anticipant les coups de l'adversaire.

## 📂 Contenu du dépôt

Ce dépôt est organisé pour inclure l'ensemble des éléments du projet :
* **Sujet** : Les consignes détaillées et les règles du tournoi.
* **Rapport** : Une analyse de la stratégie choisie, les choix de conception et les résultats obtenus.
* **Code** : L'implémentation du prédicat de jeu et des fonctions auxiliaires en Prolog.

---

## 🎮 Les Règles du Jeu

Le jeu oppose deux joueurs qui choisissent simultanément un nombre entier entre **1 et 5**.

### Version 1 : Duel de proximité
* Si les deux nombres choisis ($A$ et $B$) sont consécutifs ($|A-B|=1$), le joueur ayant misé le **plus petit nombre** remporte la somme des deux ($A+B$), tandis que l'autre gagne 0.
* Dans tous les autres cas, chaque joueur gagne la valeur du nombre qu'il a lui-même prononcé.
* *Exemple :* Si le premier joueur dit 4 et le second dit 2, ils gagnent respectivement 4 et 2 points. Si le premier dit 4 et le second dit 3, le premier gagne 0 et le second gagne 7.

### Version 2 : Le multiplicateur de répétition
* Lorsqu'un joueur prononce un nombre $N$ qui est le même que son coup précédent, le score potentiel est multiplié par lui-même.
* *Exemple :* Jouer 4, puis encore 4 permet de gagner $4 \times 4 = 16$. Une nouvelle répétition monte le gain potentiel à $16 \times 4 = 64$.
* **Risque élevé :** La répétition permet de gagner gros, mais si l'adversaire joue un nombre consécutif (ex: 3 contre votre 4 répété), il récupère l'intégralité de la somme accumulée.

---

## 💻 Spécifications Techniques

L'agent est piloté par le prédicat `joue/3`, appelé par un gestionnaire de tournoi externe.

### Structure du Prédicat
`joue(NomEquipe, Historique, MonCoup).`

* **NomEquipe** : L'identifiant unique de l'équipe (ex: `miashsForEver`).
* **Historique** : Liste des coups passés sous forme de paires `[[MonCoup, CoupAdversaire] | Reste]`. Le coup le plus récent est en tête de liste.
* **MonCoup** : L'entier entre 1 et 5 que le programme doit retourner.

---

## 🤖 Adversaires de Référence
Le programme peut être testé contre trois stratégies de base :
* `aleatwar` : Joue de manière totalement aléatoire.
* `titfortat` : Joue au hasard au premier tour, puis imite le dernier coup de l'adversaire.
* `gambler` : Répète son propre coup précédent avec 20% de probabilité, sinon joue au hasard.

---

## 🛠 Évaluation
Le projet est évalué sur la pertinence de la stratégie mise en place, la qualité de l'implémentation en Prolog et les performances obtenues lors du tournoi final.

---
*Projet réalisé dans le cadre de la licence MIASHS à l'Université Grenoble Alpes.*
