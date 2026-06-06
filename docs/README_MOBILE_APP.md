# Pulpo mobile app pack

Ce pack contient les fichiers nécessaires pour transformer Pulpo en application mobile :

- PWA installable : `manifest.webmanifest`, `sw.js`, icônes.
- Starter Capacitor : `native-starter/package.json` et `capacitor.config.json`.
- Dossier web : `www/`.

## Important

Le fichier `www/index.html` fourni ici est un shell de sécurité. Pour produire l'application réelle, remplace-le par le dernier `index.html` Pulpo mobile/téléphone.

Le dernier index mobile repéré dans ton espace contient déjà les interactions tactiles : `tap outil = ajouter`, `tap sortie puis entrée = connecter`, et `appui long = réglages`.

## Process PWA

1. Copier ton dernier `index.html` mobile dans `www/index.html`.
2. Copier `manifest.webmanifest`, `sw.js`, `icons/` à la racine du site GitHub Pages.
3. Dans `<head>` de `www/index.html`, vérifier la présence de :
   - `<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">`
   - `<link rel="manifest" href="../manifest.webmanifest">`
   - `<meta name="theme-color" content="#111827">`
   - `<link rel="apple-touch-icon" href="../icons/icon-180.png">`
4. Publier sur GitHub Pages.
5. Tester Chrome Android : menu navigateur > Installer l'application.
6. Tester Safari iPhone : Partager > Sur l'écran d'accueil.

## Process Android natif avec Capacitor

Pré-requis : Node.js, Android Studio, JDK, compte Google Play Console.

```bash
cd native-starter
npm install
npx cap init Pulpo eu.prestaterre.pulpo --web-dir=../www
npx cap add android
npx cap sync android
npx cap open android
```

Dans Android Studio :

1. Build > Generate Signed App Bundle / APK.
2. Choisir Android App Bundle `.aab`.
3. Tester sur émulateur + téléphone réel.
4. Publier dans Google Play Console.

## Process iOS natif avec Capacitor

Pré-requis : Mac, Xcode, compte Apple Developer.

```bash
cd native-starter
npm install
npx cap init Pulpo eu.prestaterre.pulpo --web-dir=../www
npx cap add ios
npx cap sync ios
npx cap open ios
```

Dans Xcode :

1. Régler Team + Bundle Identifier.
2. Tester sur simulateur + iPhone réel.
3. Product > Archive.
4. Envoyer via App Store Connect / TestFlight.

## Checklist mobile

- Android Chrome : ajout outil par tap.
- iPhone Safari : ajout outil par tap.
- Connexion : tap sortie puis tap entrée.
- Appui long sur outil : ouverture réglages.
- Zoom / pan canvas.
- Sauvegarde locale.
- Export/import JSON.
- Aide ouverte/fermée.
- Orientation portrait/paysage.
- Clavier iOS : aucun zoom intempestif sur input.
- Mode PWA lancé depuis écran d’accueil.
