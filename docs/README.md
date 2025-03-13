# Structure du projet Speech2Health (s2h-open-source)

## 1. Organisation générale

Le projet Speech2Health est structuré suivant une architecture modulaire permettant une évolution progressive des fonctionnalités, tout en maintenant une cohérence visuelle et fonctionnelle.

### 1.1 Arborescence des fichiers

```
s2h-opensource/
├── assets/
│   ├── images/             # Images et icônes du site
│   ├── fonts/              # Polices personnalisées
│   └── js/                 # Scripts JavaScript
│       ├── components/     # Composants JS réutilisables
│       └── pages/          # Scripts spécifiques à chaque page
├── css/
│   ├── s2h-styles.css      # Fichier CSS principal (BEM)
│   └── vendors/            # CSS de bibliothèques tierces
├── pages/
│   ├── explorer/           # Pages du module Explorer
│   │   ├── index.html      # Page principale Explorer
│   │   ├── detail-test.html
│   │   └── resultats.html
│   ├── creer-un-test/      # Pages du module Création
│   │   ├── index.html      # Page principale Création
│   │   ├── etape-1.html
│   │   ├── etape-2.html
│   │   └── publication.html
│   ├── evaluer-et-contribuer/
│   │   ├── index.html
│   │   └── revision.html
│   ├── communaute/
│   │   ├── index.html
│   │   ├── evenements.html
│   │   └── forum.html
│   └── mon-compte/
│       ├── index.html
│       ├── profil.html
│       ├── tests.html
│       └── resultats.html
├── templates/
│   ├── header.html         # Template du header
│   ├── footer.html         # Template du footer
│   └── sidebar.html        # Template de la barre latérale
├── index.html              # Page d'accueil principale
└── README.md               # Documentation du projet
```

## 2. Architecture des pages

### 2.1 Pages principales

Le site comporte 6 sections principales accessibles depuis le header:

1. **Accueil** (`index.html`) - Présentation générale de la plateforme
   * Accessible en cliquant sur le logo
   * Vue d'ensemble des fonctionnalités
   * Sections pour chercheurs et utilisateurs

2. **Explorer** (`pages/explorer/index.html`) - Catalogue des tests disponibles
   * Filtres par catégorie, population cible, etc.
   * Vue grille/liste des tests
   * Fonctionnalités de recherche avancée

3. **Créer un test** (`pages/creer-un-test/index.html`) - Assistant de création
   * Processus étape par étape
   * Prévisualisation et validation
   * Publication et paramètres

4. **Évaluer et contribuer** (`pages/evaluer-et-contribuer/index.html`)
   * Liste des tests en attente d'évaluation
   * Formulaires de feedback
   * Historique des contributions

5. **Communauté** (`pages/communaute/index.html`)
   * Forum d'échange
   * Événements et webinaires
   * Documentation collaborative

6. **Mon compte** (`pages/mon-compte/index.html`)
   * Tableau de bord personnel
   * Gestion des tests créés
   * Historique des résultats

### 2.2 Structure de navigation

#### Header (Nouveau design)

Le header a été revu pour offrir une meilleure expérience utilisateur:

```html
<header class="s2h-header">
  <div class="s2h-container">
    <div class="s2h-header__content">
      <!-- Logo (lien vers l'accueil) -->
      <a href="/" class="s2h-logo">
        <div class="s2h-logo__icon">S2H</div>
        <span class="s2h-logo__text">Speech2Health</span>
      </a>
      
      <!-- Navigation principale -->
      <nav class="s2h-nav">
        <ul class="s2h-nav__list">
          <li class="s2h-nav__item">
            <a href="/pages/explorer/" class="s2h-nav__link">Explorer</a>
          </li>
          <li class="s2h-nav__item">
            <a href="/pages/creer-un-test/" class="s2h-nav__link">Créer un test</a>
          </li>
          <li class="s2h-nav__item">
            <a href="/pages/evaluer-et-contribuer/" class="s2h-nav__link">Évaluer & Contribuer</a>
          </li>
          <li class="s2h-nav__item">
            <a href="/pages/communaute/" class="s2h-nav__link">Communauté</a>
          </li>
        </ul>
      </nav>
      
      <!-- Actions utilisateur -->
      <div class="s2h-header__actions">
        <div class="s2h-search">
          <input type="text" class="s2h-search__input" placeholder="Rechercher...">
          <button class="s2h-search__button">
            <span class="s2h-visually-hidden">Rechercher</span>
          </button>
        </div>
        
        <div class="s2h-user-menu">
          <a href="/pages/mon-compte/" class="s2h-user-menu__trigger">
            <div class="s2h-user-menu__avatar">JD</div>
          </a>
          <!-- Menu déroulant au clic (JS) -->
        </div>
      </div>
    </div>
  </div>
</header>
```

#### Fils d'Ariane (pour la navigation hiérarchique)

Chaque sous-page inclut un fil d'Ariane pour faciliter la navigation:

```html
<div class="s2h-breadcrumb">
  <div class="s2h-container">
    <ul class="s2h-breadcrumb__list">
      <li class="s2h-breadcrumb__item">
        <a href="/" class="s2h-breadcrumb__link">Accueil</a>
      </li>
      <li class="s2h-breadcrumb__item">
        <a href="/pages/explorer/" class="s2h-breadcrumb__link">Explorer</a>
      </li>
      <li class="s2h-breadcrumb__item s2h-breadcrumb__item--current">
        Détail du test
      </li>
    </ul>
  </div>
</div>
```

### 2.3 Architecture des sous-pages

Chaque section principale possède plusieurs sous-pages organisées logiquement:

#### Explorer
- **index.html** - Vue d'ensemble des tests disponibles
- **detail-test.html** - Présentation détaillée d'un test
- **resultats.html** - Présentation des résultats d'un test effectué

#### Créer un test
- **index.html** - Point d'entrée et configuration initiale
- **etape-1.html** - Configuration des paramètres de base
- **etape-2.html** - Construction du contenu du test
- **publication.html** - Vérification et publication

#### Évaluer et contribuer
- **index.html** - Liste des tests à évaluer
- **revision.html** - Interface de révision d'un test spécifique

#### Communauté
- **index.html** - Tableau de bord communautaire
- **evenements.html** - Calendrier et détails des événements
- **forum.html** - Discussions et échanges entre utilisateurs

#### Mon compte
- **index.html** - Tableau de bord personnel
- **profil.html** - Informations et paramètres du profil
- **tests.html** - Tests créés ou en cours de création
- **resultats.html** - Historique des tests passés

## 3. Guide de style CSS (s2h-styles.css)

Le fichier `s2h-styles.css` est le cœur du système de design de Speech2Health. Il suit la méthodologie BEM (Block, Element, Modifier) pour une organisation claire et maintenable du code CSS.

### 3.1 Principes clés du fichier CSS

1. **Variables CSS** : Toutes les couleurs, espacements, tailles de police et autres propriétés réutilisables sont définies comme variables CSS dans `:root`
2. **Préfixe** : Toutes les classes utilisent le préfixe `s2h-` pour éviter les conflits avec d'autres bibliothèques
3. **Structure BEM** : Les classes suivent la structure BEM :
   - `.s2h-block` : composant autonome (ex: `.s2h-card`)
   - `.s2h-block__element` : élément qui fait partie d'un bloc (ex: `.s2h-card__title`)
   - `.s2h-block--modifier` : variante d'un bloc (ex: `.s2h-card--primary`)

### 3.2 Composants principaux

Le fichier contient des styles pour ces composants principaux :

- **Layout** : Conteneurs, grille
- **Navigation** : Header, menu, navigation, fil d'Ariane
- **Composants interactifs** : Boutons, formulaires, onglets
- **Cartes et conteneurs** : Cartes, boîtes, sections
- **Éléments d'affichage** : Badges, étiquettes, alertes, tableaux
- **Visualisations** : Graphiques, chronologies
- **Structure de page** : En-tête, pied de page

### 3.3 Classes utilitaires

Le CSS inclut un ensemble complet de classes utilitaires pour :

- Marges et paddings (ex: `.s2h-mb-lg`, `.s2h-p-sm`)
- Typographie (ex: `.s2h-font-xl`, `.s2h-font-bold`)
- Couleurs (ex: `.s2h-text-primary`, `.s2h-bg-success`)
- Flexbox (ex: `.s2h-flex`, `.s2h-items-center`)
- Bordures et arrondis (ex: `.s2h-rounded`, `.s2h-border`)
- Affichage et positionnement (ex: `.s2h-relative`, `.s2h-hidden`)

### 3.4 Responsive Design

Le design est entièrement responsive avec des points de rupture à :
- 1200px (grand écran)
- 992px (tablette paysage)
- 768px (tablette portrait)
- 576px (mobile)

Des classes spécifiques pour le responsive sont disponibles (`.s2h-grid__col--md-6`, etc.)

### 3.5 Accessibilité

Le CSS inclut des fonctionnalités d'accessibilité comme :
- Classes pour masquer visuellement du contenu (`.s2h-visually-hidden`)
- Support pour le mode contraste élevé
- Préparation pour un mode sombre futur

## 4. Bonnes pratiques de développement

### 4.1 Organisation des nouveaux fichiers

Pour ajouter de nouvelles pages:

1. Créer le fichier HTML dans le dossier correspondant à sa section
2. Utiliser les templates existants pour la structure commune
3. Respecter la convention de nommage et l'architecture des liens

### 4.2 Ajout de nouveaux composants CSS

Pour ajouter de nouveaux composants ou styles:

1. Suivre la méthodologie BEM existante
2. Utiliser les variables CSS définies dans `:root`
3. Organiser les nouveaux styles dans des sections dédiées du fichier CSS
4. Respecter le préfixe `s2h-` pour toutes les nouvelles classes

### 4.3 Gestion des ressources

- Optimiser les images avant intégration
- Privilégier les SVG pour les icônes et illustrations
- Placer les scripts JS spécifiques dans le dossier correspondant à la page

### 4.4 Intégration HTML

Pour utiliser ce système de design dans les fichiers HTML:

1. Intégrer la feuille de style dans la section `<head>`:
```html
<link rel="stylesheet" href="/css/s2h-styles.css">
```

2. Utiliser les templates pour les éléments communs:
```html
<include src="/templates/header.html"></include>
```

3. Utiliser les classes BEM dans le corps de la page:
```html
<main class="s2h-main">
  <div class="s2h-container">
    <div class="s2h-card s2h-card--primary">
      <div class="s2h-card__header">
        <h2 class="s2h-card__title">Titre de la carte</h2>
      </div>
      <div class="s2h-card__body">
        Contenu de la carte
      </div>
    </div>
  </div>
</main>
```

## 5. Évolution future

Le projet est conçu pour évoluer avec:

- Ajout de nouvelles sections et fonctionnalités
- Intégration possible d'un système de composants JavaScript
- Support multilingue
- Intégration d'API pour les fonctionnalités avancées

La structure modulaire permet d'ajouter facilement de nouvelles pages et fonctionnalités sans impacter l'existant, tout en maintenant une cohérence globale.
