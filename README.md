# AtelierCV — aide

**Français** · [English](README.en.md) · [Español](README.es.md)

AtelierCV sert à dessiner un cerf-volant (armature, voile, bridage) et à calculer sa forme :
au repos, en vol au vent ou en vol plané. C'est **un seul fichier** : ouvrir
`AtelierCV_v390.html` dans un navigateur récent (Chrome ou Edge conseillés), sans rien installer.

Le dossier **`Modeles/`** contient une bibliothèque de cerfs-volants prêts à ouvrir (Eddy, Edo,
Flare, Sled, Eclipse, Mouette…) : bouton **Ouvrir**, puis le fichier `.json`. C'est le plus
simple pour découvrir l'outil, et une bonne base pour un nouveau dessin.

> **Un outil en développement.** AtelierCV évolue encore et ses résultats ne sont **pas fiables
> tels quels** : ils donnent des **pistes** (tendances, comparaisons entre variantes, sens d'une
> correction), à confirmer en vrai. Ses principales limites :
> - **pas de simulation de l'écoulement de l'air** : le vent est calculé par un modèle simplifié de
>   surface portante, sans décrochage réel, couche limite, turbulence ni sillage ;
> - **pas encore de gestion des structures entièrement souples** (parafoils, caissons) : la
>   pression intérieure des caissons existe, mais n'est pas validée ;
> - la toile, l'armature et le vent restent des modèles : frottement, coutures, ourlets,
>   connecteurs et tissus réels sont approchés.

Partout, le petit **ⓘ** donne l'explication d'un réglage ; la plupart des valeurs se règlent au
curseur, et un clic sur la valeur permet d'en taper une (au-delà des bornes si besoin).

L'interface existe en français, en anglais et en espagnol (choix dans l'en-tête).

## L'écran

- **À gauche — Dessin** : les couches, les outils, les réglages de ce qui est sélectionné.
- **Au centre — Calcul** : les conditions de calcul, le bouton **Calculer**, puis le bilan
  (tensions, efforts dans les tubes et les câbles, masses, vent, conseils).
- **À droite — les vues** : le dessin à plat (Dessus, Face, Côté) et la vue 3D, qui montre le
  résultat (couleurs = tension de la toile ; tubes bleus en compression, rouges en traction).

En haut : Nouveau, Ouvrir, Enregistrer (.json), exports (patrons à plat en DXF, rapport de
calcul en HTML, nomenclature), la bibliothèque, la langue, le thème, Annuler (Ctrl+Z).

## Dessiner

On travaille sur une couche à la fois ; les autres restent visibles et servent d'accroche.

| Couche | Outils |
|---|---|
| **Armature** | Tube, Latte (dans une poche de la voile), Câble, Whisker (écarteur), Ligne de construction |
| **Bridage** | Bride / ligne, Queue, Lest |
| **Voilure** | Forme (un clic par sommet), Cercle, Couture (découpe en panneaux), Liaison (voile ↔ armature), Monter |

- **Plans** : Dessus = plan XY, voile vue côté intrados, avant du cerf-volant vers le haut ;
  Face = vue depuis l'avant ; Côté = profil. Z est vertical.
- **Points** : un point partagé par plusieurs éléments devient un **nœud** (connecteur).
  Le sélectionner pour choisir son type : **rigide** (soudé), **rotule**, **coulisse**
  (l'élément qui le traverse y glisse, comme dans un manchon) ou **libre**.
  Un nœud peut aussi être **Point fixe** (ancrage au sol) ou **Anneau** (où la ligne s'attache).
- **Bords de voile** : ourlet, fourreau sur un tube, ou bord lié à un câble.
- **Symétrie** : on dessine le côté gauche (X négatif), le côté droit suit. Le bouton
  **Symétriser** reconstruit le côté droit d'un dessin existant.
- **Isoler** : n'afficher qu'une forme pour la retoucher, dans son propre plan si elle est inclinée.
- **Tubes et lattes** : matériau et section dans la bibliothèque, **surlongueur** (précontrainte),
  **Droit au repos** (décoché : la courbe dessinée est leur forme libre).
- **Voiles** : tissu (bibliothèque), patron, trous et renforts ; case **Quille** (hors du calcul au
  repos) et case **Caisson** (parafoil : peau gonflée par la pression intérieure).

## Souris et clavier

Les mêmes gestes valent dans la vue de dessin et dans la vue 3D.

| Geste | Effet |
|---|---|
| **Clic** | sélectionner ; avec un outil, poser un point (il s'accroche aux points, milieux et tracés proches) |
| **Glisser** un point ou une poignée | le déplacer |
| **Glisser sur le fond** | fenêtre de sélection : de gauche à droite = formes entièrement dedans, de droite à gauche = formes touchées |
| **Ctrl+clic** (Cmd sur Mac) | ajouter ou retirer de la sélection ; sur les points d'une forme sélectionnée : sélectionner plusieurs points |
| **Maj+clic** ou **clic droit** (sans glisser) | sur un tracé : ajouter un point ; sur un point : le retirer ; pendant un tracé : l'annuler |
| **Alt** maintenu | pas d'aimantation (point posé librement) |
| **Clic droit glissé** | tourner (vue 3D et perspective) ou déplacer la vue (vues à plat) |
| **Maj+clic droit**, **bouton du milieu** ou **Espace+glisser** | déplacer la vue |
| **Molette** | zoom (vers le curseur ; en 3D vers la croix orange, le pivot) |
| **Double-clic** | recadrer sur le cerf-volant (pendant un tracé de forme : le fermer) |
| **F** | placer le pivot sur la sélection ou sur le point sous la souris |
| **Maj** pendant un glissé de poignée de déplacement | mouvement fin (÷ 10) |

| Touche | Effet |
|---|---|
| **Ctrl+Z** / **Ctrl+Y** | annuler / rétablir |
| **Suppr** | effacer la sélection |
| **Échap** | annuler le tracé en cours, vider la sélection, sortir d'Isoler |
| **Entrée** | fermer une forme en cours (3 sommets au moins) |
| **Chiffres** pendant un tracé | taper une longueur exacte, puis Entrée |
| **Flèches** | déplacer les points sélectionnés (Maj : ×10) |
| **D** | dupliquer la sélection |
| **V** sélection · **U** tube · **A** latte · **B** câble · **W** whisker · **L** ligne · **R** bride · **T** forme · **O** cercle · **C** couture · **K** liaison · **M** monter | choisir l'outil |

## Vérifier avant de calculer

**Vérifier le dessin** liste ce qui empêcherait un calcul juste : points non raccordés, câbles
qui passent par un point libre, patrons incohérents, lattes coudées, noms en double… La plupart
des lignes ont un bouton qui corrige (Raccorder, Recouper, Aligner, Renommer…).

## Calculer

Choisir les conditions au centre, puis **Calculer** :

- **Au repos (au sol)** : la forme sous les seules précontraintes (surlongueurs, tension des
  câbles). Les quilles en sont exclues. Un cerf-volant sans armature (parafoil) n'en a pas.
  La forme au repos obtenue est gardée dans le fichier : le calcul suivant repart d'elle.
- **Tenu par la ligne (traction)** : une traction répartie sur la toile, à l'opposé de la ligne.
- **En vol, vent de face horizontal** : le vrai vent (vitesse en km/h), le cerf-volant trouve
  son orientation au bout de sa ligne, puis sa forme sous le vent, tour après tour. Le bilan donne
  la qualité du vol, un conseil de bride et la stabilité (lacet, roulis, tangage). Options :
  poids, queues, traînée des brides.
- **Vol plané (sans ligne)** : l'assiette où le cerf-volant plane stable, sa vitesse, sa pente et
  sa finesse (frottement de la toile réglable), la polaire, le meilleur plané et le **centrage** :
  de combien déplacer le centre de gravité, et quelle masse de lest poser au nez ou à l'arrière.
  Le bouton **Optimiser le plané** ajuste la masse du lest (le seul, ou celui coché « À optimiser ») par de vrais
  calculs de plané, essai après essai, jusqu'à la meilleure finesse en plané stable ; les autres lests
  (par exemple le poids de la ligne à l'anneau) restent fixes. Si le lest pend à l'anneau, une
  seconde passe déplace l'anneau le long de la bride, masse fixée. Le dessin ne change qu'avec « Appliquer ».

**Profil de calcul** : Estimation (rapide, maille grossière), Standard, Précis. En cas de doute
sur un résultat, refaire le calcul en Standard ou Précis.

Le calcul est un modèle : toile et armature sont bien calculées ; l'air l'est de façon simplifiée
(pas de décrochage ni de couche limite). Il sert surtout à **comparer des variantes** et à trouver
**dans quel sens corriger** (tension, bridage, centrage).

## Comment ça calcule

- **Le modèle.** Chaque voile est découpée en petits triangles (la *maille* ; plus la finesse est
  grande, plus ils sont petits). La toile est un tissu qui a sa raideur propre en chaîne, en trame
  et en biais, et qui ne résiste pas à la compression (elle fait des plis) ; elle a aussi une petite
  raideur en flexion, comme une feuille de papier (réglable par tissu, mesurable par l'essai du
  porte-à-faux), qui compte surtout pour les planeurs légers peu tendus. Tubes et lattes sont
  des poutres (traction, compression, flexion, torsion) ; câbles, brides et ourlets ne travaillent
  qu'en traction. Les connecteurs relient tout cela selon leur type.
- **La recherche de l'équilibre (relaxation dynamique).** Le calcul fait bouger tous les nœuds pas
  à pas, comme un objet qu'on lâche et qui s'amortit, jusqu'à ce que les forces s'annulent partout.
  Chaque pas est une **itération**.
  - **Tolérance** : l'écart de force qu'on accepte à la fin, rapporté aux efforts du cerf-volant
    (0,001 = 0,1 %). Plus petite = plus juste, mais plus long.
  - **Itérations max** : le calcul s'arrête là s'il n'a pas fini (« non convergé »).
  - **Amorce de flambement** : un tout petit défaut de départ, pour qu'un tube trop comprimé
    flambe du bon côté au lieu de rester droit en équilibre instable ; une sonde vérifie ensuite
    qu'aucun tube n'est resté droit au-delà de sa charge de flambement.
  - **Masses allégées** : un réglage du calcul qui accélère la convergence ; il ne change pas le
    résultat.
- **Le vent (méthode des anneaux tourbillonnaires).** La surface est découpée en panneaux portant
  chacun un tourbillon ; on en déduit la pression sur chaque panneau, donc la portance, la traînée
  induite et le centre de poussée. La pression suit la toile quand elle se déforme et est remise à
  jour régulièrement (*fréquence du couplage*). Le décrochage est approché panneau par panneau.
  Le vol au vent alterne : orientation du cerf-volant au bout de sa ligne, puis forme sous le vent,
  jusqu'à ce que rien ne bouge plus d'un tour à l'autre.
- **Le vol plané.** Pour chaque assiette, le moment de l'air autour du centre de gravité ; le plané
  stable est là où il s'annule en ramenant le cerf-volant. La vitesse est celle où l'air porte le
  poids ; la pente vient de la traînée (induite + frottement estimé).
- **Processeur ou carte graphique.** Le calcul tourne normalement sur le processeur, à part, pour
  que la page reste utilisable. **Calcul sur GPU** le confie à la carte graphique (navigateur
  compatible WebGPU) : mêmes équations, plus rapide sur les gros modèles. D'une machine à l'autre,
  le nombre d'itérations et le dernier chiffre des résultats peuvent varier un peu.
- **Forme au repos enregistrée.** Le résultat au repos est gardé dans le fichier ; tant que le
  cerf-volant n'a pas changé (brides exceptées), le calcul suivant repart de lui et finit vite.

## Après le calcul

- **Tendre les câbles** : raccourcit les câbles mous jusqu'à la tension voulue.
- **Patrons à plat (.dxf)** : la coupe de chaque panneau, prête pour la découpe.
- **Rapport de calcul (.html)** : tout le bilan et la vue 3D, avec le fichier du cerf-volant
  inclus (on peut le récupérer depuis le rapport).
- **PanelSearch** : envoie une voile à l'outil compagnon PanelSearch, pour chercher son panneautage.

## Soufflerie numérique FluidX3D

FluidX3D est un simulateur d'écoulement de l'air qui tourne sur la carte graphique, écrit par Moritz Lehmann
(https://github.com/ProjectPhysX/FluidX3D). Il est gratuit pour un usage personnel, éducatif ou de recherche publique ;
l'usage commercial ou militaire est interdit (voir LICENSE.md dans FluidX3D). AtelierCV ne l'inclut pas : il faut
l'installer et le compiler une seule fois. Ensuite, chaque cerf-volant passe en soufflerie sans recompiler.

### Ce qu'il faut

- Une carte graphique compatible OpenCL (NVIDIA, AMD ou Intel) avec son pilote à jour ; 4 Go de mémoire graphique ou plus conseillés.
- Windows : Visual Studio Community (gratuit), avec la charge de travail « Développement Desktop en C++ ».
- Linux : g++, make et le pilote OpenCL de la carte (paquet ocl-icd-opencl-dev, plus le pilote du fabricant).

### Installation (une fois)

1. Télécharger FluidX3D : sur sa page GitHub, bouton « Code » puis « Download ZIP », et décompresser.
2. Dans AtelierCV : **Alt + clic** sur Exporter → « Soufflerie FluidX3D (.stl) ». En plus des fichiers du cerf-volant,
   on obtient le réglage `atelier_fluidx3d.cpp` et ce guide.
3. Ouvrir `FluidX3D/src/setup.cpp`. Il contient une série d'exemples `void main_setup()`, tous entre `/*` et `*/`
   sauf un : mettre celui-là aussi en commentaire, puis coller tout le contenu de `atelier_fluidx3d.cpp` à la fin du fichier.
4. Ouvrir `FluidX3D/src/defines.hpp` :
   - mettre en commentaire (ajouter `//` devant) : `#define BENCHMARK`
   - activer (enlever le `//` devant) : `#define FP16S`, `#define EQUILIBRIUM_BOUNDARIES`, `#define SUBGRID`,
     `#define FORCE_FIELD`, `#define INTERACTIVE_GRAPHICS`
5. Compiler :
   - Windows : ouvrir `FluidX3D.sln` dans Visual Studio, choisir « Release », puis Déboguer → Exécuter sans débogage (Ctrl + F5).
   - Linux : dans `make.sh`, choisir la ligne de compilation « with X11 » (fenêtre interactive), puis lancer `./make.sh`.

Au tout premier lancement, FluidX3D ne trouve pas encore de cerf-volant : c'est normal.

### Pour chaque cerf-volant

1. Dans AtelierCV, calculer la forme, de préférence en vol au vent, puis Exporter → « Soufflerie FluidX3D (.stl) » (clic simple).
2. Copier `atelier_voile.stl`, `atelier_armature.stl` et `atelier.txt` dans `FluidX3D/stl/` (créer le dossier s'il manque), en remplaçant les anciens.
3. Relancer FluidX3D (`FluidX3D.exe` dans `FluidX3D/bin/`, ou Ctrl + F5 dans Visual Studio). Pas besoin de recompiler.

Dans la fenêtre : P lance ou met en pause, H affiche l'aide des touches, les touches 1 à 7 changent l'affichage
(lignes de flux, tourbillons…). La console affiche régulièrement la traînée, la portance et leurs coefficients.

### Réglages dans atelier.txt (sans recompiler)

- `n` : finesse, en mailles sur la longueur du cerf-volant (75 par défaut). La mémoire suit n³, le temps de calcul n⁴ environ.
- `amont`, `aval`, `largeur`, `hauteur` : taille de la soufflerie, en longueurs du cerf-volant (1, 2,5, 2,5, 2,5).
  Garder au moins 1 en amont.
- `d` : nombre de domaines, pour forcer la découpe de la grille (calculé seul d'après la carte graphique).

### Lire les résultats

- Comparer surtout en relatif (deux réglages d'un même cerf-volant) : à ces tailles, les valeurs absolues restent approximatives.
- Les tubes sont grossis pour être vus par la grille : leur traînée est surestimée.
- Les brides ne sont pas en soufflerie : ajouter leur traînée, donnée par AtelierCV (« Traînée et poids des brides »).

## Bibliothèque

Matériaux, tubes et joncs, câbles, tissus et profils de calcul. Une **référence** choisie sur un
élément peut être modifiée ensuite ; **Appliquer la bibliothèque au projet** met à jour les
éléments qui la suivent. Les fiches personnelles ne sont jamais écrasées par les nouvelles
fiches d'usine.
