---
layout: default
title: Federation
navOrder: 5
navTitle: Federation
permalink: /sp800-63c/federation/
anchor: federation
section: 5
---

# Federation {#federation}

*This section is normative.*

フェデレーションプロトコルでは，[Figure 1](sec5_federation.md#fig-1)に示すように，加入者(subscriber)，IdP，RP の間で三者関係が形成される．

<details>
<summary>原文</summary>
In a federation protocol, a three-party relationship is formed between the subscriber, the IdP, and the RP, as shown in [Figure 1](sec5_federation.md#fig-1). 
</details>
[Figure 1. Federation Overview](sec5_federation.md#fig-1){:name="fig-1"}
{:latex-ignore="true"}

![Overview diagram of federated authentication systems showing parties involved and major steps in the process.]({{site.baseurl}}/{{page.collection}}/media/federation.png 'Federation Overview'){:style="width:628px;height:600px;;min-width: 628px;min-height: 600px;" latex-src="federation.png" latex-fig="1" latex-place="h"}

IdP と RP 間のフェデレーション関係は，多段階プロセスで確立される.

1. まず，IdP と RP が信頼の合意を形成する．この合意は，当事者間の二者間，当局の要請による多者間，または信頼できる当事者を通じてプロキシされる場合がある．この手順は，件の2つのシステムが接続するための最初の許可を表す．要求および提示できるもののパラメーターはこのステップで確立されるが，特定の加入者(subscriber)の特定の RP に提示される属性の詳細は，後の段階まで延期できる．

2. 次に，IdP と RP は登録を実行してプロトコルレベルで信頼を確立し，関係者間で情報を安全に交換できるようにする．最初のステップでは，接続の許可を表すポリシー決定が必要だが，このステップでは，フェデレーションプロトコルを介した通信を許可するために，IdP と RP を表すクレデンシャルと識別子を確立する．この段階は,加入者(subscriber)が RP にログインしようとする前に，または，加入者(subscriber)が RP で IdP を使用しようとする試行への応答として発生する．

3. 続いて，IdP と RP は，加入者(subscriber)を認証するためにフェデレーション認証トランザクションに関連することを決定する．その一環として，このトランザクション中に IdP から RP に加入者(subscriber)に関するどの属性を渡すかを決定する．このステップで行われる決定は，最初のステップで形成された信頼の合意と，2番目のステップで確立された RP および IdP の アイデンティティ に基づいている．

4. 最後に，加入者(subscriber)が IdP に対して認証を行い，その認証イベントの結果がネットワークを介して RP に提示される．RP は IdP から提示されたアサーションを処理し，加入者(subscriber)との認証済みセッションを確立する．
  
<details>
<summary>原文</summary>
A federation relationship between an IdP and RP is established in a multi-stage process:

1. First, the IdP and RP agree to enter into a trust agreement. This agreement can be bilateral between the parties, multilateral at the behest of an authority, or proxied through a trusted party. This step represents initial permission for the two systems in question to connect. Parameters of what can be requested and released are established in this step, though the details of which attributes are released to a given RP for a given subscriber can be deferred until a later stage.
  
2. Next, the IdP and RP perform registration to establish their trust at a protocol level, allowing for information to be securely exchanged between the parties. While the first step entails a policy decision representing a permission to connect, this step entails establishment of credentials and identifiers representing the IdP and RP to allow communication through the federation protocol. This stage can occur before any subscriber tries to log in to the RP or as a response to a subscriber's attempt to use an IdP at an RP.
  
3. Next, the IdP and RP determine that they want to engage in a federated authentication transaction to authenticate the subscriber. As part of this, they determine which attributes about the subscriber are to be passed from the IdP to the RP during this transaction. The decision made in this step builds on the trust agreement established in the first step and the identities of the RP and IdP established in the second step.
  
4. Finally, the subscriber authenticates to the IdP and the result of that authentication event is asserted to the RP across the network. The RP processes this assertion from the IdP and establishes an authenticated session with the subscriber.

</details>


このトランザクションでは，[[SP800-63B]](../_sp800-63b/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63B"}で説明されているように，IdP は加入者(subscriber)のオーセンティケーターの検証者として機能する．認証イベント情報は，[Sec. 6](sec6_assertions.md#assertions)で説明されているアサーションを使用して IdP から RP に運ばれる．
IdP は，このアサーションの一部として，または承認されたクレデンシャルによって保護された派生のアイデンティティプロトコルを介して，加入者(subscriber)の属性情報に関するステートメントを作成することもできる．

<details>
<summary>原文</summary>
In this transaction, the IdP acts as the verifier of the subscriber's authenticators, as described in [[SP800-63B]](../_sp800-63b/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63B"}. The authentication event information is carried from the IdP to the RP through the use of an assertion, described in [Sec. 6](sec6_assertions.md#assertions). The IdP can also make statements about identity attributes of the subscriber as part of this assertion or through a secondary identity protocol protected by an authorized credential.
</details>

## 信頼の合意(Trust Agreements) {#trust-agreement}

認証サービスを提供する IdP と，それらのサービスを使用する RP は，フェデレーションのメンバーとして知られている．IdP から見ると，フェデレーションは，サービスを提供する RP で構成される．RP から見ると，フェデレーションは，使用する IdP で構成される．本節では，現在使用されている一般的なアイデンティティフェデレーションモデルの概要と要件について説明する．各モデルでは，フェデレーションのメンバー間に関係が確立される．これらの関係は，次節で説明するように，二者間または多者間で確立される．

<details>
<summary>原文</summary>
IdPs that provide authentication services and RPs that consume those services are known as members of a federation. From an IdP's perspective, the federation consists of the RPs that it serves. From an RP's perspective, the federation consists of the IdPs that it uses. This section provides an overview of and requirements for common identity federation models currently in use. In each model, relationships are established between members of the federation. These relationships are  established in either a bilateral or multilateral fashion, as described in the following sections. 
</details>

信頼の合意では，次のパラメータを確立し**なければならない(SHALL)**．

- IdP が RP へ提示できる属性のセット
- IdP がアサーションを作成できる加入者(subscriber)アカウントの集合
- RP が要求する属性のセット (利用可能な属性のサブセット)
- RP によって要求された各属性の利用目的
- 加入者(subscriber)の属性の提供に関する決定に責任を負う authorized party
- RP への属性提供について加入者(subscriber)に通知する手段
- IdP が提供可能な xAL
- RP が必要とする xAL

<details>
<summary>原文</summary>
Trust agreements **SHALL** establish the following parameters:

- The set of attributes the IdP can make available to the RP
- The population of subscriber accounts the IdP can create assertions for
- The set of attributes the RP will request (a subset of the attributes made available)
- The purpose for each attribute requested by the RP
- The authorized party responsible for decisions regarding the release of subscriber attributes
- The means of informing subscribers about attribute release to the RP
- The xALs available from the IdP
- The xALs required by the RP
</details>

信頼の合意は，静的あるいは動的に形成できる．静的に形成する場合，多くの場合において，当事者を一連の期待される行動，権利，および要件に拘束する法的または契約上の合意がある．静的に信頼の合意を行う際のパラメーターは，IdP のオペレーター，RP のオペレーター，および影響を受ける加入者(subscriber)を含む，合意に関わるのすべての関係者が利用でき**なければならない(SHALL)**．

<details>
<summary>原文</summary>
Trust agreements are able to be established either statically or dynamically. In a static establishment, there is often a legal or contractual agreement binding the parties to a set of expected behaviors, rights, and requirements. The parameters of static trust agreements **SHALL** be available to all parties in the agreement, including the operator of the IdP, the operator of the RP, and affected subscribers.
</details>


対照的に，動的に信頼を形成する場合では，加入者(subscriber)のログインのために RP と IdP が最初に相互に連絡するときに，信頼の合意が暗黙的に定義される．動的に信頼の合意を行う際のパラメータの表現は，適切なフェデレーションプロトコルによって駆動され，通常，フェデレーションパーティ間の契約上の合意に結び付けられることはない．動的に信頼の合意を行う際のパラメータは，フェデレーショントランザクション中に RP および IdP によって加入者(subscriber)に開示され**なければならない(SHALL)**．
<details>
<summary>原文</summary>
In dynamic trust establishment, in contrast, the trust agreement is implicitly defined when the RP and IdP first contact each other for the purposes of a subscriber's login. The expression of the parameters of a dynamic trust agreement is driven by the federation protocol in place, and are not usually tied to a contractual agreement between the federating parties. The parameters of a dynamic trust agreement **SHALL** be disclosed to the subscriber by the RP and the IdP during the federation transaction.
</details>

信頼の合意における _authorized party_ とは，加入者(subscriber)属性のリリースを含む，信頼の合意の対象となる特定の提示の決定に責任を負う組織，人，またはエンティティである．静的な信頼の合意の場合，authorized party は IdP を担当する組織で**もよい(MAY)**．この場合，属性提示への同意は，すべての加入者(subscriber)に対して決定され，[Sec. 5.3.1](sec5_federation.md#idp-allowlist) で説明されているようにホワイトリストによって確立される．これにより，加入者(subscriber)による直接の決定や関与なしに属性情報の開示が可能になる．静的な信頼の合意は，[Sec. 5.3.3](sec5_federation.md#idp-runtime-decision) で説明されているように，加入者(subscriber)などの個人が属性を開示することに同意するよう実行時に求められることを規定**してもよい(MAY)**． 動的な信頼の合意は加入者(subscriber)のアクションによって形成されるため，動的な信頼の合意の authorized party は常に加入者(subscriber)である．動的な信頼の合意における属性の開示は，加入者(subscriber)からの実行時の決定に従わ**なければならず(SHALL)**，IdP のホワイトリストに従っては**ならない(SHALL NOT)．

<details>
<summary>原文</summary>
The _authorized party_ in a trust agreement is the organization, person, or entity that is responsible for the specific release decisions covered by the trust agreement, including the release of subscriber attributes. For a static trust agreement, the authorized party **MAY** be the organization responsible for the IdP. In this case, consent to release attributes is decided for all subscribers and established by an allowlist as described in [Sec. 5.3.1](sec5_federation.md#idp-allowlist), allowing for the disclosure of attribute information without direct decisions and involvement by the subscriber. A static trust agreement **MAY** stipulate that an individual, such as the subscriber, is to be prompted at runtime for consent to disclose attributes as discussed in [Sec. 5.3.3](sec5_federation.md#idp-runtime-decision). Since dynamic trust agreements are established by subscriber actions, the authorized party in a dynamic trust agreement is always the subscriber. Disclosure of attributes in dynamic trust agreements **SHALL** be subject to a runtime decision from the subscriber and **SHALL NOT** be subject to an allowlist at the IdP.
</details>

たとえば, エンタープライズサービス (RP) に接続する組織 (IdP) に対して静的な信頼の合意が形成され，ホワイトリストにある組織のすべての加入者(subscriber)が利用できるようになる場合，この信頼の合意の authorized party は組織である．加入者(subscriber)がエンタープライズサービスにログインする際に，サービスに関する実行時の決定は要求されない．これは，静的な信頼の合意によってアプリオリに確立されているためである．別のシナリオでは，同じ組織のすべての加入者(subscriber)が別のサービスを利用できるようになるが，静的な信頼協定では，加入者(subscriber)が authorized party であることが規定されている．サービスに初めてログインする際に各加入者(subscriber)は，属性を RP に提示することに同意するよう求められる．別のシナリオでは，加入者(subscriber)が RP（動的な信頼の合意をしなければIdPに知られていないRP） にアクセスしようとすると，動的な信頼の合意が暗黙的に形成される．RP は IdP から要求されているすべての属性の使用について加入者(subscriber)に通知し，IdP は加入者(subscriber)に RP に属性を提示することに同意するように求める．

<details>
<summary>原文</summary>
For example, a static trust agreement is established for an organization (the IdP) connecting to an enterprise service (the RP) to be made available to all subscribers at the organization on an allowlist. The authorized party for this trust agreement is the organization. When a subscriber logs in to the enterprise service, they are not prompted with any runtime decisions regarding the service since the static trust agreement establishes this a priori. In a different scenario, another service is made available to all subscribers at the same organization, but the static trust agreement stipulates that the subscriber is the authorized party. When logging in to the service for the first time, each subscriber is prompted for their consent to release their attributes to the RP. In another scenario, a dynamic trust agreement is established implicitly when a subscriber goes to access an RP that is otherwise unknown by their IdP. The RP informs the subscriber about the uses of all attributes being requested from the IdP, and the IdP prompts the subscriber for consent to release their attributes to the RP.
</details>

IdP と RP が共有のセキュリティドメインまたは共有の法的所有権を持っている場合でも，すべてのフェデレーショントランザクションには信頼の合意の形成が必要である．そのような場合，信頼の合意の形成は，迅速に完了することができる内部プロセスである．

<details>
<summary>原文</summary>
Establishment of a trust agreement is required for all federation transactions, even those in which the IdP and RP have a shared security domain or shared legal ownership. In such cases, the establishment of the trust agreement is an internal process that can be completed quickly.
</details>

単一のフェデレーショントランザクションの過程で，IdP と RP のポリシーと期待が，すべての関係者にとって明確であることが重要である．したがって，特定のトランザクションに対して有効な信頼の合意のセットは 1 つだけである**必要がある(SHOUD)**．これは通常，単一の IdP と単一の RP で構成される一意のペアによって決定される．ただし，これらの合意は，IdP と RP が異なる加入者(subscriber)集団に対して異なる合意を形成しているなど，別の部分で異なる場合がある．
<details>
<summary>原文</summary>
During the course of a single federation transaction, it is important for the policies and expectations of the IdP and RP to be unambiguous for all parties involved. Therefore, there **SHOULD** be only one set of trust agreements in effect for a given transaction. This will usually be determined by the unique pair consisting of a single IdP and a single RP. However, these agreements could vary in other ways, such as an IdP and RP having different agreements for different populations of subscribers.
</details>


2つの当事者間の信頼の合意の存在は，合意の各当事者が他の当事者と形成する他の合意の存在を排除するものではない．つまり，IdP は同時に複数の RP と独立した合意を形成することができ (そして一般的にはそうしている)，RP は同様に複数の IdP と独立した合意を同時に形成することができる．
<details>
<summary>原文</summary>
The existence of a trust agreement between two parties does not preclude the existence of other agreements for each party in the agreement to have with other parties. That is to say, an IdP can have (and generally does have) independent agreements with multiple RPs simultaneously, and an RP can likewise have independent agreements with multiple IdPs simultaneously.
</details>

### 二者間の信頼の合意 (Bilateral Trust Agreements) {#bilateral}

二者間の信頼の合意では，IdP と RP の潜在的なペアリングが相互に信頼関係を形成する．このモデルでは，IdP と RP がそれぞれ自身の authority として機能し，フェデレーション内でその役割を実行できる相手を確立する．

<details>
<summary>原文</summary>
In a bilateral trust agreement, each potential pairing of an IdP and RP form a trust relationship with each other. In this model, the IdP and RP each act as their own authority and establish the other party as capable of performing its role within the federation.
</details>


IdP は，サポートされている IAL，AAL，FAL のレベルを RP に開示し**なければならない(SHALL)**．IdP は，アプリケーションのニーズに応じて，その機能のサブセットを特定の RP に開示**してもよい(MAY)**．たとえば，アカウントが IAL1 以上で証明されていることをリスクの低い RP にのみ開示するなど．

RP は，要求された各属性の使用目的を含め，必要な属性のリストを IdP に開示し**なければならない(SHALL)**．RP は，必要な IAL，AAL，FAL を IdP に通知し**なければならない(SHALL)**．これには、IAL または AAL は必要ないかどうかも含む．

IdP は，RP によって明示的に要求された属性のみを送信し**なければならない(SHALL)**．RP は，要求した属性をプライバシーリスク評価に含める**なければならない(SHALL)**．

<details>
<summary>原文</summary>
The IdP **SHALL** disclose its supported IAL, AAL, and FAL levels to the RP. The IdP **MAY** disclose a subset of its capabilities to a given RP depending on the needs of the application, for example only disclosing to a low-risk RP that accounts are proofed at IAL1 or better.

The RP **SHALL** disclose its list of required attributes to the IdP, including its purpose for use of each requested attribute. The RP **SHALL** communicate its required IAL, AAL, and FAL to the IdP, including whether no claim is required for IAL or AAL.

The IdP **SHALL** transmit only those attributes that were explicitly requested by the RP. RPs **SHALL** include their requested attributes in their privacy risk assessment.
</details>

### 多者間の信頼の合意 (Multilateral Trust Agreements) {#authorities}

多者間の信頼の合意では，フェデレーションの当事者は，フェデレーションの信頼に関する決定を支援し，当事者間の協力関係を確立するために，*federation authority* に従う．このモデルでは，federation authority がフェデレーション合意の IdP と RP のメンバーシップを管理する．federation authority は，フェデレーション内の各当事者に対してある程度の審査を行い，信頼の合意を定義する所定の基準に準拠していることを確認する．審査のレベルは，フェデレーション内で採用されているユースケースとモデルに固有のものである．この審査は，[図2] (sec5_federation.md#fig-2) の左側に示されている．

<details>
<summary>原文</summary>
In a multilateral trust agreement, the federated parties defer to a *federation authority* to assist in making federation trust decisions and to establish the working relationship between parties. In this model, the federation authority manages the membership of IdPs and RPs in the federation agreement. The federation authority conducts some level of vetting on each party in the federation to verify compliance with predetermined standards that define the trust agreement. The level of vetting is unique to the use cases and models employed within the federation. This vetting is depicted in the left side of [Figure 2](sec5_federation.md#fig-2).
</details>

federation authority は，IdP が特定の IAL，AAL，FAL で動作することを承認する．この情報は，[図2](sec5_federation.md#fig-2) の右側に示すように，RP が要件を満たす IdP を決定するために使われる．

<details>
<summary>原文</summary>
Federation authorities approve IdPs to operate at certain IALs, AALs, and FALs. This information is used by relying parties, as shown in the right side of [Figure 2](sec5_federation.md#fig-2), to determine which identity providers meet their requirements.
</details>

federation authority は，それらが可能にするフェデレーションリレーションシップに関連して，期待される受入れ可能な IAL，AAL，FAL に関するパラメータを確立し**なければならない(SHALL)**．federation authority は，フェデレーションの各関係者を個別に精査して，期待される基準を遵守しているかどうかを判断し**なければならない(SHALL)**．
<details>
<summary>原文</summary>
Federation authorities **SHALL** establish parameters regarding expected and acceptable IALs, AALs, and FALs in connection with the federated relationships they enable. Federation authorities **SHALL** individually vet each participant in the federation to determine whether they adhere to their expected standards.
</details>


[Figure 2. Federation Authority](sec5_federation.md#fig-2){:name="fig-2"}
{:latex-ignore="true"}

![Diagram of a federation authority providing trust decisions for a federation network of IdPs and RPs.]({{site.baseurl}}/{{page.collection}}/media/authority.png 'Federation Authority'){:style="width:789px;height:490px;;min-width:789px;min-height:490px;" latex-src="authority.png" latex-fig="2" latex-place="h"}

IdP と RP の審査では，少なくとも次のことを確立し**なければならない(SHALL)**:

* IdP によって生成されたアサーションは，[Sec. 6](sec6_assertions.md#assertions)でしめされた要件を遵守する．
* RP は，保持，集約，および第三者への開示など，加入者(subscriber)属性データを処理するための要件を遵守する．
* RP および IdP システムは，フェデレーションプロトコルの承認済みプロファイルを利用する．

<details>
<summary>原文</summary>
Vetting of IdPs and RPs **SHALL** establish, as a minimum, that:

* Assertions generated by IdPs adhere to the requirements in [Sec. 6](sec6_assertions.md#assertions).
* RPs adhere to requirements for handling subscriber attribute data, such as retention, aggregation, and disclosure to third parties.
* RP and IdP systems use approved profiles of federation protocols.
</details>

federation authority は，IdP の構成データの公開や RP のソフトウェアステートメントの発行などによって，メンバー間の技術的な接続と構成プロセスを支援**してもよい(MAY)**．

authorities を通じて管理されるほとんどの federation には，単純なメンバーシップモデルがある．たとえば，当事者は federation に属しているか，そうでないかのいずれかといったものである．より洗練された federation は，federation の他の当事者がより徹底的に審査されているかどうかを判断するために，フェデレーションの当事者が使用できる複数のメンバーシップ層を持っ**てもよい(MAY)**．IdP は，特定の加入者(subscriber)属性が上位層の RP にのみ提示可能であると決定し**てもよく(MAY)**，RP は上位層の IdP からのみ特定の情報を受け入れることを決定し**てもよい(MAY)**．

<details>
<summary>原文</summary>
Federation authorities **MAY** assist the technical connection and configuration process between members, such as by publishing configuration data for IdPs or by issuing software statements for RPs.

Most federations managed through authorities have a simple membership model: parties are either in the federation or they are not. More sophisticated federations **MAY** have multiple membership tiers that federated parties can use to tell whether other parties in the federation have been more thoroughly vetted. IdPs **MAY** decide that certain subscriber attributes are only releasable to RPs in higher tiers and RPs **MAY** decide to accept certain information only from IdPs in higher tiers.
</details>

### Proxied Federation {#proxied}

proxied federation では，IdP と RP の間のすべての通信は，2 つの当事者間の直接通信を防止する方法で仲介者を通過する．この効果を得るには複数の方法がある．一般的な構成は次のとおり．

* フェデレーションプロキシ (または *ブローカー*) として機能するサードパーティ
* 通信を分散し，エンドポイント間のプロキシとして機能するノードのネットワーク

<details>
<summary>原文</summary>
In a proxied federation, all communication between the IdP and the RP is passed through an intermediary party in a way that prevents direct communication between the two parties. There are multiple methods to achieve this effect. Common configurations include:

* A third party that acts as a federation proxy (or *broker*)
* A network of nodes that distributes the communications and functions as a proxy between the endpoints
</details>


プロキシが使用されている場合，一方は IdP として機能し，もう一方は RP として機能する．したがって，IdP および RP に適用されるすべての規範的要件は，それぞれの役割のプロキシに適用され**なければならない(SHALL)**．

<details>
<summary>原文</summary>
Where proxies are used, they function as an IdP on one side and an RP on the other. Therefore, all normative requirements that apply to IdPs and RPs **SHALL** apply to proxies in their respective roles.
</details>

[Figure 3. Federation Proxy](sec5_federation.md#fig-3){:name="fig-3"}
{:latex-ignore="true"}

![Diagram of a federation proxy accepting assertions from an upstream IdP and providing assertions to a downstream RP.]({{site.baseurl}}/{{page.collection}}/media/broker.png 'Federation Proxy'){:style="width:600px;height:150px;;min-width:600px;min-height:150px;" latex-src="broker.png" latex-fig="3" latex-place="h"}

proxied federation モデルには，いくつかの利点がある．フェデレーションプロキシは，統合用の共通インターフェイスを提供することで，RP と IdP 間の技術的統合を簡素化できる．さらに，プロキシが RP と IdP を効果的に相互にブラインドすることで，加入者(subscriber)リストを相互に保護したい組織にある程度のビジネス機密性を提供できる．プロキシは，[Sec. 5.5](sec5_federation.md#privacy-reqs) 以降で説明されているプライバシーリスクの一部を軽減することもできる．

ブラインドの技術，その使用法，および制限の詳細については， [Sec. 9.5](sec9_privacy.md#blinding)を参照．

<details>
<summary>原文</summary>
A proxied federation model can provide several benefits. Federation proxies can simplify technical integration between the RP and IdP by providing a common interface for integration. Additionally, to the extent a proxy effectively blinds the RP and IdP from each other, it can provide some business confidentiality for organizations that want to guard their subscriber lists from each other. Proxies can also mitigate some of the privacy risks described in [Sec. 5.5](sec5_federation.md#privacy-reqs) below.

See [Sec. 9.5](sec9_privacy.md#blinding) for further information on blinding techniques, their uses, and limitations.
</details>

プロキシを介して提示されるフェデレーションは，プロキシされたトランザクション中に使用される最小の FAL によって表され**なければならない(SHALL)**．たとえば，プロキシが FAL2 で IdP からアサーションを受け取ったものの，FAL1 で RP にアサーションを提示する場合，トランザクション全体が FAL1 とみなされる．同様に，federation が FAL1 でアサーションを受け取り，FAL3 で RP にアサーションを提示する場合，トランザクション全体は依然として FAL1 とみなされる．プロキシは，実行時または信頼の合意の一部としての事前構成を通じて，この側面を RP に伝達し**なければならない(SHALL)**．

<details>
<summary>原文</summary>
Federations presented through a proxy **SHALL** be represented by the lowest FAL used during the proxied transaction. For example, if a proxy takes in an assertion from the IdP at FAL2 but presents a downstream assertion to the RP at FAL1, the entire transaction is considered FAL1. Likewise if a federation takes in an assertion at FAL1 but presents a downstream assertion to the RP at FAL3, the entire transaction is still considered FAL1. The proxy **SHALL** communicate this aspect to the RP either at runtime or through pre-configuration as part of the trust agreement.
 </details>

## 登録(Registration)

フェデレーションプロトコル内では，暗号化鍵，システム識別子，サービスエンドポイントURL，および必要なアクセス権などのプロトコル固有の情報を IdP と RP の間で確立する必要があり，それらによって相互に安全に通信できるようになる．さらに，システムの信頼性と使いやすさを向上させるために，システムの表示名やホームページなどの加入者(subscriber)向けの情報を確立することができる． この情報はすべて，フェデレーションプロトコルの範囲内で IdP と RP の間の信頼をデジタル的かつプログラム的に確立するために使用される．

<details>
<summary>原文</summary>
Within federation protocols, protocol-specific information such as cryptographic keys, system identifiers, service endpoint URLs, and required access rights need to be established between the IdPs and RPs, allowing them to communicate securely with each other. Furthermore, subscriber-facing information such as system display names and home pages can be established to facilitate trust in and usability of the system. All of this information is used to digitally and programmatically establish trust between the IdP and RP within the scope of the federation protocol.
</details>
 
これらの情報交換は，フェデレーショントランザクション内で通信する IdP と RP ごとに，そのトランザクションの基礎となる信頼の合意に関係なく，ペアで行われる．このプロセスの 2 つのフェーズは，一般に，RP による IdP の　_検出(discovery)_　および IdP での RP の _登録(registration)_ として知られている．これらのプロセスは，システム管理者または開発者がターゲットシステムに情報を入力する手動の静的な方法で行うことも，人間が直接関与せずにシステム自体が情報を交換する自動化された動的な方法で行うこともできる． 
 
<details>
<summary>原文</summary>
These exchanges of information happen in a pairwise fashion for each IdP and RP communicating within a federation transaction, regardless of the trust agreement underlying that transaction. The two phases of this process are commonly known as _discovery_ of the IdP by the RP and _registration_ of the RP at the IdP. These processes can happen in a manual, static fashion, where system administrators or developers enter the information into the target systems, or in an automated, dynamic fashion, where the systems themselves exchange information without direct human involvement.
</details>
 
~~~
\clearpage
~~~
{:latex-literal="true"}

### 手動登録 (Manual Registration) {#manual-registration}

手動登録モデルでは，IdP および RP のオペレーターは，加入者(subscriber)が関与する前に，相互運用を期待する関係者に関する構成情報を手動でプロビジョニングする．

<details>
<summary>原文</summary>
In the manual registration model, the operators of the IdP and RP manually provision configuration information about parties with which they expect to interoperate, prior to involvement of the subscriber.
</details>

[Figure 4. Manual Registration](sec5_federation.md#fig-4){:name="fig-4"}
{:latex-ignore="true"}

![Diagram of the steps involved in a manual registration process between an RP and IdP.]({{site.baseurl}}/{{page.collection}}/media/manual.png 'Manual Registration'){:style="width:630px;height:400px;;min-width: 630px;min-height:400px;" latex-src="manual.png" latex-fig="4" latex-place="h"}

[図4](sec5_federation.md#fig-4) に示すように，手動登録には次の3つの手順がある．

1. RP のシステム管理者は，RP の属性を IdP のシステム管理者と共有する．IdP のシステム管理者は，それらの属性を RP に関連付ける．

2. IdP のシステム管理者は，IdP の属性を RP のシステム管理者と共有する．RP のシステム管理者は，それらの属性を IdP に関連付ける．

3. IdP と RP は，標準のフェデレーション プロトコルを使用して通信する．

<details>
<summary>原文</summary>
As shown in [Figure 4](sec5_federation.md#fig-4), manual registration involves three steps: 

1. The RP's system administrator shares the RP's attributes with the IdP's system administrator, who associates those attributes with the RP.

2. The IdP's system administrator shares the IdP's attributes with the RP's system administrator, who associates those attributes with the IdP.

3. The IdP and RP then communicate using a standard federation protocol.
</details>

IdP と RP は，[Sec. 5.1.1](sec5_federation.md#bilateral) にあるように誰とフェデレートするかについて独自の authority として機能**してもよい(MAY)**，または[Sec. 5.1.2](sec5_federation.md#authorities)のようにそれらの authority の決定を外部に外出し**してもよい(MAY)**．

鍵情報の転送を必要とするプロトコルは，登録プロセス中に安全な方法を使用して，共有鍵または公開鍵を含んだフェデレーションリレーションシップを操作するために必要な鍵情報を交換し**なければならない(SHALL)**．この関係で使用される対称鍵は，フェデレーション参加者のペアに固有のもので**なければならない(SHALL)**．

フェデレーションリレーションシップは，フェデレーションリレーションシップに関連して，期待される受け入れ可能な IAL および AAL に関するパラメータを確立**なければならない(SHALL)**．

<details>
<summary>原文</summary>
IdPs and RPs **MAY** act as their own authorities on who to federate with as in [Sec. 5.1.1](sec5_federation.md#bilateral) or **MAY** externalize those authority decisions to an external party as in [Sec. 5.1.2](sec5_federation.md#authorities).

Protocols requiring the transfer of keying information **SHALL** use a secure method during the registration process to exchange keying information needed to operate the federated relationship, including any shared secrets or public keys. Any symmetric keys used in this relationship **SHALL** be unique to a pair of federation participants.

Federation relationships **SHALL** establish parameters regarding expected and acceptable IALs and AALs in connection with the federated relationship.
</details>

### 動的登録 (Dynamic Registration) {#dynamic-registration}

フェデレーションの動的登録モデルでは，トランザクション時にフェデレーションのメンバー間の関係をネゴシエートできる．このプロセスにより，手動登録を使用して IdP と RP 間の接続を手動で確立することなく，IdP と RP を相互に接続できる ([Sec. 5.2.1](sec5_federation.md#manual-registration)を参照)．動的登録をサポートする IdP は，システム管理者の関与を最小限に抑えるような方法で，構成情報 (動的登録エンドポイントなど) を利用できるようにし**なければならない(SHALL)**．

<details>
<summary>原文</summary>
In the dynamic registration model of federation, it is possible for relationships between members of the federation to be negotiated at the time of a transaction. This process allows IdPs and RPs to be connected together without manually establishing a connection between them using manual registration (See [Sec. 5.2.1](sec5_federation.md#manual-registration)). IdPs that support dynamic registration **SHALL** make their configuration information (such as dynamic registration endpoints) available in such a way as to minimize system administrator involvement.
</details>

[Figure 5. Dynamic Registration](sec5_federation.md#fig-5){:name="fig-5"}
{:latex-ignore="true"}

![Diagram of the steps in a dynamic registration process between an IdP and an RP.]({{site.baseurl}}/{{page.collection}}/media/dynamic.png 'Dynamic Registration'){:style="width:630px;height:338px;;min-width: 630px;min-height:338px;" latex-src="dynamic.png" latex-fig="5" latex-place="h"}


[図5](sec5_federation.md#fig-5) に示すように，動的登録には次の 4 つの手順がある．

1. 検出(Discover)．RP は，IdP の既知の場所に移動して，IdP のメタデータを見つける．

2. 検証(Validate)．RP と IdP は，互いの有効性を決定する．これは，鍵情報，メタデータ，ソフトウェアステートメント，またはその他の手段によって実現される．

3. RP 属性を登録する．RP はその属性を IdP に送信し，IdP はそれらの属性を RP に関連付ける．

4. フェデレーションプロトコル．IdP と RP は，標準のフェデレーションプロトコルを使用して通信する．

<details>
<summary>原文</summary>
As shown in [Figure 5](sec5_federation.md#fig-5), dynamic registration involves four steps:

1. Discover. The RP goes to a well-known location at the IdP to find the IdP's metadata.

2. Validate. The RP and IdP determine each other's validity. This can be accomplished through keying information, metadata, software statements, or other means.

3. Register RP attributes. The RP sends its attributes to the IdP, and the IdP associates those attributes with the RP.

4. Federation Protocol. The IdP and RP then communicate using a standard federation protocol.
</details>

鍵情報の転送を必要とするプロトコルは，登録プロセス中に安全な方法を使用して，共有鍵または公開鍵を含んだフェデレーションリレーションシップを操作するために必要な鍵情報を確立し**なければならない(SHALL)**．この関係で使用される対称鍵は，フェデレーション参加者のペアに固有のもので**なければならない(SHALL)**．

IdP は，[Sec. 6.2.5](sec6_assertions.md#ppi)で説明されているように，動的に登録された RP に PPID を発行する**必要がある(SHOULD)**．

<details>
<summary>原文</summary>
Protocols requiring the transfer of keying information **SHALL** use a secure method during the registration process to establish such keying information needed to operate the federated relationship, including any shared secrets or public keys. Any symmetric keys used in this relationship **SHALL** be unique to a pair of federation participants.

IdPs **SHOULD** issue pairwise pseudonymous subject identifiers to dynamically registered RPs, as discussed in [Sec. 6.2.5](sec6_assertions.md#ppi).
</details>

可能な場合，動的登録は，信頼の合意に固定された *ソフトウェアステートメント* によって強化する**必要がある(SHOULD)**．ソフトウェアステートメントは，authority（IdP自身，[Sec. 5.1.2](sec5_federation.md#authorities)にあるような federation authority，または別の信頼できる当事者) によって暗号的に署名された，RP ソフトウェアを説明する属性のリストである．ソフトウェアステートメントを使用すると，フェデレーテッドパーティは，RP のすべての識別情報を事前に入手することなく，動的に登録されている RP の一部の属性を暗号で検証できる．この暗号的に検証可能なステートメントにより，self-assert　された属性のみに依存することなく，フェデレーションパーティ間で接続を確立または昇格させることができる．(プロトコルのソフトウェアステートメントの実装の詳細については，[[RFC7591]](references.md#ref-RFC7591)の 2.3 を参照のこと．)

<details>
<summary>原文</summary>
Where possible, dynamic registration **SHOULD** be augmented by *software statements* anchored in their trust agreement. Software statements are lists of attributes describing the RP software, cryptographically signed by an authority (either the IdP itself, a federation authority as in [Sec. 5.1.2](sec5_federation.md#authorities), or another trusted party). Software statements allow federated parties to cryptographically verify some attributes of an RP being dynamically registered without necessarily having all of the identifying information for that RP ahead of time. This cryptographically verifiable statement allows the connection to be established or elevated between the federating parties without relying solely on self-asserted attributes. (See [[RFC7591]](references.md#ref-RFC7591) Sec. 2.3 for more information on one protocol's implementation of software statements.)
</details>

## 認証と属性開示 (Authentication and Attribute Disclosure)

IdP と RP が信頼の合意を形成し，登録を完了すると，フェデレーションプロトコルを使用して IdP から RP に加入者(subscriber)属性を渡すことができる．認証を行うことができるかどうか，または属性を渡すことができるかどうかの決定は，ホワイトリスト，ブラックリスト，または実行時の決定を使用して，信頼の合意形成時に規定された authorized party によって決定され**なければならない(SHALL)**．

加入者(subscriber)の属性は，IdP と RP の間で，アイデンティティフェデレーショントランザクション，または[Sec. 5.5](sec5_federation.md#privacy-reqs)で説明されている侵害された加入者(subscriber)アカウントの識別などのサポート機能のためにのみ送信され**なければならない(SHALL)**．ホワイトリストに登録されている場合でも，加入者(subscriber)の属性を他の目的で送信してはならない．

<details>
<summary>原文</summary>
Once the IdP and RP have entered into a trust agreement and have completed registration, the federation protocol can be used to pass subscriber attributes from the IdP to the RP. The decision of whether an authentication can occur or attributes may be passed **SHALL** be determined by the authorized party stipulated by the trust agreement, through use of an allowlist, a blocklist, or a runtime decision.

A subscriber's attributes **SHALL** be transmitted between IdP and RP only for identity federation transactions or support functions such as identification of compromised subscriber accounts as discussed in [Sec. 5.5](sec5_federation.md#privacy-reqs). A subscriber's attributes are not to be transmitted for any other purposes, even when parties are allowlisted.
</details>

加入者(subscriber)の属性は，信頼の合意形成時に規定された目的以外で RP が使用し**てはならない(SHALL NOT)**．

RP へ属性が送信する際には，加入者(subscriber)に通知し**なければならない(SHALL)**．authorized party が組織である場合，組織は，承認された RP のリストと，それらの RP に送信された関連する属性のセットを加入者(subscriber)が利用できるようにし**なければならない(SHALL)**．authorized party が加入者(subscriber)である場合，加入者(subscriber)は，[Sec. 5.3.3](sec5_federation.md#idp-runtime-decision) で説明されているように，IdP での実行時の決定を使用して，属性を提示する前にプロンプトを表示され**なければならない(SHALL)**．

<details>
<summary>原文</summary>
A subscriber's attributes **SHALL NOT** be used by the RP for purposes other than those stipulated in the trust agreement.

The subscriber **SHALL** be informed of the transmission of attributes to an RP. In the case where the authorized party is the organization, the organization **SHALL** make available to the subscriber the list of approved RPs and the associated sets of attributes sent to those RPs. In the case where the authorized party is the subscriber, the subscriber **SHALL** be prompted prior to release of attributes using a runtime decision at the IdP as described in [Sec. 5.3.3](sec5_federation.md#idp-runtime-decision).
</details>

IdP は，加入者(subscriber)の苦情や問題 (たとえば，加入者(subscriber)が不正確な属性値を発見するなど) を是正するための効果的なメカニズムを提供し**なければならない(SHALL)**．救済のためのユーザビリティに関する考慮事項については，[Sec. 10](sec10_usability.md#usability)参照．
<details>
<summary>原文</summary>
The IdP **SHALL** provide effective mechanisms for redress of subscriber complaints or problems (e.g., subscriber identifies an inaccurate attribute value). See [Sec. 10](sec10_usability.md#usability) on usability considerations for redress.
</details>

### IdPにおけるRPのホワイトリスト (IdP Allowlists of RPs) {#idp-allowlist}

静的な信頼の合意では，IdP は，加入者(subscriber)に実行時に確認することなしに，IdP から認証と属性を受け取ることを許可された RP のホワイトリストを確立**してもよい(MAY)**．RP をそのホワイトリストに登録する場合，IdP は，RP が SP 800-63 ガイドラインの該当するすべての規定と要件を遵守していることを保証**なければならない(SHALL)**．IdP は，認証時にホワイトリストに登録された RP に渡される 属性を決定し**なければならない(SHALL)**．IdP は，[Sec. 9.2](sec9_privacy.md#notice) で説明されているように，加入者(subscriber)がホワイトリストを利用できるようにし**なければならない(SHALL)**．

IdP におけるホワイトリストは，使用中のフェデレーションプロトコルに適用可能なドメイン名，暗号鍵，またはその他の識別子を使用して，RP を一意に識別し**なければならない(SHALL)**．識別子を共有するすべてのエンティティは，ホワイトリストの目的で同等と見なさし**なければならない(SHALL)**．たとえば，ワイルドカードドメイン識別子「\*.example.com」は，「www.example.com」「service.example.com」「unknown.example.com」に等しく一致する． これら 3 つのサイトはすべて，ホワイトリストを使用した開示を決定する際に同じ RP として扱われる． ホワイトリストは，RP の意図しないなりすましを避けるため，できるだけ具体的にする**必要がある(SHOULD)**．

<details>
<summary>原文</summary>
In a static trust agreement, IdPs **MAY** establish allowlists of RPs authorized to receive authentication and attributes from the IdP without a runtime decision from the subscriber. When placing an RP on its allowlist, the IdP **SHALL** ensure that the RP abides by all applicable provisions and requirements in the SP 800-63 guidelines. The IdP **SHALL** determine which identity attributes are passed to the allowlisted RP upon authentication. IdPs **SHALL** make allowlists available to subscribers as described in [Sec. 9.2](sec9_privacy.md#notice).

IdP allowlists **SHALL** uniquely identify RPs through the means of domain names, cryptographic keys, or other identifiers applicable to the federation protocol in use. Any entities that share an identifier **SHALL** be considered equivalent for the purposes of the allowlist. For example, a wildcard domain identifier of "*.example.com" would match the domains "www.example.com", "service.example.com", and "unknown.example.com" equally. All three of these sites would be treated as the same RP for disclosure decisions using the allowlist. Allowlists **SHOULD** be as specific as possible to avoid unintentional impersonation of an RP.
</details>

### IdPにおけるRPのブラックリスト (IdP Blocklists of RPs)

IdP は，加入者(subscriber)によって要求された場合でも，IdP から認証アサーションまたは属性を受信することを許可されていない RP のブラックリストを確立**してもよい(MAY)**．RP が IdP のブラックリストにある場合，IdP は，いかなる状況においても，その RP をターゲットとするアサーションを生成し**てはならない(SHALL NOT)**．

IdP におけるブラックリストは，使用中のフェデレーションプロトコルに適用可能なドメイン名，暗号鍵，またはその他の識別子を使用して，RP を一意に識別し**なければならない(SHALL)**．識別子を共有するすべてのエンティティは，ブラックリストの目的で同等と見なさし**なければならない(SHALL)**．たとえば，ワイルドカードドメイン識別子「\*.example.com」は，「www.example.com」「service.example.com」「unknown.example.com」に等しく一致する． これら 3 つのサイトはすべて，ブラックリストを使用する際に同じ RP として扱われる．

<details>
<summary>原文</summary>
IdPs **MAY** establish blocklists of RPs not authorized to receive authentication assertions or attributes from the IdP, even if requested to do so by the subscriber. If an RP is on an IdP's blocklist, the IdP **SHALL NOT** produce an assertion targeting the RP in question under any circumstances.

IdP blocklists **SHALL** uniquely identify RPs through the means of domain names, cryptographic keys, or other identifiers applicable to the federation protocol in use. Any entities that share an identifier **SHALL** be considered equivalent for the purposes of the blocklist. For example, a wildcard domain identifier of "*.example.com" would match the domains "www.example.com", "service.example.com", and "unknown.example.com" equally. All three of these sites would be treated as the same RP for decisions using the blocklist.
</details>

### IdPにおける実行時の決定 (IdP Runtime Decisions) {#idp-runtime-decision}

IdP と信頼の合意を形成しているが，その IdP とのホワイトリストまたはブラックリストには含まれていないすべての RP は，IdPのデフォルトポリシーによって判断され**なければならない(SHALL)**．このポリシーでは，実行時の承認の決定は，信頼の合意時に規定された authorized party によって行われる．ほとんどの場合，実用上，authorized party は加入者(subscriber)である． ただし，加入者(subscriber)に代わって，管理者またはその他の関係者に確認される場合もある．動的な信頼の合意では，注記：属性の提示を承認できるのは実行時の決定のみである．

<details>
<summary>原文</summary>
Every RP that is in a trust agreement with an IdP but not on an allowlist or a blocklist with that IdP **SHALL** be governed by a default policy in which runtime authorization decisions will be made by an authorized party identified by the trust agreement. In most circumstances, and for practical purposes, the authorized party is the subscriber; however, it is possible for an administrator or other party to be prompted on behalf of the subscriber. Note that in a dynamic trust agreement, only a runtime decision can be used to authorize the release of attributes.
</details>

この操作モードでは，認証アサーションを提供し，加入者(subscriber)に代わって RP に特定の属性を提示することに同意するために，フェデレーショントランザクション中に authorized party が IdP によって確認を求められる．IdP は，加入者(subscriber)に関する属性が RP に送信される前に，authorized party に明示的な通知を出し，肯定的な確認をし**なければならない(SHALL)**．少なくとも，通知は，[Sec. 9.2](sec9_privacy.md#notice) に記載されている通り，最も効果的な通知を提供し，確認結果を得る立場にある当事者によって提供される**必要がある(SHOULD)**．IdP は，トランザクションが承認された場合に RP に提示される属性を開示し**なければならない(SHALL)**．使用中のフェデレーションプロトコルが実行時にオプションの属性開示を許可する場合，authorized party には，フェデレーショントランザクションを完全に終了することなく，特定の属性を RP に送信するかどうかを決定するオプションが与えられ**なければならない(SHALL)**．

<details>
<summary>原文</summary>
In this mode of operation, the authorized party is prompted by the IdP during the federation transaction for their consent to provide an authentication assertion and release specific attributes to the RP on behalf of the subscriber. The IdP **SHALL** provide the authorized party with explicit notice and prompt them for positive confirmation before any attributes about the subscriber are transmitted to the RP. At a minimum, the notice **SHOULD** be provided by the party in the position to provide the most effective notice and obtain confirmation, consistent with [Sec. 9.2](sec9_privacy.md#notice). The IdP **SHALL** disclose which attributes will be released to the RP if the transaction is approved. If the federation protocol in use allows for optional attribute disclosure at runtime, the authorized party **SHALL** be given the option to decide whether to transmit specific attributes to the RP without terminating the federation transaction entirely.
</details>

機密情報が許可なく公開される (ショルダーサーフィンなど) リスクを軽減するために，IdP はデフォルトで，authorized party に表示される機密情報をマスクし**なければならない(SHALL)**．authorized party が加入者(subscriber)である場合，IdP は，加入者(subscriber)が送信前に完全な値を表示できるように，加入者(subscriber)が一時的にマスク解除するメカニズムを提供し**なければならない(SHALL)**．マスキングの詳細については，ユーザビリティの考慮事項に関する[Sec. 10](sec10_usability.md#usability)を参照．

IdP は，authorized party の決定を記録しておき，同じ属性のセットを同じ RP に再送信するメカニズムを採用**してもよい(MAY)**．このメカニズムは，IdP によって管理される加入者(subscriber)アカウントに関連付けられる．そのようなメカニズムが提供される場合，IdP は，authorized partyが将来そのような記録されたアクセスを取り消すことを許可し**なければならない(SHALL)**．

<details>
<summary>原文</summary>
To mitigate the risk of unauthorized exposure of sensitive information (e.g., shoulder surfing), the IdP **SHALL**, by default, mask sensitive information displayed to the authorized party. If the authorized party is the subscriber, the IdP **SHALL** provide mechanisms for the subscriber to temporarily unmask such information in order for the subscriber to view full values before transmission. For more details on masking, see [Sec. 10](sec10_usability.md#usability) on usability considerations.

An IdP **MAY** employ mechanisms to remember and re-transmit the exact attribute bundle to the same RP, remembering the authorized party's decision. This mechanism is associated with the subscriber account as managed by the IdP. If such a mechanism is provided, the IdP **SHALL** allow the authorized party to revoke such remembered access at a future time.
</details>

### RPにおけるIdPのホワイトリスト (RP Allowlists of IdPs)

RP は，実行時に加入者(subscriber)に確認することなしに，RP が認証と属性を受け入れる IdP のホワイトリストを確立**してもよい(MAY)**．IdP をホワイトリストに登録する場合，RP は，IdP がガイドラインの規定と要件を遵守していることを確認し**なければならない(SHALL)**．

RP におけるホワイトリストは，使用中のフェデレーションプロトコルに適用可能なドメイン名，暗号鍵，またはその他の識別子を使用して IdP を一意に識別し**なければならない(SHALL)**．

<details>
<summary>原文</summary>
RPs **MAY** establish allowlists of IdPs from which the RP will accept authentication and attributes without a runtime decision from the subscriber. When placing an IdP in its allowlist, the RP **SHALL** ensure that the IdP abides by the provisions and requirements in these guidelines.

RP allowlists **SHALL** uniquely identify IdPs through the means of domain names, cryptographic keys, or other identifiers applicable to the federation protocol in use.
</details>

### RPにおけるIdPのブラックリスト (RP Blocklists of IdPs)

RP は，加入者(subscriber)によって要求された場合でも，RP が認証または属性を受け入れない IdP のブロックリストを確立**してもよい(MAY)**．ブロックリストに登録された IdP は，RP との有効な信頼の合意を形成している場合もある．たとえば，両方が同じ federation authority の下にある場合など．

RP におけるブロックリストは，使用中のフェデレーションプロトコルに適用可能なドメイン名，暗号化鍵，またはその他の識別子を使用して IdP を一意に識別し**なければならない(SHALL)**．

<details>
<summary>原文</summary>
RPs **MAY** also establish blocklists of IdPs that the RP will not accept authentication or attributes from, even when requested by the subscriber. A blocklisted IdP can be otherwise in a valid trust agreement with the RP, for example if both are under the same federation authority.

RP blocklists **SHALL** uniquely identify IdPs through the means of domain names, cryptographic keys, or other identifiers applicable to the federation protocol in use.
</details>

### RPにおける実行時の決定 (RP Runtime Decisions) {#rp-runtime-decision}

RP と信頼の合意を形成しているが，RP のホワイトリストまたはブロックリストには含まれていないすべての IdP は，デフォルトポリシーによって管理され**なければならない(SHALL)**．この場合RPは，authorized partyに，加入者(subscriber)に代わって認証のためにどの IdP に接続するか，選択または入力するよう要求する．このプロセスは，加入者(subscriber)が電子メールアドレスなどのhuman-facing な識別子を入力できるようにする discovery のメカニズムを使用することで容易に行うことができる．このプロセスにより，RP はその識別子に適した IdP をプログラムで選択できるようになる．

<details>
<summary>原文</summary>
Every IdP that is in a trust agreement with an RP but not on an allowlist or a blocklist with that RP **SHALL** be governed by a default policy in which runtime authorization decisions will be made by the authorized party indicated in the trust agreement. In this mode, the authorized party is prompted by the RP to select or enter which IdP to contact for authentication on behalf of the subscriber. This process can be facilitated through use of a discovery mechanism allowing the subscriber to enter a human-facing identifier such as an email address. This process allows the RP to programmatically select the appropriate IdP for that identifier.
</details>

RP は，authorized party が特定の IdP を使用することを決定したことを記録するメカニズムを採用し**てもよい(MAY)**．このメカニズムは RP での認証の前に使用されるため，RP がこのメカニズムを提供する方法（たとえば，認証されたセッション外のブラウザー Cookieなど）は，[Sec. 5.4](sec5_federation.md#rp-account) で説明されている RPの加入者(subscriber)アカウントとは別のものである．そのようなメカニズムが提供される場合，RP は，authorized party が将来そのような記録されたオプションを取り消すことを許可し**なければならない(SHALL)**．
<details>
<summary>原文</summary>
The RP **MAY** employ mechanisms to remember the authorized party's decision to use a given IdP. Since this mechanism is employed prior to authentication at the RP, the manner in which the RP provides this mechanism (e.g., a browser cookie outside the authenticated session) is separate from the RP subscriber account described in [Sec. 5.4](sec5_federation.md#rp-account). If such a mechanism is provided, the RP **SHALL** allow the authorized party to revoke such remembered options at a future time.
</details>

## RP 加入者(subscriber)アカウント (RP Subscriber Accounts) {#rp-account}

RP が *RP 加入者(subscriber)アカウント* と呼ばれる，RP 自体に対してローカルな加入者(subscriber)を表すレコードを保持することは一般的である．RP 加入者(subscriber)アカウントには，RP でのアクセス権や，加入者(subscriber)の属性のキャッシュなどを含めることができる．アクティブな RP 加入者(subscriber)アカウントは，RP の信頼する IdP からの 1 つ以上のフェデレーション識別子にバインドされる．フェデレーションプロトコルを介してフェデレーション識別子の 1 つの認証が成功すると，加入者(subscriber)は RP 加入者(subscriber)アカウントによって保護された情報と機能にアクセスできるようになる．

RP 加入者(subscriber)アカウントは，RP が加入者(subscriber)に関する一連の属性を RP の加入者(subscriber)アカウントを表すデータレコードに関連付けたときに _プロビジョニング_ される．RP 加入者(subscriber) アカウントは，少なくとも 1 つのフェデレーション識別子にバインドされ**なければならなず(SHALL)**，特定のフェデレーション識別子は，特定の RP で 1 つの RP 加入者(subscriber) アカウントにのみバインドされる．プロビジョニングは， [Sec. 5.4.1](sec5_federation.md#provisioning) で説明されている展開パターンに応じて，認証の前に，またはフェデレーション認証プロセスの結果として発生する． プロビジョニングされる前は，RP 加入者(subscriber)アカウントは存在せず，RP に関連するデータレコードも存在しない．

<details>
<summary>原文</summary>
It is common for an RP to keep a record representing a subscriber local to the RP itself, known as the *RP subscriber account*. The RP subscriber account can contain things like access rights at the RP as well as a cache of identity attributes for the subscriber. An active RP subscriber account is bound to one or more federated identifiers from the RP's trusted IdPs. Successful authentication of one of these federated identifiers through a federation protocol allows the subscriber to access the information and functionality protected by the RP subscriber account.

An RP subscriber account is _provisioned_ when the RP has associated a set of attributes about the subscriber with a data record representing the subscriber account at the RP. The RP subscriber account **SHALL** be bound to at least one federated identifier, and a given federated identifier is bound to only one RP subscriber account at a given RP. The provisioning can happen prior to authentication or as a result of the federated authentication process, depending on the deployment patterns as discussed in [Sec. 5.4.1](sec5_federation.md#provisioning). Prior to being provisioned, the RP subscriber account does not exist and has no associated data record at the RP.
</details>

RP 加入者(subscriber)アカウントは，RP が RP でのアカウントへのすべてのアクセスを削除すると _終了_ します． 終了には，フェデレーション識別子と bound authenticators の解除，監査とセキュリティ目的で必要なものを除くアカウントに関連付けられた属性と情報の削除が含まれ**なければならない(SHALL)**．RP は，フェデレーション元の加入者(subscriber)アカウントの現在の有効性に関係なく，さまざまな理由で IdP とは独立して RP 加入者(subscriber)アカウントを終了**してもよい(MAY)**．

認証されたセッションは，RP 加入者(subscriber)アカウントに関連付けられたフェデレーション識別子の発行者である IdP からの有効なアサーションを，RP が 処理および検証した場合にのみ，RP によって作成され**なければならない(SHALL)**．アサーションが FAL3 で bound authenticator の提示も必要とする場合は，[Sec. 6.1.2](sec6_assertions.md#boundauth) で説明されているように，RP 加入者(subscriber)アカウントが認証されたセッションに関連付けられる前に，bound authenticator が提示および処理され**なければならない(SHALL)**．アサーションが処理される前，および認証されたセッションが終了した後は，RP 加入者(subscriber)アカウントは認証されていないものの，プロビジョニングは可能である．

<details>
<summary>原文</summary>
An RP subscriber account is _terminated_ when the RP removes all access to the account at the RP. Termination **SHALL** include unbinding any federated identifiers and bound authenticators as well as removing attributes and information associated with the account except what is required for auditing and security purposes. An RP **MAY** terminate an RP subscriber account independently from the IdP for a variety of reasons, regardless of the current validity of the subscriber account from which it is derived.

An authenticated session **SHALL** be created by the RP only when the RP has processed and verified a valid assertion from the IdP that is the issuer of the federated identifier associated with the RP subscriber account. If the assertion also requires presentation of a bound authenticator at FAL3, the bound authenticator **SHALL** also be presented and processed before the RP subscriber account is associated with an authenticated session, as discussed in [Sec. 6.1.2](sec6_assertions.md#boundauth). Before the federated assertion is processed and after termination of the authenticated session, the RP subscriber account is unauthenticated though it could still be provisioned.
</details>

### プロビジョニングモデル (Provisioning Models) {#provisioning}

RP 加入者(subscriber)アカウントのプロビジョニングプロセスのライフサイクルは，[Sec. 5.1](sec5_federation.md#trust-agreement) で説明した信頼の合意や IdP と RP の展開パターンなどの要因によって異なる．ただし，すべての場合において，RP 加入者(subscriber)アカウントは，RP で認証されたセッションを確立する前に，次のいずれかの方法で RP にプロビジョニングされ**なければならない(SHALL)**．

<details>
<summary>原文</summary>
The lifecycle of the provisioning process for an RP subscriber account varies depending on factors including the trust agreement discussed in [Sec. 5.1](sec5_federation.md#trust-agreement) and the deployment pattern of the IdP and RP. However, in all cases, the RP subscriber account **SHALL** be provisioned at the RP prior to the establishment of an authenticated session at the RP in one of the following ways:
</details>

即時プロビジョニング
: RP 加入者(subscriber)アカウントは，RP が IdP からフェデレーション識別子が不明なアサーションを初めて受信したときに自動的に作成される．アサーション内または [Sec. 6.3](sec6_assertions.md#s-identity-api) で説明されているアイデンティティAPI を介してフェデレーションプロセス中に取得した属性は，RP 加入者(subscriber)アカウントに関連付け**てもよい(MAY)**．この方法でプロビジョニングされたアカウントは，アカウントのプロビジョニングに使用されたアサーションでフェデレーション識別子にバインドされる．これは，RP と IdP 間の調整が最小限で済むため，フェデレーションシステムでの最も一般的なプロビジョニング方法である． ただし，そのようなシステムでは，RP SHALL は，キャッシュされた属性を管理する責任を負わ**なければならない(SHALL)**．

<details>
<summary>原文</summary>
Just-In-Time Provisioning
: An RP subscriber account is created automatically the first time the RP receives an assertion with an unknown federated identifier from an IdP. Any identity attributes learned during the federation process, either within the assertion or through an identity API as discussed in [Sec. 6.3](sec6_assertions.md#s-identity-api), **MAY** be associated with the RP subscriber account. Accounts provisioned in this way are bound to the federated identifier in the assertion used to provision them.
This is the most common form of provisioning in federation systems, as it requires the least coordination between the RP and IdP. However, in such systems, the RP **SHALL** be responsible for managing any cached attributes it might have.
</details>
[Figure 6. Just-In-Time Provisioning](sec5_federation.md#fig-6){:name="fig-6"}
{:latex-ignore="true"}

![Diagram of the stages of a just-in-time provisioning of an RP subscriber account based on a subscriber account.]({{site.baseurl}}/{{page.collection}}/media/JIT-provisioning.png 'Just-In-Time Provisioning'){:latex-src="JIT-provisioning.pdf" latex-fig="6" latex-place="h"}

~~~
\clearpage
~~~
{:latex-literal="true"}

事前プロビジョニング
: RP 加入者(subscriber)アカウントは，IdP が属性を RP にプッシュするか，RP が IdP から属性をプルすることによって作成される．アカウントの事前プロビジョニングは，通常，[Sec. 5.4.3](sec5_federation.md#provisioning-api) で説明されているように，プロビジョニング API を介して一括で行われる．プロビジョニングは，代表される加入者(subscriber)がフェデレーショントランザクションを介して認証する前に行われるためである．事前にプロビジョニングされたアカウントは，プロビジョニング時にフェデレーション識別子にバインドされ**なければならない(SHALL)**．RP が特定のフェデレーション識別子を検出すると，関連付けられたアカウントがログインできる．
この形式のプロビジョニングには，IdP と RP のインフラストラクチャと計画が必要であるが，これらのプロセスは自動化されたプロトコルによって容易に行われる．RP は，まだ RP システムと対話していないユーザーに関する属性も収集する．これは，プライバシーの問題を引き起こす可能性がある．さらに，IdP と RP は，[Sec. 5.4.2](sec5_federation.md#attribute-sync) で説明したように，プロビジョニングされたアカウントのセットを時間の経過とともに同期させておく必要がある．

<details>
<summary>原文</summary>
Pre-provisioning
: An RP subscriber account is created by the IdP pushing the attributes to the RP or the RP pulling attributes from the IdP. Pre-provisioning of accounts generally occurs in bulk through a provisioning API as discussed in [Sec. 5.4.3](sec5_federation.md#provisioning-api), as the provisioning occurs prior to the represented subscribers authenticating through a federated transaction. Pre-provisioned accounts **SHALL** be bound to a federated identifier at the time of provisioning. Any time a particular federated identifier is seen by the RP, the associated account can be logged in as a result. 
This form of provisioning requires infrastructure and planning on the part of the IdP and RP, but these processes can be facilitated by automated protocols. The RP also collects attributes about users who have not interacted with the RP system yet, which can cause privacy issues. Additionally, the IdP and RP must keep the set of provisioned accounts synchronized over time as discussed in [Sec. 5.4.2](sec5_federation.md#attribute-sync).
</details>
[Figure 7. Pre-Provisioning](sec5_federation.md#fig-7){:name="fig-7"}
{:latex-ignore="true"}

![Diagram of the stages of a pre-provisioned RP subscriber account based on a subscriber account.]({{site.baseurl}}/{{page.collection}}/media/Pre-provisioning.png 'Pre-Provisioning'){:latex-src="Pre-provisioning.pdf" latex-fig="7" latex-place="h"}

~~~
\clearpage
~~~
{:latex-literal="true"}

一時的なプロビジョニング (Ephemeral)
: アサーションの処理時に RP 加入者(subscriber)アカウントが作成されるが，認証されたセッションが終了すると，RP 加入者(subscriber)アカウントは終了する．このプロセスは即時プロビジョニングに似ているが，RP は，監査およびセキュリティ目的で必要なもの (アクセスログなど) を除いて，セッションの完了時にアカウントの長期的な記録を保持しない．
この形式のプロビジョニングは，アクセス権を完全に IdP に外部化する RP にとって役立ち，RP をより簡素化して内部状態を少なくすることができる．ただし，このパターンは一般的ではない．最も単純な RP であっても，アプリケーション内の状態を追跡する必要があるか，少なくともフェデレーション識別子に関連付けられたアクションの記録を保持する必要がある傾向があるためである．

<details>
<summary>原文</summary>
Ephemeral
: An RP subscriber account is created when processing the assertion, but then the RP subscriber account is terminated when the authenticated session ends. This process is similar to a just-in-time provisioning, but the RP keeps no long-term record of the account when the session is complete, except what is required for audit and security purposes (such as access logs).
This form of provisioning is useful for RPs that fully externalize access rights to the IdP, allowing the RP to be more simplified with less internal state. However, this pattern is not common because even the simplest RPs tend to have a need to track state within the application or at least keep a record of actions associated with the federated identifier.
</details>
[Figure 8. Ephemeral Provisioning](sec5_federation.md#fig-8){:name="fig-8"}
{:latex-ignore="true"}

![Diagram of the stages of an ephemeral RP subscriber account based on a subscriber account.]({{site.baseurl}}/{{page.collection}}/media/Ephemeral-provisioning.png 'Ephemeral Provisioning'){:latex-src="Ephemeral-provisioning.pdf" latex-fig="8" latex-place="h"}

その他
: 他の RP 加入者(subscriber)アカウントプロビジョニングモデルも可能だが，そのようなモデルの詳細は，これらのガイドラインの範囲外である．代替プロビジョニングモデルの詳細は，IdP および RP のプライバシーリスク評価に含め**なければならない(SHALL)**．

すべての組織は，信頼の合意の一部としてプロビジョニングモデルを文書化し**なければならない(SHALL)**．
<details>
<summary>原文</summary>
Other
: Other RP subscriber account provisioning models are possible but the details of such models are outside the scope of these guidelines. The details of any alternative provisioning model **SHALL** be included in the privacy risk assessments of the IdP and RP.

All organizations **SHALL** document their provisioning model as part of their trust agreement.
</details>

### 属性情報の同期 (Attribute Synchronization) {#attribute-sync}

フェデレーションプロセスでは，IdP と RP はそれぞれ，加入者(subscriber)アカウントに関連付けられた属性の独自のストアを持っている．IdP は加入者(subscriber)アカウントに直接確認しているが，RP 加入者(subscriber)アカウントは，フェデレーショントランザクション中に提示される加入者(subscriber)アカウントの属性のサブセットからのものである．したがって，IdP と RP の属性ストアは，時間の経過とともに互いに乖離する可能性がある．

RP の観点からは，IdP は，IdP の加入者(subscriber)アカウントに関連付けられていると IdP が提示する属性の authoritative source である．ただし，RP は，RP 加入者(subscriber)アカウントに関連付ける他の属性を追加で収集し，オプションで検証**してもよい(MAY)**．場合によっては，これらの属性が IdP によって提示されるものを上書きすることもある．たとえば，IdP が加入者(subscriber)の完全な表示名を提示する場合，RP は，加入者(subscriber)が RP で使用する代替の名前を提供できるようにしてもよい．

<details>
<summary>原文</summary>
In a federated process, the IdP and RP each have their own stores of identity attributes associated with the subscriber account. The IdP has a direct view of the subscriber account, but the RP subscriber account is derived from a subset of attributes from the subscriber account that are presented during the federation transaction. Therefore, it is possible for the IdP's and RP's attribute stores to diverge from with each other over time.

From the RP's perspective, the IdP is the authoritative source for any attributes that the IdP asserts as being associated with the subscriber account at the IdP. However, the RP **MAY** additionally collect, and optionally verify, other attributes to associate with the RP subscriber account. Sometimes, these attributes can even override what's asserted by the IdP. For example, if an IdP asserts a full display name for the subscriber, the RP can allow the subscriber to provide an alternative preferred name for use at the RP.
</details>

IdP は，RP で利用可能な加入者(subscriber)アカウントの属性が更新されたときに，それを利用しているRP に通知する**必要がある(SHOULD)**．これは，[Sec. 5.7](sec5_federation.md#shared-signals) で説明されているように共有シグナリングを使用するか，[Sec. 5.4.3](sec5_federation.md#provisioning-api) で説明されているようにプロビジョニング API を介すか，アサーションでシグナルを提供することによって実現する (たとえば，関連する属性の最終更新時を示すタイムスタンプで RP がキャッシュの期限切れを確認するなど）．

IdP は，加入者(subscriber)アカウントが終了したとき，または加入者(subscriber)アカウントの RP へのアクセスが取り消されたときに，それを利用しているRP に通知する**必要がある(SHOULD)**．これは，[Sec. 5.7](sec5_federation.md#shared-signals) で説明されている共有シグナリングを使用するか，[Sec. 5.4.3](sec5_federation.md#provisioning-api) で説明されているプロビジョニングAPI を使用して実現される．このような信号を受信すると，RP は RP 加入者(subscriber)アカウントを終了し，RP 加入者(subscriber)アカウントに関連付けられているすべての個人情報を，監査およびセキュリティ目的で必要なものは除いて，削除し**なければならない(SHALL)**．
</詳細>
<details>
<summary>原文</summary>
The IdP **SHOULD** signal downstream RPs when the attributes of a subscriber account available to the RP have been updated. This can be accomplished using shared signaling as described in [Sec. 5.7](sec5_federation.md#shared-signals), through a provisioning API as described in [Sec. 5.4.3](sec5_federation.md#provisioning-api), or by providing a signal in the assertion (e.g., a timestamp indicating when relevant attributes were last updated, allowing the RP to determine that its cache is out of date).

The IdP **SHOULD** signal downstream RPs when a subscriber account is terminated, or when the subscriber account's access to an RP is revoked. This can be accomplished using shared signaling as described in [Sec. 5.7](sec5_federation.md#shared-signals) or through a provisioning API as described in [Sec. 5.4.3](sec5_federation.md#provisioning-api). Upon receiving such a signal, the RP **SHALL** terminate the RP subscriber account and remove all personal information associated with the RP subscriber account, except what is required for audit and security purposes.
</details>

### プロビジョニングAPI (Provisioning APIs) {#provisioning-api}

プロアクティブなプロビジョニングの一部として，_プロビジョニングAPI_ と呼ばれる汎用的な属性API を介して，RP に加入者(subscriber)属性へのアクセスを与えることができる．このタイプの API により，IdP は一定範囲の加入者(subscriber)アカウントの属性をプッシュでき，場合によっては RP がこれらの加入者(subscriber)アカウントの属性を直接クエリできるようになる．API へのアクセスはフェデレーショントランザクションのコンテキスト外で許可されるため，特定の加入者(subscriber)のプロビジョニングAPI へのアクセスは，特定の加入者(subscriber)が認証されたことを RP に示さない．アサーションを使用してフェデレーション認証プロセスを実行する方法の詳細については，[Sec. 6, Assertions](sec6_assertions.md#assertions) 参照．

<details>
<summary>原文</summary>
As part of some proactive forms of provisioning, the RP can be given access to subscriber attributes through a general-purpose attribute API known as a _provisioning API_. This type of API allows an IdP to push attributes for a range of subscriber accounts, and sometimes allows an RP to query the attributes of these subscriber accounts directly. Since access to the API is granted outside the context of a federated transaction, access to the provisioning API for a given subscriber does not indicate to the RP that a given subscriber has been authenticated. See [Sec. 6, Assertions](sec6_assertions.md#assertions) for more information on how the federated authentication process is accomplished using assertions.
</details>

特定の RP で利用可能なプロビジョニングAPI の属性は，RP がその機能を実行するために必要なものだけに制限され**なければならない(SHALL)**．信頼の合意の形成の一環としてプロビジョニングAPI へのアクセス権が RP に与えられた場合，IdP は文書化し**なければならない(SHALL)**．文書には少なくとも以下の全てを含む．

- プロビジョニングモデルを使用したアクセスの目的．
- RP で利用できる属性のセット．
- API が RP へのプッシュとして機能するか，RP からのプルとして機能するか，またはその両方として機能するか．
- 属性が RP で利用可能になっている加入者(subscriber)集団．

<details>
<summary>原文</summary>
The attributes in the provisioning API available to a given RP **SHALL** be limited to only those necessary for the RP to perform its functions. As part of establishing the trust agreement, the IdP **SHALL** document when an RP is given access to a provisioning API including at least the following:

- the purpose for the access using the provisioning model;
- the set of attributes made available to the RP;
- whether the API functions as a push to the RP, a pull from the RP, or both; and
- the population of subscribers whose attributes are made available to the RP.
</details>

IdP は，プロビジョニングAPI へのプルベースのアクセスに対して，RP からの認証を要求し**なければならない(SHALL)**．RP は，プロビジョニングAPI へのプッシュベースのアクセスに対して，IdP からの認証を要求し**なければならない(SHALL)**．

プロビジョニングAPI は，動的または暗黙な信頼の合意の下で利用可能に**してはならない(SHALL NOT)**．IdP は，信頼の合意を形成していない RP がプロビジョニングAPI を使用できるように**してはならない(SHALL NOT)**．IdP は，RPとのフェデレーショントランザクションや加入者(subscriber) アカウントの取り消しの通知などの関連機能を容易に行うことができるよう，RP とのフェデレーションリレーションシップの一部としてのみ，プロビジョニングAPI へのアクセスを提供し**なければならない(SHALL)**．IdP は，RP がその機能目的でアクセスする必要がなくなった場合，または信頼の合意が終了した場合に，RP のプロビジョニングAPI へのアクセスを無効にし**なければならない(SHALL)**．

<details>
<summary>原文</summary>
The IdP **SHALL** require authentication from the RP for any pull-based access to a provisioning API. The RP **SHALL** require authentication from the IdP for any push-based access to a provisioning API.

A provisioning API **SHALL NOT** be made available under a dynamic or implicit trust agreement. The IdP **SHALL NOT** make a provisioning API available to any RP outside of an established trust agreement. The IdP **SHALL** provide access to a provisioning API only as part of a federated identity relationship with an RP to facilitate federated transactions with that RP and related functions such as signaling revocation of the subscriber account. The IdP **SHALL** revoke an RP's access to the provisioning API once access is no longer required by the RP for its functioning purposes or when the trust agreement is terminated.
</details>

RP に提供されるすべてのプロビジョニングAPI は，IdP の管理および管轄下に**なければならない(SHALL)**．IdP は，このプロビジョニングAPI を介して属性を提供するために，外部属性プロバイダーを情報源として使用**してもよい(MAY)** が，IdP は，参照する属性属性プロバイダーによって提供される情報の内容と正確性について責任を負う．

プロビジョニングAPI が使用されている場合，IdP は，加入者(subscriber)アカウントが終了したときに RP に通知し**なければならない(SHALL)**．このような通知を受信すると，RP は関連する RP 加入者(subscriber)アカウントを終了し**なければならない(SHALL)**．
<details>
<summary>原文</summary>
Any provisioning API provided to the RP **SHALL** be under the control and jurisdiction of the IdP. External attribute providers **MAY** be used as information sources by the IdP to provide attributes through this provisioning API, but the IdP is responsible for the content and accuracy of the information provided by the referenced attribute providers.

When a provisioning API is in use, the IdP **SHALL** signal to the RP when a subscriber account has been terminated. When receiving such a signal, the RP **SHALL** terminate the associated RP subscriber account.
</details>

### Attribute Collection {#rp-attribute-collection}
<details>
<summary>原文</summary>
The RP **MAY** collect and maintain additional attributes from the subscriber beyond those provided by the IdP. These attributes are governed separately from any federation agreement since they are collected directly by the RP. All attributes associated with an RP subscriber account, regardless of their source, **SHALL** be removed when the RP subscriber account is terminated.
</details>
<details>
<summary>原文</summary>
The RP **SHALL** disclose to the subscriber the purpose for collection of any additional attributes. These attributes **SHALL** be used solely for the stated purposes of the RP's functionality and **SHALL NOT** have any secondary use, including communication of said attributes to other parties.

An RP **SHALL** disclose any additional attributes collected, and their use, as part of its System of Records Notice (SORN). The RP **SHALL** provide an effective means of redress for the subscriber to update and remove these additionally-collected attributes from the RP subscriber account. See [Sec. 10](sec10_usability.md#usability) on usability considerations for redress.
</details>

### タイムベースのRP加入者アカウントの削除 (Time-based Removal of RP Subscriber Accounts) {#stale-account}

時間の経過とともに，RP には IdP からアクセスできなくなった RP 加入者(subscriber)アカウントを蓄積される．これは，特に即時プロビジョニングモデルが使用されており，[Sec. 5.7](sec5_federation.md#shared-signals) で説明されているような IdP から加入者(subscriber)アカウントの終了を通知するための共有シグナリングが利用できない場合に，RP 加入者(subscriber)アカウントに個人情報を保持するリスクを RP にもたらす．このような状況では，RP はタイムベースのメカニズムを使用して，一定の期間アクセスがない（たとえば最終アクセスから120日経過など） RP 加入者(subscriber)アカウントを特定し，終了する**必要がある(SHOULD)**．

そのような非アクティブなアカウントを処理する場合，RP は，可能であれば，保留しているアカウントの終了について加入者(subscriber)に十分に通知し，予定された終了の前にアカウントを再アクティブ化するオプションを加入者(subscriber)に提供し**なければならない(SHALL)**．終了時に，RP は，監査およびセキュリティ目的で必要なものを除き，RP 加入者(subscriber)アカウントに関連付けられたすべての個人情報を削除し**なければならない(SHALL)**．
</詳細>
<details>
<summary>原文</summary>
Over time, an RP could accumulate RP subscriber accounts that are no longer accessible from the IdP. This poses a risk to the RP for holding personal information in the RP subscriber accounts, especially when a just-in-time provisioning model is in use and no shared signaling is available from the IdP to signal subscriber account termination as discussed in [Sec. 5.7](sec5_federation.md#shared-signals). In such circumstances, the RP **SHOULD** employ a time-based mechanism to identify RP subscriber accounts for termination that have not been accessed after a period of time, for example, 120 days since last access.

When processing such an inactive account, the RP **SHALL** provide sufficient notice to the subscriber, if possible, about the pending termination of the account and provide the subscriber with an option to re-activate the account prior to its scheduled termination. Upon termination, the RP **SHALL** remove all personal information associated with the RP subscriber account, except what is required for audit and security purposes.
</details>

## Privacy Requirements {#privacy-reqs}
<details>
<summary>原文</summary>
The ultimate goal of a subscriber is to interact with and use the RP. Federation involves the transfer of personal attributes from a third party that is not otherwise involved in a transaction &mdash; the IdP. Federation also potentially gives the IdP broad visibility into subscriber activities and status. Accordingly, there are specific privacy requirements associated with federation.

Communication between the RP and the IdP could reveal to the IdP where the subscriber is conducting a transaction. Communication with multiple RPs allows the IdP to build a profile of subscriber transactions that would not have existed without federation. This aggregation could enable new opportunities for subscriber tracking and use of profile information that do not always align with subscribers' privacy interests.
</details>
<details>
<summary>原文</summary>
If an IdP discloses information on subscriber activities at an RP to any party, or processes the subscriber's attributes for any purpose other than identity proofing, authentication, or attribute assertions (collectively "identity service"), related fraud mitigation, to comply with law or legal process, or, in the case of a specific user request, to transmit the information, the IdP **SHALL** implement measures to maintain predictability and manageability commensurate with the privacy risk arising from the additional processing. Measures **MAY** include providing clear notice, obtaining subscriber consent, or enabling selective use or disclosure of attributes. When an IdP uses consent measures, the IdP **SHALL NOT** make consent for the additional processing a condition of the identity service.

If the same subscriber account is asserted to multiple RPs, and those RPs communicate with each other, the colluding RPs could track a subscriber's activity across multiple applications and security domains. The IdP **SHOULD** employ technical measures, such as the use of pairwise pseudonymous identifiers described in [Sec. 6.2.5](sec6_assertions.md#ppi) or privacy-enhancing cryptographic protocols, to provide disassociability and discourage subscriber activity tracking and profiling between RPs.
</details>
<details>
<summary>原文</summary>
An IdP **MAY** disclose information on subscriber activities to RPs for security purposes, such as communication of suspicious activity or a compromised subscriber account as described in [Sec. 5.7](sec5_federation.md#shared-signals), if stated within the trust agreement. An RP **MAY** disclose information on subscriber activities to IdPs for security purposes, such as communication of suspicious activity or a compromised RP subscriber account, if stated within the trust agreement.

An IdP **SHOULD** signal subscriber account termination to RPs that have been provisioned with federated identifiers bound to that subscriber account using shared signaling as discussed in [Sec. 5.7](sec5_federation.md#shared-signals). RPs that receive such a signal from the IdP **SHALL** terminate the RP subscriber account and remove all personal information associated with the RP subscriber account, except what is required for audit and security purposes.
</details>
<details>
<summary>原文</summary>
The following requirements apply specifically to federal agencies:

1. The agency **SHALL** consult with their Senior Agency Official for Privacy (SAOP) to conduct an analysis determining whether the requirements of the Privacy Act are triggered by the agency that is acting as an IdP, by the agency that is acting as an RP, or both (see [Sec. 9.4](sec9_privacy.md#agency-privacy)).

2. The agency **SHALL** publish or identify coverage by a System of Records Notice (SORN) as applicable.

3. The agency **SHALL** consult with their SAOP to conduct an analysis determining whether the requirements of the E-Government Act are triggered by the agency that is acting as an IdP, the agency that is acting as an RP, or both.

4. The agency **SHALL** publish or identify coverage by a Privacy Impact Assessment (PIA) as applicable.
</details>
<details>
<summary>原文</summary>
If the RP subscriber account lifecycle process gives the RP access to attributes through a provisioning API as discussed in [Sec. 5.4.3](sec5_federation.md#provisioning-api), additional privacy measures **SHALL** be implemented given the wide nature of information access. Specifically, it is possible for the attributes of a subscriber to be provided to an RP without the subscriber ever interacting with the RP in question. As a consequence, when a provisioning API is used, the IdP **SHALL** minimize the attributes made available to the RP. To prevent the transmission of attributes for users that will never use an RP, the IdP **SHALL** limit the population of subscriber accounts available via the provisioning API to the population of subscribers authorized to use the RP by the trust agreement.
</details>
##  Reauthentication and Session Requirements in Federated Environments {#federation-session}

In a federated environment, the RP manages its sessions separately from any sessions at the IdP. The assertion is related to both sessions but its validity period is ultimately independent of them. In order for the IdP to create an assertion for the subscriber, the subscriber needs to establish an authenticated session with the IdP. To create an authenticated session at the RP, the RP needs to process a valid assertion from the IdP.

Due to the distributed nature of a federated system, the subscriber's sessions with the IdP and with the RP terminate independently of each other. The RP **SHALL NOT** assume that the subscriber has an active session at the IdP past the issuance time of the assertion. The IdP **SHALL NOT** assume that termination of the subscriber's session at the IdP will propagate to any sessions that subscriber would have at downstream RPs. The RP and IdP **MAY** communicate session termination requests to other parties in the federation network, if supported by the federation protocol.

At the time of a federated login request, the subscriber **MAY** have a pre-existing session at the IdP which **MAY** be used to generate an assertion to the RP. The IdP **SHALL** communicate any information it has regarding the time of the subscriber's latest authentication event at the IdP, and the RP **MAY** use this information in making authorization and access decisions. Depending on the capabilities of the federation protocol in use, the IdP **SHOULD** allow the RP to request that the subscriber repeat authentication at the IdP as part of a federation request.

An RP requiring authentication through a federation protocol **SHALL** specify the maximum acceptable authentication age to the IdP, either through the federation protocol (if possible) or through the parameters of the trust agreement. The authentication age represents the time since the last authentication event in the subscriber's session at the IdP, and the IdP **SHALL** reauthenticate the subscriber if they have not been authenticated within that time period. The IdP **SHALL** communicate the authentication event time to the RP to allow the RP to decide if the assertion is sufficient for authentication at the RP and to determine the time for the next reauthentication event.

If an RP is granted access to an identity API along with the assertion, the lifetime of the access to the identity API is independent from the lifetime of the assertion itself. Since access to the identity API is often combined with access to additional APIs, it is common for this access to be valid long after the assertion has expired and possibly after the session with the RP has ended, allowing the RP to access APIs on the subscriber's behalf while the subscriber is no longer present. As a consequence, the RP's ability to successfully fetch additional attributes through an identity API **SHALL NOT** be used to establish a session at the RP. Likewise, inability to access an identity API **SHOULD NOT** be used to end the session at the RP.

See [[SP800-63B]](../_sp800-63b/sec7_session.md#sec7){:latex-href="#ref-SP800-63B"}, Sec. 7 for more information about session management requirements for both IdPs and RPs.

## Shared Signaling {#shared-signals}

In some environments, it is useful for the IdP and RP to send information to each other outside of the federation transaction. These signals can communicate important changes in state between parties that would not be otherwise known. The use of any shared signaling **SHALL** be documented in the trust agreement between the IdP and RP. Signaling from the IdP to the RP **SHALL** require a static trust agreement. Signaling from the RP to the IdP **MAY** be used in a static or dynamic trust agreement.

Any use of shared signaling **SHALL** be documented and made available to the authorized party stipulated by the trust agreement. This documentation **SHALL** include the events under which a signal is sent, the information included in such a signal (including any attribute information), and any additional parameters sent with the signal. The use of shared signaling **SHALL** be subject to privacy review under the trust agreement.

The IdP **MAY** send a signal regarding the following changes to the subscriber account:

- The account has been terminated.
- The account is suspected of being compromised.
- Attributes of the account, including identifiers other than the federated identifier (such as email address or certificate CN), have changed.
- The possible range of IAL, AAL, or FAL for the account has changed.

The RP **MAY** send a signal regarding the following changes to the RP subscriber account:

- The account has been terminated.
- The account is suspected of being compromised.
- An RP-managed bound authenticator is added.
- An RP-managed bound authenticator is removed.

Additional signals from both the IdP and RP **MAY** be allowed subject to privacy and security review as part of the trust agreement.
