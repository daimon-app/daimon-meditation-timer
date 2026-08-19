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

## 2026-08-19 — Current paid standalone offer is not justified

| Field | Record |
| --- | --- |
| ID | `D-006` |
| Status | `NO GO` for current paid standalone sale; `CONDITIONAL` path retained for a post-remediation pilot. |
| Decision | Do not set a public price or activate sales for the current timer as a paid standalone product. |
| Market evidence | Insight Timer, Calm, MEISOON, Forest, and Focus To-Do demonstrate broad free or paid offerings in meditation, sleep, natural sound, focus timers, tasking, tracking, guidance, blocking, and offline features. The full source comparison is in `docs/research/M04_MARKET_COMPETITOR_PRICING_2026-08-19.md`. |
| Repository evidence | DAIMON’s differentiated nucleus is the “戻るため” intent and break-mode next-action capture. It does not have the content catalogue, synchronisation, reminders, app blocking, verified timer reliability, or commercial operations found in comparators. |
| Consequence | No subscription. No unsupported high-tier benchmark. Any later paid pilot must sell a clearly specified unique outcome/package rather than a generic timer. |
| Provisional price hypothesis | After technical remediation and validated demand, test a small one-time paid package in the ¥500–¥1,000 range only if it contains a clear, owner-supplied, distinctive “return-to-action” protocol or equivalent value. This is a test hypothesis, not an approved price. |
| Next validation | Define target segment and use case; test a free acquisition/activation flow; collect qualitative evidence; verify owner’s ability to supply a differentiated paid package; then re-evaluate. |

| D-006 | 2026-08-19 | NO GO / CONDITIONAL | Current paid standalone sale is not justified; retain a post-remediation pilot path. | Market research dated 2026-08-19 |

## 2026-08-19 — Pre-launch LP is implemented without a sales CTA

| Field | Record |
| --- | --- |
| ID | `D-007` |
| Status | `DECIDED` for pre-launch information surface; **not** a sales-launch approval. |
| Decision | Add a static, price-free pre-launch LP and bidirectional link between the app and LP. The only public-facing action in this build is opening the timer. |
| Evidence | `landing/index.html` rendered on a plain static server at `/landing/`. It included the supported product message, use moments, a browser/device limitation notice, and an app-access CTA. It showed no price, checkout, account creation, email capture, marketing opt-in, or purchase CTA. LP→app and app→LP were manually verified. `daimon-v5` cached the LP routes locally. |
| Claims boundary | The LP excludes efficacy, medical, sleep, alarm, and guaranteed background behavior claims. The phrase “次の一手を残す” refers to the implemented break input/return mechanism; it is not a promise of timely break completion until F-001 is fixed. |
| Deployment limitation | An SPA-fallback local development server served the root app for the clean LP path; a plain static server served `/landing/` correctly. Production hosting must be checked for correct directory-index/routing behavior. |
| Consequence | The sales-web first-use deficit is partially remediated, but F-004 is not resolved because legal pages, support, seller disclosure, price, payment, and purchase/delivery flow remain unavailable by design. |
| Next validation | Add owner-input-gated legal/support materials; then test production hosting, all links, and the final public copy. |

| D-007 | 2026-08-19 | DECIDED | Pre-launch LP and bidirectional app link implemented; no sales CTA. | `landing/index.html`; sales flow spec; local integration check |

## 2026-08-19 — Legal/commercial publication is owner-input-gated and sales remains NO GO

| Field | Record |
| --- | --- |
| ID | `D-008` |
| Status | `NO GO` for paid sale, price publication, checkout, lead collection, commercial email, and public publication of incomplete legal documents. |
| Decision | Prepare repository-owned drafts and official-source research, but do not publish legal notices with placeholder or invented information and do not start commercial operations. |
| Primary-source evidence | Consumer Affairs Agency guidance identifies key communications-sales disclosures (price, payment, provision timing, cancellation/withdrawal, seller particulars, additional charges, software environment) and final confirmation display. Its guide also addresses opt-in commercial email. Personal Information Protection Commission materials cover purposes, collection, management, outsourcing, third-party provision and personal-data incidents. See `docs/research/M04_JAPAN_ECOMMERCE_PRIVACY_LEGAL_RESEARCH_2026-08-19.md`. |
| Repository evidence | Current app code uses browser local storage/cache and has no app account, backend API, analytics SDK, payment, lead capture or support route. The pre-launch LP only opens the app. |
| Required owner inputs | Legal seller name/entity, actual operating address, reliable telephone, responsible person, support/contact owner, product/delivery model, price/tax/fees, payments, refund/cancellation rule, domain/hosting, processor/vendor list, analytics/marketing policy, and final publication approval. |
| Required external review | Japan-qualified review of the actual sales model, consumer disclosures, checkout, contract, privacy, refund/cancellation and claims. |
| Consequence | Drafts are stored but not linked from the public LP; sale and data collection remain blocked. |

| D-008 | 2026-08-19 | NO GO | Legal/commercial preparation saved; no publication or sales without owner input and professional review. | Legal/commercial audit; official-source research |

## 2026-08-19 — Final M04 sales-ready decision

| Field | Record |
| --- | --- |
| ID | `D-009` |
| Status | **FINAL NO GO** — do not start paid sales or commercial publication. |
| Decision | The product may remain a free/pre-launch evaluation build, but it must not be positioned or operated as a paid standalone product. |
| Technical reason | F-001 (break wall-clock recovery), F-002 (sleep wall-clock recovery), and F-003 (semantic keyboard/accessibility controls) remain `TECH_FIX_REQUIRED`. Mobile, audible audio, lock-screen, installed-PWA and production-offline QA are incomplete. |
| Product/market reason | Differentiation is a “戻るため” hypothesis, not validated willingness to pay; current paid product and price are not defined or approved. |
| Commercial/legal reason | Seller particulars, support, payment, delivery, refund/cancellation, checkout, vendor map, public privacy/terms/disclosure, and professional legal review are absent. |
| Positive completed work | GitHub source-of-truth system, specification, QA/audits, decision log, market/legal research, pre-launch LP, PWA LP cache, app↔LP flow, sales copy, SNS draft, and owner-input-gated legal/support drafts are saved. |
| Approval rule | Explicit owner approval is required only after all technical, commercial, legal/privacy, production and product-validation gates turn GREEN. Approval cannot cure unresolved technical or statutory requirements. |
| Next action | Assign and implement F-001–F-003; conduct device/production re-QA; then collect owner information and select a validated paid package/sales stack before requesting legal review and launch approval. |

| D-009 | 2026-08-19 | FINAL NO GO | M04 cannot enter paid sales; preserve as pre-launch/free evaluation until all gates pass. | `docs/audits/M04_FINAL_SALES_READY_AUDIT_2026-08-19.md` |
