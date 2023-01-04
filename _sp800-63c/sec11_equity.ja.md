---
layout: default.ja
title: 公平性の考慮事項
navOrder: 11
navTitle: 公平性
permalink: /ja/sp800-63c/equity/
anchor: equity
section: 11
---

# 公平性の考慮事項 (Equity Considerations) {#equity}

_This section is informative._

IdP および RP の機能への公平なアクセスは，フェデレーションアイデンティティシステムの不可欠な要素である．行政命令 13985 _Advancing Racial Equity and Support for Underserved Communities Through the Federal Government_ [[EO13985]](references.md#ref-EO13985) で指定されているように，フェデレーション技術を使用している場合でも，政府サービスへの公平なアクセスを提供するには，すべての加入者(subscriber)が確実に認証できることが櫃世杖ある．公平性リスクを評価する際，IdP と RP は，フェデレーションアイデンティティサービスが提供する全体的なユーザー数を考慮する必要がありる．さらに，IdP と RP は，そのサービスを使用する際に，共有された特性が，不公平なアクセス，処理，または結果の対象となる可能性がある集団内のユーザーのグループをさらに識別する． [Sec. 10](../sec10_usability.md#usability) で提供されるユーザビリティに関する考慮事項も，フェデレーションアイデンティティサービスを使用するすべての人にとっての全体的な使いやすさと公平性を確保するためにも考慮されるべきである．

> Equitable access to the functions of IdPs and RPs is an essential element of a federated identity system. The ability for all subscribers to authenticate reliably is required to provide equitable access to government services, even when using federation technology, as specified in Executive Order 13985, _Advancing Racial Equity and Support for Underserved Communities Through the Federal Government_ [[EO13985]](references.md#ref-EO13985). In assessing equity risks, IdPs and RPs should consider the overall user population served by their federated identity service. Additionally, IdPs and RPs further identify groups of users within the population whose shared characteristics can cause them to be subject to inequitable access, treatment, or outcomes when using that service. The Usability Considerations provided in [Sec. 10](../sec10_usability.md#usability) should also be considered to help ensure the overall usability and equity for all persons using federated identity services.

検証者としての役割において，IdP は，[[SP800-63A]](../_sp800-63a/sec11_equity.md#sec11){:latex-href="#ref-SP800-63A"} の11章に挙げられているような，身元確認(identity proofing)，属性の検証，および登録に関連する公平性，ならびに，[[SP800-63B]](../_sp800-63b/sec11_equity.md#sec11){:latex-href="#ref-SP800-63B"}の11章に挙げられているような，れたオーセンティケーターに関連する公平性，に関する考慮事項を認識する必要がある．FAL3 を提供する RP は，オーセンティケーターが IdP または RP で管理されているかどうかにかかわらず，バインドされたオーセンティケーターを処理する際，同様のオーセンティケーターの考慮事項を認識する必要がある．

> In its role as the verifier, the IdP needs to be aware of equity considerations related to identity proofing, attribute validation, and enrollment as enumerated in [[SP800-63A]](../_sp800-63a/sec11_equity.md#sec11){:latex-href="#ref-SP800-63A"} Sec. 11 and equity considerations concerning authenticators as enumerated in [[SP800-63B]](../_sp800-63b/sec11_equity.md#sec11){:latex-href="#ref-SP800-63B"} Sec. 11. An RP offering FAL3 will also need to be aware of these same authenticator considerations when processing bound authenticators, whether the authenticators are managed at the IdP or RP.


フェデレーションプロセスは複数のアクティブパーティ間でネットワークプロトコルを介して行われるため，フェデレーションシステムを使用して認証を行うと，次の例のような公平性の問題が生じる可能性がある．

> Since the federation process takes place over a network protocol between multiple active parties, the experience of authenticating using the federation system may present equity problems, such as the following examples:

* タイムアウトすることなくフェデレーショントランザクション全体を完了することは，信頼できるネットワーク接続を持たない加入者(subscriber) (農村地域など) にとっては難しい場合がある．
* 知的障害，発達障害，学習障害，または神経認知障害のある加入者(subscriber)の属性の提供に関する実行時の決定について，インフォームドコンセントを提供することは困難な場合がある．
* IdP と RP の両方と同時に対話するために必要な十分な処理能力，ネットワークアクセス，およびその他の機能を備えたシステムは，一部の加入者(subscriber)にとっては購入しにくい場合がある．
* デバイスを共有する加入者(subscriber)は，ホワイトリストベースのシステムを安全に管理するのが難しいと感じる場合がある．これは，デバイスの他のユーザーが，IdP でまだアクティブなセッションを介して RP への意図しないアクセスを黙って取得する可能性があるためである．
* さまざまな理由で IdP へのアクセスを失った加入者(subscriber)のために，RP でアカウントを再確立することは非常に困難になる可能性がある．

> * Completing the entire federated transaction without timing out may be difficult for subscribers without a reliable network connection, such as those in rural areas.
> * It may be difficult to provide informed consent for a runtime decision regarding the release of attributes for subscribers with intellectual, developmental, learning, or neurocognitive difficulties.
> * Systems with sufficient processing power, network access, and other features required to interact with both the IdP and the RP simultaneously may be difficult to afford for some subscribers.
> * Subscribers that share devices may find allowlist-based systems difficult to manage securely, as other users of the device could silently gain unintended access to an RP through a session still active at the IdP.
> * It could be prohibitively difficult to re-establish an account at the RP for subscribers who lose access to their IdP for any of a variety of reasons.

最も一般的であると予想されるこの分野の問題を軽減するため IdP と RP に要求する規範的な要件が確立されている．しかし，規範的(Normative)要件がすべての潜在的な公平性の問題を予期している可能性は低い．潜在的な公平性の問題も，アプリケーションによって異なる．したがって，IdP と RP は，加入者(subscriber)が不公平な認証要件を報告し，潜在的な代替認証戦略についてアドバイスするメカニズムを提供する必要がある．

> Normative requirements have been established requiring IdPs and RPs to mitigate the problems in this area that are expected to be most common. However, normative requirements are unlikely to have anticipated all potential equity problems. Potential equity problems also will vary for different applications. Accordingly, IdPs and RPs need to provide mechanisms for subscribers to report inequitable authentication requirements and to advise them on potential alternative authentication strategies.

本ガイドラインにより，追加のフェデレーション識別子を RP 加入者(subscriber)アカウントにバインドすることで，IdP アクセス損失のリスクを最小限に抑えることができる ([Sec 5.4](sec5_federation.md#rp-account) 参照)．ただし，加入者(subscriber)は，RP に受け入れられる複数の IdP アカウントを同時に持つことが難しい場合がある．この不公平性は，RP 加入者(subscriber)アカウントからの複数のフェデレーション識別子の安全なバインドおよびバインド解除を可能にする独自のアカウント回復プロセスを RP に持たせることで対処できる．

> This guideline allows the binding of additional federated identifiers to an RP subscriber account to minimize the risk of IdP access loss (see [Sec. 5.4](sec5_federation.md#rp-account)). However, a subscriber might find it difficult to have multiple IdP accounts that are acceptable to the RP at the same time. This inequity can be addressed by having the RP having its own account recovery process that allows for the secure binding and unbinding of multiple federated identifiers from the RP subscriber account.

RP は，すべての加入者(subscriber)が必ずしも同じ IdP にアクセスできるとは限らないことに注意する必要がある．RP は，そのような加入者(subscriber)に対してローカルで認証されたアカウントを作成し，後でそれらのアカウントをフェデレーション識別子にバインドできるようにする．

> RPs need to be aware that not all subscribers will necessarily have access to the same IdPs. The RPs can institute locally authenticated accounts for such subscribers, and later allow binding of those accounts to federated identifiers.
