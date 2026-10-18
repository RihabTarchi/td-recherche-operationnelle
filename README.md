# TD --- Recherche opérationnelle

Ce dépôt contient les corrections Python des exercices 2 et 3 du TD de recherche opérationnelle.

## Exercice 2 --- Problème de transport

### Objectif

Déterminer un plan de transport qui respecte les offres des dépôts et
les demandes des magasins, tout en cherchant à minimiser le coût total.

### Données

- Coûts de transport :
  - D1 vers M1, M2, M3 : 5, 3, 4
  - D2 vers M1, M2, M3 : 6, 7, 2
- Offres : D1 = 8, D2 = 9
- Demandes : M1 = 4, M2 = 5, M3 = 8

L'offre totale est de 17 conteneurs et la demande totale est également
de 17 conteneurs.

### Méthode utilisée

La recherche taboue explore des solutions voisines et utilise une liste
taboue pour éviter de répéter certaines opérations. Le programme vérifie
également que chaque solution respecte les contraintes du problème.

### Fonctions principales

- `cout_solution(x)` : calcule le coût total du plan de transport.
- `est_faisable(x)` : vérifie les offres, les demandes et la
  non-négativité des quantités.
- `solution_initiale()` : fournit un premier plan réalisable.
- `voisins(x)` : génère des plans voisins.
- `recherche_taboue()` : cherche un plan de transport de coût plus
  faible.
- `afficher(x)` : affiche le plan obtenu et son coût.

### Résultat d'exécution exercice 2

![Résultat de l'exercice 2](captures/resultat_EX2.png)

## Exercice 3 --- Problème du voyageur de commerce

### Objectif

Trouver un circuit qui visite chacune des 8 villes une seule fois et
revient à la ville de départ, en minimisant le coût total. Les liaisons
absentes du graphe ne peuvent pas être utilisées.

### Données

Les coûts des liaisons sont enregistrés dans le dictionnaire `DONNEES`.
Le circuit initial est :

`1-2-3-4-5-6-7-8-1`

### Méthodes utilisées

#### 1. Recherche taboue

La recherche taboue examine des circuits voisins obtenus en échangeant
deux villes. Elle conserve une liste taboue et compare les solutions
afin de garder la meilleure solution trouvée.

#### 2. Recuit simulé --- 5 itérations

Le recuit simulé choisit un voisin au hasard à chaque itération. Une
solution qui améliore le coût est acceptée ; une solution plus coûteuse
peut aussi être acceptée selon une probabilité qui dépend de la
température. La température diminue à chaque itération.

### Fonctions principales

- `distance(a, b)` : retourne le coût d'une liaison entre deux villes,
  ou `None` si elle n'existe pas.
- `cout(tour)` : calcule le coût du circuit complet, retour à la ville
  de départ compris.
- `voisins(tour)` : génère des circuits voisins réalisables.
- `recherche_taboue()` : applique la recherche taboue.
- `recuit_simule()` : applique le recuit simulé pendant 5 itérations
  par défaut.
- `afficher(nom, tour)` : affiche le circuit et son coût.

### Résultat d'exécution exercice 3

![Résultat de l'exercice 3](captures/resultat_EX3.png)
