---
title: "A quel monde la blockchain contribue-t-elle ? Partie 4 : un gâchis de ressources et d'énergie"
slug: blockchain-partie-4-impact-ecologique
tags: 
  - Blockchain
  - Cryptomonnaies
  - Ecologie
date: 2021-12-16
author: Bastien Huber
summary: "En raison des algorithmes qu'elles utilisent, les chaînes de blocs sont de réels gouffres écologiques, dont la consommation
excessive d'énergie n'a d'égale que l'immense quantité de déchets électroniques qu'elles finissent par laisser derrière elles. Si des
solutions moins énergivores sont connues, elles demeurent plus expérimentales et moins satisfaisantes."
---

En 1970, vers la fin des Trente Glorieuses, un club de hauts
fonctionnaires, industriels et scientifiques commanda à une petite
équipe du MIT un rapport pour étudier les effets à long terme de la
croissance économique et démographique. Publié deux ans plus tard sous
le titre de « The Limits to Growth », il détaille comment, dans un monde
aux ressources limitées, toute quête perpétuelle de la croissance finit
par se heurter à ses propres limites (manque de matières premières,
pollution, etc) avant de causer un effondrement[^1]. Suite à cela,
nombreuses sont les voix à avoir appeler pour une croissance
« immatérielle », une croissance des services. Nombreuses sont également
les voix à avoir trouvé dans le numérique un support à cette croissance
infinie et souhaitable des services et de la connaissance.

La blockchain nous rappelle aujourd'hui cruellement la naïveté de ces
souhaits. Peu de choses sont en effet aussi matérielles, consommatrices
de ressources et d'énergies, que le numérique. A titre d'exemple, le
réseau Bitcoin à lui seul consommerait annuellement près de 110 TWh
d'énergie électrique, soit à peu près autant qu'un pays de 17 millions
d'habitants comme les Pays-Bas[^2]. Pour mieux comprendre l'impact
écologiques des blockchains, nous expliquerons quels sont les facteurs
qui l'expliquent, comment le quantifier, afin d'évaluer sa pertinence
au vu du service qu'elles fournissent.

## Un service gourmand en ressources matérielles

L'impact d'un service sur l'environnement peut s'évaluer selon plusieurs
critères, comme sa consommation d'énergie, d'eau, de matières non
renouvelables ou ses émissions de gaz à effet de serre. Ces impacts sont
à évaluer sur la durée de vie complète du service, et comprennent donc
la fabrication des appareils permettant de le fournir, leur utilisation,
leur fin de vie, etc.

Dans le cas des blockchains comme le Bitcoin, le service fourni repose
principalement sur des fermes de serveurs informatiques servant à
construire la chaîne de blocs. En effet, le sceau cryptographique apposé
sur chaque bloc et qui permet d'en assurer l'immutabilité nécessite des
calculs très coûteux en puissance de calcul, devant être executés des processeurs
dédiés pour être effectués efficacement. C'est le principe du « Proof of
Work » expliqué précédemment : les processeurs doivent résoudre des
puzzle, à la difficulté croissante au fur et à mesure que le réseau
grandit, qui n'ont d'autre objectif que de s'assurer qu'il faut du temps
et de l'énergie pour miner un bloc.

Une compétition permanente existe entre les différents mineurs pour
« miner » plus vite que les autres. En effet, le minage d'un bloc génère
une récompense : quelques bitcoins sont créés et distribués à celui ou
celle ayant réussi le minage, ce qui lui permet de rentrer dans ses
frais : coût de l'électricité, d'achat et d'entretien des serveurs,
climatisation éventuelle, main d'œuvre, etc. S'il existe d'importants
« pools » de mineurs, où ces derniers se regroupent afin de partager
leurs récompenses et de lisser leur revenus, cela ne freine pas pour
autant la compétition qui règne. En effet, les récompenses sont toujours
réparties en fonction de la contribution de chaque mineur à la puissance
globale du pool : tout chose égale par ailleurs, il faut donc que sa
puissance de calcul relative reste constante, voire augmente, pour ne
pas voir ses revenus diminuer.

Si en théorie, n'importe quel processeur peut servir à miner du bitcoin
(ou d'autres crypto-monnaie), en pratique cela n'est que rarement
intéressant. N'est en effet rentable que le matériel qui permet, pour
une unité d'énergie dépensée, de :

1.  réaliser suffisamment de calculs (*hash*) pour permettre de
    participer assez significativement à la puissance d'un réseau
    toujours croissante,
2.  afin d'en tirer une récompense dont le montant varie selon le cours
    du bitcoin,
3.  permettant de générer un bénéfice au regard du coût de l'électricité
    et de l'achat dudit matériel.

On comprend ainsi aisément que seule l'utilisation d'un matériel
informatique spécifiquement optimisé pour ce genre d'opérations (on
parle de « ASIC » pour « Application Specific Integrated Circuit ») est
rentable ; et que ce dernier puisse rapidement devenir obsolète. En
résulte une importante production de puces électroniques, qui finissent
par rapidement devenir des déchets. Dans une récente étude publiée dans
le journal « Resources, Conservation and Recycling », Alex de Vries et
Christian Stoll estiment ainsi que ce matériel n'a qu'une durée de vie
en moyenne de 1,29 ans, et que le réseau Bitcoin produit à lui seul 30
700 tonnes de déchets électroniques, soit autant qu'un pays comme les
Pays-Bas[^3]. Une seule transaction sur la blockchain Bitcoin générerait
ainsi à elle seule 272g de déchets électroniques, soit plus qu'un
smartphone.

## D'importantes émissions de gaz à effet de serre


La construction de ces équipements électroniques, leur difficile recyclage, et leur utilisation au quotidien est par ailleurs fortement émettrice de gaz à effets de serre. Nous nous appuierons ici sur un mémoire intitulé « The Ecological Footprint of Blockchain » de Lukas De Loose[^4], rédigé en 2020 pour fournir des estimations chiffrées.

La majeure partie des émissions de GES des blockchains type Bitcoin est liée à la génération de l'électricité nécessaire pour faire tourner les fermes de serveurs. Si l'électricité est assez décarbonée en France, elle l'est malheureusement moins en Chine où ces dernières sont en bonne partie situées. Le Bitcoin tournerait ainsi principalement au charbon, mais également à l'hydroélectrique, les mineurs ayant tendance à utiliser l'électricité la moins chère qui se trouve souvent être le surplus généré par les barrages. En moyenne, De Loose estime ainsi que pour une consommation électrique annuelle de 80,2TWh, le réseau émettrait en moyenne 38 millions de tonnes équivalent CO2 (avec une fourchette allant de 17 à 71 MtCO2e), auxquelles il faudrait ajouter environ 1.3 MtCO2e d'émissions liées à la fabrication des puces électroniques sur l'année 2019-2020.

Au total, les blockchains émettraient ainsi plus de 39 MtCO2e par an. C'est autant que l'empreinte carbone de 3 200 000 français, soit l'équivalent d'une région comme la Bretagne.

## Perspectives de progrès

Celles et ceux défendant les blockchains noteront ici que cet impact est
celui produit *aujourd'hui* par les chaînes de bloc qui utilisent les
mécanismes de « Proof of Work », et qu'il y a de grandes marges de
progression pour les rendre plus compatibles avec nos objectifs de
réduction de gaz à effet de serre. Et force est de constater que
d'autres types de preuves existent, peuvent être implémentées, avec pour
résultat final de réduire drastiquement la puissance de calcul
nécessaire.

L'alternative la plus souvent mise en avant est celle du passage sur une
« Proof of Stake » (Preuve d'enjeu, « PoW »). Au lieu de résoudre un
puzzle cryptographique complexe, le réseau sélectionne un mineur qui
devra créer le prochain bloc. Afin d'avoir la chance d'être sélectionné,
les participants du réseau doivent mettre en jeu un certain nombre de
jetons ; plus ils en mettent, plus ils auront de chance d'être
sélectionnés. Si le système a l'avantage d'être considérablement plus
économe en énergie (i.e moins de CO2 émis) , et rend inutile
l'utilisation d'un type spécifique de processeur (i.e. moins de déchets
électroniques), il a le désavantage certain de donner plus de poids à
ceux ayant déjà accumulé le plus de capital, en plus de rallonger la
durée au bout de laquelle le réseau atteint un consensus, et donc le
temps d'attente avant la validation d'une transaction. Cette alternative
est actuellement testée par Ethereum, la 2e plus grosse blockchain
après Bitcoin, qui compte la déployer sur son réseau en 2022. Cependant,
cette bascule reste encore hypothétique, tant elle avait été annoncée il
y a longtemps[^5].

D'autres types de consensus avaient été testé, comme celui du Chia, qui
reposait sur une « Proof of Space », reposant sur la disponibilité
d'espace disque. Cependant, cette dernière avait la facheuse tendance à
griller les disques SSD sur lesquels elle tournaient, au point où de
nombreux fournisseurs de Cloud l'ont tout bonnement interdit sur leur
parc matériel[^6].

On comprend ainsi que les blockchains ont actuellement du mal à
s'éloigner de la Proof of Work, qui reste l'algorithme le plus utilisé
et le plus robuste. S'il ne fait pas de doute qu'à terme d'autres
méthodes apparaîtront, leur date d'arrivée et le temps qu'il faudra pour
qu'elles deviennent majoritaires est incertain.

## Conclusion

Comme l'avaient postulé les auteurs du rapport Meadows, nous vivons dans
un monde sous contraintes. D'une part, nous avons la contrainte de la
finitude des matières premières, qui devraient nous pousser aujourd'hui
à considérer le numérique comme une ressource critique et non
renouvelable : parmi les métaux essentiels à son fonctionnement,
certains pourraient en effet venir à manquer dans les prochaines
décennies[^7]. D'autre part, nous avons la finitude des exutoires de
notre planète, qui ne peut absorber toute notre pollution, nos déchets,
au point où nous avons un quota d'émissions de gaz à effets de serre à
ne pas dépasser si nous voulons limiter le réchauffement climatique à
1.5°C. A rebours de ce constat, le développement actuel des blockchain
consomme année après année toujours plus d'équipements informatiques
qui, périmé un ou deux ans plus tard, finissent comme déchets
électroniques ; et émet de plus en plus de CO2. A l'heure où nous devons
faire des arbitrages pour orienter les moyens, les ressources que nous
investissons dans la transition écologique, nous devrions choisir
d'utiliser ces technologies avec la plus grande modération, voire à ne
pas les utiliser du tout. Car dire aujourd'hui qu'il ne faut pas arrêter
d'utiliser le Bitcoin parce que son bilan carbone s'améliorera *un jour*
relève tout autant du greenwashing que lorsque Easy Jet, pour faire sa
promotion, annonce qu'ils feront voler des avions sans émettre de CO2...
quand la technologie le pemettra, peut-être, en 2050, sans pouvoir
apporter de garanties[^8].

[^1]: Meadows, D., Meadows, D., & Randers, J. (2017). *Les limites à la
    croissance (dans un monde fini)*. Rue de l'échiquier.

[^2]: Cambridge Centre for Alternative Finance. (s. d.). *Cambridge
    Bitcoin Electricity Consumption Index*. CBEI. Consulté le 2 décembre
    2021, à l'adresse [https://ccaf.io/cbeci/index](https://ccaf.io/cbeci/index)

[^3]: de Vries, A., & Stoll, C. (2021, 1 décembre). Bitcoin's growing
    e-waste problem. *Resources, Conservation and Recycling*.
    [https://www.sciencedirect.com/science/article/abs/pii/S0921344921005103?dgcid=author](https://www.sciencedirect.com/science/article/abs/pii/S0921344921005103?dgcid=author)

[^4]: de Loose, L. (2020, juillet). *Quantifying the Carbon Footprint of
    the Cryptocurrency Mining Industry* (Mémoire).
    [https://doi.org/10.13140/RG.2.2.15821.36325](https://doi.org/10.13140/RG.2.2.15821.36325)

[^5]: Ethereum. (2021, 5 novembre). *Proof-of-stake (PoS)*.
    Ethereum.Org.
    [https://ethereum.org/en/developers/docs/consensus-mechanisms/pos/](https://ethereum.org/en/developers/docs/consensus-mechanisms/pos/)

[^6]: *Chia Network : OVHcloud réagit à son tour*. (2021, 24 mai).
    nextinpact.com.
    [https://www.nextinpact.com/lebrief/47169/chia-network-ovhcloud-reagit-a-son-tour](https://www.nextinpact.com/lebrief/47169/chia-network-ovhcloud-reagit-a-son-tour)

[^7]: Bordage, F. (2019, août 27). *Le numérique est une ressource non
    renouvelable*. Green IT.
    [https://www.greenit.fr/2019/08/27/le-numerique-est-une-ressource-non-renouvelable/](https://www.greenit.fr/2019/08/27/le-numerique-est-une-ressource-non-renouvelable/)

[^8]: Bon pote. (2021, 2 décembre). *Bon Pote d'or 2021 : catégorie
    greenwashing*.
    [https://bonpote.com/bon-pote-dor-2021-categorie-greenwashing/](https://bonpote.com/bon-pote-dor-2021-categorie-greenwashing/)
