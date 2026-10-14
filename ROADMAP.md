# Roadmap — Détective Biggle

Objectif : couvrir le code existant par des tests unitaires pour détecter les
régressions, avant d'en dériver Don Quijote (`o5r-c5z/lumni-don-quijote`).

## 1. Infrastructure de tests

- [x] Script npm `test:ci` : `ng test --watch=false --browsers=ChromeHeadless`
- [x] Script npm `typecheck` : `tsc --noEmit` sur `tsconfig.app.json` puis
      `tsconfig.spec.json`
- [x] Premier spec trivial pour que `ng test` ne plante plus (TS18003)
- [x] `AGENTS.md` : commandes, convention `*.spec.ts`, TDD, renvoi vers la
      spec d'accessibilité du client (`ACCESSIBILITY.md`)
- [x] CI GitHub Actions : tests + vérification des types sur chaque PR

## 2. Tests de caractérisation des services

- [x] `EpisodeService` : épisode courant, étapes du quiz, reset
- [x] `AudioService` : musique de fond, effets sonores, mute, volume
- [x] `AnnouncementService`

## 3. Tests de caractérisation des composants

- [x] `EpisodeComponent` : chargement de l'épisode, musique selon l'écran
- [x] `EpisodeTitleScreenComponent` : liens vers l'épisode et le quiz
- [x] `EpisodeVideoComponent` : choix de la vidéo, navigation en fin de vidéo
- [x] `EpisodeQuizComponent` : validation, bonne / mauvaise réponse, fin du quiz
- [x] `EpisodeCompletionComponent` : écran de fin, reset
- [x] `AudioControlComponent` : bouton et raccourci `M`
- [x] `NotFoundComponent`
- [x] Routes : `:episodeNumber`, enfants, `**`

## 4. Documentation

- [x] README : lancer les tests, vérifier les types, développer en TDD
