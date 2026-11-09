# Lamis Brain Games — Version 3.0.1 Release Candidate

**Status: Release candidate / testing build. Not yet production-certified.** This is a complete static project, ready to be tested locally or staged on GitHub Pages. It has not been published to the existing live repository.

## What's inside

- iPhone-first responsive homepage, 5 distinct category library views, and 16 individual games / modes with dedicated instructions, difficulty controls, results, and navigation.
- Sudoku: standard 9×9 grid, uniquely solvable generated puzzles, notes, hints, undo/redo, highlighting, mistake counter, timer, restart, pause, local unfinished-game recovery.
- Maze: randomized 9×9, 13×13, 17×17, 21×21 and 27×27 mazes; an exit is reachable in every generated layout; keyboard, directional pad, and pointer-swipe movement with wall collisions.
- Memory: classic matching, picture matching (emoji illustrations rather than photographs), growing sequences, pattern, number, and spatial-position recall.
- Logic: 180 question records in nine topic families with four answer options and explanations. Most are generated using varied parameterized templates, **not 180 individually authored problems**. This is an outstanding content-depth limitation.
- Visual: seven original vector-based visual shape and rotation challenge modes with interactive graphical answer buttons. They currently use original SVG shapes and rotating-arrow puzzles rather than rich animated spatial scenes; this remains a major upgrade opportunity.
- Local points, streaks, badges, per-game personal bests, daily activity record, exported/imported JSON backups.
- Manifest, offline-first service worker, app icons, self-contained assets. No external scripts, paid APIs, subscriptions or fonts.

## Try locally

Requires Python 3 or an equivalent static HTTP server. From the project folder, run:

```bash
python3 -m http.server 8080
```

Open `http://localhost:8080` in a browser. Opening `index.html` using a `file://` path will not install the offline service worker.

## Automated checks

Requires Node.js 18+:

```bash
npm test
```

This covers Sudoku uniqueness/solution consistency and random stress, maze connectedness and wall collision checks and stress, and the multiple-choice question and visual answer libraries. Additional UI interactions have been exercised in Chromium at 320px, 390px and 1280px viewport widths, with no JavaScript page errors in the exercised flows. This browser harness used locally bundled scripts because direct local network navigation was restricted in the test environment, so it is not an end-to-end test of the deployed ES modules or service worker.

## Publish to your **existing** GitHub Pages repository (only after you are happy with the tests)

1. Make a backup of current GitHub contents or a release tag.
2. Go to https://github.com/kbedoui/lamis-brain-games-
3. Upload the **contents** of this ZIP to the root of the existing publishing branch (typically `main`); do not upload a parent folder.
4. Ensure the root has `index.html`, `style.css`, `manifest.webmanifest`, `sw.js`, `js/`, `assets/` and all files. Delete old, obsolete website scripts only after checking the backup, so old code is not inadvertently still referenced.
5. Under Settings → Pages verify the deployment source is the intended branch and `/ (root)`.
6. After GitHub Pages publishes, open https://kbedoui.github.io/lamis-brain-games-/ and test at least one game in every category before replacing the existing Home Screen shortcut.

## Existing iPhone Home Screen icon and updates

1. Export your progress under Settings & data if possible (the prior version may use incompatible storage keys).
2. Open the published URL in Safari while online and reload once; give the service worker a chance to install and cache the changed files.
3. If an existing Home Screen app shows an old version, fully close it and reopen it online. If needed remove the old icon and re-add it using Safari → Share → Add to Home Screen. **Removing website data can erase saved scores, so export backups first.**
4. Disconnect Wi-Fi and mobile data and relaunch the Home Screen icon to verify offline startup. Do the same with Sudoku and Maze during play.
5. Check the PWA both portrait and landscape, swipe input, and progress after closing/reopening Safari.

## Acceptance work still needed

- Real iPhone Safari and offline lifecycle checks have **not** been performed here.
- Visual and memory challenge artwork is not yet at the full premium game depth specified in the project brief.
- More individually written, non-repeating brain teasers and a wider question format variety are needed; difficulty levels have not been formally calibrated.
- In-progress recovery currently exists for Sudoku; other games save results after completion, not partial rounds.
- Automated test success does not guarantee every navigation edge case and accessibility interaction on every phone.
- The live GitHub repository has **not** been changed.

A release candidate is intended for careful user testing, not an assertion of final acceptance.
