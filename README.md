# 📊 Cockpit Directeur BU — IT / Digital / Transformation

Application React de tableau de bord multi-visions avec authentification, gestion des droits, import Excel/CSV, saisie de données et analyse IA.

---

## 🚀 Déploiement sur Netlify + GitHub

### Étape 1 — Pousser sur GitHub

```bash
cd cockpit-bu
git init
git add .
git commit -m "Cockpit BU v3 - React Vite"
git branch -M main
git remote add origin https://github.com/VOTRE_USER/cockpit-bu.git
git push -u origin main
```

### Étape 2 — Déployer sur Netlify

1. Allez sur [app.netlify.com](https://app.netlify.com)
2. **Add new site → Import an existing project**
3. Connectez votre repo GitHub `cockpit-bu`
4. Configuration :
   - **Build command** : `npm install && npm run build`
   - **Publish directory** : `dist`
5. Cliquez **Deploy site**

Netlify installera les dépendances, compilera le projet, et le déploiera automatiquement.

### Étape 3 (Optionnel) — Firebase pour multi-utilisateurs

1. Créez un projet sur [console.firebase.google.com](https://console.firebase.google.com)
2. Activez **Firestore Database** → mode test
3. Enregistrez une app Web
4. Copiez les identifiants dans `src/firebase-config.js`
5. Redéployez (git push)

---

## 🔐 Connexion

| Rôle | Identifiant | Mot de passe |
|------|-------------|--------------|
| Admin | `admin` | `1317` |

L'administrateur peut créer d'autres comptes via ⚙️ Admin.

---

## 📋 Fonctionnalités

- 4 visions dashboard + vision "Autre" auto-générée
- Import Excel (.xlsx) et CSV multi-fichiers
- Configuration des colonnes (nom, type, description)
- Catégorisation automatique ou manuelle
- Gestion des fichiers importés (visualiser, modifier, supprimer)
- Saisie mensuelle (effectifs, SLA, CSAT, PM, CA)
- Analyse IA intégrée (Claude API)
- Authentification + admin panel + gestion des droits
- Comparaison N vs N-1 et M vs M-1
- Toggle démo on/off
- Guide utilisateur intégré
- Export CSV
- Persistance localStorage ou Firebase Firestore

---

## 🛠 Développement local

```bash
npm install
npm run dev
```

L'app sera disponible sur `http://localhost:5173`

---

## 📁 Structure

```
cockpit-bu/
├── public/
├── src/
│   ├── App.jsx              ← Application principale
│   ├── main.jsx             ← Point d'entrée React
│   └── firebase-config.js   ← Config Firebase (optionnel)
├── index.html               ← Template HTML
├── package.json
├── vite.config.js           ← Configuration Vite
├── netlify.toml             ← Config déploiement Netlify
└── README.md
```
