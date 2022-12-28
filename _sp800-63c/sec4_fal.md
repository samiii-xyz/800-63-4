---
layout: default
title: Federation Assurance Level
navOrder: 4
navTitle: FAL
permalink: /sp800-63c/fal/
anchor: fal
section: 4
---

# Federation Assurance Level (FAL) {#fal}

*This section is normative.*

この章では，*フェデレーション保証レベル* (FAL) を定義する．FAL は，IdP と RP の間の関係を確立する方法や，アサーションを提示・保護する方法など，フェデレーショントランザクションを保護するための要件を示している．これらのレベルは，実行時に RP によって要求されるか，特定のトランザクションにおける RP と IdP の両方の configuration によって要求される． FAL は，アサーションを受け取る RP に対する保証と，RP が利用するアサーションを作成する IdP に対する保証を提供する．

多くの異なるフェデレーション実装オプションが可能である中，FAL は，より安全な展開オプションを表す明確なガイダンスを提供することを目的としている．最も適切な FAL を選択する方法の詳細については、[[SP800-63]](../_sp800-63/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63"} を参照のこと．

各 FAL は，FAL が増加するにつれてセキュリティと複雑さが増す一連の要件によって特徴付けられる．これらの要件は以下にリストされており，本書の他のセクションで展開される．

<details>
<summary>原文</summary>
This section defines allowable *federation assurance levels* (FALs). The FAL describes requirements for securing federation transactions, including requirements on how relationships between IdPs and RPs are established and how assertions are presented and protected. These levels can be requested by an RP at runtime or required by the configuration of both the RP and the IdP for a given transaction. The FAL provides assurances for the RP receiving the assertion as well as assurances for the IdP creating the assertion to be used by an RP.
  
While many different federation implementation options are possible, the FAL is intended to provide clear guidance representing increasingly secure deployment options. See [[SP800-63]](../_sp800-63/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63"} for details on how to choose the most appropriate FAL.

Each FAL is characterized by a set of requirements that increase the security and complexity as the FAL increases. These requirements are listed here and expanded in other sections of this document:
  
</details>


暗号の検証可能性
: フェデレーションプロトコルで提示されたアサーションは，それを発行した特定の IdP まで追跡可能であり，その接続はデジタル署名や MAC などの暗号化メカニズムで検証可能である．これにより，RP は，アサーションが変更または偽造されていないことを確認することも可能である．本項目は，すべての FAL で必須である．

対象者（Autience） の制約
: フェデレーションプロトコルで提示されるアサーションは特定の RP を対象としており，RP はアサーションの対象者であることを確認することができる．本項目は，すべての FAL で必須である．

インジェクション保護
: RP は，現在のフェデレーショントランザクションリクエスト以外の状況でアサーションを提示する攻撃者から強力に保護される．

信頼協定
: IdP と RP は，加入者（subscriber）が RP にログインする目的で，相互にフェデレーショントランザクションに参加することに同意する．これは，当事者間の静的な合意にまでさかのぼる，あるいは，接続自体から暗黙的に発生する可能性がある．

登録
: IdP と RP は，将来のフェデレーショントランザクション中にアサーションやその他のアーティファクトを検証できるように，識別子とキー マテリアルを交換する．

提示
: アサーションは，単独で（ベアラ アサーションとして）RP に提示することも，加入者（subscriber）によって提示された bound authenticator と連携して提示することもできる．

<details>
  <summary>原文</summary>
Cryptographic Verifiability
: The assertion presented in the federation protocol is traceable back to a specific IdP that issued it, and that connection can be verified with a cryptographic mechanism such as a digital signature or MAC. This also allows the RP to verify that the assertion was not modified or forged. This is required at all FALs.

Audience Restriction
: The assertion presented in the federation protocol is targeted to a specific RP and the RP can verify that it is the intended audience of the assertion. This is required at all FALs.  
  
  Injection Protection
: The RP is strongly protected from an attacker presenting an assertion in circumstances outside a current federation transaction request.  

Trust Agreement
: The IdP and RP have agreed to participate in a federation transaction with each other for the purposes of logging in the subscriber to the RP. This can be traced back to a static agreement between the parties or occur implicitly from the connection itself.

Registration
: The IdP and RP have exchanged identifiers and key material to allow for the verification of assertions and other artifacts during future federation transactions.

Presentation
: The assertion can be presented to the RP either on its own (as a bearer assertion) or in concert with a bound authenticator presented by the subscriber.  
</details>

[表1](sec4_fal.md#table-1) は，各 FAL の非規範的な側面の要約を示す．連続する各レベルは，下位レベルのすべての要件を包含し，満たす (たとえば，FAL3 でのフェデレーションプロセスは，FAL2 や FAL1 で受け入れられる．これは，FAL3 がこれらの下位レベルの要件をすべて満たしているからである)． [表1](sec4_fal.md#table-1) にない組み合わせも可能だが，ここでは範囲外としている．

[表1 フェデレーションアサーション レベル](sec4_fal.md#table-1){:name="table-1"}
{:latex-ignore="true"}

|FAL|インジェクション保護|信頼協定|登録|提示|
|:--:|----|----|----|----|----|----|
|1|推奨|Dynamic or Static|Dynamic or Static|Bearer Assertion|
|2|必須|Static|Dynamic or Static|Bearer Assertion|
|3|必須|Static|Static|Assertion and Bound Authenticator|
{:latex-table="1" latex-caption="Federation Assurance Levels" latex-columns="p@0.05\textwidth,p@0.16\textwidth,p@0.13\textwidth,p@0.15\textwidth,p@0.25\textwidth"}



<details>
<summary>原文</summary>
[Table 1](sec4_fal.md#table-1) provides a non-normative summary of aspects for each FAL. Each successive level subsumes and fulfills all requirements of lower levels (e.g., a federation process at FAL3 can be accepted at FAL2 or FAL1 since FAL3 satisfies all the requirements of these lower levels). Combinations not found in the [Table 1](sec4_fal.md#table-1) are possible but outside the scope of this volume.

[Table 1 Federation Assertion Levels](sec4_fal.md#table-1){:name="table-1"}
{:latex-ignore="true"}

|FAL|Injection Protection|Trust Agreement|Registration|Presentation|
|:--:|----|----|----|----|----|----|
|1|Recommended|Dynamic or Static|Dynamic or Static|Bearer Assertion|
|2|Required|Static|Dynamic or Static|Bearer Assertion|
|3|Required|Static|Static|Assertion and Bound Authenticator|
{:latex-table="1" latex-caption="Federation Assurance Levels" latex-columns="p@0.05\textwidth,p@0.16\textwidth,p@0.13\textwidth,p@0.15\textwidth,p@0.25\textwidth"}
</details>

すべての FAL で，すべてのアサーションは，[Sec. 5](sec5_federation.md#federation)で説明されているようにフェデレーションプロトコルと共に使用する**必要がある(SHALL)**．すべてのアサーションは，[Sec. 6](sec6_assertions.md#assertions)で説明されているように，詳細な要件に準拠する**必要がある(SHALL)**．すべてのアサーションは，[Sec. 7](sec7_presentation.md#プレゼンテーション)で説明されている方法のいずれかを使用して提示する**必要がある(SHALL)**．フェデレーテッドプロトコルで使用されるアサーションの例には，OpenID Connect の ID トークン [[OIDC]](references.md#ref-OIDC) や Security Assertion Markup Language [[SAML]](references.md#ref-SAML) で記述されたアサーションが含まれる．

すべての FAL で，IdP は，[[SP800-53]](references.md#ref-SP800-53)や，同等の連邦の標準(例: [[FEDRAMP]](references.md#ref-FEDRAMP))，業界標準で定義された中程度または高いセキュリティ制御のベースラインから，適切に調整されたセキュリティ制御（制御の強化を含む）を採用する必要がある．

<details>
<summary>原文</summary>
At all FALs, all assertions **SHALL** be used with a federation protocol as described in [Sec. 5](sec5_federation.md#federation). All assertions **SHALL** comply with the detailed requirements in [Sec. 6](sec6_assertions.md#assertions). All assertions **SHALL** be presented using one of the methods described in [Sec. 7](sec7_presentation.md#presentation). Examples of assertions used in federated protocols include the ID Token in OpenID Connect [[OIDC]](references.md#ref-OIDC) and assertions written in the Security Assertion Markup Language [[SAML]](references.md#ref-SAML).

At all FALs, the IdP **SHALL** employ appropriately tailored security controls (to include control enhancements) from the moderate or high baseline of security controls defined in [[SP800-53]](references.md#ref-SP800-53) or equivalent federal (e.g., [[FEDRAMP]](references.md#ref-FEDRAMP)) or industry standard.  
</details>


## Federation Assurance Level 1 (FAL1) {#fal1}

FAL1 では，IdP によって生成されるアサーションは，[Sec. 6](sec6_assertions.md#assertions)で定義されている主要な要件をひととおり満たす**必要がある(SHALL)**（承認された暗号化を使用して IdP によって署名されたアサーションコンテンツを取得することによる，攻撃者による変更や構築から保護を含む）．RP は，[Sec. 6](sec6_assertions.md#assertions)で説明されているように，受信時にアサーションの発信元と整合性を検証し，アサーションが期待されるソースから発信されていることを確認する**必要がある(SHALL)**．

<details>

<summary>原文</summary>
At FAL1, the assertion being generated by the IdP **SHALL** meet a core set of requirements defined in [Sec. 6](sec6_assertions.md#assertions), including protection against modification or construction by an attacker by having the assertion contents signed by the IdP using approved cryptography. An RP **SHALL** verify the origin and integrity of the assertion upon receipt, as discussed in [Sec. 6](sec6_assertions.md#assertions), ensuring that the assertion has originated from the expected source.
</details>

FAL1 でのすべてのアサーションは，特定の RP または RPのセットに対象者を制限する**必要があり(SHALL)**，RP はアサーションの対象となる RP の 1 つであることを検証する**必要がある(SHALL)**．IdP は，承認された暗号化を使用した鍵と署名でアサーションを保護することにより，RP を含むアサーションを保持する当事者が，非対象のRPでIdPになりすますことができないようにする**必要がある(SHALL)**．アサーションが非対称鍵を使用したデジタル署名によって保護されている場合，IdP は同じ公開鍵と秘密鍵のペアを使用して複数の RP へのアサーションに署名**してもよい(MAY)**．IdP は，既知の場所にある HTTPS で保護された URL など，検証可能な方法で公開鍵を公開**してもよい(MAY)**．アサーションが共有鍵を使用する鍵付きメッセージ認証コード(MAC) によって保護されている場合，IdP は RP ごとに異なる共有キーを使用する**必要がある(SHALL)**．

<details>

<summary>原文</summary>
All assertions at FAL1 **SHALL** be audience-restricted to a specific RP or set of RPs, and the RP **SHALL** validate that it is one of the targeted RPs for the given assertion. The IdP **SHALL** ensure that any party holding the assertion, including the RP, is unable to impersonate the IdP at a non-targeted RP by protecting the assertion with a signature and key using approved cryptography. If the assertion is protected by a digital signature using an asymmetric key, the IdP **MAY** use the same public and private key pair to sign assertions to multiple RPs. The IdP **MAY** publish its public key in a verifiable fashion, such as at an HTTPS-protected URL at a well-known location. If the assertion is protected by a keyed message authentication code (MAC) using a shared key, the IdP **SHALL** use a different shared key for each RP.
</details>


FAL1 では，IdP と RP の間の信頼協定を完全に動的に確立**してもよい(MAY)**．例えば，加入者(subscriber)が使用できるように RP が IdP のパラメーターを検出して自身を登録することを許容することで，加入者(subscriber)が実行時に選択した RP を IdP に対して識別させることができる．加入者(subscriber)は RP に提供する属性と提供目的を決定するようIdP から求められる．この例では，IdP と RP の間の信頼は，加入者(subscriber)の要望と行動によって完全に決定される．注記：FAL1 では，信頼の合意と登録が静的に行われることもある．

<details>

<summary>原文</summary>
At FAL1, the trust agreement between the IdP and RP **MAY** be established entirely dynamically. For instance, the subscriber can identify their chosen IdP to the RP at runtime, allowing the RP to discover the IdP's parameters and register itself for use by the subscriber. The subscriber is prompted by the IdP to determine which attributes are released to the RP, and for what purposes. In this example, the trust between the IdP and RP is driven entirely by the desires and actions of the subscriber. Note that at FAL1, it is still possible for the trust agreement and registration to happen statically.
</details>

既存のフェデレーションプロトコルで FAL1 に該当するのは， OpenID Connectの Implicitクライアントプロファイル [[OIDC-Implicit]](references.md#ref-OIDC-implicit)、[[OIDC]](参照. md#ref-OIDC)，OpenID Connectのハイブリッドクライアントプロファイル [[OIDC]](references.md#ref-OIDC), 追加機能のない SAML Web SSO [[SAML-WebSSO]](references.md#ref-SAML-websso) プロファイルであるがあげられる．これらのプロファイルのそれぞれで，アサーションは IdP によって署名され，署名によってカバーされるアサーションの一部で RP が識別される．

<details>
<summary>原文</summary>
In existing federation protocols, FAL1 can be implemented with the OpenID Connect Implicit Client profile [[OIDC-Implicit]](references.md#ref-OIDC-implicit), the OpenID Connect Hybrid Client profile in [[OIDC]](references.md#ref-OIDC), or the SAML Web SSO [[SAML-WebSSO]](references.md#ref-SAML-websso) profile with no additional features. In each of these profiles, the assertion is signed by the IdP and the RP is identified in a portion of the assertion covered by the signature.
</details>




## Federation Assurance Level 2 (FAL2) {#fal2}
本章でより具体的または厳格な要件によって上書きされる場合を除き，FAL1 のすべての要件は FAL2 にも適用される．

FAL2 では，アサーションは，攻撃者によるインジェクションからも強力に保護され**なければならない(SHALL)**．これを達成するため，アサーション は， OpenID Connect Basic Client プロファイル [[OIDC-Basic]](references.md#ref-OIDC-basic) のように[Sec. 7.1](sec7_presentation.md#back-channel)で説明されているバックチャネルで提示する**必要がある(SHOULD)**．この提示方法では，RP は使い捨てのアサーションリファレンスを使用して IdP からアサーションを直接取得するため，攻撃者が外部アクセスポイントを介してアサーションを挿入することを防ぐ．[Sec. 7.2](sec7_presentation.md#front-channel)で説明されているフロントチャネルで提示する必要がある場合は，RP によって追加のインジェクション保護が実装され**なければならない(SHALL)**．

どちらの提示方法が使われるかによらず，フェデレーショントランザクションが IdP によって開始されるのではなく，RP で開始されることを常に要求することによって，インジェクション攻撃をさらに軽減することができる．これによりRP は，受取ったアサーションを，加入者(subscriber)が連続セッション内で開始した特定の要求と関連付けることができる．

<details>
  
<summary>原文</summary>
All the requirements for FAL1 apply at FAL2 except where overridden by more specific or stringent requirements here.

At FAL2, the assertion **SHALL** also be strongly protected from being injected by an attacker. To accomplish this, the assertion **SHOULD** be presented using back channel presentation as discussed in [Sec. 7.1](sec7_presentation.md#back-channel), as in the OpenID Connect Basic Client profile [[OIDC-Basic]](references.md#ref-OIDC-basic). In this presentation method, the RP fetches the assertion directly from the IdP by using a single-use assertion reference, thereby preventing an attacker from injecting the assertions through an external access point. If front channel presentation is used as discussed in [Sec. 7.2](sec7_presentation.md#front-channel), additional injection protections **SHALL** be implemented by the RP.
  
  Regardless of the presentation method used, injection attacks can be further mitigated by always requiring that the federation transaction start at the RP instead of being initiated by the IdP, thereby allowing the RP to associate an incoming assertion with a specific request that the subscriber initiated within a continuous session.
</details>



FAL2 では，IdP と RP の間の信頼協定を静的に確立**しなければならない(SHALL)**．これには，RP で使用できる属性とその目的の制限を設定することも含まれる．この信頼協定は，IdP と RP の間の二者間**でも良く(MAY)**，多者間のフェデレーションパートナーシップを使用して管理され**ても良い(MAY)**． RP と IdP が実行時にそれらの間で確立された信頼協定への接続を証明できる場合，登録は動的に行われ**ても良い(MAY)**．このような証明の方法は，フェデレーションプロトコルによって異なるが，ソフトウェアアテステーションの提示や，信頼されたドメインの URL に対する制御の証明を含めることができる．

<details>
<summary>原文</summary>
At FAL2, the trust agreement between the IdP and RP **SHALL** be established statically, including establishing limits of which attributes are made available to the RP and for what purpose. This trust agreement **MAY** be bilateral between the IdP and RP or **MAY** be managed through the use of a multilateral federation partnership. The registration **MAY** be dynamic, provided that the RP and IdP can prove their connection at runtime to the established trust agreement between them. Such methods for this proof vary by federation protocol, but can include presentation of software attestations and proof of control over URLs at trusted domains.
</details>

FAL2 で認証アサーションを発行する(asserting authentication) 政府運営の IdP は，[[FIPS140]](references.md#ref-FIPS140) のレベル 1 以上で検証されたメカニズムを使用して，アサーションの署名や暗号化に使用する鍵を保護**しなければならない(SHALL)**．

<details>
<summary>原文</summary>
Government-operated IdPs asserting authentication at FAL2 **SHALL** protect keys used for signing or encrypting those assertions with mechanisms validated at [[FIPS140]](references.md#ref-FIPS140) Level 1 or higher.
</details>




## Federation Assurance Level 3 (FAL3) {#fal3}
本章でより具体的または厳格な要件によって上書きされる場合を除き，FAL1 並びに FAL2 のすべての要件は FAL3 にも適用される．

FAL3 では，加入者(subscriber)は，アサーションの提示に加えて，オーセンティケーターを RP に直接提示することにより RP に対して認証する**必要がある(SHALL)**．提示されるオーセンティケータは，[Sec. 6.1.2](sec6_assertions.md#boundauth)で説明されている　_bound authenticator_　として知られている． 例えば，加入者(subscriber)は IdP と RP でフェデレートされたログインプロセスを実行し，RP は，加入者(subscriber)に，その RPの加入者(subscriber)のアカウントに関連付けられている bound authenticator を要求する．FAL3 で提示される bound authenticator は，加入者(subscriber)が IdP に対して認証するために使用するオーセンティケーターと同じである必要はない．アサーションは RP の加入者(subscriber)を識別するために使用されるが，bound authenticator は，ログインしようとしている当事者がアサーションで識別された加入者(subscriber)であることを非常に高く保証する． 加入者(subscriber)が bound authenticator で認証され，提示されたオーセンティケーターがアサーションによって識別された RP の加入者(subscriber)アカウントに正しくバインドされていることを RP が確認するまで，RP では FAL3 には到達しない．


<details>
  <summary>原文</summary>
All the requirements at FAL1 and FAL2 apply at FAL3 except where overridden by more specific or stringent requirements here.


At FAL3, the subscriber **SHALL** authenticate to the RP by presenting an authenticator directly to the RP in addition to presenting an assertion. The authenticator presented is known as a _bound authenticator_, described in [Sec. 6.1.2](sec6_assertions.md#boundauth). For example, the subscriber goes through a federated login process at the IdP and RP, and the RP then prompts the subscriber for a bound authenticator that is associated with that RP subscriber account. The bound authenticator presented at FAL3 need not be the same authenticator used by the subscriber to authenticate to the IdP. The assertion is used to identify the subscriber to the RP while the bound authenticator gives very high assurance that the party attempting to log in is the subscriber identified in the assertion. FAL3 is not reached at the RP until the subscriber authenticates with the bound authenticator and the RP verifies that the authenticator presented is correctly bound to the RP subscriber account identified by the assertion.
</details>


FAL3 では，IdP と RP の間の信頼協定と登録を静的に確立**しなければならない(SHALL)**．すべての当事者 (RP に送信される属性のリストを含む) の，すべての識別キー マテリアルおよびフェデレーションパラメータは，フェデレーション認証プロセスが実行される前に，事前に修正され**なければならない(SHALL)**． 実行時の決定は，フェデレーション認証プロセスの当事者間で送信されるものをさらに制限するために使用され**ても良い(MAY)**．例えば，実行時の決定では，メールアドレスの属性が信頼協定のパラメーターに含まれていたとしても，メールアドレスを開示しないことを選択できる．

<details>
<summary>原文</summary>
At FAL3, the trust agreement and registration between the IdP and RP **SHALL** be established statically. All identifying key material and federation parameters for all parties  (including the list of attributes sent to the RP) **SHALL** be fixed ahead of time, before the federated authentication process can take place. Runtime decisions **MAY** be used to further limit what is sent between parties in the federated authentication process (e.g., a runtime decision could opt to not disclose an email address even though this attribute was included in the parameters of the trust agreement).
</details>


FAL3 で認証アサーションを発行する(asserting authentication) IdP は，[[FIPS140]](references.md#ref-FIPS140) のレベル 1 以上で検証されたメカニズムを使用して，アサーションの署名や暗号化に使用する鍵を保護**しなければならない(SHALL)**．


<details>
<summary>原文</summary>
IdPs asserting authentication at FAL3 **SHALL** protect keys used for signing or encrypting those assertions with mechanisms validated at [[FIPS140]](references.md#ref-FIPS140) Level 1 or higher.
</details>




## xALでのリクエストと処理 (Requesting and Processing xALs) {#request-xals}

IdP は，さまざまなフェデレーションパラメータを使用して，さまざまなオーセンティケータで，多くの異なる加入者(subscriber)のアイデンティティを示すことができるため，IAL，AAL，FAL は，同じ RP であっても，さまざまなフェデレーションログイン間で異なる可能性がある．

RP は，フェデレーショントランザクションごとに次の情報を通知され**なければならない(SHALL)**．

- RP に提示している加入者(subscriber)アカウントの IAL，または 身元確認(IAL) が行われていないことの表示
- IdP での加入者(subscriber)の現在アクティブなセッションの AAL，または 当人認証(AAL) が行われていないことの表示
- フェデレーショントランザクションの FAL

<details>
  <summary>原文</summary>
Since an IdP is capable of asserting the identities of many different subscribers with a variety of authenticators using a variety of federation parameters, the IAL, AAL, and FAL could vary across different federated logins, even to the same RP.

The RP **SHALL** be informed of the following information for each federated transaction:

- The IAL of the subscriber account being presented to the RP, or an indication that no IAL claim is being made
- The AAL of the currently active session of the subscriber at the IdP, or an indication that no AAL claim is being made
- The FAL of the federated transaction
</details>

RP は，[Sec. 5.1](sec5_federation.md#trust-agreement#trust-agreement)で説明されている信頼協定のパラメーターと、[Sec. 6](sec6_assertions.md#assertions)で説明されているアサーションに含まれる情報との組み合わせから，この xAL 情報を取得する．IdP と RP の間のすべてのメッセージで xAL が不変の場合，xAL の情報は IdP と RP の間の信頼協定のパラメータに含まれ**なければならない(SHALL)**．xAL が異なる場合，[Sec. 6](sec6_assertions.md#assertions) で説明されているように，アサーションの一部として情報を含め**なければならない(SHALL)**．

<details>
 <summary>原文</summary>
The RP gets this xAL information from a combination of parameters in the trust agreement as described in [Sec. 5.1](sec5_federation.md#trust-agreement#trust-agreement) and information included in the assertion as described in [Sec. 6](sec6_assertions.md#assertions). If the xAL is unchanging for all messages between the IdP and RP, the xAL information **SHALL** be included in the parameters of the trust agreement between the IdP and RP. If the xAL varies, the information **SHALL** be included as part of the assertion as discussed in [Sec. 6](sec6_assertions.md#assertions).
</details>


IdP は，特定のフェデレーショントランザクションについて，身元確認(IAL) または 当人認証(AAL) が行われていないことを示し**ても良い(MAY)**． このような場合，結果の xAL にデフォルト値は割り当てられない．つまり，信頼協定またはアサーションのいずれかで IAL 宣言のないフェデレーショントランザクションは，機能的には“IALなし“と見なされ，RP は，アカウントがこのスイートで説明されている最小の IAL である“IAL1”を満たしているとみなすことはできない．

<details>
 <summary>原文</summary>
The IdP **MAY** indicate that no claim is made to the IAL or AAL for a given federation transaction. In such cases, no default value is assigned to the resulting xAL. That is to say, a federation transaction without an IAL declaration in either the trust agreement or the assertion is functionally considered to have "no IAL" and the RP cannot assume the account meets "IAL1", the lowest numbered IAL described in this suite.
</details>


RP は，提供された機能へのアクセスのために受け入れても構わないと思っている最小の IAL，AAL，FAL を決定**しなければならない(SHALL)**．RP は，特定のフェデレーション認証の IAL，AAL，FAL に基づいて，その機能を変更**しても良い(MAY)**．例えば，RP は一般的な機能 (ダムシステムの状態の表示など) には AAL2 でのログインを許可するが，よりリスクの高い機能 (ダムシステムの流量の変更など) には AAL3 を要求する．同様に，RP は，管理機能を IAL2 で 身元確認された特定の加入者(subscriber)アカウントのみに制限しつつ，IAL に関係なくすべての加入者(subscriber)アカウントからのログインを許可することができる．

<details>
 <summary>原文</summary>
The RP **SHALL** determine the minimum IAL, AAL, and FAL it is willing to accept for access to any offered functionality. An RP **MAY** vary its functionality based on the IAL, AAL, and FAL of a specific federated authentication. For example, an RP can allow login at AAL2 for common functionality (e.g., viewing the status of a dam system) but require AAL3 be used for higher risk functionality (e.g., changing the flow rates of a dam system). Similarly, an RP could restrict management functionality to only certain subscriber accounts which have been identity proofed at IAL2, while allowing logins from all subscriber accounts regardless of IAL.
</details>

フェデレーションプロセスでは，適用可能な IAL を決定する加入者(subscriber)アカウントの詳細，並びに，適用可能な AAL を決定する IdP での認証イベントに直接アクセスできるのは IdP だけである．したがって，RP は IdP の IAL および AAL の宣言を，特定のフェデレーショントランザクションのこれらのレベルの唯一のソースと見なさ**なければならない(SHALL)**．

<details>
 <summary>原文</summary>
In a federation process, only the IdP has direct access to the details of the subscriber account, which determines the applicable IAL, and the authentication event at the IdP, which determines the applicable AAL. Consequently, the RP **SHALL** consider the IdP's declaration of the IAL and AAL as the sole source of these levels for a given federated transaction.
</details>

RP は，フェデレーショントランザクションがアサーションで宣言された FAL の要件を満たしていることを保証**しなければならない(SHALL)**．たとえば，RP は，提示方法が FAL2 以上のインジェクション保護要件を満たしていること，および適切な bound authenticator が FAL3 で提示されていることを確認しなければならない．

<details>
 <summary>原文</summary>
The RP **SHALL** ensure that the federation transaction meets the requirements of the FAL declared in the assertion. For example, the RP needs to ensure the presentation method meets the injection protection requirements at FAL2 and above, and that the appropriate bound authenticator is presented at FAL3.
</details>


IdP は，RP が信頼協定の一部として許容可能な最小 xAL のセットを指定するメカニズムをサポート**しなければならず(SHALL)**，フェデレーショントランザクションの一部として実行時により厳密な最小セットを指定する RP をサポートする**必要がある(SHOULD)**．RP が特定の xAL を要求する場合，可能であれば，IdP はその要求を満たす**必要があり(SHOULD)**，アサーションで結果の xAL を示さ**なければならない(SHALL)**．たとえば，加入者(subscriber)が AAL1 で認証されたアクティブなセッションを持っているが RP が AAL2 を要求した場合，可能であれば，IdP は加入者(subscriber)に AAL2 認証を要求して，加入者(subscriber)が IdP での対話中に IdP でセッションのセキュリティを強化する必要がある．IdP は，返却するアサーションの一部として結果の AAL（AAL1 （元のセッション）または AAL2（強化された認証）を送信する．

<details>
 <summary>原文</summary>
IdPs **SHALL** support a mechanism for RPs to specify a set of minimum acceptable xALs as part of the trust agreement and **SHOULD** support the RP specifying a more strict minimum set at runtime as part of the federation transaction. When an RP requests a particular xAL, the IdP **SHOULD** fulfill that request, if possible, and **SHALL** indicate the resulting xAL in the assertion. For example, if the subscriber has an active session that was authenticated at AAL1, but the RP has requested AAL2, the IdP needs to prompt the subscriber for AAL2 authentication to step up the security of the session at the IdP during the subscriber's interaction at the IdP, if possible. The IdP sends the resulting AAL as part of the returned assertion, whether it is AAL1 (the original session) or AAL2 (a stepped-up authentication).
  
</details>
