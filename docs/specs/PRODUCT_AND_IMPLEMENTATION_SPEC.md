# DAIMON — Product and Implementation Specification

| Field | Current specification |
| --- | --- |
| Product name | DAIMON — 整える |
| Product type | Japanese-language, browser-based static PWA for short reset sessions, natural sound, sleep sound, and a break-to-next-action flow. |
| Core promise under evaluation | Help a person make a small, intentional transition back to their next action. This is a product framing, not a health or performance guarantee. |
| Target task | A person who wants a low-friction, short interval to interrupt rumination, reset attention, or return to a chosen next action without browsing a content library. |
| Platform | Static HTML/CSS/JavaScript, no app account, no server application, browser localStorage, Web Audio API, Screen Wake Lock API where available, Service Worker. |
| Release status | **Not commercially releasable yet.** See technical audit and Decision Log. |

## Product experience

The home screen presents seven timed reset sessions: 30 seconds, 1, 3, 5, 10, 20, and 25 minutes. These correspond to Japanese labels that frame the session as interruption, breathing, return to work, restored concentration, or a deeper reset. The app also offers a sleep sound flow and a break mode where the user first writes down their next action, chooses a break duration, then receives that action back at the end. A history view records completed sessions locally.

> **Product distinction to validate:** DAIMON is designed around “戻るために使う” — using a short pause to return to an intentional next action — rather than around a catalogue of guided meditation content. The break-mode next-action capture is its clearest implemented mechanism for that distinction.

## Functional requirements currently present

| ID | Function | Current implementation | Valid public wording boundary |
| --- | --- | --- | --- |
| FR-01 | Quick start | One-tap presets on home screen start a primary timed session. | “30秒から始められる” if re-QA maintains the behavior. |
| FR-02 | Primary timekeeping | Main session derives remaining time from an absolute timestamp and recovers when app becomes visible. | “アプリに戻ったときに残り時間を再計算する。” No alarm-grade guarantee. |
| FR-03 | Pause | Main and break flows show a pause/resume control. | “一時停止・再開できる。” Subject to normal browser operation. |
| FR-04 | Natural sound | Four local sound files plus silent selection; local preview; generated fallback. | “自然音を選べる。” Do not promise playback in all background states. |
| FR-05 | Completion signal | Main/break complete functions call generated finish bell. | “終了時に音を試みる。” Avoid “必ず鳴る”. |
| FR-06 | Screen wake prevention | Main session requests Screen Wake Lock when supported and displays warning if unsupported. | “対応ブラウザでは画面消灯防止を試みる。” |
| FR-07 | Sleep mode | Choose a duration or manual stop; sound fades near intended end. | No reliable deadline claim until F-002 is fixed and re-QA’d. |
| FR-08 | Break / next action | Input next action, choose break length, show next action on completion. | “休憩後の次の一手を残せる。” Reliable timer claim blocked by F-001. |
| FR-09 | History | Completed sessions are retained in browser localStorage, max 50; user can delete entries. | “このブラウザに記録を保存・削除できる。” Deployment privacy notice required. |
| FR-10 | Offline readiness | Service worker precaches app shell, local sounds, icons. | “一度開いた後は、対応ブラウザでオフライン利用を目指した設計。” Production offline re-QA required before firmer language. |

## Explicit non-features and non-claims

DAIMON is not currently a clinical meditation programme, mental-health treatment, sleep diagnosis, alarm clock, emergency notification service, medical device, or cross-device account product. It has no account sign-in, cloud backup, guided teacher audio, social sharing, biometric measurement, streak gamification, or remotely synchronised history. No product page may imply clinical, therapeutic, productivity, safety, or sleep-outcome efficacy without separately substantiated evidence and legal review.

## Data model

| Data item | Browser key / implementation | Storage location | Retention / control |
| --- | --- | --- | --- |
| Session history | `daimon_meditation_history` | User browser localStorage | Max 50 entries; individual and all-entry deletion in app. |
| Natural sound choice | `daimon_sound_type` | User browser localStorage | Overwritten by next choice; no in-app reset apart from choosing a new value. |
| Count sound choice | `daimon_count_sound` | User browser localStorage | Overwritten by toggle. |
| Next action | Runtime variable | Browser memory during break flow | Not persisted after the flow. |
| Audio files / app resources | Service Worker cache `daimon-v4` | Browser Cache Storage | Managed by service worker version; browser user can clear site data. |

No repository code currently sends these values to an application server. This observation excludes any future sales, payment, analytics, hosting, support, or third-party service layer; those must be documented independently before release.

## Technical dependencies

| Dependency | Use | Failure mode | Product requirement |
| --- | --- | --- | --- |
| Browser timers | Display and completion scheduling. | Background throttling/suspension. | Absolute-time handling required for all timed modes. |
| Web Audio API / HTML audio | Natural sound and generated signal. | Autoplay, mute, routing, background suspension. | Provide clear caveat; do not make guaranteed-audio claims. |
| Screen Wake Lock API | Attempt to keep display awake in primary session. | API absent, denied, released by OS/browser. | Provide unsupported-state guidance; no guarantee. |
| Service Worker / Cache Storage | Offline asset availability. | Uncached first visit, update/cache failure, browser storage clearing. | Test on production HTTPS; explain first-load requirement. |
| localStorage | Local preferences/history. | Cleared browser data, private browsing restrictions, quota. | Privacy notice and user-reset guidance. |
| Google Fonts | Typography. | Offline or blocked font request. | Functional fallback must remain readable. |

## Required implementation remediation before reliability marketing

| Remediation | Owner class | Reason | Required re-QA |
| --- | --- | --- | --- |
| Convert `.tool-card` and count-sound toggle to semantic buttons with keyboard behavior and accessible labels. | Engineering | F-003 accessibility defect. | Keyboard, screen-reader semantics, visual regression. |
| Give break timer an absolute deadline, foreground recovery, accurate pause/resume, and defined Wake Lock policy. | Engineering | F-001 timer reliability defect. | Background/foreground test, pause/resume, completion. |
| Give sleep timer an absolute deadline and make fade/remaining display recover from actual wall-clock time. | Engineering | F-002 timer reliability defect. | Background/foreground, fade, duration completion, manual stop. |
| Validate primary, break, sleep behavior in iOS Safari and Android Chrome, including installed-PWA and screen-lock conditions. | Engineering / QA | Sandbox is not a device-matrix substitute. | Device evidence record. |

## Commercial scope assumption

A commercial version will need a separate sales surface, an owner-approved price and channel, a payment/access model, seller information, contact route, policy documents, and a support process. None is present in the implementation. Sales materials must state what a purchaser receives, how they access it, which browser/device conditions apply, and how they obtain support or refund consideration.
