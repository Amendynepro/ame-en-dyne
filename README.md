# Les Mains d'Âme En Dyne — Guide de gestion

## 📁 Structure du projet

```
mains-dame-en-dyne/
├── index.html              ← Site principal
├── vercel.json             ← Config déploiement Vercel
├── README.md               ← Ce fichier
├── data/
│   └── products.json       ← Liste des produits (Snipcart)
├── pages/
│   └── mentions-legales.html
└── assets/                 ← À créer — photos et images
    ├── amandyne.jpg        ← Photo d'Amandyne (section À propos)
    ├── huile-essentielle.jpg
    ├── cristal-quartz.jpg
    └── bon-cadeau.jpg
```

---

## 🚀 Mise en ligne (Vercel)

1. Créer un compte sur vercel.com avec l'email d'Amandyne
2. "Add New Project" → importer le repo GitHub
3. Vercel détecte automatiquement les fichiers statiques
4. Chaque `git push` redéploie le site automatiquement

---

## 🛒 Activer le shop (Snipcart)

### Étape 1 — Créer le compte Snipcart
1. Aller sur **app.snipcart.com**
2. Créer un compte avec l'email d'Amandyne
3. Connecter à **Stripe** (aller dans Settings → Payment)
4. Récupérer la clé publique : **Settings → API Keys → Public API Key**

### Étape 2 — Coller la clé dans index.html
Chercher dans index.html :
```html
data-api-key="YOUR_SNIPCART_PUBLIC_KEY"
```
Remplacer `YOUR_SNIPCART_PUBLIC_KEY` par la vraie clé.

### Étape 3 — Ajouter des produits
Modifier `data/products.json` pour ajouter/modifier des produits.
Chaque produit dans le JSON doit correspondre aux `data-item-id` dans index.html.

---

## 📅 Activer les réservations (Cal.com)

### Étape 1 — Créer le compte Cal.com
1. Aller sur **cal.com**
2. Créer un compte avec l'email d'Amandyne
3. Créer un "Event type" pour chaque soin :
   - Consultation Magnétisme — 60 min
   - Consultation Libération Émotionnelle — 60 min
4. Configurer les disponibilités (jours et horaires)
5. Récupérer le lien de profil (ex: `amandyne-mains-dame`)

### Étape 2 — Activer dans index.html
1. Supprimer le bloc `<div class="cal-placeholder" ...>`
2. Décommenter le bloc `data-cal-link="..."` et remplacer par le vrai lien
3. Décommenter le script Cal.com en bas de page
4. Remplacer `VOTRE_NOM_CAL` par le vrai username

---

## 📸 Ajouter la photo d'Amandyne

1. Créer un dossier `assets/` à la racine du projet
2. Y placer la photo nommée `amandyne.jpg` (format recommandé : 600×800px)
3. Dans index.html, section "À propos", remplacer :
```html
<div class="about-initials">A</div>
```
Par :
```html
<img src="/assets/amandyne.jpg" alt="Amandyne" class="about-photo">
```

---

## ✏️ Modifier les informations

### Changer un prix
Dans `index.html`, chercher le soin concerné et modifier :
- Le texte affiché : `<div class="service-price">XX €`
- Le prix Snipcart : `data-item-price="XX.00"`
- Le JSON : `data/products.json`

### Changer les horaires ou la localisation
Dans `index.html`, chercher la section `res-stats` et modifier les valeurs.

### Changer l'email de contact
Chercher `Amendynepro@gmail.com` et remplacer par le vrai email.

---

## 🔒 Mentions légales (obligatoire)

Le fichier `pages/mentions-legales.html` contient les mentions légales.
**Compléter les champs marqués [À compléter]** :
- Nom complet d'Amandyne
- Statut juridique (auto-entrepreneur, etc.)
- Numéro SIRET (après immatriculation)

---

## 💰 Récapitulatif des coûts

| Service | Coût |
|---------|------|
| Vercel (hébergement) | **Gratuit** |
| Cal.com (réservations) | **Gratuit** |
| Snipcart (panier) | **Gratuit** jusqu'à 500€/mois de ventes, puis 2% |
| Stripe (paiements) | **1,5% + 0,25€** par transaction |
| Nom de domaine .fr | **~7€/an** (OVH ou Gandi) |

**Total fixe : ~7€/an** + commissions uniquement sur les ventes
