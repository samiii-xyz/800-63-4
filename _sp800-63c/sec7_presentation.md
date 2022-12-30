---
layout: default
title: Assertion Presentation
navOrder: 7
navTitle: Presentation
permalink: /sp800-63c/presentation/
anchor: presentation
section: 7
---

# アサーションの提示 (Assertion Presentation) {#presentation}

*This section is normative.*

プロトコルの詳細に応じて，RP と IdP は 2つの方法で相互に通信する．これにより，IdP から RP にアサーションを渡すことができる 2つの異なる方法が可能になる．

  - 加入者(subscriber)と加入者(subscriber)のブラウザーを含むリダイレクトによる *フロントチャネル*．
  - 加入者(subscriber)を直接含まない，RP と IdP 間の直接接続を介した *バックチャネル*．

各モデルにはトレードオフがあるが，それぞれにアサーションの適切な検証が必要である．[Sec. 5.1.3](sec5_federation.md#proxied) で詳細に説明されているように，アサーションは，異なる提示方法を使用して IdP と RP 間のフェデレーションを促進するためにプロキシされ**てもよい(MAY)**．

<details>
<summary>原文</summary>
Depending on the specifics of the protocol, the RP and the IdP communicate with each other in two ways, which lends to two different ways in which an assertion can be passed from the IdP to the RP:

 - The *front channel*, through redirects involving the subscriber and the subscriber's browser; or
 - The *back channel*, through a direct connection between the RP and IdP, not involving the subscriber directly.

There are tradeoffs with each model, but each requires the proper validation of the assertion. Assertions **MAY** also be proxied to facilitate federation between IdPs and RPs using different presentation methods, as discussed in detail in [Sec. 5.1.3](sec5_federation.md#proxied).
</details>

## バックチャネル (Back-Channel Presentation) {#back-channel}

*バックチャネル*の提示モデルでは，加入者(subscriber)は，通常はフロントチャネルを通じて，RP に提示するためのアサーション参照を与えられる．アサーション参照自体には加入者(subscriber)に関する情報は含まれておらず，攻撃者による改ざんや偽造に対して耐性が**なければならない(SHALL)**．RP は，アサーションを取得するために，通常は RP 自体の認証とともに，アサーション参照を IdP に提示する．

<details>
<summary>原文</summary>
In the *back-channel* presentation model, the subscriber is given an assertion reference to present to the RP, generally through the front channel. The assertion reference itself contains no information about the subscriber and **SHALL** be resistant to tampering and fabrication by an attacker. The RP presents the assertion reference to the IdP, usually along with authentication of the RP itself, to fetch the assertion.
</details>
 
[Figure 12. Back-channel Presentation](sec7_presentation.md#fig-63cSec7-Figure1){:name="fig-12"}
{:latex-ignore="true"}

![Diagram of the back-channel presentation model for communicating assertions to the RP.]({{site.baseurl}}/{{page.collection}}/media/back-channel.png 'Back-channel Presentation'){:style="width:614px;height:600px;;min-width:614px;min-height:600px;" latex-src="back-channel.png" latex-fig="12" latex-place="h"}


[図12](sec7_presentation.md#fig-12) に示すように，バックチャネルの提示モデルは次の3つのステップで構成される．

1. IdP は，フロントチャネルを介して加入者(subscriber)にアサーション参照を送信する．
2. 加入者(subscriber)は，フロントチャネルを介して RP にアサーション参照を送信する．
3. RP は，バックチャネルを介して，アサーション参照と RP クレデンシャルを IdP に提示する．IdP は資格情報を検証し，アサーションを返す．

<details>
<summary>原文</summary>
As shown in [Figure 12](sec7_presentation.md#fig-12), the back-channel presentation model consists of three steps:

1. The IdP sends an assertion reference to the subscriber through the front channel.
2. The subscriber sends the assertion reference to the RP through the front channel.
3. The RP presents the assertion reference and its RP credentials to the IdP through the back channel. The IdP validates the credentials and returns the assertion.
</details>

アサーション参照:

  1. 単一の RP による使用に制限され**なければならない(SHALL)**．
  2. 使い捨てで**なければならない(SHALL)**．
  3. 時間制限が**なければならなず(SHALL)**，有効期間が数分以内である**必要がある(SHOULD)**．
  4. RP の認証とともに IdP に提示し**なければならない(SHALL)**．
  5. 少なくとも 128 ビットのエントロピーを含ま**なければならない(SHALL)**．

<details>
<summary>原文</summary>
The assertion reference:

 1. **SHALL** be limited to use by a single RP.
 2. **SHALL** be single-use.
 3. **SHALL** be time limited, and **SHOULD** have a lifetime of no more than a small number of minutes in length.
 4. **SHALL** be presented along with authentication of the RP to the IdP.
 5. **SHALL** contain at least 128 bits of entropy.
</details>

~~~
\clearpage
~~~
{:latex-literal="true"}

このモデルでは，RP は IdP からのアサーションを直接要求し，第三者 (加入者(subscriber)自身を含む) による傍受と操作の可能性を最小限に抑える．
<details>
<summary>原文</summary>
In this model, the RP directly requests the assertion from the IdP, minimizing chances of interception and manipulation by a third party (including the subscriber themselves).
</details>

この方法は，RP が IdP にアサーション自体に含まれていない加入者(subscriber)に関する追加の属性を照会することも容易にする．これは，最初の認証トランザクションが完了した後，ユーザーを IdP に送り返すことなく，バックチャネル通信が引き続き発生する可能性があるためである．[Sec. 6.3](sec6_assertions.md#s-identity-api) で説明されている通り，この照会は，アイデンティティAPIを使う際に発生する．
<details>
<summary>原文</summary>
This method also facilitates the RP querying the IdP for additional attributes about the subscriber not included in the assertion itself, since back-channel communication can continue to occur after the initial authentication transaction has been completed without sending the user back to the IdP. This query occurs using an identity API, as described in [Sec. 6.3](sec6_assertions.md#s-identity-api).
</details>

バックチャネル方式では，より多くのネットワークトランザクションが必要になるが，情報はそれを必要とする関係者のみに限定される．RP は IdP からのみ直接アサーションを取得することを期待しているため，攻撃に面する機会が減少する．したがって，アサーションを RP に直接インジェクションすることはより困難であり，この表示方法は FAL2 以降に推奨される．
<details>
<summary>原文</summary>
More network transactions are required in the back-channel method, but the information is limited to only those parties that need it. Since an RP is expecting to get an assertion only from the IdP directly, the attack surface is reduced. Consequently, it is more difficult to inject assertions directly into the RP and this presentation method is recommended for FAL2 and above.
</details>

RP は，クロスサイトスクリプティングに対する保護またはその他の承認された技術を使用して，製造またはキャプチャされたアサーション参照のインジェクションから自身を保護し**なければならない(SHALL)**．
<details>
<summary>原文</summary>
The RP **SHALL** protect itself against injection of manufactured or captured assertion references by use of cross-site scripting protection or other accepted techniques.
</details>

IdP から加入者(subscriber)へのアサーション参照の伝達，および加入者(subscriber)から RP へのアサーション参照の伝達は，認証され保護されたチャネルを介して行われ**なければならない(SHALL)**．RP から IdP へのアサーション参照の伝達，および IdP から RP へのアサーションは，認証され保護されたチャネルを介して行われ**なければならない(SHALL)**．
<details>
<summary>原文</summary>
Conveyance of the assertion reference from the IdP to the subscriber, as well as from the subscriber to the RP, **SHALL** be made over an authenticated protected channel. Conveyance of the assertion reference from the RP to the IdP, as well as the assertion from the IdP to the RP, **SHALL** be made over an authenticated protected channel.
</details>

アサーション参照が提示される場合，IdP は，アサーション参照を提示する当事者が認証を要求した当事者と同じであることを検証し**なければならない(SHALL)**．IdP は，アサーション参照を IdP に提示する際に RP が自身を認証することを要求するか，他の同様の手段を使用してこれを行うことができる．(プロトコルの動的な RP の検証方法については，[[RFC7636]](references.md#ref-RFC7636) を参照)．
<details>
<summary>原文</summary>
When assertion references are presented, the IdP **SHALL** verify that the party presenting the assertion reference is the same party that requested the authentication. The IdP can do this by requiring the RP to authenticate itself when presenting the assertion reference to the IdP or through other similar means (see [[RFC7636]](references.md#ref-RFC7636) for one protocol's method of dynamic RP verification).
</details>

注記：[Sec. 5.1.3](sec5_federation.md#proxied) で説明されているフェデレーションプロキシでは，IdP はアサーション参照とアサーションの対象者をプロキシに制限し，プロキシは新しく作成されたアサーション参照またはアサーションの送付先を RP に制限する．
<details>
<summary>原文</summary>
Note that in a federation proxy described in [Sec. 5.1.3](sec5_federation.md#proxied), the IdP audience restricts the assertion reference and assertion to the proxy, and the proxy restricts any newly-created assertion references or assertions to the downstream RP.
</details>

~~~
\clearpage
~~~
{:latex-literal="true"}

## フロントチャネル (Front-Channel Presentation) {#front-channel}

*フロントチャネル*の提示モデルでは，IdP はアサーションを作成し，認証の成功後に加入者(subscriber)に送信する．アサーションは加入者(subscriber)によって提示され，RP に対して認証される．通常は，リダイレクトなどの加入者(subscriber)のブラウザー内のメカニズムを介して行われる．
<details>
<summary>原文</summary>
In the *front-channel* presentation model, the IdP creates an assertion and sends it to the subscriber after successful authentication. The assertion is presented by the subscriber to authenticate to the RP, usually through mechanisms within the subscriber's browser such as redirects.
</details>
[Figure 13. Front-channel Presentation](sec7_presentation.md#fig-13){:name="fig-13"}
{:latex-ignore="true"}

![Diagram of the front-channel presentation model for communicating assertions to the RP.]({{site.baseurl}}/{{page.collection}}/media/front-channel.png 'Front-channel Presentation'){:style="width:686px;height:600px;;min-width:686px;min-height:600px;" latex-src="front-channel.png" latex-fig="13" latex-place="h"}

アサーションは，フロントチャネル方式で加入者(subscriber)に表示される．これにより，アサーションに含まれるシステム情報が漏えいする可能性がある．さらに，[Sec. 6.3](sec6_assertions.md#s-identity-api) で説明されているように，アイデンティティAPI を使用してアサーションを提示した後，RP が IdP に追加の属性を照会することは可能なものの，このモデルではより対応が難しい．
<details>
<summary>原文</summary>
An assertion is visible to the subscriber in the front-channel method, which could potentially cause leakage of system information included in the assertion. Further, it is possible but more awkward in this model for the RP to query the IdP for additional attributes after the presentation of the assertion using an identity API, as described in [Sec. 6.3](sec6_assertions.md#s-identity-api).
</details>

アサーションは加入者(subscriber)の制御下にあるため，フロントチャネル方式を使用すると，加入者(subscriber)は，複数の RP でアサーションをリプレイするブラウザーなどによって，意図しない関係者に単一のアサーションを送信することもできてしまう．アサーションの対象者が制限されていて意図しない RP によって拒否されたとしても，意図しない RP への提示は，加入者(subscriber)の情報や加入者(subscriber)のオンラインでの活動に関する情報の漏えいにつながる可能性がある．複数の RP に提示されるように設計されたアサーションを意図的に作成することは可能だが，この方法では，アサーション自体の対象者の制限が緩くなり，これらの RP 全体で加入者(subscriber)のプライバシーとセキュリティが侵害される可能性がある．このような複数の RP の使用は推奨されない．代わりに，RP は独自のアサーションを取得することが推奨される．
<details>
<summary>原文</summary>
Since the assertion is under the subscriber's control, the front-channel presentation method also allows the subscriber to submit a single assertion to unintended parties, perhaps by a browser replaying an assertion at multiple RPs. Even if the assertion is audience-restricted and rejected by unintended RPs, its presentation at unintended RPs could lead to leaking information about the subscriber and their online activities. Though it is possible to intentionally create an assertion designed to be presented to multiple RPs, this method can lead to lax audience restriction of the assertion itself, which in turn could lead to privacy and security breaches for the subscriber across these RPs. Such multi-RP use is not recommended. Instead, RPs are encouraged to fetch their own individual assertions.
</details>

RP は，クロスサイトスクリプティングに対する保護やその他の利用可能な技術を使用して，製造またはキャプチャされたアサーションのインジェクションから自身を保護し**なければならない(SHALL)**．

IdP から加入者(subscriber)へのアサーションの伝達，および加入者(subscriber)から RP へのアサーションの伝達は，認証された保護されたチャネルを介して行われ**なければならない(SHALL)**．
<details>
<summary>原文</summary>
The RP **SHALL** protect itself against injection of manufactured or captured assertions by use of cross-site scripting protection and other accepted techniques. 

Conveyance of the assertion from the IdP to the subscriber, as well as from the subscriber to the RP, **SHALL** be made over an authenticated protected channel.
</details>

注記：[Sec. 5.1.3](sec5_federation.md#proxied) で説明されているフェデレーションプロキシでは，IdPのアサーションの対象者はプロキシに制限し，プロキシは新しく作成されたアサーションの送り先を RP に制限する．
<details>
<summary>原文</summary>
Note that in a federation proxy described in [Sec. 5.1.3](sec5_federation.md#proxied), the IdP audience restricts the assertion to the proxy, and the proxy restricts any newly-created assertions to the downstream RP.
</details>

## 情報の保護 (Protecting Information) {#protecting-information}

IdP と RP の間の通信は，認証され保護されたチャネルを使用して転送中に保護され**なければならない(SHALL)**．加入者(subscriber)と IdP または RP (通常はブラウザーを介して) との間の通信は，認証され保護されたチャネルを使用して行われ**なければならない(SHALL)**．
<details>
<summary>原文</summary>
Communications between the IdP and the RP **SHALL** be protected in transit using an authenticated protected channel. Communications between the subscriber and either the IdP or the RP (usually through a browser) **SHALL** be made using an authenticated protected channel.
</details>

注記：IdP は，デバイス識別子，場所，システムのヘルスチェック，構成管理などのセキュリティポリシーを適用する際に RP にとって役立つ情報にアクセスできる場合がある．その場合，[Sec. 9.2](sec9_privacy.md#notice) で説明されている加入者(subscriber)のプライバシー設定の範囲内で，この情報を RP に渡すことをお勧めする．
<details>
<summary>原文</summary>
Note that the IdP may have access to information that may be useful to the RP in enforcing security policies, such as device identity, location, system health checks, and configuration management. If so, it may be a good idea to pass this information along to the RP within the bounds of the subscriber's privacy preferences described in [Sec. 9.2](sec9_privacy.md#notice).
</details>

ユーザーに関する追加の属性は，[Sec. 6.3](sec6_assertions.md#s-identity-api) で説明されているように，アイデンティティAPI への承認されたアクセスを使用して，アサーション自体の外部に含め**てもよい(MAY)**． この方法でユーザー情報を分割すると，ユーザーのプライバシーを保護するのに役立ち，認証アサーション自体の重要な情報に加えて，識別属性の限定的な開示が可能になる．
<details>
<summary>原文</summary>
Additional attributes about the user **MAY** be included outside of the assertion itself by use of authorized access to an identity API as discussed in [Sec. 6.3](sec6_assertions.md#s-identity-api). Splitting user information in this manner can aid in protecting user privacy and allow for limited disclosure of identifying attributes on top of the essential information in the authentication assertion itself.
</details>

可能な場合，RP は，[Sec. 9.3](sec9_privacy.md#minimization) で説明されているように，完全な属性値ではなく，派生属性値を要求し**なければならない(SHALL)**．IdP は，派生属性値を可能な限りサポートし**なければならない(SHALL)**．
<details>
<summary>原文</summary>
The RP **SHALL**, where feasible, request derived attribute values rather than full attribute values as described in [Sec. 9.3](sec9_privacy.md#minimization). The IdP **SHALL** support derived attribute values to the extent possible.
</details>
