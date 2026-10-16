# StudyLens — build intégré caméra + affichage (sans IA)

Ce dépôt est un fork du Meta Wearables Device Access Toolkit iOS. Le workflow
`.github/workflows/studylens-integrated.yml` construit **un seul IPA** depuis
l'application officielle `BirdSpotter`, qui utilise déjà les modules DAT de
caméra et d'affichage dans une même cible iOS.

## Ce que cette version apporte

- Un seul build iOS et un seul artefact IPA non signé.
- Le nom affiché sur l'écran d'accueil est changé en `StudyLens`.
- L'application sous-jacente conserve les écrans et parcours de démonstration
  BirdSpotter, notamment ses fonctions de capture et d'affichage DAT.
- Pas d'OCR ni d'IA ajoutés.
- Les exemples `CameraAccess` et `DisplayAccess` restent dans le dépôt et ne
  sont pas modifiés.

## Lancer le build

1. Envoyer ce dépôt sur GitHub (ou copier le fichier workflow dans le dépôt existant).
2. Ouvrir l'onglet **Actions**.
3. Choisir **StudyLens - Build integrated Camera and Display**.
4. Cliquer sur **Run workflow**.
5. Quand le workflow est terminé en vert, ouvrir l'exécution et télécharger
   l'artefact `StudyLens-Integrated-iPhone-unsigned`.
6. Installer l'IPA avec AltStore, comme pour le build précédent.

## Limites importantes

- L'IPA est **non signé**; il faut le signer via AltStore avec ton identifiant Apple.
- Le bundle identifier reste celui du sample (`com.meta.pixelandtexel.birdspotter`)
  afin d'éviter de modifier le projet Xcode et ses références internes.
- Cette version est un prototype intégré basé sur l'interface BirdSpotter : elle
  n'est pas encore une interface StudyLens personnalisée.
- Le workflow de compilation ne prouve pas le fonctionnement sur les lunettes.
  L'enregistrement de l'application, le mode développeur et les mises à jour
  requises par Meta restent nécessaires.
- L'application officielle CameraAccess arrête son aperçu quand elle passe en
  arrière-plan. Ne suppose donc pas que la capture vidéo continue quand l'iPhone
  est verrouillé. Il faut valider le comportement sur le matériel réel.
- Le flux de question → traitement → réponse n'existe pas encore : aucune IA,
  aucun OCR et aucun serveur ne sont inclus.

## Pourquoi partir de BirdSpotter ?

Le dépôt contient déjà une application plus large que les deux petits exemples :
elle configure DAT et possède des dépôts caméra et affichage reliés à la même
session. C'est une base de compilation intégrée plus fiable que de copier à
l'aveugle des morceaux de deux projets Xcode indépendants.
