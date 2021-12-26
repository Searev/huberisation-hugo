---
title: "A quel monde la blockchain contribue-t-elle ? Partie 1 : La technique"
slug: blockchain-partie-1-technique
tags: 
  - Blockchain
  - Cryptomonnaies
date: 2021-12-13
author: Bastien Huber
summary: "Dans un contexte de crise économique mondiale en 2008, un papier de recherche est publié, jetant les bases de
la blockchain et des cryptomonnaies. 13 ans plus tard, les cryptos affolent les bourses du monde entier, l'occasion de
proposer un premier bilan du monde auquel la blockchain contribue."
---

Le 15 septembre 2008, la 4e plus grosse banque d\'investissement
américaine, *Lehman Brothers*, se déclare en situation de faillite. Dans
son sillage, elle entraîne toutes les bourses mondiales, dans ce que
l\'on retiendra comme l\'une des pires crises bancaires de l\'histoire.
Les citoyens du monde entier découvrent stupéfaits les méfaits de
l\'opacité du système financier, tandis que le journal *Le Monde* fait
état de 25 000 milliards de dollars « partis en fumée ».[^1]

C\'est dans ce contexte de crise économique mondiale qu\'apparaît en
novembre de la même année un petit papier de recherche d\'à peine 9
pages : [Bitcoin : A Peer-to-Peer Electronic Cash
System](http://satoshinakamoto.me/bitcoin.pdf). Signé du pseudonyme
« Satoshi Nakamoto », il décrit le fonctionnement d\'un système
monétaire virtuel transparent, immuable, et indépendant de toute
institution financière. Il signe ainsi le début des « cryptomonnaies »,
dont le Bitcoin ne sera que la première implémentation. Il décrit
également une structure de données sous-jacente, la « blockchain » (ou
chaîne de blocs), qui donne au système toute sa robustesse.

Le Bitcoin apparaît ainsi dès le début comme comme un objet hybride, à
la fois mathématique, scientifique, mais également économique,
social et politique. Un hybride à l\'ambition démesurée, puisqu\'il ne
cherche rien de moins qu\'à entraîner une recomposition de tous nos
échanges, économiques ou non, au sein d\'un système ne nécessitant pas
de confiance en un tiers, comme aujourd\'hui.

13 ans plus tard, le Bitcoin affiche une capitalisation folle, les
cryptomonnaies attisent les intérêts de quantité d\'organisations,
privées ou étatiques, tandis que la Blockchain est utilisée dans la
supply chain ou encore le marché de l\'art. Elle attise également les
critiques sur sa consommation énergétique démesurée, ou sur sa capacité
à contribuer au financement d\'organisations criminelles.

Comment se retrouver au milieu de tous ces éléments ? Quelle position
les ingénieurs qui conçoivent, utilisent, et souvent promeuvent ce genre
de structure devraient-ils adopter ? Dans la lignée d'une éthique
conséquentialiste, qui s'interroge sur les *conséquences* de nos actes
plus que sur nos intentions, fussent-elles bonnes ou mauvaises, la
question que nous nous poserons dans cette série d\'article est donc :

> *A quel monde la blockchain contribue-t-elle ?*

Pour y répondre, nous commencerons tout d\'abord par expliquer la nature
et le fonctionnement général de la blockchain - ou plutôt *des*
blockchains, puisqu\'il en existe une infinité de sortes - en évoquant
les problèmes techniques auxquelles elles répondent. Nous aborderons
ensuite les promesses des promoteurs des blockchains, qui ambitionnent
de remodeler nos structures socio-économiques.

Nous verrons alors comment les acteurs économiques actuels - entreprises
de la tech, états, etc - ont réagit afin de se ré-approprier ces
technologies qui promettaient de renverser la table... afin de les
retourner à leur avantage.

Nous évoquerons enfin, dans une dernière série d'articles, les
différents reproches qu\'il est possible de faire aux blockchains,
allant de leur impact écologique problématiques aux différentes
problématiques économiques et philosophiques inhérentes à leur
conception.

## Un peu d'histoire

Les systèmes comptables et monétaires que nous utilisons aujourd'hui
fonctionnent de manière dite « centralisée », c'est-à-dire qu'ils se
reposent sur *un* acteur précis : la banque qui tient le registre de ses
clients, le « bon père de famille » qui établit la comptabilité de son
foyer, etc. Ce système a l'avantage de la simplicité, puisqu'il repose
sur un nombre très limité d'acteurs. Si vous êtes un commerçant à qui un
client veut acheter un bien, vous n'avez qu'à interroger sa banque pour
savoir s'il a les liquidités qui le permettent.

Il n'en a cependant pas toujours été ainsi. Dans son livre *Utopies
Réalistes[^2]*, Ruther Bregman relate par exemple un improbable épisode
de grève des banques en Irlande, en 1970. Avec 85 % des réserves
financières du pays bloqués, on peut imaginer la catastrophe qui aurait
dû se produire : l'impossibilité de payer les loyers, d'avoir du
liquide, etc. Pourtant, après 6 mois de grève, l'économie irlandaise se
portait encore assez bien. Les irlandais s'étaient simplement tournés
vers d'autres acteurs économiques que les banquiers, à savoir... les
patrons des quelques 11 000 pubs du pays, qui, pour leur avoir servi à
boire pendant des années, étaient assez au fait de l'état de leurs
finances ! Un système décentralisé s'était ainsi mis en place
naturellement, fondé sur la cohésion sociale et la confiance mutuelle.
Un gérant de pub à Dublin déclarait ainsi « je ne traitais qu'avec mes
habitués... je refusais les étrangers. Je suppose que j'ai permis à
quelques usines de fonctionner ».[^3]

## Le problème de la double dépense

L'idée d'un système monétaire décentralisé, numérique ou non, n'est
ainsi pas récente. Elle fait cependant face, dans les faits, à un
problème particulier, celui de la « double dépense ». Imaginez ainsi que
vous étiez un irlandais vivant à Dublin en 1970, habitué de deux pubs,
le « Celt Pub » et le « Arthur's Bar ». Imaginez maintenant que vous
souhaitiez vous offrir un appartement de 100 000£, mais vous n'avez
« que » 50 000£. Vous pouviez imaginer aller au « Celt's Pub » demander
un retrait de 50 000£, puis courir au « Arthur's Bar » demander la même
chose, avant que les deux patrons de bar n'aient eu le temps d'échanger
sur le sujet. Vous auriez alors récupéré deux fois les mêmes 50 000£ !
Forcément, le pot-au-roses aurait tôt ou tard été découvert, mais vous
auriez déjà pu acquérir votre logement.

Tout réseau monétaire décentralisé doit faire face à ce problème, qui
est inhérent à la vitesse de propagation de l'information auprès du
réseau. Si le patron du « Celt's Pub » avait passé un coup de fil à
celui du « Arthur's Bar » avant de vous avoir fourni les 50 000£, cela
n'aurait pas pu arriver. Mais imaginez maintenant que vos comptes de
soient pas gérés par 2, mais par des milliers d'acteurs : comment faire
pour que chacun ait une information fiable et à jour ?

### La solution apportée par le Bitcoin

Le réseau Bitcoin fonctionne de manière assez similaire à ce réseau des
patrons de pubs. Les tenanciers sont remplacés par les fameux
« mineurs », qui possèdent tous une copie du registre des transactions
effectuées sur le réseau. Ils communiquent entre eux en permanence, pour
savoir lequel a la version la plus « à jour » du registre.

Ce registre a une forme assez particulière, qui a donné son nom à la
technologie, à savoir celle d'une chaîne de blocs. Chaque bloc contient
un ensemble de transactions vérifiées (« Alice a envoyé 1 Bitcoin à Bob,
*et elle le peut parce qu'elle en avait reçu 1 de Eve au préalable* »),
sa date de création, la référence du bloc précédent, puis est scellé
cryptographiquement avant d'être proposé au reste du réseau. Ce dernier
peut alors en vérifier l'authenticité et l'accepter. Se forme ainsi,
bloc après blocs, une chaîne regroupant l'intégralité des transactions
effectuées sur le réseau.

![Structure d'une chaîne de blocks](../../images/blockchain_structure.svg)

Chaque mineur travaillant de manière indépendante, plusieurs versions de
la chaîne peuvent exister en parallèle. Cependant, la norme est de
toujours travailler sur la chaîne la plus longue. Si un mineur a le
choix entre 2 chaînes sur lesquelles travailler, il choisira toujours de
travailler avec la plus longue des deux. Si les deux sont de longueur
égale, il pourra choisir indifféremment l'une des deux : cependant,
l'une finira forcément par devenir plus longue que l'autre. Le réseau
converge ainsi forcément vers une solution unique, à savoir la chaîne la
plus longue disponible, qui devient l'unique version du registre des
transactions effectuées.

Le problème de la double dépense est alors résolu « à terme ». En effet,
si deux mineurs éloignés ont permis à un même bitcoin d'être dépensé en
même temps de deux manières différentes, ces deux transactions doivent
figurer dans des blocs différents, qui ne peuvent être présents dans une
même chaîne. En effet, comme on l'a vu, chaque transaction est *vérifiée*,
c'est-à-dire que le mineur doit s'assurer que le bitcoin qu'Alice envoie à
Bob n'a pas déjà été dépensé précédemment. Deux transactions dépensant un
même bitcoin ne peuvent alors pas se suivre. Dans ce cas, deux versions de
la chaîne existeraient en parallèle, mais inévitablement, l'une finira par
être plus longue que l'autre, et sera acceptée. L'une des deux transactions
sera alors caduque.

Qu'est-ce qui empêche cependant un acteur malicieux de modifier un bloc
précédent, afin d'y supprimer par exemple une transaction ? C'est tout
le principe du sceau cryptographique qui est appliqué, reposant sur le
principe de la « Preuve de Travail » (« Proof of work », PoW en abrégé).
Pour sceller un bloc, l'ordinateur du mineur doit effectuer une série
d'opérations mathématiques, une sorte de puzzle dont l'objectif
d'atteindre une valeur particulière, en ne modifiant à chaque reprise
qu'un seul paramètre, appelée « nounce » (valant 0, puis 1, 2, 3, etc).
Ces opérations complexes sont très chronophages, et leur difficulté,
croissante, est dictée par le réseau de sorte à ce que la création d'un
bloc prenne toujours à peu près autant de temps. Ainsi, si un acteur
veut modifier l'avant-dernier bloc, il devra en créer un nouveau valide,
puis un autre, dans l'espoir de rattraper la chaîne la plus longue, qui
continuera d'avancer pendant ce temps... Ce qui est *très* improbable, à
moins que l'acteur en question ait plus de puissance de calcul que le
reste du réseau. C'est ce que l'on appelle « *l'attaque des 51 %* » : si
un acteur possède plus de 51 % de la puissance du réseau, alors en
théorie, il serait en mesure de reconstruire une chaîne de blocs plus
longue en partant de n'importe quel bloc, et donc, en théorie, de
ré-écrire l'historique des transactions... quitte à en faire disparaître
certaines.

La blockchain est ainsi une structure qui fonctionne sans qu'il n'y ait
à avoir confiance dans un acteur spécifique. Alors que les tenanciers
irlandais ne prêtaient qu'à leurs clients, les mineurs peuvent valider
les transactions de n'importe quel acteur du réseau. En retour, les
acteurs du réseau n'ont pas besoin d'avoir confiance en *un* mineur
particulier, puisque cette confiance est diluée dans le *réseau en
lui-même* : si l'un d'entre eux est malicieux, il finira par être
écarté.

## Les différents acteurs de la blockchain

Nous avons déjà évoqués l'une des typologie d'acteurs des blockchains,
les « mineurs ». Ces derniers mettent à disposition du réseau leur
puissance de calcul et leur mémoire afin de stocker les registres et de
créer les blocs permettant de construire la blockchain. L'intérêt qu'ils
ont à faire cela est que, pour chaque bloc créé, ils reçoivent une
récompense : de nouveaux bitcoins, créés sur le moment, en plus de
commissions qu'ils perçoivent sur chaque transaction. Le nombre de ces
bitcoins créés avec le temps décroît, de sorte à ce que la quantité de
bitcoin disponible finisse par se stabiliser autour d'une valeur
pré-définie.

Les autres acteurs importants de la blockchain sont celles et ceux
effectuant des transactions sur son réseau : Alice, envoyant son bitcoin
à Bob. Mais comment être sûr que c'est bien à Bob que la transaction est
destinée, et qu'Alice en est bien l'autrice ? La solution est apportée
par la *cryptographie asymétrique*. Alice possède ainsi deux clefs :
l'une publique, qu'elle peut communiquer à tout le monde, et l'autre
privée, qu'elle garde avec elle. La clef privée permet de chiffrer un
message, qui ne peut alors être déchiffré qu'en utilisant la clef
publique. Il est par ailleurs impossible de retrouver la clef privée à
partir de la clef publique. Ainsi, lorsqu'Alice envoie 1 bitcoin à Bob,
elle chiffre cette transaction en utilisant sa clef privée. Les mineurs
recevant la transactions peuvent alors vérifier que c'est bien elle qui
a fait l'opération en utilisant sa clef publique pour déchiffrer le
message.

Un dernier problème peut alors se poser, si Alice oublie, ou perd, sa
clef privée. Il ne s'agit en effet que d'un fichier stocké sur un
ordinateur, une clef usb ou un téléphone, qui peut facilement être
supprimé. Un mot de passe permet en général de la re-générer, mais peut
également être égaré. Pour celles et ceux ayant perdu les deux, il est
alors impossible de récupérer son portefeuille, et d'utiliser les
bitcoins qu'ils ou elles ont pu avoir. On estime aujourd'hui que près de
25 % des bitcoins sont ainsi perdus à jamais...[^4]

## Les autres blockchains

Nous avons pour l'instant principalement parlé de la blockchain Bitcoin,
historique, mais beaucoup d'autres ont vu le jour depuis. La majorité
d'entre elles ne changent que quelques détails de l'implémentation du
protocole, mais demeurent fidèle au principe de la « cryptomonnaie ».
Elles s'appellent Ripple, Tether, Dash, Dogecoin... et forment ce que
l'on appelle globalement les « Alt Coins ».

D'autres implémentations cherchent à ajouter de nouvelles
fonctionnalités au concept de blockchain. C'est notamment le cas de la
blockchain « Ethereum ». L'objectif de cette dernière n'est ainsi pas
seulement d'être un registre comptable distribué, mais d'être, en
quelque sorte, un *ordinateur* distribué, capable d'exécuter des
programmes simples, appelés « contrats intelligents » (« smart
contracts »). Par exemple, de tels contrats pourraient être utilisés
pour envoyer automatiquement une quantité de cryptomonnaie à une
personne en fonction d'un service rendu, et l'intégralité du réseau
serait garant de ce transfert.

Beaucoup d'autres acteurs se sont également lancés sur le marché des
blockchains. Inutile de toutes les lister, mais citons à titre d'exemple
les nombreuses blockchains regroupées dans la maison-mère
« Hyperledger », sponsorisée par la Linux Foundation, qui se distinguent
sur plusieurs points :

* Elles ne se reposent pas forcément sur une cryptomonnaie comme le
  Bitcoin et l'Ether.
* Elles peuvent être privées, de sorte à ce que seules certaines
  personnes puissent y accéder, à l'opposé de Bitcoin ou d'Ethereum
  qui sont des blockchains publiques. En particulier, cela leur permet
  d'être plus adaptée aux besoins des entreprises qui veulent limiter
  les accès leur système d'information.
* Elles implémentent parfois des algorithmes différents de la « Preuve
  de Travail » afin de permettre l'immutabilité du registre.
* Elles peuvent avoir un objectif très précis : gestion de supply
  chain, d'un référentiel d'identités, etc

Il existe ainsi une infinité de blockchains possibles, qui ont néanmoins
toutes les mêmes bases, à savoir : fonctionner de manière décentralisée,
et viser à rendre les données qu'elles gèrent impossible à modifier.

Dans le [prochain article](../blockchain-partie-2-promesses), nous essaierons de brosser un portrait du
monde tel que le rêvent celles et ceux qui promeuvent ces technologies.

[^1]: Delhommais, P.-A., Lacombe, C., & Roche, M. (2008, 25 octobre).
    *25 000 milliards de dollars évanouis*. Le Monde.fr.
    [https://www.lemonde.fr/la-crise-financiere/article/2008/10/25/25-000-milliards-de-dollards-evanouis_1110953_1101386.html](https://www.lemonde.fr/la-crise-financiere/article/2008/10/25/25-000-milliards-de-dollards-evanouis_1110953_1101386.html)

[^2]: *Bregman, R. (2017). *Utopies Réalistes*. Seuil.*

[^3]: Moshinsky, B. (2016, 21 janvier). *Pubs replaced banks in Ireland
    in 1970 and the economy was fine*. Business Insider.
    [https://www.businessinsider.com/pubs-replaced-banks-in-ireland-in-1970-and-the-economy-was-fine-2016-1?IR=T](https://www.businessinsider.com/pubs-replaced-banks-in-ireland-in-1970-and-the-economy-was-fine-2016-1?IR=T)

[^4]: Reiff, N. (2019, 25 juin). *20% of All BTC is Lost, Unrecoverable,
    Study Shows*. Investopedia.
    [https://www.investopedia.com/news/20-all-btc-lost-unrecoverable-study-shows/](https://www.investopedia.com/news/20-all-btc-lost-unrecoverable-study-shows/)
