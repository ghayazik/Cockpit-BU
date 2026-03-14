# 📊 Cockpit Directeur BU — IT / Digital / Transformation

Tableau de bord multi-visions avec authentification, gestion des droits, import Excel/CSV, saisie de données et analyse IA.

---

## 🚀 Déploiement en 5 minutes

### Étape 1 — Pousser sur GitHub

```bash
# Créer un repo sur github.com puis :
git init
git add .
git commit -m "Cockpit BU v3"
git branch -M main
git remote add origin https://github.com/VOTRE_USER/cockpit-bu.git
git push -u origin main
```

### Étape 2 — Déployer sur Netlify

1. Allez sur [netlify.com](https://app.netlify.com)
2. Cliquez **"Add new site" → "Import an existing project"**
3. Connectez votre repo GitHub `cockpit-bu`
4. Configuration :
   - **Build command** : _(laisser vide)_
   - **Publish directory** : `public`
5. Cliquez **"Deploy site"**

Votre site sera en ligne en ~30 secondes.

### Étape 3 (Optionnel) — Activer Firebase pour le multi-utilisateurs

Sans Firebase, les données sont sauvegardées dans le **localStorage** du navigateur (chaque navigateur a ses propres données).

Avec Firebase, tous les utilisateurs partagent les mêmes données (comptes, projets, fichiers).

1. Créez un projet sur [console.firebase.google.com](https://console.firebase.google.com)
2. Activez **Firestore Database** → mode "test"
3. Allez dans **Project Settings → General → Your apps → Web** → Enregistrer une app
4. Copiez les identifiants dans `public/index.html` (section `window.__FIREBASE_CONFIG__`)
5. Redéployez sur Netlify (push git)

**Règles Firestore** (copiez dans Firestore → Rules) :
```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if true;
    }
  }
}
```

---

## 🔐 Accès par défaut

| Rôle | Identifiant | Mot de passe |
|------|-------------|--------------|
| Admin | `admin` | `1317` |

L'administrateur peut créer d'autres comptes via ⚙️ Admin.

---

## 📋 Fonctionnalités

- **4 visions dashboard** : Financière, Opérationnelle, RH, Gouvernance
- **Vision "Autre"** : dashboard auto-généré pour les données non catégorisées
- **Import Excel/CSV** multi-fichiers avec catégorisation automatique ou manuelle
- **Gestion des fichiers** : visualiser, re-catégoriser, supprimer individuellement ou en masse
- **Saisie mensuelle** : effectifs, SLA, CSAT, PM, CA (actuel + prévisionnel N+1 à N+3)
- **Analyse IA** intégrée via Claude API
- **Comparaison N vs N-1** et M vs M-1
- **Authentification** avec gestion des rôles et droits par vision
- **Panel admin** : CRUD utilisateurs, reset mot de passe, droits d'accès
- **Toggle démo** : activer/désactiver les données de démonstration
- **Export CSV**
- **Base de données** : localStorage (par défaut) ou Firebase Firestore

---

## 📁 Structure du projet

```
cockpit-bu/
├── public/
│   └── index.html      ← Application complète (tout-en-un)
├── .gitignore
├── netlify.toml         ← Config Netlify
├── package.json
└── README.md
```

L'application est 100% front-end, aucun serveur nécessaire.

---

## 🛠 Technologies

- React 18 (CDN)
- Recharts (graphiques)
- Papaparse (CSV)
- JSZip (lecture XLSX)
- Firebase Firestore (optionnel)
- Claude API (analyse IA)
