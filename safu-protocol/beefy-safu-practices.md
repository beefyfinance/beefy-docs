---
description: >-
  SAFU est une appellation dérivée de Safe, traduisible en français par "En
  sûreté".
---

# Bonnes pratiques Beefy SAFU

_"Don't Trust, Verify" que l'on peut traduire par "Ne faites pas confiance, vérifiez."_

## Les nouvelles fermes sur Beefy

Avant qu'une nouvelle ferme ne reçoive un vault sur Beefy, le projet doit passer une vérification stricte des règles SAFU : &#x20;

* Les contrats ont été vérifiés dans l'explorateur de blocs;
* Les jetons non-natifs doivent provenir de Bridges connus et réputés;
* Il y a assez de liquidité pour échanger les jetons obtenus en récompense;
* Les fonctions permettant de déplacer les fonds des utilisateurs ont été supprimées ou sont derrière un timelock conséquent;
* Les taux d'émission des jetons de la ferme doivent être derrière un timelock (Si les paires de jetons de la ferme sont dans un vault);
* Les possesseurs de jetons avec plus de 5% de la Supply en circulation ne sont pas des EOAs (Externally Owned Accounts) ou des multi-sigs;
* Toutes les modifications d'implémentation mandataires doivent être timelock.

## Les nouveaux vaults sur Beefy

Nos stratèges suivent une procédure de tests manuels sur chaque nouveau vault avant que celui-ci ne soit mis en ligne. Ces vérifications sont effectuées pour assurer que le vault fonctionne comme prévu et que les fonds des utilisateurs soient toujours _SAFU_.

1\. Dépôt d'un petit montant d'un actif;\
2\. Retirer tout;\
3\. Second dépôt, attendre 1 minute et vérifier si le `callReward()` n'est pas à 0;\
4\. Récolter la stratégie;\
5\. Passer la stratégie en Panic State (état de panique); \
6\. Retirer 50% du total du vault pendant l'état de panique pour s'assurer que les utilisateurs peuvent bien sortir de la stratégie.\
7\. Essayer de déposer, une erreur devrait apparaître et le dépôt ne devrait pas s'effectuer; \
8\. Rétablir la stratégie à l'état normal;\
9\. Déposer les 50% retirés pendant l'état de panique et effectuer une nouvelle récolte.

## Amélioration de stratégie

Parfois, il est possible que les stratèges Beefy vont mettre au point une nouvelle stratégie innovante, ou que les fermes de rendement modifient leur contrat de récompense. Si cette situation se produit, les vaults Beefy ont la flexibilité de s'adapter à ces changements, et ont la capacité de changer les stratégies appliquées afin que les utilisateurs n'aient pas besoin de migrer leurs fonds vers un nouveau vault grâce à une amélioration de stratégie.

La nouvelle stratégie est tout d'abord déployée sur un vault factice, et les tests manuels cités ci-dessus sont tous appliqués pour en vérifier la fonctionnalité. Après avoir passé les vérifications, la nouvelle stratégie est assignée au vrai vault. La stratégie est proposée au vault via un portefeuille multi-signature, qui devra attendre que le timelock soit passé avant de l'utiliser.

## Mode Panique

Parfois, des problèmes peuvent survenir sur la ferme de rendements sous-jacents, il est donc primordial de réagir rapidement. Nos stratégies Beefy ont un système de surveillance qui est autorisé à passer en mode panique, retirant ainsi les fonds déposés de la ferme vers le contrat de la stratégie et révoquant les autorisations. Cela permet d'assurer aux utilisateurs Beefy qu'ils aient toujours accès à leurs fonds en cas d'urgence.
