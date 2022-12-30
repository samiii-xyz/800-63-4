---
layout: default.ja
title: アサーション
navOrder: 6
navTitle: アサーション
permalink: /ja/sp800-63c/assertions/
anchor: assertions
section: 6
---

# アサーション (Assertions) {#assertions}

*This section is normative.*

認証に使用されるアサーションは，フェデレーションアイデンティティシステムで IdP から RP に渡される認証済み加入者(subscriber)に関する（またはそれに関連付けられた）属性値や派生属性値のパッケージ化されたセットである．アサーションにはさまざまな情報が含まれる．アサーションメタデータ，加入者(subscriber)に関する属性値と派生属性値，IdP での加入者(subscriber)の認証に関する情報，RP が活用できるその他の情報 (制限や有効期間など) などである．アサーションの主な機能は RP に対してユーザーを認証することであるが，アサーションで伝達される情報は，多くのユースケースで RP によって使用できる．たとえば，Web サイトの承認やパーソナライズなど．これらのガイドラインは，選択されたソリューションがここに含まれるすべての必須要件を満たしている限り，RP のユースケース，使用されるプロトコルやフェデレーションに使うデータペイロードの種類を制限しない．
> An assertion used for authentication is a packaged set of attribute values or derived attribute values about or associated with an authenticated subscriber that is passed from the IdP to the RP in a federated identity system. Assertions contain a variety of information, including: assertion metadata, attribute values and derived attribute values about the subscriber, information about the subscriber's authentication at the IdP, and other information that the RP can leverage (e.g., restrictions and validity time window). While the assertion's primary function is to authenticate the user to an RP, the information conveyed in the assertion can be used by the RP for a number of use cases &mdash; for example, authorization or personalization of a website. These guidelines do not restrict RP use cases nor the type of protocol or data payload used to federate an identity, provided the chosen solution meets all mandatory requirements contained herein.



アサーションは，IdP で加入者(subscriber)の個別の認証イベントを表さ**なければならなず(SHALL)**，RP で個別の認証イベントとして処理され**なければならない(SHALL)**．
> Assertions **SHALL** represent a discrete authentication event of the subscriber at the IdP and **SHALL** be processed as a discrete authentication event at the RP.

すべてのアサーションには，次の属性が含まれてい**なければならない(SHALL)**．

1. 主体識別子(subject identifier): アサーションが適用される当事者（つまり，加入者(subscriber)）の識別子．
2. 発行者識別子(issuer identifier): アサーションの発行者（つまり，IdP）の識別子．
3. 対象者識別子(audience identifier): アサーションを消費することを意図した当事者（つまり，RP）の識別子．
4. 発行時刻(issuance time): IdP がアサーションを発行した時刻を示すタイムスタンプ．
5. 有効期間(validity time window): ここで示される期間以外では，加入者(subscriber)を認証し，RP で認証されたセッションを開始する目的で，アサーションを RP が有効として受け入れては **ならない(SHALL NOT)** ．これは通常，発行タイムスタンプに加えて，アサーションの有効期限タイムスタンプによって通知される．
6. アサーション識別子(assertion identifier): このアサーションを一意に識別する値で，攻撃者が以前のアサーションをリプレイすることを防ぐために使用される．
7. 署名(signature): アサーション全体をカバーする，IdP に関連付けられた鍵識別子または公開鍵を含む，デジタル署名またはメッセージ認証コード(MAC)．
8. 認証時間(authentication time): IdP が主要な認証イベント（利用可能な場合）を通じて IdP で加入者(subscriber)の存在を最後に確認した日時を示すタイムスタンプ．
9. IAL: アサーションで表されている加入者(subscriber)アカウントの IAL のインジケーター，または IAL が提示されていないことのしるし．
10. AAL: 加入者(subscriber)が IdP に対して認証されたときに使用された AAL のインジケーター，または AAL が提示されていないことのしるし．
11. FAL: アサーションによって表されるフェデレーションプロセスの IdP の意図した FAL のインジケーター．

> All assertions **SHALL** include the following attributes:
> 
> 1. Subject identifier: An identifier for the party to which the assertion applies (i.e., the subscriber).
> 2. Issuer identifier: An identifier for the issuer of the assertion (i.e., the IdP).
> 3. Audience identifier: An identifier for the party intended to consume the assertion (i.e., the RP).
> 4. Issuance time: A timestamp indicating when the IdP issued the assertion.
> 5. Validity time window: A period of time outside of which the assertion **SHALL NOT** be accepted as valid by the RP for the purposes of authenticating the subscriber and starting an authenticated session at the RP. This is usually communicated by means of an expiration timestamp for the assertion in addition to the issuance timestamp.
> 6. Assertion identifier: A value uniquely identifying this assertion, used to prevent attackers from replaying prior assertions.
> 7. Signature: Digital signature or message authentication code (MAC), including key identifier or public key associated with the IdP, covering the entire assertion.
> 8. Authentication time: A timestamp indicating when the IdP last verified the presence of the subscriber at the IdP through a primary authentication event (if available).
> 9. IAL: Indicator of the IAL of the subscriber account being represented in the assertion, or an indication that no IAL is asserted.
> 10. AAL: Indicator of the AAL used when the subscriber authenticated to the IdP, or an indication that no AAL is asserted.
> 11. FAL: An indicator of the IdP's intended FAL of the federation process represented by the assertion.


[Sec. 6.1.2](sec6_assertions.md#boundauth) で説明されているように，FAL3 でアサーションが bound authenticator と共に使用される場合，アサーションは以下を含ま**なければならない(SHALL)**．

1. Authenticator binding: 公開鍵，鍵識別子，その他の加入者(subscriber)が保持する bound authenticator の識別子（IdP 管理の bound authenticator の場合) ，RP 管理の bound authenticator が 個のアサーションの検証に必要であることを示すインジケーター．

> If the assertion is used at FAL3 with a bound authenticator as described in [Sec. 6.1.2](sec6_assertions.md#boundauth), the assertion **SHALL** include the following:
> 
> 1. Authenticator binding: The public key, key identifier, or other identifier of subscriber-held bound authenticator (for IdP-managed bound authenticators) or indicator that an RP-managed bound authenticator is required for verification of this assertion. 

アサーションには，次の情報を含む追加の項目が含まれ**てもよい(MAY)**．

1. 属性値と派生属性値: 加入者(subscriber)に関する情報．
2. 属性メタデータ: NIST Internal Report 8112 [[NISTIR8112]](references.md#ref-nistir8112) で説明されているような，1 つまたは複数の加入者(subscriber)属性に関する追加情報．

> Assertions **MAY** also include additional items, including the following information:
> 
> 1. Attribute values and derived attribute values: Information about the subscriber.
> 2. Attribute metadata: Additional information about one or more subscriber attributes, such as those described in NIST Internal Report 8112 [[NISTIR8112]](references.md#ref-nistir8112).


アサーションは，認証イベントが提示されている場合は AAL を指定し，身元証明(identity proofing)された属性 (またはそれらの属性から派生した値) が提示されている場合は IAL を指定する**必要がある(SHOULD)**．

> Assertions **SHOULD** specify the AAL when an authentication event is being asserted and IAL when identity proofed attributes (or values derived from those attributes) are being asserted.

アサーション内のすべてのメタデータは，受信時に RP によって検証され**なければならない(SHALL)**．

  - *発行者の検証*: アサーションが，RP が期待する IdP によって発行されたことを確認する．
  - *署名の検証*: アサーションの署名が有効であり，アサーションを送信する IdP に属する鍵に対応していることを確認する．
  - *時間の検証*: 有効期限と発行時間が現在のタイムスタンプの許容範囲内であることを確認する．
  - *対象者の制限*: この RP がアサーションの意図された受信者であることを確認する．

> All metadata within the assertion **SHALL** be validated by the RP upon receipt:
> 
>  - *Issuer verification*: ensuring the assertion was issued by the IdP the RP expects it to be from.
>  - *Signature validation*: ensuring the signature of the assertion is valid and corresponds to a key belonging to the IdP sending the assertion.
>  - *Time validation*: ensuring the expiration and issue times are within acceptable limits of the current timestamp.
>  - *Audience restriction*: ensuring this RP is the intended recipient of the assertion.


RP は，主体識別子を本質的にグローバルに一意ではないものとして扱わ**なければならない(SHALL)**．代わりに，アサーションの主体識別子の値は通常，アサーション発行者の制御下にある名前空間にある．これにより，RP は，異なる IdP からの主体を誤って混同することなく，複数の IdP と通信することができる．
> An RP **SHALL** treat subject identifiers as not inherently globally unique. Instead, the value of the assertion's subject identifier is usually in a namespace under the assertion issuer's control. This allows an RP to talk to multiple IdPs without incorrectly conflating subjects from different IdPs.


アサーションには，加入者(subscriber)に関する追加の属性を含め**てもよい(MAY)**．[Section 6.2.3](sec6_assertions.md#encrypted-assertion) には，アサーションで属性を提示するためのプライバシー要件が含まれている．RP は，加入者(subscriber)の追加の属性を取得するために RP が使用できるアサーションと共に，[Sec. 6.3](#s-identity-api) で説明されているように，アイデンティティAPI への制限付きアクセスを与えられ**てもよい(MAY)**．

> Assertions **MAY** include additional attributes about the subscriber. [Section 6.2.3](sec6_assertions.md#encrypted-assertion) contains privacy requirements for presenting attributes in assertions. The RP **MAY** be given limited access to an identity API as discussed in [Sec. 6.3](#s-identity-api) along with the assertion, which the RP can use to fetch additional identity attributes for the subscriber.


詳細は使用しているフェデレーションプロトコルによって異なるが，アサーションは RP への個別のログインイベントを表す．アサーションの有効期間は，IdP または RP でのセッション管理に関連しているが，それとは別のものである．具体的には，IdP での認証済みセッションの中でアサーションが作成され，アサーションを処理すると RP で認証済みセッションが作成される．IdP がアサーションを作成した後，IdP のセッションの有効性はアサーションの有効性とは無関係である．IdP でセッションがまだ有効な間に，認証を繰り返す要求が IdP に送信されると，それ用の有効期間で作成される新しい別のアサーションが発生する．同様に，RP がアサーションを消費した後，RP のセッションの有効性はアサーションの有効性とは無関係である．また同様に，アイデンティティAPI に付与されたアクセスは，アサーションの有効性や RP での認証済みセッションの有効期間とは無関係である．セッション管理の詳細については，[Sec. 5.3](sec5_federation.md#federation-session)  を参照．

> Although details vary based on the exact federation protocol in use, an assertion represents a discrete login event to the RP. The validity time window of an assertion is related to but separate from any session management at the IdP or RP. Specifically, an assertion is created during an authenticated session at the IdP, and processing an assertion creates an authenticated session at the RP. After the IdP creates the assertion, the validity of the IdP's session is independent of the validity of the assertion. If a request comes to the IdP for a repeated authentication while the session is still valid at the IdP, this results in a new and separate assertion being created with its own validity time window. Similarly, after the RP consumes the assertion, the validity of the RP's session is independent of the validity of the assertion. Access granted to an identity API is likewise independent of the validity of the assertion or the lifetime of the authenticated session at the RP. See [Sec. 5.3](sec5_federation.md#federation-session) for more information on session management.


アサーションの有効期間は，発行から有効期限までの時間である．この期間は，RP がアサーションを処理し，加入者(subscriber)のローカルアプリケーションセッションを作成できるように十分な長ささである必要があるが，そのような処理に必要な時間を超えて長くすべきではない．有効期間の長いアサーションは，盗まれたりリプレイされたりするリスクが高くなる．アサーションの有効期間を短くすると，このリスクが軽減される．アサーションの有効期間は，RP でのセッションを制限するために使用しては**ならない(SHALL NOT)**．詳細は [Sec. 5.3](sec5_federation.md#federation-session) を参照．
> The assertion's validity time window is the time between its issuance and its expiration. This window needs to be large enough to allow the RP to process the assertion and create a local application session for the subscriber, but should not be longer than necessary for such establishment. Long-lived assertions have a greater risk of being stolen or replayed; a short assertion validity time window mitigates this risk. Assertion validity time windows **SHALL NOT** be used to limit the session at the RP. See [Sec. 5.3](sec5_federation.md#federation-session) for more information.

 


## Assertion Binding  {#assertion-binding}

アサーションバインディングは，主張者(claimant)によるアサーションの提示が，加入者(subscriber)として RP と現在セッション中の当事者にバインディングするのに十分かどうか，または加入者(subscriber)にバインドされたオーセンティケーターが提示されたことを通して RP が追加の証明を必要とするかどうかに基づいて分類できる．
> Assertion binding can be classified based on whether presentation by a claimant of an assertion is sufficient for binding to the party currently in session with the RP as the subscriber, or if the RP requires additional proof through the successful presentation of an authenticator bound to the subscriber.


### Bearer Assertions  {#bearer}

ベアラーアサーションは，ベアラーのアイデンティティの証明として，どの当事者でも提示できる．同様に，ベアラアサーション参照は，任意の当事者によってRPに提示され，RP がアサーションを取得するために使用できる（この場合のアサーションもベアラアサーションとみなされる）．加入者(subscriber)を表す有効なアサーションまたはアサーション参照を，攻撃者がキャプチャまたは作成でき，そのアサーションまたは参照をRPに正常に提示できる場合，攻撃者はその RP で加入者(subscriber)になりすますことができる．

> A bearer assertion can be presented by any party as proof of the bearer's identity. Similarly, a bearer assertion reference can be presented by any party to the RP and used by the RP to fetch an assertion; the assertion in this instance is also considered a bearer assertion. If an attacker can capture or manufacture a valid assertion or assertion reference representing a subscriber and can successfully present that assertion or reference to the RP, then the attacker could be able to impersonate the subscriber at that RP.

注記：ベアラーアサーションまたは参照を単に所有するだけでは，加入者(subscriber)になりすますのに十分ではない．たとえば，アサーションがバックチャネルフェデレーションモデル ([Sec. 7.1](sec7_presentation.md#back-channel) で説明) で提示される場合，RP を不正行為からさらに保護するのに役立つ追加の制御 (RP の識別やアサーションインジェクション保護など) をトランザクションに配置し**てもよい(MAY)**．

> Note that mere possession of a bearer assertion or reference is not always enough to impersonate a subscriber. For example, if an assertion is presented in the back-channel federation model (described in [Sec. 7.1](sec7_presentation.md#back-channel)), additional controls **MAY** be placed on the transaction (such as identification of the RP and assertion injection protections) that help further protect the RP from fraudulent activity.


### Bound Authenticators {#boundauth}

bound authenticator は，加入者(subscriber)によってアサーションと共に RP に提示されるオーセンティケーターである．RP に bound authenticator を所有していることを証明する際に，加入者(subscriber)は，自分がアサーションの正当な主体であることをある程度保証して証明する．加入者(subscriber)に発行されたアサーションを攻撃者が盗んで使用することは，攻撃者がアサーションだけでなく bound authenticator も盗み，それらを一緒に提示できなけれならないため，より困難である．さらに，bound authenticator を使用すると，独立した認証により，悪意のあるまたは侵害された IdP から RP を保護する．

> A bound authenticator is an authenticator presented to the RP by the subscriber alongside the assertion. In proving possession of the bound authenticator to the RP, the subscriber also proves with a certain degree of assurance that they are the rightful subject of the assertion. It is more difficult for an attacker to use a stolen assertion issued to a subscriber since the attacker would need to steal the bound authenticator as well as the assertion and be able to present them together. Furthermore, use of a bound authenticator protects the RP against malicious or compromised IdPs through the use of independent authentication.


bound authenticator は，RP の加入者(subscriber)ごとに一意で**なければならない(SHALL)** ため，2つの加入者(subscriber)が別々の RP 加入者(subscriber)アカウントに対して同じオーセンティケーターを提示することはできない．すべての bound authenticator は，フィッシング耐性が**なければならない(SHALL)**．したがって，記憶されたシークレットなどの加入者(subscriber)が選択した値は，bound authenticator として使用できない．
RP は，アサーションを処理するコンテキストでのみ，bound authenticator からの認証を受け入れ**なければならない(SHALL)**．したがって，加入者(subscriber)は bound authenticator を使用して RP に直接ログインできず，IdP をバイパスする．
> A bound authenticator **SHALL** be unique per subscriber at the RP such that two subscribers cannot present the same authenticator for their separate RP subscriber accounts. All bound authenticators **SHALL** be phishing resistant. Consequently, subscriber-chosen values such as a memorized secret cannot be used as bound authenticators.
The RP **SHALL** accept authentication from a bound authenticator only in the context of processing an assertion. Consequently, the subscriber can not use a bound authenticator to log into the RP directly, bypassing the IdP in the process.


以下のセクションで詳しく説明するように，bound authenticator は，さまざまな状況下で IdP または RP のいずれかによって管理される． FAL3 アサーションには，加入者(subscriber)が FAL3 に到達するために RP にて特定の IdP 管理の bound authenticator または RP 管理の bound authenticator を提示することを IdP が期待するかどうかの指示が含まれる．

> A bound authenticator can be managed by either the IdP or the RP under different circumstances, as detailed in the sections below. An FAL3 assertion contains an indication of whether the IdP expects the subscriber to present a specific IdP-managed bound authenticator or an RP-managed bound authenticator at the RP to reach FAL3.


#### IdP 管理の bound authenticator (IdP-Managed Bound Authenticators)

[図9](sec6_assertions.md#fig-9)のように bound authenticator が IdP によって管理されている場合 ，オーセンティケータの一意の識別子（その公開鍵など）は，RP に提示されるアサーションに含まれ**なければならない(SHALL)**．RP は，加入者(subscriber)に，識別された bound authenticator の所有を証明するように促さ**なければならない(SHALL)**．

> When the bound authenticator is managed by the IdP as in [Fig. 9](sec6_assertions.md#fig-9), a unique identifier for the authenticator (such as its public key) **SHALL** be included in the assertion presented to the RP. The RP **SHALL** prompt the subscriber to prove possession of the identified bound authenticator.


[図9. IdP-Managed Bound Authenticators](sec6_assertions.md#fig-9){:name="fig-9"}
{:latex-ignore="true"}

![Diagram illustrating the use of bound authenticators managed at the IdP.]({{site.baseurl}}/{{page.collection}}/media/IdP-Managed-Bound-Auth.png 'IdP-Managed Bound Authenticators'){:latex-src="IdP-Managed-Bound-Auth.pdf" latex-fig="9" latex-place="h"}

IdP 管理の bound authenticator は，加入者(subscriber)が IdP への認証に使用する主要なオーセンティケータとは異っ**てもよい(MAY)**．IdP で管理される bound authenticator は，フィッシング耐性が**なければならず(SHALL)**，公開鍵インフラストラクチャなどの相互に信頼できるセキュリティフレームワークに基づいて RP によって個別に逆参照可能で**なければならない(SHALL)**．IdP 管理の bound authenticator を初めて処理するとき，RP は，オーセンティケーターが提示する情報の属性からのアカウント解決などを通じて，提示されているオーセンティケーターが加入者(subscriber)アカウントに関連付けられるのに適切であるかどうかを検証する**必要がある(SHOULD)**． 
> An IdP-managed bound authenticator **MAY** be distinct from the primary authenticator the subscriber uses to authenticate to the IdP. Bound authenticators managed at the IdP **SHALL** be phishing resistant and **SHALL** be independently dereferenceable by the RP based on a mutually-trusted security framework, such as a public-key infrastructure. When processing an IdP-managed bound authenticator for the first time, the RP **SHOULD** verify whether the authenticator being presented is appropriate to be associated with the subscriber account, such as through account resolution from the attributes in the authenticator's presented information.


たとえば，加入者(subscriber)は，多要素暗号化デバイスである，証明書が読み込まれたスマートカードを持つことができる．証明書は IdP と RP の両方に提示できるため，IdP は RP へ送る FAL3 アサーションに証明書の識別子を含めることができる．RP は加入者(subscriber)に，FAL3 に到達するためにスマートカードから証明書を提示するように要求する．

> For example, a subscriber could have a smart card loaded with a certificate, which is a multi-factor cryptographic device. Since the certificate can be presented to both the IdP and the RP, the IdP can include an identifier for the certificate in the FAL3 assertion to the RP. The RP would then prompt the subscriber to present the certificate from their smart card in order to reach FAL3.

「Holder of Key」(HoK) アサーションは，IdP 管理の bound authenticatorsの一例である．これは，IdP が RP で使用される加入者(subscriber)の鍵を認識しており，RP に提示されるアサーションに鍵情報が含まれているためである．

> "Holder of Key" (HoK) assertions are one example of IdP-managed bound authenticators, since the IdP knows the subscriber's key to be used at the RP and includes the key information in the assertion presented to the RP.


~~~
\clearpage
~~~
{:latex-literal="true"}

#### RP 管理の bound authenticator (RP-Managed Bound Authenticators)

bound authenticator が　[図10](sec6_assertions.md#fig-10) のようにRP によって管理される場合，IdP は，アサーションが FAL3 でバインドされたオーセンティケータとともに使用されるというインジケータをアサーションに含め**なければならない(SHALL)**．オーセンティケータの一意の識別子 （その公開鍵など）は，RP 加入者(subscriber)アカウントに格納し**なければならない(SHALL)**．

> When the bound authenticator is managed by the RP as in [Fig. 10](sec6_assertions.md#fig-10), the IdP **SHALL** include an indicator in the assertion that the assertion is to be used with a bound authenticator at FAL3. The unique identifier for the authenticator (such as its public key) **SHALL** be stored in the RP subscriber account.


[図10. RP-Managed Bound Authenticators](sec6_assertions.md#fig-10){:name="fig-10"}
{:latex-ignore="true"}

![Diagram illustrating the use of bound authenticators managed at the RP.]({{site.baseurl}}/{{page.collection}}/media/RP-Managed-Bound-Auth.png 'RP-Managed Bound Authenticators'){:latex-src="RP-Managed-Bound-Auth.pdf" latex-fig="10" latex-place="h"}

RP が FAL3 アサーションを正常に受け入れる前に，RP 加入者(subscriber)アカウントに bound authenticator が含まれていなければならない．これらのオーセンティケータは，RP または加入者(subscriber)のいずれかによって提供できる．それぞれの場合で，オーセンティケータの RP 加入者(subscriber)アカウントへの初期バインディングに適用される要件はわずかに異なる．
> Before an RP can successfully accept an FAL3 assertion, the RP subscriber account must include a bound authenticator. These authenticators can be provided by either the RP or the subscriber, with slightly different requirements applying to the initial binding of the authenticator to the RP subscriber account in each case.


RP 提供のオーセンティケーターの場合，RP の管理者は，FAL3 ログインで使用するために，加入者(subscriber)にオーセンティケーターを直接発行し**なければならない(SHALL)**．RP SHALL の管理者は， bound authenticator の一意の識別子を RP 加入者(subscriber) アカウントに格納し**なければならない(SHALL)**．RP の管理者は，オーセンティケータが発行される当事者が RP 加入者(subscriber)アカウントの識別された主体であることを，独立した手段を通じて決定し**なければならない(SHALL)**．
> For RP-provided authenticators, the administrator of the RP **SHALL** issue the authenticator to the subscriber directly for use with an FAL3 login. The administrator of the RP **SHALL** store a unique identifier for the bound authenticator in the RP subscriber account. The administrator of the RP **SHALL** determine through independent means that the party to which the authenticator is issued is the identified subject of the RP subscriber account.


加入者(subscriber)提供のオーセンティケーターで，RP 加入者(subscriber) アカウントに関連付けられている bound authenticator がない場合，RP は [図11](sec6_assertions.md#fig-11)に示すように，オーセンティケーター，加入者(subscriber)，および RP 加入者(subscriber)アカウント間の接続を確立するためにバインディング儀式を実行し**なければならない(SHALL)**．RP は，最初に FAL3 の他のすべての要件を満たすアサーションでフェデレーションを使用して，認証されたセッションを確立し**なければならない(SHALL)**．これには，アサーションが RP 管理の bound authenticator を使用して FAL3 で使用するためのものであるという指示が含まれる．加入者(subscriber)は，提案されたオーセンティケーターを提示して認証するようにすぐに求められ**なければならない(SHALL)**．オーセンティケータの提示が成功すると，RP はオーセンティケータの一意の識別子 (公開鍵など) を格納し**なければならず(SHALL)**，これをフェデレーション識別子に関連付けられた RP 加入者(subscriber)アカウントに関連付ける．加入者(subscriber)が適切なオーセンティケーターを正常に提示できなかった場合，バインディング儀式は失敗する．バインディング儀式のセッションは，5分以内にタイムアウトし**なければならない(SHALL)**．儀式中に使用されるセッションは，ログインのための認証済みセッションではない．バインディング儀式が正常に完了したら，RP はすぐに IdP から FAL3 の新しいアサーションを要求し**なければならない(SHALL)** （新しくバインドされたオーセンティケーター加入者(subscriber)に要求することを含む）．
> For subscriber-provided authenticators, if no bound authenticators are associated with the RP subscriber account, the RP **SHALL** perform a binding ceremony to establish the connection between the authenticator, the subscriber, and the RP subscriber account as shown in [Fig. 11](sec6_assertions.md#fig-11). The RP **SHALL** first establish an authenticated session using federation with an assertion that meets all the other requirements of FAL3, including an indication that the assertion is intended for use at FAL3 with an RP-managed bound authenticator. The subscriber **SHALL** immediately be prompted to present and authenticate with the proposed authenticator. Upon successful presentation of the authenticator, the RP **SHALL** store a unique identifier for the authenticator (such as its public key) and associate this with the RP subscriber account associated with the federated identifier. If the subscriber fails to successfully present an appropriate authenticator, the binding ceremony fails. The binding ceremony session **SHALL** have a timeout of five minutes or less. The session used during the ceremony is not an authenticated session for the purposes of logging in. Upon successful completion of the binding ceremony, the RP **SHALL** immediately request a new assertion from the IdP at FAL3, including prompting the subscriber for the newly-bound authenticator.


[図11. Binding Ceremony](sec6_assertions.md#fig-11){:name="fig-11"}
{:latex-ignore="true"}

![Sequence diagram of the steps involved in the binding ceremony used for bound authenticators managed at the RP and provided by the subscriber.]({{site.baseurl}}/{{page.collection}}/media/Binding-Ceremony.png 'Binding Ceremony'){:latex-src="Binding-Ceremony.pdf" latex-fig="11" latex-place="h"}

RP は，加入者(subscriber)が FAL3 で複数の加入者(subscriber)提供のオーセンティケーターをバインドできるように**してもよい(MAY)**．これが当てはまり，RP 加入者アカウントに 1 つ以上の既存の bound authenticator がある場合，バインディング儀式は FAL3 に到達する既存の機能を利用する．加入者(subscriber)は，最初に FAL3 に到達するために既存の bound authenticator を提示するように求めら**なければならない(SHALL)**．認証が成功すると，RP は直ちに加入者(subscriber)に新しく bound authenticator を要求し**なければならない(SHALL)**．
> An RP **MAY** allow a subscriber to bind multiple subscriber-provided authenticators at FAL3. If this is the case, and the RP subscriber account has one or more existing bound authenticators, the binding ceremony makes use of the existing ability to reach FAL3. The subscriber **SHALL** first be prompted to present an existing bound authenticator to reach FAL3. Upon successful authentication, the RP **SHALL** immediately prompt the subscriber for the newly-bound authenticator.



RP は，加入者(subscriber)がバインドされた加入者(subscriber)提供のオーセンティケーターを RP 加入者(subscriber)アカウントからバインド解除することを許可**してもよい(MAY)**．これにより，そのオーセンティケーターを FAL3 に使用する機能が削除される．bound authenticator がバインド解除された場合，RP は加入者(subscriber)の現在のすべての FAL3 セッションを終了し**なければならず(SHALL)**，IdP からの加入者(subscriber)の再認証を要求し**なければならない(SHALL)**．注記：多くの場合，加入者(subscriber)は，オーセンティケーターの紛失または侵害を考慮して，bound authenticator のバインドを解除する必要がある．したがって，加入者(subscriber)は，バインド解除プロセス中にオーセンティケーターにアクセスできない．
> An RP **MAY** allow a subscriber to unbind a bound subscriber-provided authenticator from their RP subscriber account, thereby removing the ability to use that authenticator for FAL3. When a bound authenticator is unbound, the RP **SHALL** terminate all current FAL3 sessions for the subscriber and **SHALL** require reauthentication of the subscriber from the IdP. Note that in many cases, a subscriber will need to unbind a bound authenticator to account for a lost or compromised authenticator, and the subscriber will therefore not have access to the authenticator during the unbinding process.


~~~
\clearpage
~~~
{:latex-literal="true"}

次のイベントのいずれかが発生した場合，RP は out-of-band のメカニズムを通じて加入者(subscriber)に通知し**なければならず(SHALL)**，共有信号システム（[Sec. 5.7](sec5_federation.md#shared-signals) 参照）を使用して IdP に通知する**必要がある(SHOULD)**．

- 新しいオーセンティケータが RP 加入者(subscriber)アカウントにバインドされた．
- 既存の bound authenticator が RP 加入者(subscriber)アカウントからバインド解除された．

> The RP **SHALL** notify the subscriber through an out-of-band mechanism, and **SHOULD** notify the IdP using a shared signaling system (see [Sec. 5.7](sec5_federation.md#shared-signals)), if any of the following events occur:
> 
> - A new authenticator is bound to the RP subscriber account.
> - An existing bound authenticator is unbound from the RP subscriber account.


たとえば，加入者(subscriber)は，オーセンティケーターとして単一要素暗号化デバイスを持つことができる．このオーセンティケーターは，名前ベースのフィッシング耐性を使用するため，IdP と RP は，それぞれの場所で使用されたときに異なる鍵を認識する．ここで説明したバインディング儀式を使用して，RP は，加入者(subscriber)がこのデバイスを FAL3 で bound authenticator として使用できるようにする．RP は，IdP から この加入者(subscriber)の FAL3 のアサーションを確認するたびに，加入者(subscriber)にこのオーセンティケーターを要求する．
> For example, a subscriber could have a single factor cryptographic device as an authenticator. This authenticator uses name-based phishing resistance so the IdP and RP would see different keys when used in each location. The RP can use a binding ceremony as described here to allow the subscriber to use this device as a bound authenticator at FAL3. The RP will prompt the subscriber for this authenticator whenever it sees an assertion for this subscriber at FAL3 from the IdP.


#### bound authenticator の処理 (Processing Bound Authenticators)

RP が bound authenticator に関連付けられたアサーションを受信すると，加入者(subscriber)は bound authenticator を所有していることを RP に直接証明する． IdP での主要な認証と RP でのフェデレーション認証は別々に処理される．加入者(subscriber)は，IdP での主要な認証に同じオーセンティケーターを使用でき，RP で bound authenticator として使用できるが，これらが同じであるという前提はない．
> When the RP receives an assertion associated with a bound authenticator, the subscriber proves possession of the bound authenticator directly to the RP. The primary authentication at the IdP and the federated authentication at the RP are processed separately. While the subscriber could use the same authenticator during the primary authentication at the IdP and as the bound authenticator at the RP, there is no assumption that these will be the same.


次の要件は，bound authenticator に関連付けられたすべてのアサーションに適用される．

1. 加入者(subscriber)は，アサーション自体の提示に加えて，bound authenticator の所有を RP に証明し**なければならない(SHALL)**．
2. オーセンティケーターが IdP で管理されている場合，アサーション内の特定のオーセンティケータへの参照は，アサーション内の他のすべての情報と同じレベルで信頼され**なければならない(SHALL)**．
3. オーセンティケーターが IdP で管理されている場合，アサーションを提示する際に，オーセンティケータとして使用される暗号化していない秘密鍵または対称鍵を含めては**ならない(SHALL NOT)**．
4. RP は，bound authenticator に加えて，アサーションを処理および検証し**なければならない(SHALL)**．
5. bound authenticator で認証に失敗した場合，RP でエラーにし**なければならない(SHALL)**．

> The following requirements apply to all assertions associated with a bound authenticator:
> 
> 1. The subscriber **SHALL** prove possession of the bound authenticator to the RP, in addition to presentation of the assertion itself.
> 2. If the authenticator is managed at the IdP, reference to a given authenticator found within an assertion **SHALL** be trusted at the same level as all other information within the assertion.
> 3. If the authenticator is managed at the IdP, the assertion **SHALL NOT** include an unencrypted private or symmetric key to be used as an authenticator with the presentation.
> 4. The RP **SHALL** process and validate the assertion in addition to the bound authenticator.
> 5. Failure to authenticate with the bound authenticator **SHALL** result in an error at the RP.




## アサーションの保護 (Assertion Protection)

バインディングメカニズム（[Sec. 6.1](sec6_assertions.md#assertion-binding) で説明）またはそれらを取得するために使用されるフェデレーションモデル（[Sec. 5.1](sec5_federation.md#trust-agreement) で説明）とは無関係に，アサーションには，攻撃者が有効なアサーションを作成したり，キャプチャしたアサーションを異なる RP で再利用したりするのを防ぐための一連の保護を含め**なければならない(SHALL)**．必要な保護は，検討中のユースケースの詳細によって異なる．具体的な保護を示す．
> Independent of the binding mechanism (discussed in [Sec. 6.1](sec6_assertions.md#assertion-binding)) or the federation model used to obtain them (described in [Sec. 5.1](sec5_federation.md#trust-agreement)), assertions **SHALL** include a set of protections to prevent attackers from manufacturing valid assertions or reusing captured assertions at disparate RPs. The protections required are dependent on the details of the use case being considered, and specific protections are listed here.



### アサーション識別子 (Assertion Identifier) {#assertion-id}
アサーションは，ターゲットの RP が一意に識別することを許可するのに十分に一意で**なければならない(SHALL)**．アサーションは，埋め込まれたナンス，発行タイムスタンプ，アサーション識別子，またはこれらまたは他の手法の組み合わせを使用して，これを達成**してもよい(MAY)**．
> Assertions **SHALL** be sufficiently unique to permit unique identification by the target RP. Assertions **MAY** accomplish this by use of an embedded nonce, issuance timestamp, assertion identifier, or a combination of these or other techniques.


### 署名付きアサーション (Signed Assertion) {#signed-assertion}

アサーションは，発行者 (IdP) によって暗号署名され**なければならない(SHALL)**．RP は，発行者の鍵に基づいて，アサーションのデジタル署名または MAC を検証し**なければならない(SHALL)**．この署名は，アサーション識別子，発行者，対象者，主体，および有効期限を含むアサーション全体をカバーし**なければならない(SHALL)**．

> Assertions **SHALL** be cryptographically signed by the issuer (IdP). The RP **SHALL** validate the digital signature or MAC of each such assertion based on the issuer's key. This signature **SHALL** cover the entire assertion, including its identifier, issuer, audience, subject, and expiration.

アサーション署名は，非対称鍵を使用するデジタル署名か，RP と発行者の間で共有される対称鍵を使用する MAC のいずれかで**なければならない(SHALL)**．IdP がこの目的で使用する共有対称鍵は，アサーションを送信する RP ごとに独立してい**なければならず(SHALL)**，通常は RP の登録中に確立される．デジタル署名を検証するための公開鍵は，安全な方法で RP に転送し**なければならず(SHALL)**，実行時に安全な方法 (IdP によってホストされる HTTPS URL など) で RP によって取得され**てもよい(MAY)**．承認された暗号化を使し**なければならない(SHALL)**．

> The assertion signature **SHALL** either be a digital signature using asymmetric keys or a MAC using a symmetric key shared between the RP and issuer. Shared symmetric keys used for this purpose by the IdP **SHALL** be independent for each RP to which they send assertions, and are normally established during registration of the RP. Public keys for verifying digital signatures **SHALL** be transferred to the RP in a secure manner, and **MAY** be fetched by the RP in a secure fashion at runtime, such as through an HTTPS URL hosted by the IdP. Approved cryptography **SHALL** be used.




### 暗号化されたアサーション (Encrypted Assertion) {#encrypted-assertion}
暗号化されたアサーションは，アサーションのコンテンツが意図しない第三者によって読み取られることを防ぎ，対象の RP のみがアサーションを読み取ることができるようにする．アサーションの暗号化には，主に2つの利点がある．目的の RP 以外はアサーションの内容を見ることができない点と，対象の RP 以外はアサーションを使用できない点である．

> Encrypted assertions protect the contents of the assertion from being read by unintended parties, ensuring that only the targeted RP is able to read the assertion. Encrypting assertions provides two primary benefits: the assertion contents cannot be seen by any party other than the intended RP, and the assertion cannot be used by any RP other than the targeted one.

アサーションを暗号化する場合，IdP は RP の公開鍵または共有対称鍵のいずれかを使用してアサーションの内容を暗号化し**なければならない(SHALL)**．IdP がこの目的で使用する共有対称鍵は，アサーションを送信する RP ごとに独立してい**なければならず(SHALL)**，通常は RP の登録中に確立される．暗号化のための公開鍵は，IdP に安全に転送され**なければならず(SHALL)**，RP によってホストされる HTTPS URL などを通じて，実行時に安全な方法で IdP によって取得され**てもよい(MAY)**．

> When encrypting assertions, the IdP **SHALL** encrypt the contents of the assertion using either the RP's public key or a shared symmetric key. Shared symmetric keys used for this purpose by the IdP **SHALL** be independent for each RP to which they send assertions, and are normally established during registration of the RP. Public keys for encryption **SHALL** be securely transferred to the IdP and **MAY** be fetched by the IdP in a secure fashion at runtime, such as through an HTTPS URL hosted by the RP.


アサーションのすべての暗号化は，承認された暗号化を使用し**なければならない(SHALL)**．

> All encryption of assertions **SHALL** use approved cryptography.

個人を特定できる情報がアサーションに含まれ，アサーションがブラウザなどの仲介者によって処理される場合，フェデレーションプロトコルはアサーションを暗号化して，アサーション内の機密情報が意図しない関係者に漏洩するのを防が**なければならない(SHALL)**．たとえば，SAML のアサーションは XML暗号化を使用して暗号化でき，OpenID Connect の IDトークンは JSON Web 暗号化 (JWE) を使用して暗号化できる．

> When personally-identifiable information is included in the assertion and the assertion is handled by intermediaries such as a browser, the federation protocol **SHALL** encrypt assertions to protect the sensitive information in the assertion from leaking to unintended parties. For example, a SAML assertion can be encrypted using XML-Encryption, or an OpenID Connect ID Token can be encrypted using JSON Web Encryption (JWE).


### 対象者の制限 (Audience Restriction)

アサーションは，それが発行されたアサーションの意図された対象者であるかどうかを RP が認識できるようにするために，対象者制限技術を使用し**なければならない(SHALL)**．すべての RP は，ある RP に対して生成されたアサーションを，別の RP でインジェクションやリプレイで利用されることを防ぐために，アサーションの対象者に RP の識別子が含まれていることを確認し**なければならない(SHALL)**．
> Assertions **SHALL** use audience restriction techniques to allow an RP to recognize whether or not it is the intended target of an issued assertion. All RPs **SHALL** check that the audience of an assertion contains an identifier for their RP to prevent the injection and replay of an assertion generated for one RP at another RP.


### ペアワイズ仮名識別子 (Pairwise Pseudonymous Identifiers) {#ppi}

状況によっては，共通の識別子を使用して加入者アカウントが複数の RP で簡単にリンクされるのを防ぐことが望ましい場合がある．ペアワイズ仮名識別子 (PPI) を使用すると，IdP は単一の加入者(subscriber)アカウントでも，異なる RP には複数の異なるフェデレーション識別子を提供することができる．これにより，さまざまな RP が共謀して，フェデレーション識別子を使用して加入者(subscriber)を追跡することが防止される．
> In some circumstances, it is desirable to prevent the subscriber account from being easily linked at multiple RPs through use of a common identifier. A pairwise pseudonymous identifier (PPI) allows an IdP to provide multiple distinct federated identifiers to different RPs for a single subscriber account. This prevents different RPs from colluding together to track the subscriber using the federated identifier.


#### 一般的な要件 (General Requirements)

RP 向けに，IdP によって生成されたアサーション内でペアワイズ仮名識別子を使用する場合，IdP は以下の [Sec. 6.2.5.2](sec6_assertions.md#ppi-gen) で説明されているように，RP ごとに異なるフェデレーション識別子を生成する必要がある．
> When using pairwise pseudonymous identifiers within the assertions generated by the IdP for the RP, the IdP **SHALL** generate a different federated identifier for each RP as described in [Sec. 6.2.5.2](sec6_assertions.md#ppi-gen) below.


PPI が属性と一緒に RP と共に使用される場合，依然として，複数の共謀 RP が，これらの属性を使用するシステム間の相互関係によって加入者(subscriber)を再識別できる可能性がある．たとえば，2つの独立した RP がそれぞれ，異なるペアワイズ仮名識別子で識別された同じ加入者(subscriber)を確認した場合でも，名前，メールアドレス，住所，それぞれのアサーション内でペアワイズ仮名識別子と共に提示されるその他の識別属性を比較することにより，加入者(subscriber)が同一人物であると判断することができる．プライバシーポリシーは，そのような相関を禁止する**必要があり(SHOULD)**，ペアワイズ仮名識別子は，属性相関を管理する作業を増やすことで，これらのポリシーの有効性を高めることができる．
> When PPIs are used with RPs alongside attributes, it may still be possible for multiple colluding RPs to re-identify a subscriber by correlation across systems using these identity attributes. For example, if two independent RPs each see the same subscriber identified with different pairwise pseudonymous identifiers, they could still determine that the subscriber is the same person by comparing the name, email address, physical address, or other identifying attributes carried alongside the pairwise pseudonymous identifier in the respective assertions. Privacy policies **SHOULD** prohibit such correlation, and pairwise pseudonymous identifiers can increase effectiveness of these policies by increasing the administrative effort in managing the attribute correlation.


注記：プロキシは，加入者(subscriber)がアクセスしている RP を IdP が認識できないようにする可能性があるため，プロキシされたフェデレーションモデルでは，最初の IdP は最終的な RP のペアワイズ仮名識別子を生成できない可能性がある．このような状況では，通常，IdP とフェデレーションプロキシ自体の間でペアワイズ仮名識別子が確立される．IdP として機能するプロキシ自体が，ペアワイズ仮名識別子を RP に提供できる．プロトコルによっては，フェデレーションプロキシは，アイデンティティプロトコルを機能させるために，ペアワイズ仮名識別子を IdP からの関連付けられた識別子にマッピングし直す必要がある場合がある．そのような場合，プロキシは，どのペアワイズ仮名識別子が異なる RP で同じ加入者(subscriber)を表しているかを追跡および判断することができる．プロキシは，ペアワイズ仮名識別子とその他の識別子との間のマッピングを第三者に開示しては**ならない(SHALL NOT)**．また，フェデレーション認証，関連する詐欺の軽減，法律または法的手続きの遵守，特定のユーザーからの情報の要求以外の目的で情報を使用しては**ならない(SHALL NOT)**．
> Note that in a proxied federation model, the initial IdP may be unable to generate a pairwise pseudonymous identifier for the ultimate RP, since the proxy could blind the IdP from knowing which RP is being accessed by the subscriber. In such situations, the pairwise pseudonymous identifier is generally established between the IdP and the federation proxy itself. The proxy, acting as an IdP, can itself provide pairwise pseudonymous identifiers to downstream RPs. Depending on the protocol, the federation proxy may need to map the pairwise pseudonymous identifiers back to the associated identifiers from upstream IdPs in order to allow the identity protocol to function. In such cases, the proxy will be able to track and determine which pairwise pseudonymous identifiers represent the same subscriber at different RPs. The proxy **SHALL NOT** disclose the mapping between the pairwise pseudonymous identifier and any other identifiers to a third party or use the information for any purpose other than federated authentication, related fraud mitigation, to comply with law or legal process, or in the case of a specific user request for the information.


#### ペアワイズ仮名識別子の生成 (Pairwise Pseudonymous Identifier Generation) {#ppi-gen}

ペアワイズ仮名識別子は，加入者(subscriber)に関する識別情報を含まないようにし**なければならない(SHALL)**．また，加入者(subscriber)を特定する情報にアクセスできる当事者が推測できないものにし**なければならない(SHALL)**．ペアワイズ仮名識別子は，ランダムに生成され，IdP によって加入者(subscriber)に割り当てられ**てもよい(MAY)**．あるいは，不可逆な方法で生成され,推測不可能な方法である場合 (たとえば，秘密鍵でハッシュ関数を使用するなど)，他の加入者(subscriber)情報から生成し**てもよい(MAY)**．
> Pairwise pseudonymous identifiers **SHALL** contain no identifying information about the subscriber. They **SHALL** also be unguessable by a party having access to some information identifying the subscriber. Pairwise pseudonymous identifiers **MAY** be generated randomly and assigned to subscribers by the IdP or **MAY** be derived from other subscriber information if the derivation is done in an irreversible, unguessable manner (e.g., using a keyed hash function with a secret key). 


通常，識別子は1つのエンドポイントのペア (例: IdP-RP) によってのみ認識され，使用され**なければならない(SHALL)**．IdP は，複数の RP の要求に応じて，複数の RP で加入者(subscriber)に同じ識別子を生成し**てもよい(MAY)**．下記のような場合である．

* 信頼の合意(trust agreement)は，RP の特定のファミリーの共有仮名識別子を規定している．
* authorized party は，共有仮名識別子の使用に同意し，その使用について通知されている．
* RP に，共有のセキュリティドメインや共有の法的所有権など，運用上の必要性を正当化する実証可能な関係がある．
* 識別子を共有するすべての RP は，そのような方法で関連付けられることに同意する (つまり，ある RP は，他の RP の同意なしに，別の RP の PPI を要求することはできない)．

> Normally, the identifiers **SHALL** only be known by and used by one pair of endpoints (e.g., IdP-RP). An IdP **MAY** generate the same identifier for a subscriber at multiple RPs at the request of those RPs, provided:
> 
> * The trust agreement stipulates a shared pseudonymous identifier for a specific family of RPs;
> * The authorized party consents to and is notified of the use of a shared pseudonymous identifier;
> * Those RPs have a demonstrable relationship that justifies an operational need for the correlation, such as a shared security domain or shared legal ownership; and
> * All RPs sharing an identifier consent to being correlated in such a manner (i.e., one RP cannot request to have another RP's PPI without that other RP's knowledge and consent).


RP は，共通識別子の要求に関連するプライバシーリスクを考慮するために，プライバシーリスク評価を実施し**なければならない(SHALL)**．プライバシーに関するその他の考慮事項は，[Sec. 9.2](sec9_privacy.md#notice) を参照．

> The RPs **SHALL** conduct a privacy risk assessment to consider the privacy risks associated with requesting a common identifier. See [Sec. 9.2](sec9_privacy.md#notice) for further privacy considerations.

IdP は，意図した RP のみが関連付けられるようにし**なければならない(SHALL)**．そうしない場合，不正な RP が相関する RP の一部として装うことで，相関する RP の仮名識別子を知ることができてしまう．

> The IdP **SHALL** ensure that only intended RPs are correlated; otherwise, a rogue RP could learn of the pseudonymous identifier for a set of correlated RPs by fraudulently posing as part of that set.




## アイデンティティAPI (Identity APIs) {#s-identity-api}

プロファイル情報を含む加入者(subscriber)に関する属性は，_アイデンティティAPI_ として知られる保護された _属性API_ を通じて RP に提供され**てもよい(MAY)**．RP は，アサーションと連携して，フェデレーショントランザクション中に アイデンティティAPI への制限付きアクセスを許可される． たとえば，OpenID Connect では，UserInfo エンドポイントは，加入者(subscriber)に関する属性を取得するための標準化された アイデンティティAPI を提供する．この API は，OpenID Connect のアサーションである ID トークンとともに RP に発行される OAuth 2.0 アクセス トークンによって保護される．フェデレーションアサーションと共に アイデンティティAPI を使用すると，フェデレーションシステムの全体的なセキュリティ，プライバシー，および効率性にいくつかの利点がある．
> Attributes about the subscriber, including profile information, **MAY** be provided to the RP through a protected _attribute API_ known as the _identity API_. The RP is granted limited access to the identity API during the federation transaction, in concert with the assertion. For example, in OpenID Connect, the UserInfo Endpoint provides a standardized identity API for fetching attributes about the subscriber. This API is protected by an OAuth 2.0 Access Token, which is issued to the RP along with OpenID Connect's assertion, the ID Token. The use of identity APIs along with federation assertions has several advantages for the overall security, privacy, and efficiency of the federation system. 


アイデンティティAPI で属性を使用できるようにすることで，IdP はアサーションを使用して多くの情報を RP に伝える必要がなくなる．これは，機密属性をアサーション自体で保持する必要がないことを意味するだけでなく，アサーションを小さくし，RP による処理を容易にする．アサーションの内容は，必須フィールド (例えば，一意の主体識別子) と，提示される即時認証イベントに関する情報に限定することができる．
> By making attributes available at an identity API, the IdP no longer has to use the assertion to convey as much information to the RP. This not only means that sensitive attributes do not have to be carried in the assertion itself, it also makes the assertion smaller and easier to process by the RP. The contents of the assertion can then be limited to essential fields (e.g., unique subject identifiers) and information about the immediate authentication event being asserted.


RP は，[Sec. 5.4](../sec5_federation.md#rp-account)で説明されているように，RP 加入者(subscriber)アカウントで IdP によって提供される属性をキャッシュすることがよくある．アサーションで提供される属性はログインごとに渡される．RP は属性が要求される前に加入者(subscriber)の アイデンティティ を知らないため，IdP はアサーション自体にできるだけ多くの情報を含めるようにしようとする．ただし，加入者(subscriber)の属性のほとんどはその後のログイン間で変更されないため，この情報は冗長になる．結果として，これらの変更される頻度の低い属性のほとんどは，代わりに，必要な場合にのみ RP によって呼び出される アイデンティティAPI を介して使用できるようになる．IdP は，加入者(subscriber)の属性が加入者(subscriber)アカウントで最後に更新された時期をアサーションで示すことができる．これにより，RP は属性を新たにフェッチする必要があるかどうか，または それらの RP 加入者(subscriber)アカウントの属性は十分であるかどうかを判断できまる．
> The RP often caches attributes provided by the IdP in an RP subscriber account, discussed in [Sec. 5.4](../sec5_federation.md#rp-account). Attributes provided in the assertion are passed on every login, and since the RP does not know the identity of the subscriber before the attribute is requested, the IdP is incentivized to include as much information as possible in the assertion itself. However, most of a subscriber's attributes will not change in between subsequent logins, making this information redundant. As a consequence, most of these more-stable attributes can instead be made available through an identity API that is called by the RP only when necessary. The IdP can indicate in the assertion when the last time the subscriber's attributes have been updated in the subscriber account, allowing the RP to decide if it needs to fetch the attributes anew or if those in the RP subscriber account are sufficient.


アイデンティティAPI へのアクセスは時間が制限され**なければならない(SHALL)**．制限される時間は，アサーションの有効期間および RP での認証済みセッションの有効期間とは別のものである．関連付けられた有効なアサーションのない RP による アイデンティティAPI へのアクセスでは，RP で認証されたセッションを確立ために十分であっては**ならない(SHALL NOT)**．．
> Access to the identity API **SHALL** be time limited. The time limitation is separate from the validity time window of the assertion and the lifetime of the authenticated session at the RP. Access to an identity API by the RP without an associated valid assertion **SHALL NOT** be sufficient for the establishment of an authenticated session at the RP.


特定の アイデンティティAPI を用意することで，IdP がアサーションを作成できるすべての加入者(subscriber)に属性を提供できることが期待されている．ただし，アイデンティティAPI へのアクセスがフェデレーショントランザクションのコンテキスト内で許可される場合，アイデンティティAPI によって提供される属性は，関連付けられたアサーションで識別される単一の加入者(subscriber)のみに関連付けられ**なければならない(SHALL)**．アイデンティティAPI が IdP によってホストされている場合，返される属性には加入者(subscriber)の主体識別子が含まれ**なければならない(SHALL)**．これにより，RP はアサーションの主体を返された属性に積極的に関連付けることができる．注記：[Sec. 5.4.1](sec5_federation.md#provisioning) で説明されているように，属性 API へのアクセスが RP 加入者(subscriber)アカウントの事前プロビジョニングの一部として提供される場合，RP は通常，フェデレーショントランザクションのコンテキスト外でアイデンティティAPI への制限のないアクセスが許可され，これらの要件は適用されない．
> A given identity API deployment is expected to be capable of providing attributes for all subscribers for whom the IdP can create assertions. However, when access to the identity API is granted within the context of a federation transaction, the attributes provided by an identity API **SHALL** be associated with only the single subscriber identified in the associated assertion. If the identity API is hosted by the IdP, the returned attributes **SHALL** include the subject identifier for the subscriber. This allows the RP to positively correlate the assertion's subject to the returned attributes. Note that when access to an attribute API is provided as part of pre-provisioning of RP subscriber accounts as discussed in [Sec. 5.4.1](sec5_federation.md#provisioning), the RP is usually granted blanket access to the identity API outside the context of the federated transaction and these requirements do not apply.


### 属性プロバイダー(Attribute Providers) {#s-attribute-providers}

フェデレーションで使用されるほとんどの属性 API は IdP の一部としてホストされるが，IdP が外部属性プロバイダーによってホストされる アイデンティティAPI へのアクセスを許可することも可能である．これらのサービスは，IdP から直接利用できる属性に加えて，更なる加入者(subscriber)に関する属性を提供する．

> While most attribute APIs used in federation are hosted as part of the IdP, it is also possible for the IdP to grant access to identity APIs hosted by external attribute providers. These services provide attributes about the subscriber in addition to those made available directly from the IdP.

IdP が属性プロバイダーへのアクセスを許可するとき，IdP は，属性プロバイダーから返された情報が，関連付けられたアサーションで識別された加入者(subscriber)に関連付けられていることを明示的に宣言する．信頼の合意(trust agreement)の目的上，IdP は属性 API の正確さと内容について責任を負う．

> When the IdP grants access to an attribute provider, the IdP is making an explicit statement that the information returned from the attribute provider is associated with the subscriber identified in the associated assertion. For the purposes of the trust agreement, the IdP is the responsible party for the accuracy and content of the attribute API.


属性プロバイダーによって返される属性は，IdP から直接返される属性とは無関係であると想定されるため，異なる識別子，形式，またはスキーマを使用**してもよい(MAY)**．RP は，識別された属性プロバイダーが，該当する信頼の合意(trest agreement)の下で，存在する種類の属性について提供することを許容されているか確認し**なければならない(SHALL)**．

> The attributes returned by the attribute provider are assumed to be independent of those returned directly from the IdP, and as such **MAY** use different identifiers, formats, or schemas. The RP **SHALL** verify that the identified attribute provider is capable of providing the kinds of attributes that are present, under the auspices of the applicable trust agreement.

たとえば，IdP が，フェデレーションプロセスの一部として加入者(subscriber)の医師免許情報へのアクセスを提供している場合，IdP が免許の状態を直接提示する代わりに，IdP は，医師免許機関の加入者(subscriber)のレコードへの RP からのアクセスを提供する．この場合，免許情報は IdP が使用する主体識別子と同じものを使用しない可能性があるが，RP は現在の加入者(subscriber)と免許情報との間に強力な関連付けを作成できる．

> For example, an IdP could provide access to a subscriber's medical license information as part of the federation process. Instead of the IdP asserting the license status directly, the IdP provides the RP access to a record for the subscriber at a medical licensure agency. The RP can make a strong association between the current subscriber and the license record, even though the license record will not likely use the same subject identifier that the IdP does in this case.
