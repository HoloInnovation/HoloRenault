# HoloRenault

- [Introduction](#introduction)
- [Fonctionalités](#fonctionalités)
  - [Mapping de l'environment](#mapping-de-lenvironment)
  - [Afficher un asset depuis le Unity Store](#afficher-un-asset-depuis-le-unity-store)
  - [Déplacement indépendant des objets](#déplacement-indépendant-des-objets)
  - [Changement d'échelle des assets](#changement-déchelle-des-assets)
  - [Création d'un objet à partir d'un menu](#création-dun-objet-à-partir-dun-menu)
- [Difficultés rencontrées](#difficultés-rencontrées)
  - [Complexité de la pièce](#complexité-de-la-pièce)
  - [Nouvelle technologie](#nouvelle-technologie)
- [Limites du casque](#limites-du-casque)
  - [Limites des assets](#limites-des-assets)
  - [Difficultés d'afficher des assets complexes](#difficultés-dafficher-des-assets-complexes)
  - [Champs de vision](#champs-de-vision)
- [Améliorations possibles](#améliorations-possibles)
  - [Assembler plusieurs assets](#assembler-plusieurs-assets)
  - [Avoir un asset modifié](#avoir-un-asset-modifié)
  - [License](LICENSE.md)

## Introduction
Le Microsoft Hololens.
Le nouveau casque de réalité mixte developpé par Microsoft a été introduit en 2016 aux communautés de developpeurs offrant alors une nouvelle plateforme propice à l'innovation.
Dans le cadre de notre projet de 4ème année en école d'ingénieur, nous avons choisi de travailler avec Actimage, une société spécialisée dans la transformation digitale, afin de travailler sur cette nouvelle technologie qui marie le monde virtuel au monde réél.

*Mixed reality (MR), sometimes referred to as hybrid reality, is the merging of real and virtual worlds to produce new environments and visualizations where physical and digital objects co-exist and interact in real time.
Mixed reality takes place not only in the physical world or the virtual world, but is a mix of reality and virtual reality, encompassing both augmented reality and augmented virtuality via immersive technology.*

*- [Wikipedia](https://en.wikipedia.org/wiki/Mixed_reality)*

Ayant pour objectif d'innover, nous avons pris contact avec de nombreuses entreprises en exposant les avantages de la réalité mixte dans l'industrie.
Nous avons concentrés nos effort sur l'industrie automobile.
C'est ainsi que nous avons pu prendre contact avec le *Quality Roadmap Team Leader* chez Renault, qui s'est montré receptif lors de la présentation de notre idée.
Nous nous sommes rencontrées lors du salon *Microsoft Experiences '17* à Paris afin de définir les besoins.
A la suite de notre échange, nous sommes arrivé à la conclusion que la réalité mixte peut jouer un rôle important au sein des usines de Renault.
Non pas uniquement à la formation des travailleurs mais également au niveau de la sécurité sur les chaines de montage par le biais de l'enregistrement virtuel de l'usine.

Aujourd'hui les entreprises font face à de réél problèmes.
Les chaines de montages ont besoin d'être optimisés afin d'assurer la sécurité et la productivité.
En d'autres termes, notre idée pourrait très bien être utilisé tout aussi bien pour des entreprises dans l'industrie automobile mais également adapté pour des entreprises relevant d'autre domaines.
Pour ce qui relève de la sécurité, le casque permetterai de reduire grandement le temps d'inspection des machines grâce à l'enregistrement dans les usines.
De plus, un bon placement des machines est essentiel pour garantir l'optimisation lors de leur fonctionnement.

Afin de répondre aux besoins, nous avons developper une application permettant de modifier en temps réél le placement des machines tout en visualisant leur fonctionnement.
C'est en applicant notre savoir faire d'ingénieur que nous avons construit notre équipe et établit notre plan de travail.
Cette technologie est relativement jeune et les principes de l'ingénieurie sont essentiels pour avancer.
Aujourd'hui, apès une année de travail, nous partageons notre expérience avec la communauté en fournissant une base d'informations aux futurs developpeurs.

## Fonctionalités
### Mapping de l'environment

*Spatial mapping provides a detailed representation of real-world surfaces in the environment around the HoloLens, allowing developers to create a convincing mixed reality experience.*

*- [Microsoft](https://docs.microsoft.com/en-us/windows/mixed-reality/spatial-mapping)*

![Spatial Mapping](/img/spatial-mapping.png "Spatial Mapping")

La majorité des applications developpé sur Hololens nécessite un  ```SpatialMapping```.
C'est une fonctionalité existante de que nous avons uniquement besoin d'implanter dans l'application sur Unity.
Lors du lancement de l'application, le casque effectue un premier mapping de la pièce.
Dans notre application, lorsque l'utilisateur selctionne un asset à déplacer, le dessin d'un mapping est révélé indiquant ainsi les endroits où la machine peut etre placé.

Avec la dernière version du [HololToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity), il est possible de parametrer la précision du mapping en modifiant le nombre de triangles à afficher: ```TrianglesPerCubicMeter```. 
Par défault, le nombre est fixé à 500 et peut aller jusqu'à 1200 triangles.

Comme il est bien expliquer dans [Hologram 230](https://docs.microsoft.com/en-us/windows/mixed-reality/holograms-230) les triangles peuvent être ajouter ou retirer lors du mapping.


### Afficher un asset depuis le Unity Store


### Déplacement indépendant des objets
Avec pour objectif principal de notre projet de placer les machines Renault en usine, la caractéristique au coeur de notre application est la possibilité de selectionner un holograme et de le placer dans l'environment.
Pour cela, nous avons utiliser un script disponible dans le HololToolkit: ``TapToPlace``
Afin d'utiliser ce script, il est nécessaire d'implementer auparavant dans la scène Unity le ``GazeManager``, le ``GestureManager`` et le ``SpatialMapping``.

### Changement d'échelle des assets
La mise à l'échelle est une foncitonalités importante de l'application.
Dans le cas ou une simulation à taille réél n'est pas nécessaire, par exemple dans le cas d'une présentation, il s'avère plus pratique de disposer d'une machine à taille réduite pour faciliter le déplacement.

Dans Microsoft Visual Studio, la mise à l'échelle d'un objet se passe par la création d'un Vecteur3 étant donner que nous travaillons dans un espace à 3 dimensions.
Le vecteur prend 3 paramètres *float* en arguments répresenant les axes X, Y, Z.
Afin de conserver la précision d'un nombre fractionel, il suffit d'ajouter *(float)* à l'argument.

### Création d'un objet à partir d'un menu
Pour la mise en place de l'usine, notre application devrait avoir la possibilité d'instancier de nouvelles machines dans la scène.
Pour cela, nous avons ajouter un bouton *Add asset* au menu.
Celui-ci permet à l'utilisateur de faire aparaitre un Hologram en face de lui lors du click.
Cette machine est sélectionné dans le panel composants sur Unity.
Voici une simple démonstration [vidéo](https://www.youtube.com/watch?v=J7vCS75DC6w) de l'application montrant les fonctionalités de bases aves des pièces d'exemple.

## Difficultés rencontrées
### Complexité de la pièce
Pendant le developpement de l'application, nous avons effectuer des testz sur l'Hololens dans différentez situations: salles de classes, *open-space* et même en usine.
Nous avons observer que le mapping est fortement impacter par l'environement. Plusieurs variables rentrent en jeu pour la qualité du mapping comme la couleur des murs, les matériaux du sol.
Cela repose particulièrement sur comment la lumière et les rayons ultra-rouge sont refractés sur les surfaces. 
L'Hololens est en difficultés lorsqu'il est utilisé dans des environement avec un espace plus restreint comme de petites salles. 
Les options d'utilisations sont alors rapidement limités.
Les meubles ont une part de responsabilité également.
Les différence de hauteurs des meubles sont suceptiblent de causer des erreurs dans le mapping.
Les objets plus sombres du fait de l'absorption de la lumière sont parfois à l'origine de trous dans le mapping, le rendant irrégulier et discontinue.
Cela implique que les objets ne peuvent pas être placé n'importe où dans l'environement.

### Nouvelle technologie
Nous avons rencontré différent types de problèmes auquels nous avons fais face.
Nous n'arrivions pas à trouver facilement les solutions sur le net du fait de la jeune adoption de la technologie.
Une grande partie de notre travail était donc de comprendre comment est-ce que le casque fonctionne.

## Limites du casque
### Limites des assets
Le casque est équipé d'un porcesseur graphique appélé *Microsoft Holographic Unit (HPU 1.0)* et un d'un processeur Intel 32-bit.
Il est équipé de 2GB de RAM et 64GB de mémoire flash.
Il possède une limite de 900MB d'allocation de mémoire.

Il est donc très important de garder les applications suffisament légère pour maintenir 60FPS et assurer une utilisation confortable à l'utilisateur.
Il est également important de minimiser la fatigue oculaire et pour ce faire, les assets doivent être placer dans la zone de confort.
En effet, *Microsoft Windows Miwed Reality Academy* recommande de changer la valeur du ```Near Clip Plane Field``` de 0.3 à 0.85, équivalent à 0.85 mètre.
Cela permet de reduir de la pénibilité visuel lorsqu'un hologram est trop proche de l'utilisateur.

![Placement d'un Hologram](/img/hololens-hologram-placement.png "Hologram Placement")


### Difficultés d'afficher des assets complexes
Au court de notre projet, nous avons utilisé des assets d'une grande complexité avec plus de 8 million de polygones.
Ces assets sont trop large et nécessite une trop grande puissance de calcul pour le casque.
Nous avons trouver qu'idéalement les assets ont besoin d'être composé de 100'000 polygones ou moins pour être proprement gérer par l'Hololens.

Dans un cas comme celui ci, un bon logiciel pour la simplification de pièce est [Simplygon](https://www.simplygon.com/):

*Simplygon is a 3D computer graphics software for automatic 3D optimization, based on proprietary methods for creating level of detail (LODs) through Polygon mesh reduction and other optimization techniques.*

*- [Wikipedia](https://en.wikipedia.org/wiki/Simplygon)*

Cependant, passer d'une simplification de 8M à 100k polygones est compliquer à faire. 
Le résultat est insatisfaisant, la pièce obtenus est iregulière et imprécise.
Une meilleurs solution serait de manuellement simplifier la pièce en supprimant les groupes de polygones inutiles, généralement les détails invisibles à l'oeil.
Ainsi cela faciliterai grandement le processus de simplification du logiciel.

### Champs de vision
Microsoft donne un chiffre assez faible de 35% pour le champs de vision du casque Hololens.
Ce petit champs de vision impact grandement l'expérience de l'utilisateur.
Celui-ci est forcé d'effectuer de plus grand mouvements de tête pour naviguer dans le milieu virtuel, propice à l'apparition plus rapide des douleurs musculaire.
Placer un seul hologram est généralement suffisant pour remplir le champs de vision et limite grandement les capacités du casque.
Le plus grand inconvéniant est l'utilisation d'assets de 3 à 4 mètres de largeur.
Déjà limiter par les performances du casque, l'experience est moins immersive lorsque l'utilisateur se retrouve à l'interieur de la machine. (plus de détails dans la partie [Assembler plusieurs assets](#assembler-plusieurs-assets))

## Améliorations possibles
### Assembler plusieurs assets
Les modèles de pièces de Renault étaient bien trop large pour une échelle 1:1.
Les tests que nous avons effectué dans les espaces retreint des salles de cours souligne la difficulté de bouger librement autour de l'asset.
Par exemple, dans une salle plus petite, l'utilisateur avance dans la réalité mais sa position dans le monde virtuel reste quasi statique et mène parfois à la sensation de bouger dans la direction opposé à la direction souhaiter.
Cela s'explique par l'imposante taille du modèle.

Avec une largeur de plus de 5 mètre, le casque renontre des difficultés à relayer la sensation de réél à l'utilisateur.

Un solution serait de redimensionner les assets à 4 mètres ou moins.
Mais cela irait à l'encontre du but de la réalité mixte étant donné que les dimensions ne seraient pas representatif de la réalité.

Une autre solution serait de couper le modèle.
Encore une fois, même si cela pourrait marcher sur certaines machines, cela irait à l'encontre de l'objectif de la réalité mixte.

Une meilleurs solution qui permetterai de minimiser l'impact negatif sur l'experience tout en apportant des avantages à l'utilisateur serait de reconstruir la machine avec le casque à partir des différentes pièces qui la compose.
Prenons l'exemple d'un employé dans l'indutrie automobile.
En ajoutant les pièces de la machine dans l'environement, l'employé contriburait avec chaque addition de pièce à la machine final.
C'est une oportunité d'intéragir individuellement avec chaque partie qui compose la machine et d'apprendre par la même ocasion les fonctionalités de chaque assets.

### Avoir un asset modifié

## License
Ci-joint la [license](LICENSE.md).
Ce document est mis à disposition de la communauté mais possède des popriétés intellectuelles portégées comme l'idée et l'application.

L'utilisations sans consentement des créateurs est punis.

CC BY-NC-SA 2.0 - Propritété intellectuelle protégée.
