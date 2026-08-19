# DAIMON M04 — QA Specification

| Field | Requirement |
| --- | --- |
| Product | DAIMON — 整える |
| Test purpose | 販売開始前に、タイマーが意図した時間・状態・保存・オフライン挙動を提供し、公開コピーが検証範囲を超えないことを確認する。 |
| Test environment | 2026-08-19 JST。GitHub `main`。ローカル静的配信 `http://127.0.0.1:4173/`。Chromium sandbox browser。 |
| Baseline commit | `9cbd5b6ee53f58c06c73fe40dd8647704304843c`。アプリ実装は `651e5830bc2a047b55d8c334bb1f9b14e1eec62e` から未変更。 |
| Evidence rule | 各結果は実コード、ブラウザ画面、コンソール、またはHTTP応答で裏づける。未実行項目をPASSにしない。 |

## Test cases

| ID | Area | Procedure | Acceptance criterion | Release impact on failure |
| --- | --- | --- | --- | --- |
| QA-CORE-01 | Primary timer start | ホームから30秒セッションを開始する。 | モード、残り時間、進行状態、停止・終了操作が即時に表示される。 | `TECH_FIX_REQUIRED` |
| QA-CORE-02 | Primary pause/resume | セッション中に一時停止・再開する。 | 表示とボタン文言が一時停止／再開状態と整合し、再開後の期限が停止時間分だけ延長される。 | `TECH_FIX_REQUIRED` |
| QA-CORE-03 | Primary background recovery | セッション中に期限を越えて復帰相当処理を行う。 | 絶対時刻に基づき残り時間を再計算し、終了画面と履歴保存へ一度だけ遷移する。 | `TECH_FIX_REQUIRED` |
| QA-CORE-04 | Completion sound | カウント音設定に依存しない終了ベルを実行する。 | AudioContextが利用可能な通常状態で終了ベル生成関数が実行される。OSミュート・ブラウザ自動再生制約は別途明記する。 | Public guarantee prohibited; `TECH_FIX_REQUIRED` only if code fails. |
| QA-CORE-05 | Sound selection | 4種類の自然音と無音を選ぶ。 | 選択状態が保存され、セッション開始時に選択音または明示したフォールバックが使われる。 | `TECH_FIX_REQUIRED` |
| QA-CORE-06 | History/privacy | セッション完了後、履歴を表示・個別削除・全削除する。 | 履歴は端末のlocalStorageに限定され、表示値が安全にテキスト出力され、削除操作が機能する。 | `TECH_FIX_REQUIRED` / privacy claim prohibited |
| QA-BREAK-01 | Break timer precision | 休憩タイマーの開始、停止、期限超過後の復帰を検証する。 | 主セッションと同等に絶対時刻で正確に復帰する。 | `TECH_FIX_REQUIRED`; not approved until fixed and re-QA’d. |
| QA-SLEEP-01 | Sleep timer precision | 睡眠タイマーの開始、期限超過後の復帰、音量フェードを検証する。 | 経過・残り・終了時刻がバックグラウンドの間引きに依存しない。 | `TECH_FIX_REQUIRED`; not approved until fixed and re-QA’d. |
| QA-WAKE-01 | Screen Wake Lock | 主セッションでWake Lock対応・非対応・再取得処理を確認する。 | 対応端末で要求され、取得不可時は注意文を表示する。画面消灯防止を保証しない。 | Public guarantee prohibited; `TECH_FIX_REQUIRED` if state handling fails. |
| QA-PWA-01 | Manifest | インストール可能なWeb App Manifestを確認する。 | `name`、`short_name`、`display`、`start_url`、`scope`、テーマ色、192/512アイコンが有効である。 | `TECH_FIX_REQUIRED` |
| QA-PWA-02 | Service worker/cache | Service Worker登録とプリキャッシュを確認する。 | アプリシェル、マニフェスト、4音源、アイコンが同一スコープのキャッシュに存在する。 | `TECH_FIX_REQUIRED` |
| QA-PWA-03 | Offline availability | 一度オンラインでロード・インストール後、ネットワーク不通相当で起動する。 | キャッシュ済みアプリシェルと音源で本体が使える。Google Fontsの未キャッシュ時フォント差替えは許容するが、機能を停止させない。 | `TECH_FIX_REQUIRED` if app shell fails. |
| QA-MOB-01 | Mobile layout | 375×667相当の狭幅画面でホーム、主セッション、睡眠選択、休憩入力を確認する。 | 横スクロールがなく、コア操作のタップ対象・本文・終了操作が画面内で読める。 | `TECH_FIX_REQUIRED` |
| QA-UX-01 | First-use clarity | 初回表示でプロダクト目的、開始方法、音の初期状態、データの扱い、インストール導線、サポート先を確認する。 | 行動開始の妨げにならず、販売公開時に必要な情報へのリンクを提供する。 | Sales/Web remediation required. |
| QA-A11Y-01 | Semantic controls | キーボード・支援技術の視点で主要操作を確認する。 | 操作可能要素は適切なボタンまたはリンクとして認識され、フォーカス可能である。 | `TECH_FIX_REQUIRED` |

## Test boundaries and non-claims

DAIMONはWebブラウザとOSの通知、音量、バックグラウンド実行、バッテリー最適化、端末の自動再生ポリシーを完全には制御できない。したがって「必ず鳴る」「画面が絶対に消えない」「バックグラウンドでも常に正確」といった無条件の公開表現は、このQAの対象外であり使用禁止とする。

モバイル実機、iOS Safari、Android Chrome、インストール済みPWA、画面ロック状態の完全な網羅テストには実機またはクラウド端末が必要である。本セッションでは明示的に実行した範囲と、コード上の観察に留まる範囲を分離して結果へ記載する。

## Exit criteria

主要瞑想セッション、履歴、PWAキャッシュ、モバイル狭幅レイアウトが再現可能な証拠とともにPASSとなり、すべての `TECH_FIX_REQUIRED` が解消・再QA済みであることが技術GOの条件である。未解決のコード欠陥がある限り、販売開始判定は `CONDITIONAL` または `NO GO` とする。
