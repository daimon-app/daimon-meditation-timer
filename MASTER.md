# DAIMON — Master Record

| Field | Current canonical state |
| --- | --- |
| Product | **DAIMON — 整える**。短時間の瞑想、睡眠時の自然音、次の一手を残す休憩を、静的PWAとして提供するプロダクト。 |
| Current Stage | **Stage 1 — Source-of-Truth established / Technical & Sales-Readiness audit in progress** |
| Repository | `https://github.com/daimon-app/daimon-meditation-timer` |
| Branch | `main` |
| Baseline HEAD | `651e5830bc2a047b55d8c334bb1f9b14e1eec62e` (`2026-06-13T22:48:08+09:00`, `Add files via upload`) |
| Latest canonical commit | `be72a6cb55fc9dc7c04d652e1d54a8e2135f8e80` (`docs: establish M04 sales-ready source of truth`; pushed to `origin/main`) |
| Latest QA | Initial live browser check recorded in [`docs/audits/INITIAL_TECHNICAL_OBSERVATIONS.md`](docs/audits/INITIAL_TECHNICAL_OBSERVATIONS.md). Formal QA specification and result are pending creation. |
| Latest Audit | Initial code, PWA cache, and live interaction observation recorded in [`docs/audits/INITIAL_TECHNICAL_OBSERVATIONS.md`](docs/audits/INITIAL_TECHNICAL_OBSERVATIONS.md). Formal technical audit is pending. |
| Primary blocker | Technical reliability findings require full QA classification before a sales claim can be approved. |
| Sales blocker | No canonical sales channel, payment setup, seller identity, business address/contact details, domain, support contact, refund policy decision, or owner-approved price exists in the repository. |
| Approval Required | Owner approval is mandatory before domain publication, terms/privacy publication with seller particulars, payment activation, pricing release, external promotion, and sales start. |
| Git status at source-of-truth initialization | Baseline working tree was clean. The current documentation set is newly authored as a separate, reviewable change set. |
| Next Action | Complete and save the technical QA specification and results; then conduct sourced market and competitor research before authoring sales materials and final go/no-go decision. |

## Canonical documentation map

| Record | Location | Status |
| --- | --- | --- |
| Controlling M04 specification | [`docs/specs/M04_SALES_READY_EXECUTION_SPEC.md`](docs/specs/M04_SALES_READY_EXECUTION_SPEC.md) | Saved; awaiting initial commit. |
| Product and implementation specification | `docs/specs/PRODUCT_AND_IMPLEMENTATION_SPEC.md` | Pending. |
| QA specification and results | `docs/qa/` | Pending. |
| Technical and sales audit | `docs/audits/` | Pending. |
| Market and competitor research | `docs/research/` | Pending. |
| Decision log | `docs/decisions/DECISION_LOG.md` | Pending. |
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
