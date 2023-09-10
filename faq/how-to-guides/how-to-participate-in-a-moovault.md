---
description: >-
  Ce guide visuel vous guidera à travers les étapes requises pour déposer des
  fonds dans un vault
---

# Comment déposer des jetons dans un vault

### Prérequis

* Vous devez avoir des jetons du vault en question. [Cliquez ici si vous ne savez pas comment alimenter votre portefeuille](../../comment-bien-debuter/alimenter-votre-portefeuille.md).
* Vous devez utiliser un portefeuille compatible, Metamask ou Trustwallet. [Cliquez ici si vous ne savez pas connecter votre portefeuille à Beefy](../../comment-bien-debuter/connecter-votre-portefeuille-a-beefy.md).

### Guide

#### 1.  Allez sur le site [Beefy.finance ](https://app.beefy.finance/)et cliquez sur  “WALLET” (Portefeuille) en haut à droite pour le connecter.

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption><p>Date du screenshot : 10 Octobre 2022</p></figcaption></figure>

Assurez-vous que votre portefeuille est connecté et qu'il est alimenté en jetons.

#### 2. Utilisez les filtres pour trouver le vault dans lequel vous souhaitez déposer vos jetons :

<figure><img src="../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

Les logos des différentes chaînes, les boutons de sélection prédéfinis et le barre de recherche font tous office de filtres.

#### 3. Exemple d'utilisation du filtre

Pour ce guide, nous utiliserons le vault BIFI Maxi sur le réseau Arbitrum :

<figure><img src="../../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

Vous pouvez noter que le BIFI Earnings Pool, dans lequel vous pouvez recevoir des WETH en y déposant des BIFI, apparaît également. Ouvrez le vault BIFI Maxi en cliquant n'importe où dans le champ encadré en rouge ci-dessus.

#### 4. Dans le vault BIFI Maxi :&#x20;

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

Sur la page de vault, beaucoup d'informations sont disponibles. Premièrement, la TVL (Total Value Locked, la Valeur Totale Bloquée), le prix et l'APY (Annual Percentage Yield, le Rendement Annuel en Pourcentage). Plus bas sont aussi disponibles les détails sur le ou les jetons concernés par le vault, ainsi que la stratégie appliquée sur celui-ci ([Qu'est-ce qu'une stratégie de vault ?](../../ecosystem-1/strategies.md)).

#### 5. Le module de dépôt (Deposit) et de retrait (Withdraw) :

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

Dans cet exemple, le module repère automatiquement que vous avez 1 BIFI disponible dans notre portefeuille à déposer. Un bouton « Buy Token » (Acheter des jetons) est prévu au cas où vous n'auriez pas de BIFI ou que vous souhaiteriez en acheter davantage pour effectuer un dépôt, ainsi qu'un bouton « Bridge BIFI » pour passer des BIFI présents sur une autre blockchain vers Arbitrum (Si vous avez besoin d'aide pour cela, voici [Broken link](broken-reference "mention")).&#x20;

Un champ de saisie ainsi qu'un bouton "Max" permettent de saisir le montant exact de BIFI que vous souhaitez déposer. Les frais d'utilisation du vault sont aussi indiqués. Pour plus de détails, vous pouvez consulter ici [Comment sont partagés les frais d'un vault](../../ecosystem-1/vaults.md#comment-sont-partages-les-frais-dun-coffre-fort).

#### 6. Un exemple de dépôt :



Cliquez d'abord sur le bouton « Max » puis sur le bouton « Deposit All » (Tout Déposer) pour déposer tous les BIFIs présents dans votre portefeuille.

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

Lorsqu'il s'agit de la première fois que vous effectuez un dépôt dans ce vault, vous devez accorder la permission au contrat intelligent d'accéder à vos fonds dans une première transaction :

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

Puis une seconde transaction se déclenche afin d'effectuer le dépôt dans le vault :

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

Le dépôt dans un nouveau vault nécessite toujours deux transactions : la première pour accorder l'accès à vos fonds et la seconde pour le dépôt.

#### 7. Confirmation du dépôt :

<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

Une fois la transaction réussie, un message s'affiche pour confirmer le dépôt et contient un lien vers la transaction dans l'explorateur de blocs. Il est très important de comprendre que votre portefeuille contient désormais une preuve de dépôt tokenisée appelée un « mooToken » ([Les MooTokens, qu'est ce que c'est ?](../../ecosystem-1/vaults.md#les-mootokens-quest-ce-que-cest)). Ce mooToken est **nécessaire** pour effectuer le retrait de vos jetons du vault, **ne le perdez pas** !

Sur la page de l'explorateur de blocs de votre transaction de dépôt, vous pouvez constater que les mooTokens sont envoyés dans votre portefeuille après le dépôt de vos jetons dans le vault. Le transfert de jetons ressemblera à quelque chose comme ceci :

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

Les mooTokens étant porteurs d'intérêts, ils ont plus de valeur que leurs homologues "normaux" (Dans notre exemple, en déposant du BIFI dans ce vault, vous récupérerez du mooArbitrumBIFI). C'est la raison pour laquelle le montant de mooToken reçu ne correspond pas 1:1 au montant de jetons initialement déposé ([Comment les mooTokens rapportent-ils des intérêts ?](../../ecosystem-1/vaults.md#comment-les-mootokens-rapportent-ils-des-interets)).

C'est tout ! Désormais, lorsque la fonction de récolte de ce vault est appelée, vous gagnez du rendement !
