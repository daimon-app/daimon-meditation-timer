# DAIMON M04 — Technical, UX, Mobile, Offline and PWA Audit

| Field | Audit record |
| --- | --- |
| Audit date | 2026-08-19 JST |
| Repository / branch | `daimon-app/daimon-meditation-timer` / `main` |
| Implementation baseline | `651e5830bc2a047b55d8c334bb1f9b14e1eec62e` |
| Canonical documentation baseline | `9cbd5b6ee53f58c06c73fe40dd8647704304843c` |
| Audit methods | Source-code inspection; local static HTTP response checks; Chromium live rendering; service worker and Cache Storage inspection; visible start/pause interaction; foreground-return simulation; Wake Lock observation. |
| Overall conclusion | **CONDITIONAL / not technically sales-ready.** Primary meditation flow is materially stronger than sleep and break flows, but unresolved timer and accessibility defects prevent a reliability-quality GO. |

## 1. Implemented product surface

| Capability | Evidence in implementation | Audit status |
| --- | --- | --- |
| Primary meditation timer | 30 seconds; 1, 3, 5, 10, 20, 25 minutes; mode-specific copy; ring progress; pause/end. | Pass for the tested primary flow. |
| Natural sound | Ocean, river, forest, rain, silent; local selection; generated-wave fallback; sleep fade. | Partial; audible output has not been verified on a device. |
| Completion sound | Synthesised bell with AudioContext resume attempt. | Partial; execution path inspected, audibility unverified. |
| Local history | Up to 50 entries in localStorage; per-entry and full deletion; `textContent` rendering. | Pass in sandbox browser for add and per-entry delete. |
| Sleep | 30/60/90/480 minutes, manual stop, sound fade. | Fail as a reliable timer because time is interval-derived. |
| Break | 5/10/15/20 minutes, next-action prompt, pause/end. | Fail as a reliable timer because time is interval-derived. |
| PWA | Manifest, standalone display, portrait orientation, two icons, SW registration, cached app shell and sounds. | Pass for registration/cache; offline launch and installed-device behavior remain partial. |

## 2. Primary timer correctness

The primary timer sets an absolute `sessionEndTime` at start and derives remaining seconds by subtracting the current `Date.now()` value. The `visibilitychange`, `focus`, and `pageshow` handlers invoke foreground recovery, recompute the remaining value, update the ring and display, and complete the session if it has expired. This architecture resists ordinary timer-interval throttling better than decrementing a counter. Runtime simulation confirmed that expiry after a foreground return produced remaining time `0`, the complete screen, and one stored history record.

> **Finding:** The primary flow may be described conservatively as “a timer that recalculates remaining time when the app becomes active again.” It must not be described as a guaranteed alarm or a guarantee that background audio will wake a locked device.

| Risk | Current mitigation | Remaining limitation | Release position |
| --- | --- | --- | --- |
| Interval drift | Absolute deadline and foreground recomputation. | Completion cannot execute while the browser process is fully suspended until the app becomes active again. | Do not promise alarm-grade notification. |
| Pause duration | Remaining milliseconds captured at pause and added to a new absolute deadline at resume. | Long-duration physical device verification has not been completed. | Accept as functional path; re-QA on mobile. |
| Wake Lock release | Released on cancel and completion; reacquired on foreground if needed. | Browser and OS can decline or release the lock. | Warn, do not guarantee. |

## 3. Break and sleep timer defects

The break flow initializes `breakRemainingSeconds` and subtracts one each `setInterval`. The sleep flow increments `sleepSeconds` once each `setInterval`. Neither flow persists an absolute deadline or recomputes from wall-clock time when visibility returns. Both will therefore under-count elapsed time if timer callbacks are delayed, throttled, or halted while backgrounded. The sleep fade schedule also derives from the same interval count.

| Defect | Code-level observation | User impact | Classification | Required remediation |
| --- | --- | --- | --- | --- |
| Break drift | `breakTick()` uses `breakRemainingSeconds--`; no `breakEndTime`; no foreground handler path. | A 5–20 minute break can finish later than intended after backgrounding. | **F-001 / TECH_FIX_REQUIRED** | Establish an absolute deadline, derive display from it, recover on visibility/focus/pageshow, and re-QA. |
| Sleep drift | `startSleep()` increments `sleepSeconds++`; no persisted/absolute sleep end time; no foreground recovery. | The selected stop time and final fade can occur late. | **F-002 / TECH_FIX_REQUIRED** | Use an absolute sleep deadline, update fade from wall-clock time, reconcile on foreground, and re-QA. |
| Inconsistent screen-lock policy | Only primary session calls `requestWakeLock()`. | Users cannot infer screen behavior consistently between modes. | `TECH_FIX_REQUIRED` if product intent is to keep screen awake; otherwise document mode-specific policy. | Define intended policy and implement or disclose it. |

## 4. Audio and device limitations

The implementation uses local MP3 files through `Audio` elements and includes a Web Audio generated-wave fallback. The completion bell is generated through oscillators. That design avoids a server dependency once cached. However, browsers may block unprompted playback, mute system output, suspend audio in background, or route sound differently by device. The sandbox cannot objectively verify human audibility.

The app already includes a useful caveat on the primary session screen: users should combine deep sessions with their phone’s standard alarm. This caveat should remain, be made more prominent on relevant modes, and be harmonized with the product and FAQ language. Claims such as “終了を確実に知らせる” or “朝まで確実に流れる” are disallowed until device-specific QA demonstrates an appropriately bounded claim.

## 5. Mobile, first-use, and accessibility audit

The CSS is mobile-centered: `.screen` uses `100dvh`, the home grid has a 380px maximum width, and core controls use broad visual regions. In the desktop browser’s live rendering, the home screen contained all principal paths without vertical scrolling. This supports a mobile-first intent but is not a substitute for 375px-wide / iOS / Android testing.

The initial screen communicates an emotionally distinct philosophy — “休むためではなく、戻るために使う。” — and makes a one-tap timer start possible. For an already-informed user this is strong. For a purchaser, it lacks explanatory onboarding, how-to-use instruction, installation guidance, data/privacy route, support route, terms, price, purchase CTA, and an explanation of the unique value of the break’s next-action design. Those are sales-web deficiencies, not proof that the timer UI is unusable.

| Area | Finding | Classification |
| --- | --- | --- |
| Timer cards | The 9 `.tool-card` controls are clickable `div` elements using inline `onclick`. | **F-003 / TECH_FIX_REQUIRED**. They lack native keyboard and button semantics. |
| Count-sound control | A clickable `div` toggles a persisted preference. | **F-003 / TECH_FIX_REQUIRED**. Same semantic/keyboard issue. |
| Buttons | Natural-sound choices, history/information controls, pause/end actions, sleep and break time choices predominantly use semantic buttons. | Positive, but inconsistent with timer cards. |
| Color/contrast | The dark, gold visual system is coherent in the rendered view. Exact WCAG contrast verification was not run. | Re-QA before an accessibility claim. |
| First-use information | App enters directly into tool selection; no technical support or policies are discoverable. | Sales/Web remediation required. |

## 6. Offline and PWA audit

The manifest reports standalone display, portrait orientation, a root start URL and scope, matching dark theme/background colors, and 192px and 512px icons. The live browser registered an active service worker. Cache `daimon-v4` contained the app shell, manifest, four audio assets, and both icons.

| PWA / offline control | Result | Evidence | Limitation |
| --- | --- | --- | --- |
| Manifest link | PASS | `index.html` links `manifest.json`; manifest properties inspected. | Actual platform install prompt not tested. |
| Service worker | PASS | Browser registration active at `http://127.0.0.1:4173/`. | Production HTTPS scope needs re-test. |
| Core cache | PASS | `daimon-v4` includes `/`, `/index.html`, `/manifest.json`, sound assets, and icons. | Cache version/update behavior needs re-test after future changes. |
| First offline load | PARTIAL | Required assets are cache-listed. | A never-before-loaded device cannot retrieve cache while offline. This normal PWA limit must be disclosed in support language. |
| Typography offline | PARTIAL | Fonts are referenced from Google Fonts but not cached by the custom service worker. | Functional fallback exists, but exact typography may differ offline. |

## 7. Data handling observation

The application stores history, the selected sound, and the count-sound preference in browser `localStorage`. Code inspection found no analytics SDK, network API, account system, database, server endpoint, or explicit third-party tracking code in the repository. It is therefore accurate only to say, subject to final deployment verification, that **the current code stores those settings and records locally in the browser and does not include a code-path for server transmission**.

That statement must not be upgraded to a general “no data collection” policy until production hosting, HTTP headers, domain analytics, payment/sales platform, customer support tooling, and any future embedded services are audited. A public privacy notice must precisely distinguish the app itself from the sales and support surfaces.

## 8. Technical release gate

| Gate | Status | Exit evidence required |
| --- | --- | --- |
| Primary timer start/pause/foreground recalculation | Conditional pass | iOS/Android installed-PWA test and longer duration test. |
| Break timer reliability | **Blocked** | Implementation corrected; background/foreground re-QA PASS. |
| Sleep timer reliability | **Blocked** | Implementation corrected; background/foreground/fade re-QA PASS. |
| Semantic access | **Blocked** | Tool cards and count control use semantic button interactions; keyboard re-QA PASS. |
| Audible notification | Partial | At least representative iOS/Android browser and installed-PWA test; bounded copy. |
| Mobile layout | Partial | 375px and real iOS/Android verification. |
| Offline | Partial | Online preload followed by explicit offline launch and sound test on production HTTPS. |
| Sales information surface | **Blocked** | LP, policy links, support, price/CTA, and owner details are live and verified. |

## 9. Audit verdict

**Verdict: CONDITIONAL — DO NOT START SALES.** The primary meditation timer and PWA cache show a credible functional core. Nevertheless, the break and sleep promises cannot presently be trusted under ordinary background conditions, semantic control defects remain, mobile/device behavior is unproven, and no sales/legal/support surface exists. These conditions require correction and documented re-QA before a commercial launch approval.
