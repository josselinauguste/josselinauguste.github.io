---
layout: post
title: Réduire la boucle de rétroaction par le typage
date: 2018-07-14T19:58:43+02:00
---

Au sein de la communauté des développeurs, l’éternel débat pour l’élection de l’outil le plus à même de nous épauler dans notre tâche ne prendra jamais fin. Les utilisateurs de langages fortement typés alà Haskell militent fortement pour l’idée que ces langages permettent de réduire significativement les bugs, par leur capacité à formaliser (plus ou moins) précisément une problématique, et à vérifier cette formalisation de manière autoritaire, lors de la compilation.

Il reste néanmoins difficile de conclure sur cet avantage, comme le montre par exemple la récente étude _[A Large-Scale Study of Programming Languages and Code Quality in Github](https://cacm.acm.org/magazines/2017/10/221326-a-large-scale-study-of-programming-languages-and-code-quality-in-github/fulltext)_, qui peine à montrer qu’il y ait un réel rapport entre le langage et la qualité des programmes (hormis pour les langages à gestion manuelle de la mémoire, mais c’est une autre histoire).

En marge de cela, la question de la productivité du développeur est beaucoup moins abordée. En particulier, les avantages que le typage statique apporte dans la réduction de la boucle de rétroaction.

De la même manière que le [développement guidé par les tests](https://en.wikipedia.org/wiki/Test-driven_development) m’aide à être plus efficace en raccourcissant au maximum le temps entre ma réflexion sur le code, son écriture et sa validation, les langages à typage statique m’aident à plus vite détecter mes erreurs durant l’écriture de code, grâce aux vérifications rendues possibles pour le compilateur.

Voici quelques fonctionnalités des systèmes de type apportant ce gain de fluidité :

- Tirer parti des IDEs ;
- L’identification des impacts lors de la modification du code ;
- La détection des fonctions non totales ;
- L’interdiction des états invalides.

## Tirer parti des IDEs

Le compilateur étant capable de déterminer précisément les types des expressions, il est aussi capable de proposer une auto-complétion précise et exhaustive.

C’est d’autant plus intéressant lors de l’utilisation de bibliothèques mal documentées, car cela permet une exploration des fonctionnalités proposées par ces bibliothèques à travers l’auto-complétion proposée.

Dans le même ordre d’idée, le typage statique permet de tirer pleinement partie des outils de refactoring et de navigation dans le code (renommage, recherche des usages, extraction d’expression, etc.).

## L’identification des impacts lors de la modification du code

Lors de la modification d’une structure de données, d’une signature de fonction, ou autre liée au type, le compilateur montre immédiatement les endroits impactés par la modification, car la compilation va échouer pour le code concerné. Le gain de temps produit par cet effet de bord de la compilation est dans mon expérience la chose qui me manque le plus lors de l’utilisation de langages à typage dynamique.

Et plus le système de type nous permettra de définir des types précis, plus on pourra tirer parti de cette fonctionnalité.

## La détection des fonctions non totales

Une fonction totale est une fonction définie pour l’ensemble des valeurs de ses paramètres d’entrée.

Le pattern matching permet de vérifier simplement à la compilation l’exhaustivité des cas qu’il couvre en fonction du type de données de l’expression _matchée_.

Par exemple le code suivant, qui oublie de traiter le cas `Bee` :

```haskell
data Animal = Cat | Bear | Bee

getColor :: Animal -> String
getColor Cat  = "Black"
getColor Bear = "Brown"
```

Provoque l’erreur suivante lors de la compilation :

```
Pattern match(es) are non-exhaustive
    In an equation for ‘getColor’: Patterns not matched: Bee
   |
 4 | getColor Cat  = "Black"
   | ^^^^^^^^^^^^^^^^^^^^^^^...
```

## L’interdiction des états invalides

Les états invalides peuvent être interdits par l’utilisation de types de données algébriques, ce qui permet de gagner du temps sur la compréhension du métier.

Par exemple si l’on déclare les coordonnées de bateaux d’une bataille navale comme ceci :

```haskell
type Coordonnées = (int, int)
```

Rien ne nous interdit de définir des coordonnées en dehors de la grille. Alors que si on les définit comme cela :

```haskell
data Vertical = A | B | C | D | E | F | G | H | I | J
data Horizontal = Un | Deux | Trois | Quatre | Cinq | Six | Sept | Huit | Neuf | Dix
newtype Coordonnées = Coordonnée (Vertical, Horizontal)
```

Il n’est alors plus possible de définir de position enfreignant les règles métiers, favorisant la compréhension des règles métiers lors de la lecture/modification du code.

Cela va aussi avoir un impact positif sur la masse de code à produire, car dans le premier exemple il aurait certainement fallut fournir des fonctions de vérification du format ou des bornes, accompagnées de tests unitaires. Dans le second exemple, tout ce code de vérification devient caduque.