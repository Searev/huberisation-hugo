---
title: "Ecoconception web : faut-il en finir avec les « Single-page Applications » ?"
slug: ecoconception-finir-spa
tags: 
  - Ecoconception
  - Numérique
  - Low Tech
date: 2021-03-24
author: Bastien Huber
summary: "Les applications monopages, ou « Single-page applications » (SPA) se sont imposées au fil de la décennie 2010 comme la principale manière de concevoir et de développer un site Internet. Leur poids plus important ainsi que les lourdeurs qu'elles
apportent posent cependant question à l'heure où l'impact environnemental du numérique devient préoccupant."
---

Ayant pour objectif de rendre les sites Internet plus dynamiques et fluides, les "SPA" ont été rendues possibles d'une par
l'amélioration des performances des navigateurs, et d'autre part par l'augmentation des débits mobiles permise par la 4G.
Si elles permettent, sous certaines conditions, une navigation plus agréable, elles ont cependant le défaut d'être également plus lourdes&nbsp;; de sorte que le poids moyen d'une page Internet est passé de 500Ko en 2011 à près de 2Mo en 2020 - pour un service rendu souvent assez identique. Cette augmentation du poids n'est pas neutre d'un point de vue environnemental, chaque octet transféré faisant appel à des serveurs, une infrastructure réseau, quantité de câbles, d'antennes, et d'appareils en tout genre. Nous nous rendons ainsi compte que l'impact carbone du numérique est aujourd'hui similaire à celui de l'aviation, et que l'empreinte énergétique directe du numérique augmente de 9% par an[^1].

Les pratiques d'écoconception logicielle ont précisément pour objectif de ramener cette empreinte du numérique à des doses plus raisonnables au regard des bénéfices produits. Elles cherchent pour cela à miminimer la configuration requise de l'internaute, monopoliser le moins longtemps possible réseau et serveurs, et nécessiter le moins de serveurs possibles pour générer les pages web, pour un service rendu équivalent.[^2]

Ces deux tendances sont ainsi a priori contraires, entre d'une part une architecture logicielle de plus en plus gourmande en ressources, et une nécessité d'en consommer de moins en moins. L'objectif de cet article est ainsi de comprendre en quoi les SPAs peuvent poser problème d'un point de vue écoconception, d'analyser d'un oeil critique les réponses qu'elles y apportent, et d'étudier les solutions alternatives qui s'offrent à nous.

## A l'origine du problème

Un site web « classique » n'envoie au client (le navigateur Internet : Google Chrome, Mozilla Firefox, etc) que les informations dont ce dernier a besoin pour afficher la page, à savoir :
- du HTML pour la structure et le contenu

- du CSS pour le style (couleurs, positionnement, etc)

- du Javascript pour ajouter un peu de dynamisme

- les images, vidéos et autres contenus multimédia à afficher

Cette logique aboutit naturellement a des pages assez légères, pour peu qu'elles ne cherchent pas à afficher des miniatures en 4K. Depuis une dizaine d'années cependant, une autre logique de conception de site web est apparue, les SPAs. La logique est pour elles similaire à une application traditionnelle : de la même manière que vous devez télécharger l'intégralité d'une application sur votre ordinateur ou votre smartphone pour pouvoir l'exécuter, vous devez télécharger l'intégralité (ou presque) d'une SPA pour qu'elle s'affiche dans votre navigateur.

Par exemple, si vous voulez réserver un train, un site web classique devra charger trois pages distinctes :

- une page affichant un formulaire vous demandant où vous souhaitez
  vous rendre et quand

- une page vous affichant les résultats de cette recherche

- une dernière pour confirmer votre achat

Entre chacune de ces pages, le navigateur devra recharger intégralement le HTML, et éventuellement le CSS et le Javascript s'ils sont réutilisés ou non. Pour ces derniers, il pourra en effet utiliser son *cache* afin de ne pas avoir à les redemander au serveur.

Une SPA, quant à elle, chargera le code permettant d'afficher ces 3 pages *d'un seul coup*, avant d'afficher les *mêmes* pages. Pour cela la quasi-totalité du site est codé en Javascript et CSS plutôt qu'en HTML/CSS/Javascript. Mais surtout, le site doit souvent charger d'autres bibliothèques logicielles :

- une permettant d'assurer le rendu dynamique de l'application : on parle
  de moteur de rendu et de moteur de réconciliation, permettant de savoir
  quelles modifications exactes sont à apporter à la page (ajouter un
  bouton ici, modifier une couleur là)

- une autre permettant de gérer la navigation de page en page à
  l'intérieur de l'application,

- une autre permettant de gérer *l'état* de l'application (par exemple votre
  compte, votre demande de train, les résultats de votre requête et le billet
  que vous souhaitez prendre)

- une autre pour interroger le serveur lorsque certaines informations sont à
  récupérer (les trains correspondant à votre requête...)

- etc

Cette approche a quelques avantages : la navigation semble plus fluide, et il est parfois bien plus aisé de développer certains comportements un peu complexes. Sur certaines applications, elle est même obligatoire (un tableau collaboratif sur lequel chacun peut interagir en temps réel par exemple). Mais sur d'autres, elle est facultative (notre exemple de réservation d'un billet par exemple).

Mais surtout, on comprend aisément que le site classique devrait être plus léger que la SPA.

## Un problème de taille

Pour donner un ordre d'idée, j'ai développé un site en tout point identique en utilisant les deux approches. Il permet d'afficher une page d'accueil, une liste d'utilisateurs et un formulaire dynamique permettant de les modifier. Les pages sont compressées au moment de l'envoi, de sorte à minimiser leur taille : j'afficherai ainsi à la fois la taille des pages *transférées* (avec compression) et *décompressées*

<aside>

**Note technique**

Pour celles et ceux familiers avec le développement web, voici les technologies que j'ai utilisé&nbsp;:

- le premier a été créé en utilisant [Symfony](https://symfony.com/) pour générer
  les pages HTML/CSS, et [Svelte](https://svelte.dev/) pour rajouter un peu de
  dynamisme par endroits en Javascript.

- le deuxième a été créé en utilisant [Angular](https://angular.io/) pour la
  partie « SPA », et [ExpressJS](https://expressjs.com/) pour la partie serveur.

Dans les deux cas, les mêmes règles de style ont été appliquées en utilisant certains composants spécifiques de 
[Bulma](https://bulma.io) afin d'en minimiser la taille, et le rendu final est *strictement* identique.

Les deux sites ont ensuite été déployés en utilisant [Docker](https://www.docker.com) : le site symfony en utilisant
une image php-fpm et une nginx, le site angular utilisant un nginx et l'API ExpressJS tournant directement sur une
image NodeJS. Les containeurs reposant sur Nginx ont été configurés afin d'utiliser une compression gzip.
</aside>

J'ai ensuite navigué sur ces trois pages afin de voir le poids total des pages ainsi transférées.

|                                     | Site classique   | SPA       |
|-------------------------------------|------------------|-----------|
| Poids des pages transférées         | 66,64 Ko         | 153,76 Ko |
| Poids total des pages décompressées | 257,27 Ko        | 537,16 Ko |
| Nombre de requêtes                  | 15 (+4 en cache) | 17        |

On remarque ainsi que pour un même site, affichant les mêmes informations, la SPA pèse 2,3 fois plus au moment du transfert. L'expérience utilisateur est pourtant rigoureusement la même sur les deux sites, pour une personne ayant une bonne connexion.

Mais que se passe-t-il maintenant si la connexion est limitée, par exemple pour atteindre le niveau d'une 3G « normale » ? Une option dans le navigateur permet de simuler une telle limite de connexion. J'ai donc recommencé ma navigation pour voir leur temps d'affichage.

|                                   | Site classique | SPA    |
|-----------------------------------|----------------|--------|
| Temps d'affichage de la 1ere page | 414 ms         | 1,41 s |
| Temps d'affichage de la 2e page   | 255 ms         | 405 ms |
| Temps d'affichage de la 3e page   | 390 ms         | 366 ms |

On comprend cette fois-ci que les deux sites ne proposent en réalité *pas du tout* la même expérience utilisateur. Alors qu'avec un débit réduit, le site classique affiche la page de manière tout à fait fluide, il lui faut plus d'1 seconde sur le second. L'effet d’obsolescence est donc double. D'une part sur les téléphones, puisqu'il devient impossible de naviguer sur un vieux téléphone n'étant pas équipé de puce 4G, d'autre part sur les infrastructures réseaux qui doivent être surdimensionnées.

De manière plus surprenante aussi, alors que la SPA vante une meilleure fluidité, on se rend compte qu'elle ne met pas forcément moins de temps à afficher les 2e et 3e pages. Cela est notamment lié au fait que si les SPAs récupèrent des données plus légères que les sites classiques, elles doivent souvent faire *plus* d'appels pour les récupérer, ce qui peut prendre, au final, plus de temps.

## L'impossible « retour sur investissement »

Il convient cependant de nuancer le propos. Les SPAs sont plus longues au démarrage, c'est un fait largement connu. Des solutions existent pour les rendre plus « véloces » à ce moment, c'est ce qu'on appelle le rendu « hybride »&nbsp;: l'application envoie initialement la première page comme le ferait un site classique, avant d'envoyer le reste de l'application prendre la main comme une SPA classique.

Si cette approche permet de fluidifier l'expérience utilisateur, elle implique cependant d'augmenter la quantité de données transitant sur le réseau - ce que nous cherchons à limiter. Cette approche ne saurait donc être la panacée.

Un point que peuvent mettre en avant les défenseurs de ce mode d'architecture est cependant le « retour sur investissement » qu'elles peuvent produire. Si elles sont plus longues à charger initialement, elles peuvent faire, sur de multiples utilisations, une meilleure utilisation du cache du navigateur, jusqu'à fonctionner sans connexion Internet.

Un site classique devra en effet systématiquement charger au moins l'intégralité du HTML pour bien s'afficher, le CSS/Javascript ayant tendance à rester en cache. Une SPA devra quant à elle uniquement chercher des informations plus ponctuelles, et dans des formats plus légers qu'un HTML. À tel point qu'à un moment, la quantité de données transférées avec une SPA serait *inférieure* à celle d'un site classique.

Regardons ainsi le coût d'une « navigation supplémentaire » pour nos deux sites

|                                     | Site classique | SPA        |
|-------------------------------------|----------------|------------|
| Poids de la page transférée         | 2,36 Ko        | 686 octets |
| Poids total de la page décompressée | 12,75 Ko       | 995 octets |

La nouvelle navigation coûte ainsi 3,4 fois moins de bande passante pour la SPA que pour le site classique !

Nous pouvons ainsi estimer qu'il faudrait naviguer **52 fois** sur ce site pour rentabiliser la SPA. Il semble ainsi très peu probable que nous finissions par rentabiliser ce coût. Nous ne naviguons que rarement autant de fois sur une même *version* d'un site, hors besoins très spécifiques.

Par ailleurs, tous les gains sont annulés à partir du moment où une nouvelle version du site est déployée : le cache du navigateur est en effet invalidé à ce moment. Hors, les quelques sites sur lesquels nous *pourrions* naviguer aussi souvent (mail, réseaux sociaux...) sont mis à jour très régulièrement, potentiellement plusieurs fois par jour. Sans compter le fait que le cache du navigateur ne dure qu'un temps, et peut très bien être vidé manuellement.

Mais plus encore, nous ne devrions jamais compter sur le *cache* du navigateur pour excuser un manque d'optimisation d'un site. Pour vous donner un exemple personnel, mon navigateur par défaut sur téléphone est Firefox Focus, qui permet de purger à la fin de ma navigation historique, cookies, cache, afin de mieux protéger ma vie privée. Par ailleurs, je me rends régulièrement sur Twitter depuis mon téléphone, suite à des liens que partagent des amis sur des applications de messagerie. Cette navigation ne se fait jamais en utilisant le cache du navigateur : il peut alors arriver que je doive *télécharger plusieurs Mo de données pour afficher un simple Tweet avec une petite image*. C'est complètement inacceptable, et cela contribue à expliquer, avec le streaming, pourquoi l'utilisation de données mobiles augmente de 50% par an [^3].

## L'impact inattendu des SPAs sur le poids de nos logiciels

On l'a vu, les SPAs sont en partie responsable de l'augmentation sensible du poids de nos pages web depuis une dizaine d'années. Mais leur impact ne saurait s'y limiter. En effet, de plus en plus d'applications pour ordinateur sont conçues et développées avec les mêmes technologies. C'est le cas par exemple des clients d'applications de messagerie comme Discord, Slack, WhatsApp, mais également de Spotify, Figma, Visual Studio Code, etc [^4].

Si le problème des SPAs sur le web réside dans le fait qu'elles doivent charger beaucoup de contenu inutile pour afficher une simple page, même blanche, le problème est cependant différent pour une application plus traditionnelle. En effet, il faut de toute manière la télécharger intégralement. Le problème repose alors dans l'environnement qui lui permet de s'exécuter.

En effet, ces applications, développées avec les langages du web, s'exécutent en réalité… dans une version adaptée du moteur du navigateur Google Chrome. Cela a de multiples avantages :  mutualiser les coûts de développement d'un site web et d'une application PC (voire d'une application mobile), avoir une version instantanément compatible Windows, Mac OS et Linux, se reposer sur l'immense écosystème de développement Javascript permettant d'intégrer quantité de fonctionnalités sans effort, bénéficier de facilités pour apporter plus d'effort sur l'enrobage graphique… Cependant, Chrome n'est pas connu pour sa frugalité. Ces facilités de développement se compensent donc par un poids global de l'application bien plus important, une réactivité moindre, et une consommation accrue des ressources de la machine.

Les applications se reposant sur cette technique pèse ainsi au minimum plus centaines de Mo là où elles ne devraient souvent en peser que quelques dizaines. Leur usage en RAM est également bien plus important qu'il ne le devrait - surtout pour des performances plus que modestes. L'ensemble donne ainsi toujours l'impression d'un ordinateur qui rame alors qu'il ne le devrait pas, créant une certaine forme d’obsolescence matérielle.

## Les alternatives

On l'a vu, il existe de multiples manières de concevoir un site web ou une application. Pour les applications en temps réel, comme un client de messagerie, les SPAs sont tout indiquées, même si l'on commence à entrevoir d'autres manières de faire. Des solutions comme [Phoenix LiveView](https://hexdocs.pm/phoenix_live_view/Phoenix.LiveView.html) permettent ainsi de mettre à jour le navigateur, en temps réel, depuis le serveur&nbsp;; en n'embarquant qu'un minimum de Javascript (une trentaine de Ko tout au plus [^5].).

Cependant, la majeure partie des sites n'ont pas besoin de temps réel, ni de fonctionner en mode *hors ligne*. Il ne faut pas oublier que les premières versions de Facebook ont été développées en PHP, le même langage utilisé par exemple pour Wikipedia, ou Wordpress. Il n'y avait pas de SPA à l'époque. Il serait donc plus raisonnable de revenir aujourd'hui à des techniques qui ont fait leurs preuves à une époque ou le débit moyen était le 512kbits/s, et qui étaient nécessairement plus légères. Cela implique de :
- générer les pages côté serveur dans la mesure du possible

- ne pas compter sur un rendu « hybride » pour prendre le relais comme une SPA puisque
  cela augmente la taille totale de la page

- n'ajouter des composants Javascript que dans la mesure où cela est nécessaire et par
  petites doses, en utilisant des solutions comme [React](https://fr.reactjs.org/) ou
  [Svelte](https://svelte.dev/), qui permettent de ne créer que de petits composants.

Ces principes sous-tendent de manière générale une conception des sites allant vers le [Low Tech](https://solar.lowtechmagazine.com/), dont le mot d'ordre devrait être :

> Chercher à avoir un site plus accessible, plutôt qu'un site plus dynamique.

## Conclusion

L'objectif de cet article n'est pas de clouer les SPAs au pilori, comme on pourrait le croire. Cette manière de développer une application - web, mobile ou desktop - a ses avantages et ses inconvénients. Cependant, alors que le monde des TIC commence à s'interroger sur son rapport ambivalent à la question environnementale, à la fois porteur de solutions et gros pollueur, il est important de noter que l'ubiquité actuelle des SPAs n'est pas sans causer de réels problèmes. Les applications conçues ainsi, pour un même service rendu, sont bien plus lourdes qu'elles n'ont besoin de l'être, bien trop lentes au vu des capacités actuelles de nos ordinateurs, et causent un vrai problème d'obsolescence.

Plutôt que de vouloir surdimensionner des infrastructures réseaux en ajoutant quantité d'antennes, 5G ou non, il est ainsi plus pertinent, et durable, de commencer par réduire la taille de nos applications actuelles. Comme tout outil, les SPAs ne devraient être utilisées que lorsqu'elle sont utiles et *nécessaires*, et remplacées par d'autres méthodes de création de sites ou d'applications, plus légères, lorsque le coût (environnemental) à payer ne le justifie pas.

## Sources

[^1]: The Shift Project. (2018). *Lean ICT : Pour une sobriété numérique*, [https://theshiftproject.org/wp-content/uploads/2018/11/Rapport-final-v8-WEB.pdf](https://theshiftproject.org/wp-content/uploads/2018/11/Rapport-final-v8-WEB.pdf)

[^2]: Bordage, F. (2019). *Ecoconception web : les 115 bonnes pratiques*. Eyrolles.

[^3]: ARCEP. (2020, janvier). Les services de communications électroniques en France. [https://www.arcep.fr/fileadmin/cru-1600420872/reprise/observatoire/3-2019/obs-marches-services-T32019-160120.pdf](https://www.arcep.fr/fileadmin/cru-1600420872/reprise/observatoire/3-2019/obs-marches-services-T32019-160120.pdf)

[^4]: Voir [https://www.electronjs.org/apps](https://www.electronjs.org/apps) pour une liste détaillée

[^5]: McCord, C. (2018). Phoenix LiveView: Interactive, Real-Time apps. No Need to write Javascript. [https://dockyard.com/blog/2018/12/12/phoenix-liveview-interactive-real-time-apps-no-need-to-write-javascript](https://dockyard.com/blog/2018/12/12/phoenix-liveview-interactive-real-time-apps-no-need-to-write-javascript)