# MANUS M04 — 瞑想タイマー SALES READY EXECUTION SPEC

| 項目 | 正本内容 |
| --- | --- |
| Product | DAIMON — 整える（瞑想・整え・睡眠・休憩タイマー） |
| Repository | `daimon-app/daimon-meditation-timer` |
| Source of Truth | GitHub上の当該リポジトリ。作業状況、根拠、判断、次工程は必ずリポジトリ内の文書から復元できる状態にする。 |
| Initial branch | `main` |
| Initial HEAD | `651e5830bc2a047b55d8c334bb1f9b14e1eec62e` |
| Initial stage | GitHub正本確認済み。販売READY施工・監査を開始。 |
| Delivery boundary | 販売・公開を実行する直前まで自走し、公開、決済開始、販売開始など不可逆な対外実行は本人承認を得る。 |

## 1. 受領した販売READY施工指示

本施工の目的は、瞑想タイマーを独立商品として販売可能な状態まで完成させることである。過去の会話を完成根拠にせず、作業開始時にGitHub正本、Repository、branch、commit、実コード、実画面、PWA状態を確認する。実装・画面・PWAを実査した後に、公開・販売開始直前まで施工する。

監査と施工の対象には、タイマー精度、開始・停止、バックグラウンド挙動、音、モバイル、画面消灯防止関連、オフライン、PWA、初回UX、データ取扱い、市場、競合、差別化、価格、商品説明、LP、FAQ、privacy、規約、特商法等、問い合わせ、返金、SNS、販売導線、最終監査を含める。コード問題は最終的に `TECH_FIX_REQUIRED` として明示する。販売・Web側の問題は、既存実装や安全境界を壊さない範囲で可能な限り施工する。

商品設計では、無料瞑想タイマーが大量に存在することを前提に「なぜこの商品を買うのか」を実装済み価値から明確にする。差別化が成立しなければ、無理にGOを出さず `CONDITIONAL` または `NO GO` とする。

最終成果物は **MEDITATION TIMER SALES READY REPORT** とし、少なくともRepository、Commit、Core QA、Mobile、Offline、PWA、Differentiation、Market、Price、LP、Legal、Privacy、SNS、Final Audit、Technical Fix Required、Owner Info Required、SALES READY、本人承認 Required、Next Actionを明記する。

## 2. GitHub Source-of-Truth 必須ルール

本施工に関する情報をChat内だけに残してはならない。施工開始から販売READYまでの証拠をGitHubへ継続保存する。正本化する対象には、設計施工仕様指示書、商品仕様、SALES READY要件、実装仕様、修正指示、AIへの施工指示、市場・競合調査結果、Manus調査・施工結果、Claudeレビュー・監査結果、Gemini調査結果、Codex施工結果、QA仕様、QA結果、FAIL内容、修正履歴、再QA結果、販売監査全文、GO / CONDITIONAL / NO GO判定、Decision Log、本人承認待ち、販売者情報待ち、現在Stage、次の一手を含める。

既存Repositoryの `MASTER.md`、`AGENTS.md`、`ZERO_SPEC.md` 等がある場合はその規則を優先する。既存の正本規則がない場合は、`docs/specs/` を仕様書、`docs/audits/` を監査全文、`docs/research/` を市場・競合調査、`docs/qa/` をQA仕様・結果、`docs/decisions/` をDecision Log、`docs/sales/` を販売仕様・SALES READY資料として使用する。

施工状態が変わるたびに、リポジトリ上で少なくともProduct、Current Stage、Repository、Branch、HEAD、Latest QA、Latest Audit、Blockers、Approval Required、Next Actionを復元できるよう `MASTER.md` を更新する。AIの回答は無条件に事実認定せず、実コード、実画面、一次情報、QAとの照合結果をDecision Logに残す。

Git運用では、既存未コミット作業を勝手に巻き込まず、`git add .`、他施工のdiscard、`reset --hard`、force push、無関係な変更のcommitを禁止する。安全にcommit可能なら正本更新を施工単位でcommitする。安全な分離ができない場合は正本ファイルを作成して `GIT_COMMIT_HOLD` と明記し、理由を記録する。

完了条件は販売READYだけではない。商品施工完了、QA完了、最終監査完了、GitHub正本更新、施工仕様書保存、Decision Log更新、HEAD / branch / commit記録、次工程記録をすべて満たして初めて完了とする。

## 3. 正本ドキュメントの運用

| 保存先 | 目的 | 現時点の扱い |
| --- | --- | --- |
| `MASTER.md` | 現在地・ブロッカー・最新証跡・次工程の一読復元 | 本仕様と同時に新設する。 |
| `docs/specs/` | 受領仕様、商品仕様、実装仕様、修正仕様 | 本ファイルを起点とする。 |
| `docs/audits/` | 技術・販売・最終監査全文 | 実画面とコードの照合結果を保存する。 |
| `docs/research/` | 市場・競合・価格の一次情報と分析 | 出典URL・取得日・結論を保存する。 |
| `docs/qa/` | QA仕様、実行結果、FAIL、再QA | 再現手順と結果を保存する。 |
| `docs/decisions/` | GO判定、根拠、未解決事項、承認要件 | AI出力と実証済み事実を区別して残す。 |
| `docs/sales/` | LP、FAQ、Privacy、Terms、特商法、返金、販売導線、SNS | 公開直前の販売素材と要入力事項を保存する。 |

## 4. 現時点の施工上の前提

現行アプリは単一の静的HTMLアプリケーションであり、主要な瞑想セッション、睡眠モード、休憩モード、自然音選択、ローカル履歴、PWAのマニフェストおよびサービスワーカーを実装している。販売チャネル、販売者情報、支払事業者、公開ドメイン、問い合わせ先、購入後アクセス方式は、本仕様受領時点でRepositoryから確認できない。これらは本人情報と事業判断を要するため、所有者入力・本人承認待ちとして正本化する。

## 5. 本仕様の変更履歴

| 日時（JST） | 変更 | 根拠 |
| --- | --- | --- |
| 2026-08-19 | 初版作成。初回のM04販売READY施工依頼と、GitHub Source-of-Truth必須ルールを統合。 | ユーザー受領指示 |

## 6. 次の正本アクション

本ファイルを起点に、`MASTER.md`、Decision Log、QA仕様・結果、技術監査、商品仕様、市場・競合調査、販売準備文書を追加し、施工単位で安全にcommit・pushする。公開・課金・販売開始は本人承認が必要な最終ゲートとして保持する。
