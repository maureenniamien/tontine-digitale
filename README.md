# Tontine Digitale — Guide APK

## Prérequis

- Node.js 18+ installé
- Android Studio installé (https://developer.android.com/studio)
- Java JDK 17+ installé
- Variable `ANDROID_HOME` configurée dans ton environnement

---

## Étapes pour générer l'APK

### 1. Installer les dépendances
```bash
cd tontine-digitale
npm install
```

### 2. Ajouter la plateforme Android
```bash
npx cap add android
```

### 3. Synchroniser les fichiers web vers Android
```bash
npx cap sync android
```

### 4. Ouvrir dans Android Studio
```bash
npx cap open android
```

### 5. Générer l'APK dans Android Studio
Dans Android Studio :
- Menu **Build → Build Bundle(s) / APK(s) → Build APK(s)**
- L'APK sera généré dans :
  `android/app/build/outputs/apk/debug/app-debug.apk`

---

## APK signé (release)

Pour un APK signé prêt pour le Play Store :
- Menu **Build → Generate Signed Bundle / APK**
- Crée ou utilise un keystore existant
- Sélectionne **APK** → **release**

---

## Structure du projet

```
tontine-digitale/
├── www/
│   └── index.html        ← L'app web (landing page)
├── android/              ← Généré par `cap add android`
├── capacitor.config.json ← Config Capacitor
├── package.json
└── README.md
```

---

## Modifier l'identité de l'app

Dans `capacitor.config.json` :
```json
{
  "appId": "com.tontinedigitale.app",   ← ID unique Play Store
  "appName": "TontineDigitale",          ← Nom affiché
  "webDir": "www"
}
```

---

## Icône & Splash Screen

Après `cap add android`, remplace les fichiers dans :
```
android/app/src/main/res/
  mipmap-hdpi/ic_launcher.png      (72x72)
  mipmap-xhdpi/ic_launcher.png     (96x96)
  mipmap-xxhdpi/ic_launcher.png    (144x144)
  mipmap-xxxhdpi/ic_launcher.png   (192x192)
  drawable/splash.png              (2048x2048)
```

Ou utilise l'outil : https://capacitorjs.com/docs/guides/splash-screens-and-icons

---

## Permissions Android

Les permissions sont dans `android/app/src/main/AndroidManifest.xml`.
Capacitor en ajoute automatiquement selon les plugins utilisés.

---

## Ressources

- Capacitor Docs : https://capacitorjs.com/docs
- Android Studio : https://developer.android.com/studio
