# DAIMON — Sales-Ready Audit Notes

## Source of truth

- Repository: `daimon-app/daimon-meditation-timer`
- Branch: `main`, tracking `origin/main`
- Commit inspected: `651e5830bc2a047b55d8c334bb1f9b14e1eec62e` (`2026-06-13T22:48:08+09:00`, `Add files via upload`)
- Working tree: clean at clone time.

## Initial live verification — 2026-08-19

- The app renders as a single-screen Japanese experience with preset timers, sleep mode, break mode, sound selection, local history, and an information page.
- The first-screen visual hierarchy is coherent and mobile-centered, but it contains no product explanation, install guidance, privacy link, support route, terms, price, or purchase CTA.
- On `http://127.0.0.1:4173/`, the manifest is linked and a service worker is active at the app scope.
- Cache `daimon-v4` contains the app shell, manifest, all four audio files, and both icon files. Offline caching is therefore operational in this local verification.

## Key implementation finding

- The primary session timer calculates remaining time from an absolute `Date.now()` end time and recomputes it on foreground return, which is the correct approach for timer drift mitigation.
- The break and sleep timers instead decrement one second per `setInterval`; they are likely to drift or freeze when the browser is throttled/backgrounded and need dedicated remediation before a reliability claim can be made.
- Wake Lock is requested only for the primary meditation session, not for break or sleep modes. The current UI presents a fallback warning when the API is unavailable.

## Audit status

- This is a working note, not a final release approval.
- Technical defects will be classified as `TECH_FIX_REQUIRED` in the final report in line with the requested release gate.

## Session interaction verification — 2026-08-19

A 30-second session was started through the visible home-screen card. The session screen displayed the intended mode label, countdown, guidance copy, optional natural-sound control, standard-alarm caveat, pause action, and end action. The countdown was observed at 28 seconds shortly after start and transitioned to 22 seconds with the UI state changing to `一時停止中` after the pause control was activated. The control label changed to `再開する`; the primary start/pause interaction therefore behaves correctly in the live browser check.

The design uses visible text labels for core controls, although the timer presets and count-sound setting are clickable `div` elements rather than semantic buttons. This is an accessibility and keyboard-operation defect, and the final release gate will classify it as `TECH_FIX_REQUIRED`.
