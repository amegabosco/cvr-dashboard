# CVR Dashboard - Documentation Mémoire Claude

## 📋 Vue d'ensemble du projet

**Nom**: CVR Dashboard
**Version**: 1.0.0 (Codename: Anacarde 🌰)
**Organisation**: MINUSCA/UNOPS
**Objectif**: Dashboard de suivi et d'analyse du Programme Communautés et Violence Reduction en République Centrafricaine

---

## 🗂️ Structure du projet

```
DASHY/
├── dashboard.html          # Page principale avec KPIs et graphiques
├── map.html               # Cartographie interactive Mapbox
├── index_.html            # Page d'accueil
├── kaggle-style.css       # Styles globaux
├── manifest.json          # Métadonnées de l'application
├── claude.md              # Ce fichier (documentation mémoire)
├── assetes/
│   ├── welc.jpg          # Image de bienvenue optimisée (320KB)
│   ├── welc_backup.png   # Backup original (1.5MB)
│   ├── logo.png          # Logo UNOPS
│   └── geoBoundaries-CAF-ADM3_simplified.geojson  # Données géographiques
└── map.html.backup        # Backup de la carte
```

---

## 🎯 Fonctionnalités principales

### 1. **Dashboard (dashboard.html)**

#### Modal de bienvenue ✨
- **Affichage**: Automatique au premier chargement
- **Image**: `assetes/welc.jpg` avec teinte bleue (gradient overlay + mix-blend-mode)
- **Contenu**:
  - Titre: "Bienvenue au Dashboard CVR"
  - Description du programme CVR
  - 2 paragraphes explicatifs
- **Contrôles**:
  - Bouton "Commencer"
  - Checkbox "Ne plus afficher ce message" (localStorage: `cvr_hideWelcomeModal`)
  - Fermeture: Bouton / Overlay / ESC
- **Emplacement code**: Lignes 770-831 (HTML), 512-766 (CSS), 2373-2434 (JS)

#### Sections du dashboard
1. **Hero Section**: Stats principales (bénéficiaires, formations, districts)
2. **KPIs**: Indicateurs de performance
3. **Graphiques**: Chart.js (bar, line, doughnut)
4. **Navigation flottante**: Menu latéral avec scroll smooth
5. **Bouton scroll-to-top**: Retour en haut

### 2. **Carte interactive (map.html)**

#### Panneau d'information des districts 🗺️
- **Hauteur fixe**: 250px (max-height: 250px)
- **Position**: Bottom-right, 80% largeur
- **Système d'onglets** (3 tabs):
  1. **📊 Statistiques**: 4 KPIs (Bénéficiaires, Formations, Sessions, Taux)
  2. **📋 Activités**: Liste des activités en cours avec statuts
  3. **📈 Graphiques**: Progression + Répartition H/F

#### Caractéristiques carte
- **Provider**: Mapbox GL JS v3.0.1
- **Centre**: Bangui [18.5550, 4.3947]
- **Zoom**: 11
- **Districts**: 9 (Arrondissements 1-8 + Bimbo)
- **Centres de formation**: 3
  - Centre de Formation PK5 (150 places)
  - Centre Agropastoral Bimbo (200 places)
  - Centre Sensibilisation Begoua (120 places)

#### Interactions
- Clic sur district → Zoom + Panneau info
- Hover sur district → Highlight
- Recherche → Geocoder Mapbox + recherche locale
- Toggle layers → Districts / Centres de formation
- Submenu districts → Checkbox individuels

#### Emplacement code clés
- CSS panneau: Lignes 178-194
- CSS onglets: Lignes 254-295
- HTML panneau: Lignes 643-731
- JS onglets: Lignes 1350-1362
- JS affichage panneau: Lignes 1162-1267

---

## 🎨 Design System

### Couleurs principales
```css
--kaggle-blue: #20BEFF
--kaggle-dark-blue: #0C7BB3
--text-primary: #1a1a1a
--text-secondary: #6c757d
--bg-card: #ffffff
--border-light: #dee2e6
```

### Palette districts (9 couleurs)
```javascript
['#E41A1C', '#377EB8', '#4DAF4A', '#984EA3',
 '#FF7F00', '#FFFF33', '#A65628', '#F781BF', '#999999']
```

### Typographie
- **Primary**: Inter (400, 500, 600, 700)
- **Monospace**: Roboto Mono

### Icônes
- **Library**: Tabler Icons (webfont)
- **Usage**: Navigation, stats, activités

---

## 📦 Dépendances externes

### Libraries JavaScript
1. **Chart.js** v4.4.0 - Graphiques
   - CDN: `https://cdn.jsdelivr.net/npm/chart.js@4.4.0/dist/chart.umd.min.js`

2. **Mapbox GL JS** v3.0.1 - Cartographie
   - CDN: `https://api.mapbox.com/mapbox-gl-js/v3.0.1/mapbox-gl.js`
   - CSS: `https://api.mapbox.com/mapbox-gl-js/v3.0.1/mapbox-gl.css`

3. **Mapbox Geocoder** v5.0.0 - Recherche
   - CDN: `https://api.mapbox.com/mapbox-gl-js/plugins/mapbox-gl-geocoder/v5.0.0/mapbox-gl-geocoder.min.js`

### Fonts & Icons
- Google Fonts: Inter, Roboto Mono
- Tabler Icons: Latest webfont

---

## 🔧 Modifications récentes (2025-11-05)

### ✅ Navigation entre dashboard et carte
1. **Bouton "Mapping du projet"** lié à `map.html`
   - Ligne 874: `onclick="window.location.href='map.html'"`
   - Remplace la navigation interne `showPage(5)`
   - Permet d'ouvrir directement la carte interactive

### ✅ Amélioration des icônes sur la carte (map.html)
1. **Ombre portée SVG améliorée**
   - Filtre SVG personnalisé avec `feGaussianBlur` (stdDeviation: 2)
   - Offset vertical: 2px
   - Opacité: 60% pour un effet subtil
   - Lignes 984-996: Définition du filtre SVG
2. **Halo Mapbox ajouté**
   - `icon-halo-color`: rgba(0, 0, 0, 0.3)
   - `icon-halo-width`: 2px
   - `icon-halo-blur`: 3px
   - Lignes 1016-1021: Propriétés de peinture
3. **Résultat**: Icônes des centres de formation beaucoup plus lisibles sur tous les fonds

### ✅ Modal de bienvenue (dashboard.html)
1. **Création CSS complet** avec animations (fadeIn, slideUp, fadeOut)
2. **Image teintée bleue**:
   - Technique: `background gradient + mix-blend-mode: overlay + ::after overlay`
   - Conversion PNG → JPEG 75% (1.5MB → 320KB, -80%)
3. **HTML structuré**: Header + Body + Footer
4. **JavaScript complet**: localStorage, fermetures multiples (button/overlay/ESC)
5. **Suppression des 3 widgets** (highlights) pour design épuré

### ✅ Redesign panneau districts (map.html)
1. **Hauteur fixe**: 250px (au lieu de max-height dynamique)
2. **Système d'onglets**: 3 tabs fonctionnels
   - CSS: `.panel-tab`, `.tab-pane`
   - JS: Event listeners sur tabs
3. **Optimisations d'espace**:
   - Header: 40px → 36px
   - Tabs padding: 8px → 6px
   - Content padding: 12px → 10px
   - Canvas charts: 100px max-height
4. **Media queries**: Hauteur 250px maintenue sur tous breakpoints

---

## 🗺️ Données géographiques

### Districts de Bangui (9)
```javascript
const districts = [
  'Arrondissement 1', 'Arrondissement 2', 'Arrondissement 3',
  'Arrondissement 4', 'Arrondissement 5', 'Arrondissement 6',
  'Arrondissement 7', 'Arrondissement 8', 'Bimbo'
];
```

### GeoJSON
- **Fichier**: `assetes/geoBoundaries-CAF-ADM3_simplified.geojson`
- **Format**: FeatureCollection avec polygones
- **Propriétés**: shapeName, color, activities

### Données activités (simulées)
Chaque district contient:
- `beneficiaries`: Nombre de bénéficiaires
- `trainings`: Nombre de formations
- `sessions`: Nombre de sessions
- `completed`: Taux de complétion (%)
- `men`: Bénéficiaires hommes
- `women`: Bénéficiaires femmes
- `activities[]`: Liste d'activités avec statut (active/completed/pending)

---

## 🚀 Points d'entrée / URLs

### Fichiers principaux
- **Dashboard**: `file:///Users/amegabosco/Documents/Projets/unops/CVR/DASHY/dashboard.html`
- **Carte**: `file:///Users/amegabosco/Documents/Projets/unops/CVR/DASHY/map.html`
- **Index**: `file:///Users/amegabosco/Documents/Projets/unops/CVR/DASHY/index_.html`

### Commande d'ouverture
```bash
open /Users/amegabosco/Documents/Projets/unops/CVR/DASHY/dashboard.html
```

---

## 🔍 Debugging & Maintenance

### LocalStorage keys
- `cvr_hideWelcomeModal`: Boolean pour masquer le modal de bienvenue

### Reset modal de bienvenue
```javascript
// Dans la console du navigateur
localStorage.removeItem('cvr_hideWelcomeModal');
// Puis recharger: F5
```

### Vérifier état districts
```javascript
// Dans la console de map.html
console.log(window.searchableItems.districts);
console.log(window.searchableItems.centers);
```

### Structure Chart.js
```javascript
// Variables globales pour les graphiques (dans map.html)
let trainingsChart = null;
let genderChart = null;

// Destruction avant recréation
if (trainingsChart) trainingsChart.destroy();
trainingsChart = new Chart(ctx, config);
```

---

## 📊 Statistiques & Performance

### Optimisations effectuées
1. **Image welc.png**: 1.5MB → 320KB (-80%)
2. **CSS compact**: Padding réduits pour espace 250px
3. **Canvas charts**: Max-height 100px pour panneau compact
4. **Animations**: Hardware-accelerated (transform, opacity)

### Responsive breakpoints
- **Mobile**: < 768px
- **Tablet**: 769px - 1200px
- **Desktop**: > 1200px

---

## 🎓 Concepts clés à retenir

### 1. Modal de bienvenue
- ✅ Overlay avec backdrop-filter: blur
- ✅ Image teintée avec mix-blend-mode
- ✅ LocalStorage pour préférence utilisateur
- ✅ Multiples méthodes de fermeture

### 2. Panneau districts
- ✅ Hauteur fixe 250px (overflow: hidden)
- ✅ Flex layout: header + tabs + content scrollable
- ✅ Tabs avec data-attributes
- ✅ Feature state Mapbox pour hover/select

### 3. Mapbox interactions
- ✅ Click handlers: districts-fill layer
- ✅ Feature states: hover, selected
- ✅ Geocoder local + remote
- ✅ Layer controls: visibility toggle

---

## 🧩 Patterns de code importants

### Toggle onglets (map.html)
```javascript
document.querySelectorAll('.panel-tab').forEach(tab => {
  tab.addEventListener('click', (e) => {
    const targetTab = e.currentTarget.dataset.tab;

    // Remove active from all
    document.querySelectorAll('.panel-tab').forEach(t => t.classList.remove('active'));
    document.querySelectorAll('.tab-pane').forEach(pane => pane.classList.remove('active'));

    // Activate target
    e.currentTarget.classList.add('active');
    document.getElementById('tab-' + targetTab).classList.add('active');
  });
});
```

### Gestion modal (dashboard.html)
```javascript
function closeModal() {
  if (dontShowCheckbox.checked) {
    localStorage.setItem('cvr_hideWelcomeModal', 'true');
  }

  welcomeModal.style.animation = 'fadeOut 0.3s ease-out';
  setTimeout(() => {
    welcomeModal.classList.add('hidden');
    welcomeModal.style.animation = '';
  }, 300);
}
```

### Feature state Mapbox (map.html)
```javascript
// Set hover state
map.setFeatureState(
  { source: 'districts', id: hoveredDistrictId },
  { hover: true }
);

// CSS styling based on feature-state
'fill-opacity': [
  'case',
  ['boolean', ['feature-state', 'hover'], false], 0.3,
  ['boolean', ['feature-state', 'selected'], false], 0.5,
  0.15
]
```

---

## 🔮 Suggestions d'amélioration futures

### Fonctionnalités
- [ ] Export PDF des rapports
- [ ] Filtres temporels interactifs
- [ ] Authentification utilisateurs
- [ ] API backend pour données réelles
- [ ] Mode sombre (dark mode)
- [ ] Notifications en temps réel
- [ ] Comparaison multi-districts

### Technique
- [ ] Build process (Webpack/Vite)
- [ ] TypeScript pour type safety
- [ ] Tests unitaires (Jest)
- [ ] CI/CD pipeline
- [ ] Progressive Web App (PWA)
- [ ] Offline support (Service Worker)

### UX
- [ ] Tutoriel interactif (onboarding)
- [ ] Tooltips contextuels
- [ ] Animations micro-interactions
- [ ] Accessibilité WCAG 2.1 AA
- [ ] Multi-langue (FR/EN)

---

## 📞 Contact & Support

**Organisation**: UNOPS/MINUSCA
**Email**: cvr-rca@unops.org
**Localisation**: Bangui, République Centrafricaine
**Confidentialité**: Internal Use Only

---

## 📝 Notes de développement

### Conventions de code
- Indentation: 2 spaces
- Quotes: Single quotes pour JS, double pour HTML
- Naming: camelCase JS, kebab-case CSS
- Comments: Français pour explications métier, Anglais pour code

### Git (si utilisé)
```bash
# Branches suggérées
main          # Production
develop       # Développement
feature/*     # Nouvelles fonctionnalités
hotfix/*      # Corrections urgentes
```

### Backups importants
- `map.html.backup` - Version avant redesign panneau
- `assetes/welc_backup.png` - Image originale avant optimisation

---

**Dernière mise à jour**: 2025-11-05
**Version Claude Code**: Sonnet 4.5
**Généré par**: Claude (Anthropic)
