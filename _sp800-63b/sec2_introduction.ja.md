---
layout: default.ja
title: Introduction
navOrder: 2
navTitle: Introduction
permalink: /sp800-63b/introduction/
anchor: sec2
section: 2
---

# Introduction {#sec2}

_This section is informative._

デジタル認証は，デジタルアイデンティティを主張するために使用される 1つ以上のオーセンティケーターの有効性を判断するプロセスである．当人認証は，デジタルサービスにアクセスしようとしている対象者が，当人認証に使用されるテクノロジを制御していることを確立する．再来が存在するサービスの場合，当人認証に成功すると，今日サービスにアクセスする対象者が以前にサービスにアクセスした対象者と同じであるという合理的なリスクベースの保証が提供される．

> Digital authentication is the process of determining the validity of one or more authenticators used to claim a digital identity. Authentication establishes that a subject attempting to access a digital service is in control of the technologies used to authenticate. For services in which return visits are applicable, successfully authenticating provides reasonable risk-based assurances that the subject accessing the service today is the same as the one who accessed the service previously.

加入者(subscriber)の進行中の認証は，加入者(subscriber)をオンラインでの活動 (つまり，_加入者(subscriber)アカウント_) に関連付けるプロセスの中心である．加入者(subscriber)認証は，特定の加入者(subscriber)アカウントに関連付けられた 1つ以上の *authenticator* (SP 800-63 の一部の以前のバージョンでは *トークン* と呼ばれていた) を主張者(Claimant)が制御していることを確認することによって実行される．認証が成功すると，仮名または非仮名の識別子と，必要に応じてその他のアイデンティティ情報が RP に提示される．

> The ongoing authentication of subscribers is central to the process of associating a subscriber with their online activity (i.e., with their _subscriber account_). Subscriber authentication is performed by verifying that the claimant controls one or more *authenticators* (called *tokens* in some earlier versions of SP 800-63) associated with a given subscriber account. A successful authentication results in the assertion of a pseudonymous or non-pseudonymous identifier and optionally other identity information to the relying party (RP).

本書は，さまざまな *当人認証保証レベル* (AAL) で使用される可能性がある，オーセンティケーターの選択を含む，認証プロセスの種類に関する推奨事項を提供する．また，紛失や盗難が発生した場合の失効といったオーセンティケーターのライフサイクルに関する推奨事項も提供する．

> This document provides recommendations on types of authentication processes, including choices of authenticators, that may be used at various *authentication assurance levels* (AALs). It also provides recommendations on the lifecycle of authenticators, including revocation in the event of loss or theft.

本技術ガイドラインは，ネットワークを介したシステムに対する対象者のデジタル認証に適用される．デジタルアクセスに使用されるいくつかのクレデンシャルは，物理アクセス認証にも使用される場合があるが，物理アクセス（建物など）に対する個人の認証には対応していない．本技術ガイドラインでは，認証プロトコルに参加する連邦システムとサービスプロバイダーが加入者(subscriber)に対して認証されることも要求している．

> This technical guideline applies to digital authentication of subjects to systems over a network. It does not address the authentication of a person for physical access (e.g., to a building), though some credentials used for digital access may also be used for physical access authentication. This technical guideline also requires that federal systems and service providers participating in authentication protocols be authenticated to subscribers.

AAL は，認証トランザクションの強度を順序カテゴリとして特徴付ける．より強力な認証 (より高い AAL) では，悪意のあるアクターが認証プロセスをうまく覆すために，より優れた機能を持ち，より多くのリソースを消費する必要がある．より高い AAL での認証は，攻撃のリスクを効果的に減らすことができる．各 AAL の技術要件の概要を以下に示す．特定の規範的(Normative)要件については，このドキュメントの [Sec. 4](sec4_aal.md#AAL_SEC4) と [Sec. 5](sec5_authenticators.md#AAL_SEC5)を参照のこと．

> The AAL characterizes the strength of an authentication transaction as an ordinal category. Stronger authentication (a higher AAL) requires malicious actors to have better capabilities and to expend greater resources in order to successfully subvert the authentication process. Authentication at higher AALs can effectively reduce the risk of attacks. A high-level summary of the technical requirements for each of the AALs is provided below; see [Sec. 4](sec4_aal.md#AAL_SEC4) and [Sec. 5](sec5_authenticators.md#AAL_SEC5) of this document for specific normative requirements.

**当人認証保証レベル1**：AAL1 は，申請者(applicant)が加入者(subscriber)アカウントにバインドされたオーセンティケータを制御するという保証を提供する．AAL1 では，利用可能なさまざまな認証技術を使用した単一要素認証または多要素認証が必要である．認証を成功させるには，要求者(claimant)が安全な認証プロトコルを介してオーセンティケータの所有と管理を証明する必要がある．

> **Authentication Assurance Level 1**: AAL1 provides some assurance that the claimant controls an authenticator bound to the subscriber account. AAL1 requires either single-factor or multi-factor authentication using a wide range of available authentication technologies. Successful authentication requires that the claimant prove possession and control of the authenticator through a secure authentication protocol.

**当人認証保証レベル2**：AAL2 は，申請者(applicant)が加入者(subscriber)アカウントにバインドされた 1つ以上のオーセンティケータを制御しているという高い信頼性を提供する．安全な認証プロトコルを通じて，2つの異なる認証要素の所有と管理の証明が必要である．AAL2 以上では，承認された暗号技術が必要である．

> **Authentication Assurance Level 2**: AAL2 provides high confidence that the claimant controls one or more authenticators bound to the subscriber account. Proof of possession and control of two different authentication factors is required through secure authentication protocols. Approved cryptographic techniques are required at AAL2 and above.

**当人認証保証レベル3**：AAL3 は，申請者(applicant)が加入者(subscriber)アカウントにバインドされた 1つ以上のオーセンティケータを制御しているという非常に高い信頼性を提供する．AAL3 での認証は，暗号化プロトコルによる鍵の所有証明に基づいている．AAL3 認証には，ハードウェアベースのオーセンティケーターとフィッシング耐性のあるオーセンティケーターが必要である ([Sec. 5.2.5](sec5_authenticators.md#verifimpers) 参照)．同じデバイスがこれらの両方の要件を満たす場合もある．AAL3 で認証を行うには，要求者(claimant)は，安全な認証プロトコルを通じて，2つの異なる認証要素の所有と管理を証明する必要がある．承認された暗号技術が必要である．

> **Authentication Assurance Level 3**: AAL3 provides very high confidence that the claimant controls one or more authenticators bound to the subscriber account. Authentication at AAL3 is based on proof of possession of a key through a cryptographic protocol. AAL3 authentication requires a hardware-based authenticator and a phishing-resistant authenticator (see [Sec. 5.2.5](sec5_authenticators.md#verifimpers)); the same device may fulfill both these requirements. In order to authenticate at AAL3, claimants are required to prove possession and control of two distinct authentication factors through secure authentication protocols. Approved cryptographic techniques are required.

The following list states which sections of the document are normative and which are informative:

- 1 Purpose _Informative_
- 2 Introduction _Informative_
- 3 Definitions and Abbreviations _Informative_
- 4 Authentication Assurance Levels  _Normative_
- 5 Authenticator and Verifier Requirements  _Normative_
- 6 Authenticator Lifecycle Management  _Normative_
- 7 Session Management  _Normative_
- 8 Threat and Security Considerations _Informative_
- 9 Privacy Considerations _Informative_
- 10 Usability Considerations _Informative_
- 11 Equity Considerations _Informative_
- References _Informative_
- Appendix A Strength of Memorized Secrets _Informative_
- Appendix B Change Log _Informative_
