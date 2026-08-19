# DAIMON — LP Copy and Sales Flow Specification

| Field | Canonical state |
| --- | --- |
| Status | **Draft for owner review; not authorised for publication, payment, or sales.** |
| Product statement | DAIMONは、休むためではなく、次の一手へ戻るための短時間の整えタイマーである。 |
| Evidence basis | 現行ホームの「休むためではなく、戻るために使う。」、30秒からのプリセット、休憩前に記す「次の一手」、ローカル履歴。 |
| Prohibited claims | 医療・治療・診断、睡眠改善、ストレス解消、生産性向上、必ず鳴る、必ず画面が消えない、バックグラウンドで常に正確、効果保証。 |
| Price / CTA state | **No public price. No payment CTA.** D-006により現行の有料単体販売はNO GO。 |
| Sales gate | F-001〜F-003の修正と再QA、差別化された有償成果物、所有者情報、販売チャネル、法定表示、本人承認が揃うまで販売開始不可。 |

## LP narrative

### Hero

> **休むためではなく、戻るために。**
>
> 次の一手へ戻るための、30秒からの整えタイマー。

選ぶことを増やさず、今の状態に合わせて短く止まる。DAIMONは、作業・現場・会議・移動の合間に、気持ちを切り替え、次の一手を見つめ直すための小さな時間をつくる。

**Primary CTA (current pre-launch state):** `DAIMONをひらく` → `/index.html`

**Secondary CTA (only after owner approves a feedback route):** `公開のお知らせを受け取る` → owner-supplied lawful contact or approved form.

### Problem and use moments

集中が散ったとき、感情を引きずりそうなとき、休憩から動き出せないとき。大きな習慣を始める前に、まず30秒だけ使う。DAIMONは、長いコンテンツを選ぶ前の、短い戻り道として設計されている。

| Moment | Current DAIMON path | Valid wording |
| --- | --- | --- |
| 断ち切りたい | 30秒「断ち切り」 | 「30秒から始められる」 |
| ひと息入れたい | 1分「一息リセット」 | 「短い時間を選べる」 |
| 集中に戻りたい | 3分〜10分のプリセット | 「作業前後の切替に使える」 |
| 休憩から戻りたい | 次の一手を記して休憩時間を選ぶ | 「休憩後に最初にやることを残せる」※タイマー精度修正後に訴求可能 |
| 静かな音がほしい | 波・川・森・雨・無音 | 「自然音または無音を選べる」 |

### What is included in the current app

DAIMONには、30秒〜25分のプリセット、自然音または無音の選択、主セッションの一時停止、対応ブラウザでの画面消灯防止の試行、ブラウザ内の履歴、睡眠モード、次の一手を残す休憩モードがある。機能ごとの動作範囲と端末依存の制約はFAQと技術情報で明記する。

### Why DAIMON rather than another meditation timer

DAIMONは、瞑想コンテンツを探し続けるためのアプリではない。選択肢を絞り、短い時間を選び、必要なら次の一手を書き、終わったら戻る。**「整える」ことを目的にせず、戻るための余白として使う。**

この差別化は価値仮説であり、一般的な瞑想・睡眠・集中アプリより優れていることを示すものではない。販売前には、対象顧客の実利用・継続・支払意思で検証する。

### How it works

| Step | Copy |
| --- | --- |
| 1 | 今の状態に近い時間を選ぶ。30秒でもよい。 |
| 2 | 画面の言葉だけを見て、呼吸を整える。自然音も無音も選べる。 |
| 3 | 休憩なら、戻った直後にする「次の一手」を先に書いておく。 |
| 4 | 終わったら、次の一手へ戻る。 |

### Privacy-safe app explanation

現行アプリでは、選んだ音、カウント音の設定、完了した記録をこのブラウザ内に保存する実装になっている。記録はアプリ画面から削除できる。販売ページ、決済、問い合わせで扱う情報は別の方針として公開前に明示する。

### Reliability note

DAIMONはブラウザで動作する。端末の省電力設定、画面ロック、ブラウザのバックグラウンド制御、音量や出力先により、音や画面表示の挙動は変わる。深く入る時間には、必要に応じて端末標準アラームも併用する。

### CTA state by launch stage

| Stage | CTA | Permitted only when |
| --- | --- | --- |
| Current | `DAIMONをひらく` | Always; no payment or personal data collection. |
| Demand test | `公開のお知らせを受け取る` | Owner has approved a contact processor, privacy notice, consent text, and support contact. |
| Paid pilot | `内容と価格を見る` | Technical fixes/re-QA PASS; defined paid package; price/tax/payment/delivery/refund disclosures; owner approval. |
| Sale | `購入して利用を始める` | All legal, technical, commercial, and owner approval gates are GREEN. |

## Sales flow specification

| Step | Customer sees | Operator requirement | Current state |
| --- | --- | --- | --- |
| 1. Acquisition | Social/profile/QR → LP | Valid public domain, analytics decision, SNS owner approval. | Not configured. |
| 2. Understanding | Hero, use moments, included features, limitations, FAQ. | Claims must match code/QA. | Draft ready. |
| 3. App trial | `DAIMONをひらく` → static app. | Hosting, HTTPS, PWA re-QA, support route. | App exists; production hosting unknown. |
| 4. Consent / contact | Optional update registration only. | Lawful form/provider, privacy text, storage and deletion path. | Blocked by owner choice. |
| 5. Purchase | Product scope, price incl. tax, payment, delivery/access, terms, refund, seller data. | Checkout provider, legal pages, seller info, owner approval. | Not designed; no sale. |
| 6. Post-purchase | Access confirmation, support, cancellation/refund route. | Service-level owner and responder; documented policy. | Blocked by owner input. |

## Owner review questions

Before any public CTA beyond app access, the owner must answer: Who is the primary audience? What exactly is the paid deliverable beyond the free timer? Will the product be a one-time digital purchase, a subscription, a cohort, or a team/bulk offering? Which sales processor and domain will be used? Who responds to customers, and within what timeframe? Which price, tax treatment, cancellation, and refund policy will apply?

## LP implementation verification — 2026-08-19 JST

`landing/index.html` was rendered successfully from a plain static server at `/landing/`. The live page presented the intended title, hero, use moments, four-step use explanation, differentiation, device-limit notice, and two working app-access CTAs. It intentionally displayed no price, purchase, registration, checkout, or email capture control. This satisfies the current pre-launch copy goal and does **not** satisfy a sales-launch goal.

During verification, a development server configured with an SPA fallback routed the clean LP path to the root app; a plain static server served `/landing/` correctly. Production hosting must preserve static directory index handling or an equivalent explicit route before the LP can be published. This is a deployment verification requirement, not evidence of a repository code defect.

The primary LP CTA was clicked in the plain static server environment and navigated successfully to the home timer. After the home page loaded, the active service worker cache was `daimon-v5`; it contained `/landing/` and `/landing/index.html` in addition to the app shell, manifest, four sound files, and icons. The home screen also exposed the new `はじめに` link to `landing/`. The LP and bidirectional app access therefore pass the local static integration check.
