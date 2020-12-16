# Rapport

---

## Decision Tree

**Un arbre de décision est un outil d'aide à la décision représentant un ensemble de choix sous la forme graphique d'un arbre**. Les différentes décisions possibles sont situées aux extrémités des branches (les « feuilles » de l'arbre), et sont atteintes en fonction de décisions prises à chaque étape. 

L'arbre de décision est un outil utilisé dans des domaines variés tels que la sécurité, la fouille de données, la médecine, etc.   

Il a l'avantage d'être **lisible et rapide** à exécuter. Il s'agit de plus d'une représentation calculable automatiquement par des algorithmes d'apprentissage supervisé.

- <ins>Avantages :</ins>

    - Facile à comprendre : Le 1er avantage de cet algorithme c’est qu’il est intuitif. Comme vous pourrez le voir dans les explications de son fonctionnement il est vraiment simple à comprendre. Et naturellement on a toujours tendance à préférer utiliser quelque chose que l’on comprend et que l’on maitrise.

    - Facile à interpréter : Son 2e avantage c’est qu’il est facile à interpréter. Les résultats peuvent être présentés à des équipes métier et les règles de décision produites par l’arbre sont faciles à comprendre.

    - Temps d’exécution raisonnable. Enfin un dernier avantage qui peut avoir son importance, c’est un algorithme assez simple qui n’est pas très coûteux en temps de calcul.

- <ins>Inconvénients :</ins>

    - Faible performance. Le principal inconvénient des arbres de décision pour moi est le manque de performance par rapport à d’autres algorithmes. Mais il est parfois nécessaire de faire un choix entre performance et interprétabilité.

    - Risque de sur-apprentissage : Deuxième inconvénient ou en tout cas un piège dans lequel il ne faut pas tomber… L’overfitting c’est-à-dire le sur-apprentissage (l’algorithme apprend avec tellement de précision les données d’entrainement qu’il ne parvient pas à généraliser un résultat satisfaisant sur de nouvelles données). Pour éviter cela il est important de bien élaguer son arbre de décision.

## Random Decision Forest

La base du calcul repose sur l'apprentissage par arbre de décision. La proposition de Breiman vise à corriger plusieurs inconvénients connus de la méthode initiale, comme la sensibilité des arbres uniques à l'ordre des prédicteurs, en calculant un ensemble de ***B*** arbres partiellement indépendants.

Une présentation rapide de la proposition peut s'exprimer comme suit :

- Créer ***B*** nouveaux ensembles d'apprentissage par un double processus d'échantillonnage :
    - sur les observations, en utilisant un tirage avec remise d'un nombre ***N*** d'observations identique à celui des données d'origine (technique connue sous le nom de bootstrap)
    - et sur les {\displaystyle {p}}{p} prédicteurs, en n'en retenant qu'un échantillon de cardinal `m < √p` (la limite n'est qu'indicative).
- Sur chaque échantillon, on entraîne un arbre de décision selon une des techniques connues, en limitant sa croissance par validation croisée.
- On stocke les ***B*** prédictions de la variable d'intérêt pour chaque observation d'origine.
- La prédiction de la forêt aléatoire est alors un simple vote majoritaire *(Ensemble learning)*.

Le principal inconvénient de cette méthode est que l'on perd l'aspect visuel des arbres de décision uniques.