# DAIMON — Master Record

| Field | Current canonical state |
| --- | --- |
| Product | **DAIMON — 整える**。短時間の瞑想、睡眠時の自然音、次の一手を残す休憩を、静的PWAとして提供するプロダクト。 |
| Current Stage | **Stage 2 — Initial technical QA complete; market, sales, and legal-preparation work pending** |
| Repository | `https://github.com/daimon-app/daimon-meditation-timer` |
| Branch | `main` |
| Baseline HEAD | `651e5830bc2a047b55d8c334bb1f9b14e1eec62e` (`2026-06-13T22:48:08+09:00`, `Add files via upload`) |
| Latest canonical commit | `c4c9777867236127e9e3ad909577ee533f633a91` (`docs: add M04 technical QA and release gate`; pushed to `origin/main`) |
| Latest QA | [`docs/qa/M04_QA_RESULTS_2026-08-19.md`](docs/qa/M04_QA_RESULTS_2026-08-19.md): **FAIL / technical GO blocked**. |
| Latest Audit | [`docs/audits/M04_TECHNICAL_AUDIT_2026-08-19.md`](docs/audits/M04_TECHNICAL_AUDIT_2026-08-19.md): **CONDITIONAL / do not start sales**. |
| Primary blocker | `TECH_FIX_REQUIRED`: F-001 break timer wall-clock recovery; F-002 sleep timer wall-clock recovery; F-003 semantic controls. Mobile, audible sound, explicit offline launch, and device-lock behavior also require re-QA. |
| Sales blocker | No canonical sales channel, payment setup, seller identity, business address/contact details, domain, support contact, refund policy decision, or owner-approved price exists in the repository. |
| Approval Required | Owner approval is mandatory before domain publication, terms/privacy publication with seller particulars, payment activation, pricing release, external promotion, and sales start. |
| Git status at source-of-truth initialization | Baseline working tree was clean. The current documentation set is newly authored as a separate, reviewable change set. |
| Next Action | Commit the initial technical QA/audit evidence; then conduct sourced market and competitor research to validate differentiation and price before authoring sales materials. |

## Canonical documentation map

| Record | Location | Status |
| --- | --- | --- |
| Controlling M04 specification | [`docs/specs/M04_SALES_READY_EXECUTION_SPEC.md`](docs/specs/M04_SALES_READY_EXECUTION_SPEC.md) | Saved and pushed in `be72a6c`. |
| Product and implementation specification | [`docs/specs/PRODUCT_AND_IMPLEMENTATION_SPEC.md`](docs/specs/PRODUCT_AND_IMPLEMENTATION_SPEC.md) | Saved; awaiting current evidence commit. |
| QA specification and results | [`docs/qa/M04_QA_SPEC.md`](docs/qa/M04_QA_SPEC.md), [`docs/qa/M04_QA_RESULTS_2026-08-19.md`](docs/qa/M04_QA_RESULTS_2026-08-19.md) | Saved; QA result is technical FAIL. |
| Technical and sales audit | [`docs/audits/M04_TECHNICAL_AUDIT_2026-08-19.md`](docs/audits/M04_TECHNICAL_AUDIT_2026-08-19.md) | Technical audit saved; sales audit pending. |
| Market and competitor research | `docs/research/` | Pending. |
| Decision log | [`docs/decisions/DECISION_LOG.md`](docs/decisions/DECISION_LOG.md) | D-001 through D-005 recorded. |
| Sales materials and legal publishing checklist | `docs/sales/` | Pending. |

## Operating rules

This repository is the source of truth for the M04 sales-ready work. Chat messages and unverified AI output are not release evidence. Material research claims require linked primary or authoritative sources. Technical claims require a code or runtime observation. Every release-impacting decision must appear in the Decision Log with its evidence and open assumptions.

No automated or human action may publish the app, activate payment, send marketing, or create a legally binding sales presence without the owner’s explicit approval in the relevant channel.

## Resume protocol

A future operator should read, in order: this file; the controlling M04 specification; the latest Decision Log; the latest QA result; the latest audit; and the most recent Git commit. If any of those records is absent or contradicts the repository state, treat the release as **not sales-ready** until the discrepancy is resolved and recorded.

## Status history

| Date (JST) | Event | Evidence |
| --- | --- | --- |
| 2026-08-19 | Canonical repository, `main` branch, and baseline commit were verified from GitHub and cloned for inspection. | Initial shell audit; baseline commit above. |
| 2026-08-19 | Live app load, active service worker, PWA cache contents, 30-second session start/pause, and foreground-return completion logic were observed. | [`docs/audits/INITIAL_TECHNICAL_OBSERVATIONS.md`](docs/audits/INITIAL_TECHNICAL_OBSERVATIONS.md) |
| 2026-08-19 | GitHub Source-of-Truth operating rule and M04 execution specification were saved. | `docs/specs/M04_SALES_READY_EXECUTION_SPEC.md` |
| 2026-08-19 | Initial source-of-truth documentation was committed and pushed without staging application code or unrelated files. | `be72a6cb55fc9dc7c04d652e1d54a8e2135f8e80` |
| 2026-08-19 | Initial technical QA and technical audit completed; F-001 through F-003 block technical GO. | `docs/qa/M04_QA_RESULTS_2026-08-19.md`; `docs/audits/M04_TECHNICAL_AUDIT_2026-08-19.md`; D-005 |
| 2026-08-19 | Technical QA, audit, implementation specification, and release gate were committed and pushed without application-code changes. | `c4c9777867236127e9e3ad909577ee533f633a91` |
