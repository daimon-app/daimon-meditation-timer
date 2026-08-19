# DAIMON M04 — Japan E-commerce and Privacy Legal Research

> **Draft — legal review required before publication, reliance, or sale.** This is an implementation-oriented research note, not formal legal advice. The owner must have qualified Japanese counsel review the final sales model, disclosures, privacy notice, refund language, checkout, payment provider terms, advertising claims, and cross-border data flows before launch.

| Field | Research record |
| --- | --- |
| Scope | Japanese online sale of a digital browser/PWA product, optional lead capture, direct sales page, and post-purchase support. |
| Method | Consumer Affairs Agency’s official Specified Commercial Transactions Act guide and Personal Information Protection Commission official materials. |
| Current consequence | No price, checkout, subscription, registration, seller disclosure, or support channel may be published from the current DAIMON repository. |

## 1. Communications sales and specified-commercial-transactions requirements

The Consumer Affairs Agency defines communications sales as transactions where a seller advertises through media including the internet and receives applications through communications methods; the guide says an individual can be a seller where they conduct transactions as a business.[1] Internet websites and email are within the advertising scope when customers can apply based on the displayed information.[2]

The Agency’s guide lists advertising items that include price, payment timing and method, delivery/provision timing, cancellation/withdrawal terms including any return terms, seller name, address and telephone number, additional customer costs, software operating environment, recurring-contract conditions, and special sales conditions.[1] For web-based sales, the final confirmation screen must also display required ordering information and allow the customer to confirm and correct the order; misleading application or confirmation display is prohibited.[1] [3]

| DAIMON launch item | Official-source implication | Current status |
| --- | --- | --- |
| Seller identity | Individuals need legal name or registered trade name, accurate operating address and reliable telephone number; corporations also need representative or responsible person information for web advertising.[2] | **Owner required; unavailable.** |
| Price and customer burden | Sales price and all purchaser charges must be clear; digital delivery normally removes shipping, but tax, payment fees, platform fees, or any other charge must be stated accurately. [1] [2] | **Not decided.** |
| Payment and timing | All payment methods and timing must be displayed; provision timing must be specific. [1] [2] | **Not selected.** |
| Digital/software environment | Software sales advertising must show operating environment. [1] [2] | Draft technical environment exists; final browser/OS/support matrix needs owner decision and device re-QA. |
| Recurrence / subscription | If continuing contracts are required, their terms and provision conditions must be clear. [1] | Current recommendation is no subscription. |
| Withdrawal / cancellation | Sales advertising must explain application withdrawal/cancellation terms. Return terms must be stated clearly; if a contract provides repeated/ongoing services, cancellation method and any detriment such as fee must be clear. [1] [2] | **Policy and channel missing.** |
| Final checkout | A final confirmation view must permit review/correction and contain required order information. [1] [3] | **No checkout.** |
| E-mail marketing | Unsolicited commercial email is generally prohibited without prior consent, and consent/request records must be retained for the period described by the official guide. [1] | **No mailing list or consent process.** |
| Advertising accuracy | Materially false or excessively advantageous advertising is prohibited. [1] | LP has been constrained; final copy must remain code- and QA-supported. |

The official guide states that, for sale of goods, consumers generally have an eight-day post-delivery withdrawal/termination right unless an advertised return special term applies; the specific digital product, access provision, and transaction structure should be reviewed by counsel before adopting a refund/cancellation position.[1] A seller must not use vague language such as “we will discuss returns case by case” where a concrete return-term disclosure is required.[2]

## 2. Privacy and data-handling implications

The Personal Information Protection Commission’s official materials include, among other topics, the definition of personal information, the requirement to specify purposes of use, how information is obtained, management of personal data, outsourcing, third-party provision, and breach-related handling.[4] The Commission’s Q&A expressly lists email address and telephone number questions within the personal-information definition section, and its purpose-of-use section addresses how precisely use purposes must be specified.[4]

The current DAIMON app code uses browser `localStorage` for history, natural-sound choice, and count-sound choice; it has no app account, backend API, analytics SDK, or cloud database in the inspected repository. That supports a narrow app-level statement: **“The current app stores these settings and records in this browser.”** It does not support a broader website-level statement until hosting logs, analytics, forms, payment, email, support inboxes, cookies, CDN, and third-party processors are selected and audited.

| Data surface | Current observed state | Required pre-publication decision |
| --- | --- | --- |
| Timer history / settings | Browser localStorage; individual/all history deletion exists in-app. | State this limited scope accurately; explain how users can clear browser site data. |
| Service Worker cache | Browser Cache Storage retains application resources/sounds. | Include cache/offline behavior in technical FAQ; verify cache-version behavior on production hosting. |
| Lead capture / wait list | Not implemented. | Before adding: select controller, purpose, fields, retention/deletion, processor, consent language, withdrawal method, support contact, and public notice. |
| Payment | Not implemented. | Select payment service; assess provider role, data flow, policy links, receipts, cancellation/refund flow. |
| Analytics / advertising | Not implemented in repository. | Decide opt-in/consent and disclosure strategy before any trackers or ad pixels are added. |
| Support contact | Not configured. | Choose mailbox/helpdesk and document who accesses messages, purpose, retention, processors, response target, and deletion route. |

## 3. Owner information and legal decisions required

| Required input | Needed for |
| --- | --- |
| Legal seller name / entity type | Specified commercial transactions disclosure; terms; privacy controller. |
| Accurate operating address and reliable phone number | Specified commercial transactions disclosure. |
| Representative or sales-responsible person | Corporate web-sales disclosure where applicable. |
| Public support email / phone / helpdesk and responsible operator | Contact, cancellation/refund handling, privacy inquiries, service notices. |
| Product classification and exact paid deliverable | Terms, delivery/access wording, refund/cancellation design, claim boundary. |
| Price, tax treatment, payment methods, fees, sales area/currency | Commercial disclosure and checkout. |
| Delivery/access timing and method | Commercial disclosure and post-purchase flow. |
| Refund/cancellation rule | Commercial disclosure and final checkout. |
| Sales platform / payment processor / hosting / email / analytics providers | Privacy notice, data flow, security and contract review. |
| Governing-law / dispute policy | Terms; counsel review. |
| Marketing-consent and mailing policy | Email consent capture, opt-out, record retention. |

## 4. Minimum public document set for a future paid release

The following documents can be prepared as owner-input-gated drafts but must not be published with fictional details.

| Document | Required before paid checkout | Current release state |
| --- | --- | --- |
| 特定商取引法に基づく表記 | Yes | Owner data missing. |
| 利用規約 | Yes | Transaction model and owner data missing. |
| プライバシーポリシー | Yes if any personal data/support/payment/analytics are processed; strongly recommended in all cases. | Deployment/vendor decisions missing. |
| 返金・キャンセルポリシー | Yes | Owner policy and product-delivery model missing. |
| FAQ | Yes | Draft may be prepared with clear limitations. |
| 問い合わせページ | Yes | Support route/response owner missing. |
| Checkout final-confirmation design | Yes | No payment provider or purchase model. |
| Consent / unsubscribe flow | Yes if marketing email is used. | No lead system or marketing policy. |

## References

[1] [消費者庁 — 通信販売（特定商取引法ガイド）](https://www.no-trouble.caa.go.jp/what/mailorder/)

[2] [消費者庁 — 通信販売広告について](https://www.no-trouble.caa.go.jp/what/mailorder/advertising.html)

[3] [消費者庁 — 通信販売の申込み段階に関するガイドライン案内](https://www.no-trouble.caa.go.jp/what/mailorder/guidelines.html)

[4] [個人情報保護委員会 — 個人情報保護法ガイドラインに関するQ&A](https://www.ppc.go.jp/personalinfo/faq/APPI_QA/)
