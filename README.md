# Mesure crânienne

Outil web de mesure assistée sur photos de nourrissons :

- **Dessus** : CVAI, indice céphalique (IC) de la vue de dessus, CVA en mm si la photo est calibrée
- **Profil** : longueur antéro-postérieure glabelle–opisthocranion (mm)
- **Face** : largeur maximale euryon–euryon (mm)
- **Synthèse** : moyenne ± écart-type sur les clichés validés, IC orthogonal (largeur de face / longueur de profil × 100), résumé à copier

Tout le traitement se fait dans le navigateur. Aucune image ni mesure n'est envoyée ni conservée : tout disparaît à la fermeture de la page. Seule la longueur de la référence (en mm) est mémorisée localement.

## Mise en ligne avec GitHub Pages

1. Créer un dépôt public sur GitHub, par exemple `mesure-cranienne`.
2. Y déposer `index.html` : *Add file → Upload files*.
3. Aller dans *Settings → Pages → Build and deployment*, choisir *Deploy from a branch*, puis la branche `main` et le dossier `/ (root)`.
4. Après une minute environ, la page est accessible à l'adresse `https://<identifiant>.github.io/mesure-cranienne/`.

Sur iPad ou iPhone, *Partager → Sur l'écran d'accueil* ajoute la page comme une application.

## Utilisation

1. Choisir la vue (Dessus / Profil / Face), puis prendre ou importer une ou plusieurs photos.
2. **Calibration** (obligatoire pour profil et face) : toucher les deux extrémités de l'objet de référence, dont la longueur est réglée en haut de la page. L'échelle est reprise pour les photos suivantes de la vue (c'est indiqué à l'écran), et l'outil *Calibrer* permet de la refaire.
3. **Dessus** : tracer un cadre autour de la tête (*Détourage auto*), ou utiliser *Contour par points*, puis toucher la pointe du nez.
   **Profil / face** : l'outil *Pied à coulisse* s'active d'emblée (glabelle → opisthocranion, ou euryon → euryon). Le détourage automatique reste disponible en option.
4. **Contrôler** : tous les points se déplacent au doigt, et une loupe apparaît pendant le placement. Valider avec le bouton ou la touche Entrée.

### Contour par points
- Toucher pour ajouter un point. Il s'insère automatiquement au bon endroit du contour.
- Glisser un point pour le déplacer. Toucher un point sans le glisser pour le retirer.
- S'il existe déjà un contour automatique, *Contour par points* le convertit en 14 points à corriger là où les cheveux le faussent.
- *Ajuster automatiquement aux bords* (activé par défaut) : la courbe passant par les points est attirée vers le bord net le plus proche, dans une bande d'environ 4 % de la taille de la tête. Les petites imprécisions de pointage sont ainsi corrigées. À travers des cheveux, en revanche, le bord le plus net peut être celui des cheveux : il faut alors décocher l'option.
- Les points restent modifiables après *Terminer le contour*, et la mesure se recalcule aussitôt.

Navigation dans l'image : pincer ou utiliser la molette pour zoomer, glisser à deux doigts (ou clic droit, ou Espace + glisser) pour se déplacer.

## Synthèse
- Les vues sont regroupées dans une même séance, mais leurs indices sont calculés séparément : le CVAI (et la CVA) viennent de la vue de dessus, l'IC orthogonal vient de la face et du profil. L'IC de la vue de dessus est affiché à titre de contrôle de cohérence.
- Chaque indice est placé sur une jauge des seuils publiés, avec l'écart-type entre les clichés.
- *Copier le résumé* produit un texte prêt à coller dans le dossier, avec les valeurs de référence.

### Valeurs de référence utilisées
| Indice | Seuils | Source |
|---|---|---|
| CVAI | < 3,5 % normal · 3,5–6,25 léger · 6,25–8,75 modéré · 8,75–11 sévère · ≥ 11 très sévère | Échelle de Children's Healthcare of Atlanta |
| CVA | < 3 mm physiologique · 3–12 mm léger à modéré · > 12 mm sévère | Moss ; Mortenson & Steinbok |
| IC | 75–85 % normal · ≥ 90 % brachycéphalie (90–93 légère, 93–97 modérée, > 97 sévère) · < 75 % dolichocéphalie | Graham et al., *J Clin Med* 2020 |

Les seuils de brachycéphalie varient beaucoup selon les auteurs (de ≥ 80 % à ≥ 97 %).

## Conseils de prise de vue

- Fond uni et contrasté, bonnet en nylon pour plaquer les cheveux.
- Appareil bien perpendiculaire au plan mesuré, photographier à 1–1,5 m en zoomant plutôt que de près.
- Placer la référence à la même distance de l'objectif que le plan mesuré (plan sagittal médian pour le profil).

## Méthode

- **Dessus** : l'axe antéro-postérieur passe par le nez et le centre de gravité du contour. La largeur maximale est cherchée perpendiculairement à cet axe. Les diagonales sont tracées à ±30° depuis l'intersection de la longueur et de la largeur. CVAI = (D_max − D_min) / D_max × 100. Les niveaux de sévérité suivent l'échelle de Children's Healthcare of Atlanta.
- **Profil** : l'opisthocranion est le point du contour le plus éloigné de la glabelle, cherché vers l'arrière (±35° de l'horizontale).
- **Face** : la plus grande largeur horizontale est cherchée dans les 65 % supérieurs de la tête.
