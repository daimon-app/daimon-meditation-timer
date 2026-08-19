# DAIMON 特定商取引法表示・返金・問い合わせ（公開前レビュー用ドラフト）

> **公開禁止ドラフトです。** 事実でない販売者情報、価格、返金条件、連絡先、提供時期を記載して公開してはいけません。全ての`[要入力]`を確定し、専門家レビューと本人承認を経るまで、この文書を販売ページ・決済画面・SNS・メールに転載しないでください。

| Field | Draft state |
| --- | --- |
| Sales status | **販売していない。** 価格、決済、注文フォーム、購入ボタンは存在しない。 |
| Legal review | Required before publication and before any payment or order acceptance. |
| Source basis | 消費者庁の通信販売ガイドは、価格、支払方法・時期、提供時期、撤回・解除、販売業者の氏名・住所・電話番号、ソフトウェア動作環境等を広告表示事項として挙げる。[1] [2] |

## A. 特定商取引法に基づく表記（販売時のみ公開する確定版）

| 項目 | 公開時の確定記載 | Current state |
| --- | --- | --- |
| 販売事業者 | `[要入力：個人の戸籍上の氏名／登記上の法人名]` | 未提供 |
| 運営責任者 | `[要入力：代表者または通信販売業務責任者]` | 未提供 |
| 所在地 | `[要入力：実際に活動している正確な住所]` | 未提供 |
| 電話番号 | `[要入力：確実に連絡できる電話番号]` | 未提供 |
| 電子メール / 問い合わせ先 | `[要入力]` | 未提供 |
| 販売URL | `[要入力：本番URL]` | 未提供 |
| 販売価格 | `[要入力：消費税込み価格、プランごとの価格]` | 未決定 |
| 商品代金以外の必要料金 | `[要入力：なし／決済手数料等を金額で]` | 未決定 |
| 支払方法 | `[要入力：実際に利用可能な全方式]` | 未選定 |
| 支払時期 | `[要入力：例：注文時に決済]` | 未決定 |
| 商品の引渡し／利用開始時期 | `[要入力：決済後直ちに／承認後○時間以内等の具体的時期]` | 未決定 |
| 提供形態 | `[要入力：ブラウザ利用権、ダウンロード、コード、コース等]` | 未決定 |
| 対応環境 | `[要入力：専門家・技術再QA済みのOS、ブラウザ、端末、ネットワーク要件]` | 未確定 |
| 申込期間・数量等の条件 | `[要入力：なし／ある場合は正確な期間・条件]` | 未決定 |
| 継続課金・更新 | `[要入力：なし／期間、更新、解約、料金、方法]` | 現行推奨はなし |
| キャンセル・返金 | 下記Bの確定版 | 未決定 |
| 不具合対応 | `[要入力：連絡窓口、対応方法、範囲]` | 未決定 |

### 表示・チェックアウト運用要件

販売開始時は、上表への容易な到達、購入前の明瞭な条件表示、最終確認画面での注文内容確認・訂正、販売価格・支払・提供・キャンセル条件の一覧性を確保する。[1] [2] [3] CTA、リンク、SNS投稿、メール、決済画面、購入後メールの全てで、実際の条件と矛盾しないことを確認する。

## B. 返金・キャンセルポリシー（方針決定用ドラフト）

現行では購入を受け付けないため、返金・キャンセルを受け付ける条件も定めない。デジタル提供物を販売する前に、少なくとも次の分岐を所有者と法務担当が決め、販売条件、最終確認画面、注文確認、サポート手順に同一内容を記載する。

| Decision question | Owner must choose | Operational proof required |
| --- | --- | --- |
| 販売対象 | ブラウザ利用権／ダウンロード／デジタルガイド／コース／継続サービスのいずれか | 購入者が実際に何をいつ受け取るか。 |
| 提供時点 | 決済直後／手動承認後／利用開始日 | 注文・決済・アクセス・通知の記録。 |
| 任意返金 | 返金を認める／認めない／期間・条件を定める | 明確で実行可能な案内と担当者。 |
| 不具合時 | 修復、代替提供、返金の順序・期限・窓口 | 技術的に実行可能な基準。 |
| 継続契約 | なし／自動更新あり、解約期限・方法・料金 | 顧客が容易に解約できる画面・手順。 |
| 例外 | 不正利用、法令、重複購入、誤課金等 | 一貫した審査と説明手順。 |

消費者庁の公式ガイドは、通信販売における撤回・解除や返品特約の内容を明確に表示する必要があること、申込みの条件・方法・効果を示す必要があることを説明する。[1] [2] デジタル商品、役務、継続課金、提供開始後の取消・返金の設計は取引形態に依存するため、一般論の「返金不可」等を無審査で採用しない。

## C. 問い合わせ・不具合・苦情対応（公開前の運用設計）

| Item | Minimum publication standard | Owner-required decision |
| --- | --- | --- |
| Contact method | 公開された、実際に受信・返信できる連絡先。 | メール、フォーム、電話、ヘルプデスクの選択。 |
| Response scope | 購入前、技術不具合、決済、返金、Privacy、削除請求の受付範囲。 | 何を受け付けるか。 |
| Response target | 例：`[要入力：営業日○日以内に一次返信]`。 | 人員と時間帯。 |
| Case record | 問い合わせ番号、受信日、分類、対応者、決定、返信、完了日を最小限で記録。 | 保管場所・保管期間・アクセス権。 |
| Escalation | 決済事業者、ホスティング、技術担当、法務の連絡経路。 | 担当者と連絡先。 |
| Accessibility | 連絡方法に配慮し、電話のみ等の単一手段に依存しない。 | 実装する窓口。 |
| Privacy | 問い合わせフォームには必要最小限の項目のみを求め、センシティブな健康情報の送信を促さない。 | フォーム文言・保管・削除手順。 |

### Draft support acknowledgement

> お問い合わせを受け付けました。内容を確認のうえ、`[要入力：応答目標]`を目安にご連絡します。購入・決済・個人情報に関するご相談は、`[要入力：窓口]`へお願いします。医療上または緊急の支援が必要な場合は、DAIMONのサポートではなく、地域の緊急窓口または資格を有する専門家へ連絡してください。

## D. Before-sale sign-off

| Sign-off | Evidence required | Owner sign-off |
| --- | --- | --- |
| Seller particulars | Legal name, address, phone, responsible person verified. | `[ ]` |
| Product scope & price | Customer-visible deliverable, tax, fees, payment, delivery specified. | `[ ]` |
| Refund / cancellation | Reviewed and reflected in product, checkout, support process. | `[ ]` |
| Support | Inbox/helpdesk works; responsible operator and response target set. | `[ ]` |
| Privacy | All processors, purposes, retention, deletion and contact notice confirmed. | `[ ]` |
| Checkout | Final confirmation supports review/correction and shows conditions. | `[ ]` |
| Legal review | Japan-qualified review for actual model completed. | `[ ]` |

## References

[1] [消費者庁 — 通信販売（特定商取引法ガイド）](https://www.no-trouble.caa.go.jp/what/mailorder/)

[2] [消費者庁 — 通信販売広告について](https://www.no-trouble.caa.go.jp/what/mailorder/advertising.html)

[3] [消費者庁 — 通信販売の申込み段階に関するガイドライン案内](https://www.no-trouble.caa.go.jp/what/mailorder/guidelines.html)
