# Détective Biggle — consignes pour les agents

Application Angular 19 (composants standalone). Voir `README.md` pour le
contenu du dépôt et `ROADMAP.md` pour le travail en cours.

## Commandes

```sh
npm install          # dépendances (npm install <paquet> pour en ajouter une)
npm start            # serveur de développement sur http://localhost:4200/
npm run build        # build de production
npm test             # tests unitaires en watch (Karma + Jasmine, Chrome)
npm run test:ci      # tests unitaires une fois, Chrome headless
npm run typecheck    # vérification des types (code applicatif et specs)
```

Avant de pousser : `npm run typecheck` et `npm run test:ci` doivent passer.
La CI GitHub Actions les lance sur chaque pull request.

## Tests

- Un fichier `*.spec.ts` à côté du fichier testé
  (`episode.service.ts` → `episode.service.spec.ts`).
- Jasmine pour les assertions et les espions, `TestBed` pour les services et
  les composants.
- Tester le comportement observable (DOM rendu, navigation, valeurs émises),
  pas les détails d'implémentation.
- Les dépendances externes (lecteur Vimeo, `Audio`, `fetch`, `LiveAnnouncer`)
  sont remplacées par des doublures : aucun test ne joue de son ni n'appelle
  le réseau.

## Développement en TDD

Toute nouvelle fonctionnalité ou correction de bug commence par un test qui
échoue :

1. **Rouge** — écrire un seul test pour le comportement visé et le voir
   échouer pour la bonne raison.
2. **Vert** — écrire l'implémentation minimale qui le fait passer.
3. **Refactor** — améliorer la structure, la suite restant verte.

Pour le code existant non couvert, écrire d'abord des tests de
caractérisation qui figent le comportement actuel avant de le modifier.

## Accessibilité

L'application doit rester utilisable au clavier et avec un lecteur d'écran.
Règles reprises de `.cursor/rules/`.

### HTML

Formulaires :

- L'ordre du focus est cohérent pour l'utilisateur.
- Seuls les éléments interactifs prennent le focus.
- Chaque champ est lié à son libellé.
- Chaque champ est lié à son message d'erreur par `aria-describedby`.
- Chaque partie d'un formulaire est regroupée dans un `fieldset` avec une
  `legend`.
- Un `fieldset` contenant un champ obligatoire a `aria-required="true"`.
- L'attribut `aria-checked` des cases à cocher et boutons radio est renseigné.

Étapes :

- Chaque `fieldset` d'un formulaire indique l'étape (par exemple
  « Question 1 sur 3 »).

Lecteurs d'écran :

- L'application est compatible avec NVDA, VoiceOver et TalkBack.
- Les éléments décoratifs sont ignorés par les lecteurs d'écran.
- Les images porteuses de sens ont un attribut `alt`.

### SCSS

- Les éléments interactifs ont un contour de focus d'un contraste d'au moins
  3:1.

### TypeScript

- Quand une partie d'un formulaire est masquée et qu'une autre s'affiche, le
  focus est placé sur le premier élément de la partie affichée.
