---
layout: default.ja
title: はじめに
navOrder: 2
navTitle: はじめに
permalink: /sp800-63c/introduction/
anchor: introduction
section: 2
---

# はじめに (Introduction) {#introduction}
 
*This section is informative.*

フェデレーションは，ネットワーク化されたシステム間で認証属性と加入者(subscriber)属性を伝達できるようにするプロセスである．フェデレーションシナリオでは，CSP は ID プロバイダー (IdP) と呼ばれるサービスを提供する． IdP は，CSP によって発行されたオーセンティケーターの検証者として機能する．IdP は，この認証イベントに関するアサーションと呼ばれるメッセージを RP に送信する． RP は IdP によって提供されたアサーションを受け取り，それを認証および承認の決定に使用するが，RP はオーセンティケーターを直接検証しない．

> Federation is a process that allows for the conveyance of authentication attributes and subscriber attributes across networked systems. In a federation scenario, the CSP provides a service known as an identity provider, or IdP. The IdP acts as a verifier for authenticators issued by the CSP. The IdP sends a message, called an assertion, about this authentication event to the RP. The RP receives the assertion provided by the IdP and uses it for authentication and authorization decisions, but the RP does not verify the authenticator directly.

アサーションは，加入者の認証イベントを表す，IdP から RP への検証可能なステートメントである．フェデレーションは通常，RP と IdP が単一のエンティティではないか，共通の管理下にない場合に使用されるが，フェデレーションはさまざまな理由で単一のセキュリティドメイン内にも適用できる．RP は，アサーション内の情報を使用して加入者(subscriber)を識別し，RP によって制御されるリソースへのアクセスに関する承認の決定を行う．

> Assertions are verifiable statements from an IdP to an RP that represent an authentication event for a subscriber. Federation is generally used when the RP and the IdP are not a single entity or are not under common administration, though federation can be applied within a single security domain for a variety of reasons. The RP uses the information in the assertion to identify the subscriber and make authorization decisions about their access to resources controlled by the RP.

フェデレーションアイデンティティシナリオでは，加入者(subscriber)は RP に対して直接認証されない． 代わりに，フェデレーションプロトコルは，通常，RP からの明示的な要求に応答して，IdP が加入者(subscriber)に関連付けられたアサーションを生成するメカニズムを定義する．IdP は加入者(subscriber)の認証を担当する([[SP800-63B]](../_sp800-63b/sec7_session.md#sec7){:latex-href="#ref-SP800-63B"}の7章 で説明されているように，セッション管理を使用する場合がある)．フェデレーションプロセスにより，加入者(subscriber)は，各 RP で個別のオーセンティケータを保持または維持する必要なく，複数の RP のサービスを利用できる．このプロセスは「シングル サインオン」と呼ばれることもある．

> In a federated identity scenario, the subscriber does not authenticate directly to the RP. Instead, the federation protocol defines a mechanism for an IdP to generate an assertion associated with a subscriber, generally in response to an explicit request from the RP. The IdP is responsible for authenticating the subscriber (though it may use session management as described in [[SP800-63B]](../_sp800-63b/sec7_session.md#sec7){:latex-href="#ref-SP800-63B"}, Sec. 7). The federation process allows the subscriber to obtain services from multiple RPs without the need to hold or maintain separate authenticators at each RP, a process sometimes known as *single sign-on*.

加入者(subscriber)は，*フェデレーション識別子*によって RP に対して一意に識別される．これは，IdP によってアサートされる *サブジェクト識別子* と IdP 自体の一意の識別子の論理的な組み合わせである．異なる IdP がそれぞれのサブジェクト識別子を個別に管理し，異なるサブジェクトに対するサブジェクト識別子の選択で衝突する可能性があるため，このマルチパート識別子パターンは必要である．したがって，どの IdP がそのサブジェクト識別子 を発行したかを考慮せずに，RP がサブジェクト識別子を処理しないことが不可欠である．
> The subscriber is uniquely identified to the RP by a *federated identifier*, which is a logical combination of the *subject identifier* as asserted by the IdP as well as a unique identifier for the IdP itself. This multi-part identifier pattern is required because different IdPs manage their subject identifiers independently, and could therefore potentially collide in their choices of subject identifiers for different subjects. Therefore, it is imperative that an RP never process the subject identifier without taking into account which IdP issued that subject identifier.

アサーションには加入者(subscriber)のフェデレーション識別子が含まれており，加入者(subscriber)と，複数の認証済みセッションを介した RP との対話との関連付けを可能にする．アサーションには，加入者(subscriber)をさらに特徴付けてRP での承認決定をサポートする，属性値または派生属性値も含まれる場合がある．追加の属性は，より大きなフェデレーションプロトコルの一部として，アサーションの外部でも使用できる場合がある．これらの属性値と派生属性値は，属性ベースのアクセス制御 (ABAC) のアクセス権限を決定したり，トランザクションを促進したり (配送先住所の提供など) する際によく使用される．

> An assertion includes a federated identifier for the subscriber, allowing association of the subscriber with their interactions with the RP over multiple authenticated sessions. Assertions may also include attribute values or derived attribute values that further characterize the subscriber and support authorization decisions at the RP. Additional attributes may also be available outside of the assertion as part of the larger federation protocol. These attribute values and derived attribute values are often used in determining access privileges for attribute-based access control (ABAC) or facilitating a transaction (e.g., providing a shipping address).

フェデレーションには，緻密なセキュリティとプライバシーの要件を持つ比較的複雑なマルチパーティプロトコルが必要である．特定のフェデレーション構造を評価するときは，それを構成要素の相互作用 (IdP への加入者(subscriber)，RP への IdP，RP への加入者(subscriber)) に分割することが有益な場合がある．フェデレーションプロトコルの各当事者は，フェデレーションシステムが意図したとおりに機能するために満たされなければならない特定の責任と期待を負う．

> Federation requires relatively complex multiparty protocols that have subtle security and privacy requirements. When evaluating a particular federation structure, it may be instructive to break it down into its component interactions: the subscriber to the IdP, the IdP to the RP, and the subscriber to the RP. Each party in a federation protocol bears specific responsibilities and expectations that must be fulfilled in order for the federated system to function as intended.


IdP は，[[SP800-63A]](../_sp800-63a/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63A"} で定義された _加入者(subscriber)アカウント_ をフェデレーション固有のアイテムのセットで補強する加入者(subscriber)のレコードを維持する．以下を含むがこれらに限定されない:

- フェデレーションプロトコルで使用するための1つまたは複数の外部サブジェクト識別子
- アクセス権のセット．どの RP が加入者(subscriber)アカウントのどの属性にアクセスできるか，詳細を記す(加入者(subscriber)による実行時の決定など)．
- フェデレーションアカウントの使い方の情報
- IdP によって加入者(subscriber)に収集または割り当てられる追加の属性

> The IdP maintains a record for the subscriber that augments the _subscriber account_ defined in [[SP800-63A]](../_sp800-63a/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63A"} with a set of federation-specific items, including but not limited to the following:
> 
> - One or more external subject identifiers, for use with a federation protocol
> - A set of access rights, detailing which RPs can access which attributes of the subscriber account (such as runtime decisions by the subscriber)
> - Federated account usage information
> - Additional attributes collected or assigned by the IdP to the subscriber

RP は多くの場合，加入者(subscriber)の *RP 加入者(subscriber)アカウント* を維持する．これは，IdP によって RP に開示され拡張された加入者(subscriber)アカウント情報から派生する．[Sec. 5.4](../sec5_federation.md#rp-account) で説明されているように，RP 加入者(subscriber)アカウントには，RP 自体にローカルな情報も含まれている．

> The RP often maintains an *RP subscriber account* for the subscriber, which is derived from the augmented subscriber account information disclosed to the RP by the IdP. The RP subscriber account also contains information local to the RP itself, as described in [Sec. 5.4](../sec5_federation.md#rp-account).

本書の要件は，これらのガイドラインの他のボリュームの要件に基づいている．加入者(subscriber)と IdP の間の認証は，[[SP800-63B]](../_sp800-63b/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63B"} に示されている認証メカニズムに基づいており，フェデレーションプロトコルは[[SP800-63A]](../_sp800-63a/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63A"} の手順を使用して IdP で確立された属性を RP に伝達する．

> The requirements in this document build on the requirements in the other volumes of these guidelines. Authentication between the subscriber and the IdP will be based on the authentication mechanisms presented in [[SP800-63B]](../_sp800-63b/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63B"}, while the federation protocol will convey attributes to the RP established at the IdP using procedures in [[SP800-63A]](../_sp800-63a/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63A"} (along with other attributes).

次の表は，本書のどの章が normative で，どの章が informative であるかを示す．

- 1 目的 _Informative_
- 2 はじめに _Informative_
- 3 定義と略語 _Informative_
- 4 フェデレーション保証レベル (FAL) _Normative_
- 5 フェデレーション _Normative_
- 6 アサーション _Normative_
- 7 アサーションの提示 _Normative_
- 8 セキュリティ _Informative_
- 9 プライバシーに関する考慮事項 _Informative_
- 10 ユーザビリティに関する考慮事項 _Informative_
- 11 公平性に関する考慮事項 _Informative_
- 12 例 _Informative_
- 参考文献 _Informative_

> The following table states which sections of the document are normative and which are informative:
> 
> - 1 Purpose _Informative_
> - 2 Introduction _Informative_
> - 3 Definitions and Abbreviations _Informative_
> - 4 Federation Assurance Level (FAL)  _Normative_
> - 5 Federation  _Normative_
> - 6 Assertion  _Normative_
> - 7 Assertion Presentation  _Normative_
> - 8 Security _Informative_
> - 9 Privacy Considerations _Informative_
> - 10 Usability Considerations _Informative_
> - 11 Equity Considerations _Informative_
> - 12 Examples _Informative_
> - References _Informative_