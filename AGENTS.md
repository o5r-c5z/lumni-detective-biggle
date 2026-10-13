# Détective Biggle — agent instructions

Angular 19 application (standalone components). See `README.md` for the
repository contents and `ROADMAP.md` for the work in progress. The user-facing
text, `README.md` and `ROADMAP.md` are in French; this file, code, commits and
pull requests are in English.

## Commands

```sh
npm install          # dependencies (npm install <package> to add one)
npm start            # dev server on http://localhost:4200/
npm run build        # production build
npm test             # unit tests in watch mode (Karma + Jasmine, Chrome)
npm run test:ci      # unit tests once, headless Chrome
npm run typecheck    # type check (application code and specs)
```

Before pushing, `npm run typecheck` and `npm run test:ci` must pass. The
GitHub Actions CI runs both on every pull request.

## Tests

- One `*.spec.ts` file next to the file under test
  (`episode.service.ts` → `episode.service.spec.ts`).
- Jasmine for assertions and spies, `TestBed` for services and components.
- Test observable behavior (rendered DOM, navigation, emitted values), not
  implementation details.
- External dependencies (Vimeo player, `Audio`, `fetch`, `LiveAnnouncer`) are
  replaced by test doubles: no test plays a sound or hits the network.

## Test-driven development

Every new feature or bug fix starts with a failing test:

1. **Red** — write a single test for the target behavior and watch it fail
   for the right reason.
2. **Green** — write the minimal implementation that makes it pass.
3. **Refactor** — improve the structure while the suite stays green.

For existing code without tests, first write characterization tests that pin
down the current behavior, then change it.

## Accessibility

The application must stay usable with a keyboard and a screen reader. Rules
taken from `.cursor/rules/`.

### HTML

Forms:

- Focus order makes sense to the user.
- Only interactive elements take focus.
- Every input is linked to its label.
- Every input is linked to its error message through `aria-describedby`.
- Every part of a form is grouped in a `fieldset` with a `legend`.
- Required inputs carry the native `required` attribute. `aria-required` is
  only for roles that support it (for example a custom control or a
  `radiogroup`), never on a plain `fieldset`.
- Native checkboxes and radio buttons expose their checked state themselves:
  do not set `aria-checked` on them. Only a custom control (`role="checkbox"`
  or `role="radio"`) carries `aria-checked`, bound to its real state.

Steps:

- Every `fieldset` of a multi-step form states the step (for example
  "Question 1 sur 3").

Screen readers:

- The application works with NVDA, VoiceOver and TalkBack.
- Decorative elements are hidden from screen readers.
- Meaningful images have an `alt` attribute.

### SCSS

- Interactive elements have a focus outline with a contrast ratio of at
  least 3:1.

### TypeScript

- When one part of a form is hidden and another is shown, focus moves to the
  first element of the newly shown part.
