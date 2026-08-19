# DAIMON — SNS Pre-launch and Content Specification

| Field | Canonical state |
| --- | --- |
| Status | Draft only. No account, posting authority, platform, handle, profile URL, consent process, or publication approval has been provided. |
| Objective | 汎用的な瞑想アプリとして売り込むのではなく、「戻る前の短い余白」という使用場面を検証し、無料のアプリ利用または待機リストへ誘導する。 |
| Current CTA | `DAIMONをひらく`。メール登録・購入・割引・販売告知は未承認。 |
| Claim policy | 医療・治療・睡眠改善・ストレス解消・生産性向上の保証、未検証のタイマー信頼性、競合優位、希少性、利用者数を表現しない。 |

## Channel strategy

現時点で推奨するのは、所有者が実際に継続運用できる**単一の主チャネル**から始めることである。短文中心ならX、静止画・短尺動画中心ならInstagramまたはTikTok、仕事・現場・チーム導入を検証するならLinkedInが候補になる。ただし、対象顧客・所有者の発信継続性・プロフィール導線が未確定であるため、チャネル選定は所有者判断待ちとする。

投稿の目的は即時販売ではない。投稿→LP→アプリ開始という小さな導線で、どの使用場面が反応を得るかを把握する。データ取得を始める場合は、収集目的、測定ツール、保存先、プライバシー告知を先に確定する。

## Content pillars

| Pillar | Message | Evidence basis | Safe CTA |
| --- | --- | --- | --- |
| 30秒の余白 | 「気持ちを切り替える前に、30秒だけ止まる。」 | 30秒プリセット。 | DAIMONをひらく。 |
| 次の一手 | 「休憩の前に、戻った最初の一手を決めておく。」 | 次の一手入力・表示。タイマー精度修正までは時間終了を強調しない。 | 使い方を見る。 |
| 選ばない設計 | 「長いリストを探さず、今の時間を選ぶ。」 | 7つの時間プリセット。 | 時間を選ぶ。 |
| 無音も選べる | 「音が要らない日には、無音で。」 | 5つの音状態（4音＋無音）。 | 自分の音を選ぶ。 |
| ローカルな記録 | 「積み上げを、このブラウザに残す。」 | localStorage履歴。公開Privacy確定後に限定表現で使用。 | 記録を見る。 |

## Draft post examples

### Post A — 30 seconds

> 仕事を続ける前に、解決しなくていい30秒がある。
>
> DAIMONは、休むためではなく、次の一手へ戻るための短いタイマーです。
>
> まずは30秒から。
> [DAIMONをひらく]

### Post B — break to next action

> 休憩の前に、戻ったら最初にやることを一行だけ書いておく。
>
> 「何から戻るか」を決めておくと、休憩の終わりに迷いにくい。
>
> DAIMONの休憩モードは、その一手を残すための場所です。
> [使い方を見る]

### Post C — no performance claim

> 散ったときに、整え直そうとしなくていい。
>
> 30秒だけ、次の一手を見る。
>
> [DAIMONをひらく]

### Post D — silent option

> 音が欲しい日も、欲しくない日もある。
>
> 波、川、森、雨、無音。
> その日のまま、短く止まる。
>
> [DAIMONをひらく]

## Required approval before posting

| Required item | Why it is needed |
| --- | --- |
| Owner-approved platform and account | 投稿・DM・プロフィール変更は外部公開行為であり、本人の権限と承認が必要。 |
| Final LP URL and approved landing state | 壊れた導線、未公開価格、未整備の法定情報に誘導しないため。 |
| Public claims review | 実装、QA、Privacy、販売条件と一致させるため。 |
| Response owner and response target | コメント・DM・問い合わせへの対応範囲を明確にするため。 |
| Analytics/privacy decision | 計測やフォーム入力がある場合に、収集目的と保存先を告知するため。 |

## Measurement plan after lawful setup

| Question | Minimum event | Interpretation boundary |
| --- | --- | --- |
| Which use moment resonates? | UTM or platform post identifier → LP visit. | クリックは購入意向の証明ではない。 |
| Does the LP lead to first use? | `DAIMONをひらく` click. | 起動は継続利用の証明ではない。 |
| Does the first session begin? | App-side opt-in event only after privacy design; otherwise user testing. | localStorage内の個人利用履歴を無断収集しない。 |
| Is there qualitative pull? | Explicit voluntary feedback prompt. | 少数意見を市場全体へ一般化しない。 |

## Publication prohibition

本書にある文章、価格仮説、投稿例は公開承認ではない。公開、投稿、広告出稿、DM送信、リンク設置、価格告知、購入案内、決済開始は、技術再QAと所有者の明示承認を通過するまで禁止する。
