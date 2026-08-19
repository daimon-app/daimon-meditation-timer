# DAIMON — Decision Log

## Decision status legend

| Status | Meaning |
| --- | --- |
| `DECIDED` | Repository evidence or authoritative source supports the decision and no owner input is needed to continue. |
| `PROVISIONAL` | A working hypothesis that must not be treated as a public claim or launch approval. |
| `OWNER_REQUIRED` | Information, business choice, identity, authorization, or external account access must be supplied or approved by the owner. |
| `TECH_FIX_REQUIRED` | A code or runtime defect must be corrected and re-QA’d before a related release claim is allowed. |

## 2026-08-19 — GitHub source-of-truth rule adopted

| Field | Record |
| --- | --- |
| ID | `D-001` |
| Status | `DECIDED` |
| Decision | This repository is the canonical record for the M04 sales-ready work. Specifications, audit evidence, research, QA, sales assets, open decisions, owner requirements, and stage status must be saved here and committed in separable units. |
| Evidence | The owner explicitly required GitHub source-of-truth operation and a recoverable repository-only record. No pre-existing `MASTER.md`, `AGENTS.md`, `ZERO_SPEC.md`, README, or documentation convention was found in the baseline tracked tree. |
| Consequence | `MASTER.md` and the `docs/` canonical map were introduced. Chat-only information is non-canonical. |
| Next validation | Confirm that the initial documentation commit is narrowly staged, committed, and pushed without unrelated files. |

## 2026-08-19 — Current product framing is not a generic meditation utility

| Field | Record |
| --- | --- |
| ID | `D-002` |
| Status | `PROVISIONAL` |
| Decision | Until market research is complete, DAIMON will be evaluated as a **return-to-action timer** for moments of disruption, fatigue, and transition rather than as a broad meditation-content library. |
| Repository evidence | The home copy says “休むためではなく、戻るために使う。”; the presets are labelled “断ち切り”, “一息リセット”, “現場呼吸”, “集中戻し”, “精度回復”, “深い整え”, and “ストレス耐性”; the break flow captures a “次の一手”. |
| Limitation | This is an interpretation of current implementation and copy, not evidence that customers will pay for it or that claimed outcomes are substantiated. It must not be published as an efficacy claim. |
| Next validation | Compare the distinct job-to-be-done, product mechanisms, and price alternatives against primary competitor pages and app-store listings. |

## 2026-08-19 — No sales or publication authorization exists

| Field | Record |
| --- | --- |
| ID | `D-003` |
| Status | `OWNER_REQUIRED` |
| Decision | No public launch, pricing publication, payment activation, paid social post, or sales start may occur at this stage. |
| Repository evidence | The baseline contains no sales platform configuration, pricing, seller identity, domain configuration, support contact, payment provider, privacy policy, terms, commercial-disclosure information, or owner authorization. |
| Consequence | The release outcome cannot be `GO` until owner details and approval are supplied and the technical release gate has passed. |
| Owner inputs required | Legal seller name/entity, representative or responsible party, business address, contact method, price/tax treatment, payment methods, delivery/access method, refund/cancellation policy, applicable jurisdiction, public domain, support contact, sales channel, and approval of final public copy. |

## 2026-08-19 — Technical reliability must be release-gated

| Field | Record |
| --- | --- |
| ID | `D-004` |
| Status | `TECH_FIX_REQUIRED` (preliminary; detailed QA pending) |
| Decision | DAIMON must not make reliability claims for break or sleep countdowns until they use an absolute time basis and are re-QA’d under background/foreground conditions. |
| Code evidence | The primary session uses `sessionEndTime = Date.now() + ...` and recalculates remaining time on foreground return. The break flow decrements `breakRemainingSeconds--` each `setInterval`, and the sleep flow increments `sleepSeconds++` each `setInterval`; neither records an absolute deadline nor rehydrates on visibility return. |
| Runtime evidence | Primary session foreground-return logic was observed to recalculate to zero, show the completion screen, and save one local history entry. This observation does not validate break or sleep reliability. |
| Next validation | Formalize reproducible QA tests, run them, and capture any pass/fail results before final audit. |

## Decision ledger

| ID | Date | Status | Short decision | Canonical evidence |
| --- | --- | --- | --- | --- |
| D-001 | 2026-08-19 | DECIDED | GitHub is source of truth. | This log; M04 specification; `MASTER.md` |
| D-002 | 2026-08-19 | PROVISIONAL | Position as return-to-action, not generic meditation. | Existing UI and copy; research pending |
| D-003 | 2026-08-19 | OWNER_REQUIRED | No sales/publication authorization. | Baseline code and repository audit |
| D-004 | 2026-08-19 | TECH_FIX_REQUIRED | Break/sleep clock reliability is a release gate. | `index.html`; runtime check; QA pending |

## 2026-08-19 — Technical QA blocks a commercial release

| Field | Record |
| --- | --- |
| ID | `D-005` |
| Status | `TECH_FIX_REQUIRED` |
| Decision | A commercial `GO` is prohibited at the end of the initial technical QA. The strongest tested flow is the primary meditation timer; the break and sleep flows do not meet the same reliability standard. |
| Verified evidence | The primary 30-second flow started, paused, resumed, recalculated to expiry on foreground-return simulation, displayed completion, saved history, and acquired/released Wake Lock in the sandbox browser. PWA service worker and required caches were active. |
| Failing evidence | Break decrements a counter on interval; sleep increments a counter on interval; neither has an absolute deadline or foreground reconciliation. Timer cards and count sound use clickable `div` controls rather than semantic buttons. |
| Canonical evidence paths | `docs/qa/M04_QA_SPEC.md`, `docs/qa/M04_QA_RESULTS_2026-08-19.md`, `docs/audits/M04_TECHNICAL_AUDIT_2026-08-19.md`, `docs/specs/PRODUCT_AND_IMPLEMENTATION_SPEC.md`. |
| Consequence | Do not state or imply reliable break/sleep end timing, guaranteed background completion, guaranteed screen wake prevention, or accessible keyboard support. Do not start sales. |
| Next validation | Engineering remediation of F-001, F-002, F-003 followed by mobile device, installed-PWA, offline, audio, and screen-lock re-QA. |

| D-005 | 2026-08-19 | TECH_FIX_REQUIRED | Initial technical QA blocks commercial GO. | QA result and technical audit dated 2026-08-19 |
