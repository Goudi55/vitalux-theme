# Vitalux — Thème Shopify COD

Thème Shopify minimaliste, ultra-optimisé pour la conversion COD (Cash on Delivery) sur le marché francophone (FR / Maroc / Algérie / Tunisie). Compatible **EasySell COD app**. Trafic principal : Facebook & TikTok Ads (mobile 80%+).

## Philosophie

Ce thème **n'est pas un thème e-commerce classique**. C'est un thème **landing-page-only** :

- 3 landing pages produit auto-suffisantes (Magnésium, Moringa, Betterave)
- Aucun header/footer global, aucune navigation, aucun panier classique
- Tout est inline dans chaque section (CSS + HTML + JS) pour la vitesse
- Pas de Google Fonts, pas de librairies externes
- Mobile-first : prix visible sans scroller, sticky CTA en bas

## Structure des fichiers

```
vitalux-theme/
├── layout/theme.liquid                    # Wrapper minimal
├── config/
│   ├── settings_schema.json               # Réglages thème (logo, téléphone, couleurs)
│   └── settings_data.json                 # Valeurs par défaut
├── locales/fr.default.json                # Traductions FR
├── sections/
│   ├── product-landing-magnesium.liquid   # Landing Magnésium (Navy + Or)
│   ├── product-landing-moringa.liquid     # Landing Moringa (Émeraude + Or)
│   └── product-landing-beetroot.liquid    # Landing Betterave (Bordeaux + Or)
├── templates/
│   ├── index.liquid                       # Hub d'entrée (3 produits)
│   ├── product.liquid                     # Fallback produit générique
│   ├── product.magnesium.liquid           # Template Magnésium
│   ├── product.moringa.liquid             # Template Moringa
│   ├── product.beetroot.liquid            # Template Betterave
│   ├── cart.liquid                        # Fallback panier (EasySell intercepte)
│   └── 404.liquid
└── README.md
```

## Installation

### 1. Préparer le zip

```bash
cd /Users/mac/vitalux-theme
zip -r vitalux-theme.zip . -x "*.DS_Store" "README.md"
```

### 2. Uploader sur Shopify

1. Admin Shopify → **Boutique en ligne → Thèmes**
2. **Ajouter un thème → Importer un fichier zip**
3. Choisir `vitalux-theme.zip`
4. Une fois importé : **Actions → Publier**

### 3. Créer les 3 produits

Dans **Produits → Ajouter un produit**, crée :

| Produit       | Handle (slug)  | Template à assigner    |
|---------------|----------------|------------------------|
| Magnésium     | `magnesium`    | `product.magnesium`    |
| Moringa       | `moringa`      | `product.moringa`      |
| Betterave     | `betterave`    | `product.beetroot`     |

Pour chaque produit, dans la section **Theme template** (colonne droite), sélectionne le template correspondant.

### 4. Configurer le téléphone et le logo

**Personnaliser → Réglages du thème** :
- **Identité** : logo, nom de marque, numéro de téléphone service client
- **Couleurs** : ajuste si besoin

## Configuration EasySell COD

### Installation

1. Shopify App Store → installer **EasySell COD Form & Upsells**
2. Activer EasySell

### Form Builder — Design dark premium

Dans **EasySell → Form Builder**, configure :

- **Template** : Midnight Luxe (ou custom)
- **Background** : `#06101f` (assorti aux landings)
- **Text** : `#ffffff`
- **Border** : `#1a3a68`
- **Input bg** : `#0a1628`
- **Input border** : `#1a3a68`
- **Button bg** : gradient or `#c9a96e → #e8c97e`
- **Button text** : `#0a1628`

### Quantity Offers (offres de quantité)

Dans **EasySell → Quantity Offers**, pour chaque produit :

| Offre        | Quantité | Label                          | Pré-sélectionné | Badge          |
|--------------|----------|--------------------------------|-----------------|----------------|
| Offre 1      | 1        | 1 Flacon — Cure 1 mois         | Non             | —              |
| Offre 2      | 2        | 2 Flacons — Cure 2 mois        | **OUI**         | POPULAIRE (or) |
| Offre 3      | 3        | 3 Flacons — Cure 3 mois        | Non             | MAX VALUE (vert)|

### Form Fields (champs)

Champs minimum à activer :
- Prénom + Nom (obligatoires)
- Téléphone (obligatoire, validation par pays)
- Ville (dropdown ou texte selon pays)
- Adresse complète
- Notes (optionnel)

### Pays

Activer : **France, Maroc, Algérie, Tunisie** (selon ton scope de livraison).

## Test avant lancement

Checklist mobile (le plus important — 80% du trafic) :

- [ ] Ouvrir chaque landing sur mobile : `/products/magnesium`, `/products/moringa`, `/products/betterave`
- [ ] Le **prix est visible sans scroller** (au-dessus du fold)
- [ ] Le bouton CTA principal fonctionne (ouvre EasySell ou scroll vers le form)
- [ ] La sticky bar du bas apparaît au scroll
- [ ] Le formulaire EasySell s'affiche bien (fond sombre, texte lisible)
- [ ] Le numéro de téléphone en bas est cliquable
- [ ] La FAQ s'ouvre/ferme correctement
- [ ] Aucun header/footer du thème ne traîne en haut/bas
- [ ] Aucun lien de navigation visible (sauf logo non cliquable)
- [ ] Test PageSpeed : score > 80 mobile

## Pourquoi pas de Google Fonts ?

Le marché cible (Maghreb, certaines zones FR) a une connexion mobile lente. Google Fonts ajoute 1-3 secondes au First Paint. On utilise les system fonts (SF Pro / Segoe UI / Roboto) — toujours nets, instantanés, zéro requête.

## Modifier le copy

Tout le contenu texte est dans les 3 fichiers `sections/product-landing-*.liquid`. Cherche le H1, les bénéfices, témoignages, FAQ — modifie directement dans le code Shopify (**Modifier le code** dans l'admin).

## Codes couleur des 3 landings

| Produit   | Fond        | Accent       | CTA principal       |
|-----------|-------------|--------------|---------------------|
| Magnésium | `#0a1628` (navy) | `#c9a96e` (or) | gradient or         |
| Moringa   | `#0d1f15` (émeraude foncé) | `#d4af37` (or) | `#22c55e` (vert)    |
| Betterave | `#1a0612` (bordeaux foncé) | `#e8b34a` (or) | `#dc2655` (rouge)   |

## Support

- Téléphone service client : à configurer dans Réglages → Identité
- Toute modification de design : édite directement les fichiers `sections/*.liquid`

---

**Vitalux** © {{ year }} — Santé naturelle premium.
