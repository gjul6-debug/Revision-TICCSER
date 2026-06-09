# Révision TICCSER

Site statique de révision (flashcards · quiz · tableaux) hébergé sur GitHub Pages.
Aucun backend, aucune base de données. La progression est enregistrée en local
dans le navigateur (`localStorage`).

## Fichiers à déposer dans GitHub

Tous à la **racine** du dépôt :

- `index.html` — page d'accueil / tableau de bord (CSS et JS intégrés, **autonome**)
- `revision_tuyaux_soudure.html`
- `revision_sanitaire_evacuation.html`
- `revision_cvc_complet.html`

> Le dossier `css/` n'est **plus nécessaire** : l'accueil n'en dépend plus.
> Tu peux le supprimer. Les pages de révision ont toujours leur CSS intégré.

## Structure attendue

```text
Revision-TICCSER/
├── index.html
├── revision_tuyaux_soudure.html
├── revision_sanitaire_evacuation.html
└── revision_cvc_complet.html
```

## Mise en ligne

1. Déposer les 4 fichiers à la racine du dépôt (commit + push).
2. GitHub → Settings → Pages → Source = branche principale, dossier `/ (root)`.
3. Patienter 1–2 min, puis ouvrir l'URL GitHub Pages.

## Progression et scores

- Suivi **local au navigateur** (pas de compte, pas de synchro entre appareils).
- Clés utilisées :
  - `ticcser_progress` : objet JSON `{ "fichier.html": { visited, best, last, attempts } }`
  - `ticcser_last` : dernier module ouvert (pour le bouton « Reprendre »)
- Le bouton « Réinitialiser ma progression » de l'accueil efface ces deux clés.

## Ordre des modules

Tuyaux & Soudure (Ch.1–2) → Sanitaire & Évacuation (Ch.4–10) → CVC / ECS·VMC·CETI·Solaire (Ch.11–15).
Le bouton « Module suivant » en fin de quiz suit cet ordre.

## À vérifier après mise en ligne

- Les 3 cartes ouvrent la bonne page ; le bouton « ← Accueil » revient bien.
- Finir un quiz puis recharger l'accueil → la carte passe en « Quiz fait · meilleur X% »
  et le panneau « Reprendre » apparaît.
- Fin de quiz : le bouton « Module suivant » mène au bon module (et au dernier
  module il propose « ← Tous les modules »).
- « Réinitialiser » vide bien la progression.
- Affichage mobile : cartes en 1 colonne, statistiques en 2 colonnes.
