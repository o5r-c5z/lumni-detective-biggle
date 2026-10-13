# Roadmap — Détective Biggle

Objectif : couvrir le code existant par des tests unitaires pour détecter les
régressions, avant d'en dériver Don Quijote (`o5r-c5z/lumni-don-quijote`).

## 1. Infrastructure de tests

- [x] Script npm `test:ci` : `ng test --watch=false --browsers=ChromeHeadless`
- [x] Script npm `typecheck` : `tsc --noEmit` sur `tsconfig.app.json` puis
      `tsconfig.spec.json`
- [x] Premier spec trivial pour que `ng test` ne plante plus (TS18003)
- [x] `AGENTS.md` : commandes, convention `*.spec.ts`, TDD, règles
      d'accessibilité reprises de `.cursor/rules/`
- [x] CI GitHub Actions : tests + vérification des types sur chaque PR

## 2. Tests de caractérisation des services

- [ ] `EpisodeService` : épisode courant, étapes du quiz, reset
- [ ] `AudioService` : musique de fond, effets sonores, mute, volume
- [ ] `AnnouncementService`

## 3. Tests de caractérisation des composants

- [ ] `EpisodeComponent` : chargement de l'épisode, musique selon l'écran
- [ ] `EpisodeTitleScreenComponent` : liens vers l'épisode et le quiz
- [ ] `EpisodeVideoComponent` : choix de la vidéo, navigation en fin de vidéo
- [ ] `EpisodeQuizComponent` : validation, bonne / mauvaise réponse, fin du quiz
- [ ] `EpisodeCompletionComponent` : écran de fin, reset
- [ ] `AudioControlComponent` : bouton et raccourci `M`
- [ ] `NotFoundComponent`
- [ ] Routes : `:episodeNumber`, enfants, `**`

## 4. Accessibilité

- [ ] Quiz : retirer `aria-required` du `fieldset` et l'`aria-checked` statique
      des boutons radio natifs (règles d'`AGENTS.md`), une fois le quiz
      couvert par les tests de caractérisation

## 5. Documentation

- [ ] README : lancer les tests, vérifier les types, développer en TDD
