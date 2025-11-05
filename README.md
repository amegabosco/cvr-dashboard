# CVR Dashboard 🌰

[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](https://github.com/yourusername/cvr-dashboard)
[![License](https://img.shields.io/badge/license-Proprietary-red.svg)](LICENSE)
[![Status](https://img.shields.io/badge/status-Active-success.svg)](https://github.com/yourusername/cvr-dashboard)

> Dashboard de suivi et d'analyse du Programme Communautés et Violence Reduction (CVR) - Initiative conjointe MINUSCA/UNOPS pour la réintégration communautaire en République Centrafricaine

## 📋 Table des matières

- [À propos](#à-propos)
- [Fonctionnalités](#fonctionnalités)
- [Structure du projet](#structure-du-projet)
- [Installation](#installation)
- [Utilisation](#utilisation)
- [Technologies](#technologies)
- [Documentation](#documentation)
- [Licence](#licence)

## 🎯 À propos

Le **CVR Dashboard** est une application web interactive développée pour la MINUSCA et l'UNOPS en République Centrafricaine. Elle permet de suivre en temps réel les activités, les bénéficiaires et les indicateurs de performance du programme CVR à travers :

- 📊 **Dashboard analytique** avec KPIs et graphiques interactifs
- 🗺️ **Cartographie interactive** des districts de Bangui avec Mapbox
- 📈 **Visualisations** temporelles et géographiques
- 👥 **Suivi des bénéficiaires** par district et activité

**Version actuelle** : 1.0.0 (Codename: Anacarde 🌰)

## ✨ Fonctionnalités

### Dashboard Principal
- ✅ **Modal de bienvenue** avec présentation du projet
- ✅ **Vue d'ensemble** avec statistiques principales
- ✅ **Graphiques interactifs** (Chart.js) : barres, lignes, camemberts
- ✅ **Navigation flottante** avec scroll smooth
- ✅ **Suivi temporel** du projet avec timeline et countdown
- ✅ **Pages multiples** : Vue d'ensemble, Bénéficiaires, Activités, Rapports

### Carte Interactive
- ✅ **Mapbox GL JS** pour cartographie professionnelle
- ✅ **9 districts** de Bangui (Arrondissements 1-8 + Bimbo)
- ✅ **3 centres de formation** géolocalisés
- ✅ **Panneau d'information** (250px) avec système d'onglets :
  - 📊 Statistiques (KPIs)
  - 📋 Activités en cours
  - 📈 Graphiques (Progression + Répartition H/F)
- ✅ **Recherche** de districts et centres (Geocoder)
- ✅ **Contrôles de couches** avec toggles individuels
- ✅ **Interactions** : hover, click, zoom, popup

### Design & UX
- 🎨 **Design moderne** inspiré de Kaggle
- 📱 **Responsive** : mobile, tablette, desktop
- 🌙 **Ombre portée** améliorée sur les icônes
- ⚡ **Animations fluides** et transitions
- ♿ **Accessible** avec navigation au clavier

## 📁 Structure du projet

```
DASHY/
├── dashboard.html              # Dashboard principal
├── map.html                   # Carte interactive Mapbox
├── index_.html                # Page d'accueil
├── kaggle-style.css           # Styles globaux
├── manifest.json              # Métadonnées de l'application
├── claude.md                  # Documentation mémoire Claude
├── README.md                  # Ce fichier
├── .gitignore                 # Fichiers exclus de Git
├── assetes/
│   ├── welc.jpg              # Image de bienvenue optimisée (320KB)
│   ├── welc_backup.png       # Backup original (1.5MB)
│   ├── logo.png              # Logo UNOPS
│   └── geoBoundaries-CAF-ADM3_simplified.geojson
└── map.html.backup            # Backup de la carte
```

## 🚀 Installation

### Prérequis
- Navigateur web moderne (Chrome 90+, Firefox 88+, Safari 14+, Edge 90+)
- Connexion Internet (pour CDN : Mapbox, Chart.js, Google Fonts, Tabler Icons)

### Cloner le dépôt
```bash
git clone https://github.com/yourusername/cvr-dashboard.git
cd cvr-dashboard
```

### Lancer l'application
Ouvrir simplement `dashboard.html` dans votre navigateur :

```bash
# macOS
open dashboard.html

# Linux
xdg-open dashboard.html

# Windows
start dashboard.html
```

Ou double-cliquer sur `dashboard.html` dans l'explorateur de fichiers.

## 📖 Utilisation

### Dashboard
1. Ouvrir `dashboard.html`
2. Le **modal de bienvenue** s'affiche automatiquement (cocher "Ne plus afficher" pour masquer)
3. Naviguer entre les pages avec les boutons en haut
4. Cliquer sur **"Mapping du projet"** pour accéder à la carte

### Carte Interactive
1. Ouvrir `map.html` (ou depuis le dashboard)
2. **Cliquer sur un district** pour voir ses informations
3. **Rechercher** un district ou centre avec la barre de recherche
4. **Naviguer entre les onglets** : Statistiques, Activités, Graphiques
5. **Toggle les couches** : Districts, Centres de formation

### Réinitialiser le modal de bienvenue
Si vous avez coché "Ne plus afficher" et souhaitez revoir le modal :

```javascript
// Dans la console du navigateur (F12)
localStorage.removeItem('cvr_hideWelcomeModal');
// Recharger la page (F5)
```

## 🛠️ Technologies

### Frontend
- **HTML5** / **CSS3** (Flexbox, Grid, Animations)
- **JavaScript ES6+** (Vanilla JS, no framework)

### Bibliothèques externes
- [**Chart.js**](https://www.chartjs.org/) v4.4.0 - Graphiques interactifs
- [**Mapbox GL JS**](https://docs.mapbox.com/mapbox-gl-js/) v3.0.1 - Cartographie
- [**Mapbox Geocoder**](https://github.com/mapbox/mapbox-gl-geocoder) v5.0.0 - Recherche

### Assets
- [**Tabler Icons**](https://tabler-icons.io/) - Icônes webfont
- [**Google Fonts**](https://fonts.google.com/) - Inter & Roboto Mono
- **GeoJSON** - Données géographiques CAF (ADM3)

### Color Scheme
```css
--kaggle-blue: #20BEFF
--kaggle-dark-blue: #0C7BB3
--text-primary: #1a1a1a
--text-secondary: #6c757d
```

## 📚 Documentation

### Fichiers de documentation
- **[manifest.json](manifest.json)** - Métadonnées complètes de l'application
- **[claude.md](claude.md)** - Documentation technique détaillée pour Claude AI
- **[README.md](README.md)** - Ce fichier (vue d'ensemble)

### Documentation technique
Consultez [claude.md](claude.md) pour :
- Architecture détaillée du code
- Emplacements des fonctions clés (avec numéros de ligne)
- Patterns de code importants
- Commandes de debugging
- Historique des modifications

### API Mapbox
⚠️ **Important** : Ce projet utilise Mapbox GL JS qui nécessite un token d'accès.
Le token actuel est inclus dans le code pour développement uniquement.

Pour production, créez votre propre token sur [Mapbox](https://account.mapbox.com/) :
```javascript
// Dans map.html, ligne 713
mapboxgl.accessToken = 'VOTRE_TOKEN_ICI';
```

## 🔄 Historique des versions

### v1.0.0 - Anacarde 🌰 (2025-11-05)
- ✅ Modal de bienvenue avec image teintée bleue
- ✅ Optimisation image welc.png (1.5MB → 320KB)
- ✅ Redesign panneau districts (250px max height)
- ✅ Système d'onglets (Statistiques, Activités, Graphiques)
- ✅ Amélioration ombre portée sur icônes carte
- ✅ Bouton "Mapping" lié à map.html
- ✅ Documentation complète (manifest.json, claude.md)
- ✅ Repository Git + Push GitHub

## 👥 Contributeurs

**Organisation** : UNOPS / MINUSCA
**Développement** : Projet interne UNOPS République Centrafricaine
**AI Assistant** : Claude (Anthropic) - Documentation & Code Review

## 📄 Licence

**Proprietary - UNOPS/MINUSCA**
Confidentialité : Internal Use Only

Ce projet est la propriété de l'UNOPS et de la MINUSCA. Toute reproduction, distribution ou utilisation non autorisée est strictement interdite.

## 📞 Contact & Support

**Email** : cvr-rca@unops.org
**Localisation** : Bangui, République Centrafricaine
**Organisation** : United Nations Office for Project Services (UNOPS)

---

**Développé avec ❤️ pour la paix et la réintégration communautaire en RCA**

🌍 MINUSCA | 🇺🇳 UNOPS | 🇨🇫 République Centrafricaine
