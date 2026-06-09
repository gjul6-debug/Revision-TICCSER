# Révision TICCSER

Site de révision pour la formation **TICCSER** (CVC / plomberie) : flashcards pour
mémoriser, quiz pour tester, tableaux pour retrouver une valeur rapidement.

Site **statique** : pas de backend, pas de base de données, pas de framework.
Hébergé sur **GitHub Pages**. La progression est enregistrée dans le navigateur
de l'utilisateur (`localStorage`).

> Support de révision collaboratif. Les contenus sont organisés par thèmes et
> restent des supports de révision, sans recopier intégralement des documents protégés.

---

## Modules

| Ordre | Module | Chapitres | Fichier |
|------:|--------|-----------|---------|
| 1 | Tuyaux & Soudure | Ch.1–2 | `revision_tuyaux_soudure.html` |
| 2 | Sanitaire & Évacuation | Ch.4–10 | `revision_sanitaire_evacuation.html` |
| 3 | CVC — ECS · VMC · CETI · Solaire | Ch.11–15 | `revision_cvc_complet.html` |

L'accueil (`index.html`) sert de tableau de bord : modules disponibles, modules
commencés, quiz faits, score moyen, et un bouton « Reprendre » vers le dernier
module ouvert.

---

## Utilisation

1. Ouvrir l'accueil et choisir un module.
2. Dans un module, trois onglets : **Flashcards**, **Quiz**, **Tableau**.
3. Terminer un quiz enregistre le score ; l'accueil affiche alors « Quiz fait · meilleur X% ».
4. En fin de quiz, le bouton **« Module suivant »** enchaîne dans l'ordre ci-dessus.
5. Le bouton **« Réinitialiser ma progression »** (accueil) efface les données locales.

La progression est **locale au navigateur** : pas de compte, pas de synchronisation
entre appareils. Vider le cache ou changer de navigateur remet les scores à zéro.

---

## Structure du dépôt

Tous les fichiers sont à la **racine** :

```text
Revision-TICCSER/
├── index.html                          # accueil / tableau de bord (CSS + JS intégrés)
├── revision_tuyaux_soudure.html        # module 1
├── revision_sanitaire_evacuation.html  # module 2
├── revision_cvc_complet.html           # module 3
├── README.md
└── README_INSTALLATION.md              # mémo d'installation (optionnel)
```

Chaque page est **autonome** (CSS et JavaScript intégrés). Aucun dossier `css/`
n'est requis.

---

## Données enregistrées (`localStorage`)

| Clé | Contenu |
|-----|---------|
| `ticcser_progress` | `{ "fichier.html": { "visited": true, "best": 90, "last": 70, "attempts": 3 } }` |
| `ticcser_last` | dernier module ouvert (pour le bouton « Reprendre ») |

`visited` = module ouvert au moins une fois ; `best` = meilleur score (%) ;
`last` = dernier score ; `attempts` = nombre de quiz terminés.

---

## Mise en ligne (GitHub Pages)

1. Déposer tous les fichiers à la racine du dépôt (commit + push).
2. **Settings → Pages → Source** : branche principale, dossier `/ (root)`.
3. Attendre 1–2 min, puis ouvrir l'URL GitHub Pages.

---

## Ajouter un nouveau module

1. **Créer la page** `revision_<nom>.html` (sur le modèle d'une page existante :
   flashcards / quiz / tableau, CSS et JS intégrés). Conserver les identifiants
   `#quizResult`, `#rBig` et la fonction `showResult()` : le suivi de score s'y appuie.
2. **Ajouter la carte** dans `index.html` (section `cards-grid`) en copiant un bloc
   `<a class="module-card …">` existant, avec son `data-module="revision_<nom>.html"`
   et une classe couleur (`card-tuyaux`, `card-sanitaire`, `card-cvc`, ou une nouvelle).
3. **Mettre à jour l'ordre** dans le script de suivi présent **en bas de chaque page
   de révision** : ajouter le fichier dans le tableau `ORDER` et son libellé dans
   `LABELS`. C'est ce qui pilote le bouton « Module suivant ».

> ⚠️ Point de maintenance : le tableau `ORDER` est dupliqué dans chaque page de
> révision. Si tu ajoutes un module, pense à mettre à jour `ORDER`/`LABELS` dans
> **toutes** les pages, sinon l'enchaînement « Module suivant » sera incomplet.

---

## Règle de contenu

Ne pas modifier le contenu pédagogique (questions, réponses, cours, valeurs
techniques, explications). Les évolutions de présentation (UI / UX, navigation,
score) ne touchent jamais au fond.

---

GAUTIER ENERGIES · mémo de révision interactif · HTML statique sur GitHub Pages.
