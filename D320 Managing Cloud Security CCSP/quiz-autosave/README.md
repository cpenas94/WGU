# D320 Cloud Security — Autosave Practice Quiz

A small, AI-assisted browser study tool created while preparing for **WGU D320: Managing Cloud Security**.

## Why this exists

The [WGUEXAMS Cloud Security practice quiz](https://wguexams.github.io/cloud-security/) does not retain an unfinished test across page reloads. This companion tool adds:

- Browser-based autosave and resume for unfinished attempts
- Randomized 20-, 40-, or 117-question sessions
- Flagging, question navigation, scoring, and missed-answer review
- A manual **Choose File** option if the browser blocks fetching the source question bank

## How to use

1. Download [index.html](index.html) (GitHub: **Raw** → Save As) and open it in Chrome.
2. If the quiz cannot retrieve questions automatically, visit the [original practice quiz](https://wguexams.github.io/cloud-security/), press **Ctrl+S**, and save it as **Webpage, HTML Only**.
3. Back in the autosave tool, use **Choose File** to select the downloaded original `index.html`.
4. Choose a session length and begin. Answers are saved in the browser's `localStorage` after each selection.
5. Reopen the same local HTML file and browser profile to resume.

**Note:** The question bank is **not included** in this repository. The app reads it from the original source at runtime or from a locally selected HTML file. Internet access is needed for automatic loading; browsers may block cross-origin requests from local files. A fresh question bank must be loaded each time the app opens. Avoid simultaneous tabs and private browsing for reliable progress saving.

## Attribution and scope

- Original questions and explanations: [WGUEXAMS/cloud-security](https://github.com/WGUEXAMS/cloud-security). All rights to that material remain with its creators.
- Companion autosave interface: AI-assisted adaptation developed for personal study.
- No affiliation with WGU, ISC2, or WGUEXAMS.
- This is a study aid, not an official assessment or a verified predictor of exam performance.

## Known limitations

- Questions depend on the upstream HTML structure and may stop loading if it changes.
- Saved progress is browser/profile-specific and is not synced across devices.
- The current version has not been comprehensively browser-tested.
