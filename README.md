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
2. **Calibration** (obligatoire pour profil et face) : toucher les deux extrémités de l'objet de référence, dont la longueur est réglée en haut de la page.
3. **Cadrer** : tracer un rectangle autour de la tête. Le contour est détouré automatiquement.
4. **Pointer** : le nez (vue de dessus) ou la glabelle (profil). La vue de face n'en a pas besoin.
5. **Contrôler** : les points se déplacent au doigt. Une loupe apparaît pendant le placement. Le curseur *Lissage* retire les oreilles et le nez du contour. Valider avec le bouton ou la touche Entrée.

Si le détourage automatique échoue :
- *Contour manuel* : toucher le pourtour du crâne, puis *Terminer le contour*.
- *Pied à coulisse* (profil et face) : mesurer directement entre deux points.

Navigation dans l'image : pincer ou utiliser la molette pour zoomer, glisser à deux doigts (ou clic droit, ou Espace + glisser) pour se déplacer.

## Conseils de prise de vue

- Fond uni et contrasté, bonnet en nylon pour plaquer les cheveux.
- Appareil bien perpendiculaire au plan mesuré, photographier à 1–1,5 m en zoomant plutôt que de près.
- Placer la référence à la même distance de l'objectif que le plan mesuré (plan sagittal médian pour le profil).

## Méthode

- **Dessus** : l'axe antéro-postérieur passe par le nez et le centre de gravité du contour. La largeur maximale est cherchée perpendiculairement à cet axe. Les diagonales sont tracées à ±30° depuis l'intersection de la longueur et de la largeur. CVAI = (D_max − D_min) / D_max × 100. Les niveaux de sévérité suivent l'échelle de Children's Healthcare of Atlanta.
- **Profil** : l'opisthocranion est le point du contour le plus éloigné de la glabelle, cherché vers l'arrière (±35° de l'horizontale).
- **Face** : la plus grande largeur horizontale est cherchée dans les 65 % supérieurs de la tête.
