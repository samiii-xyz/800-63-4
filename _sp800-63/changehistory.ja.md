---
layout: default.ja
title: Change Log
navOrder: 10
navTitle: Change Log
permalink: /sp800-63/changelog/
anchor: changelog
section: B
---

# Change Log {#changelog}

## SP 800-63-1

NIST SP 800-63-1 updated NIST SP 800-63 to reflect current authenticator (then referred to as "token") technologies and restructured it to provide a better understanding of the digital identity architectural model used here. Additional (minimum) technical requirements were specified for the CSP, protocols used to transport authentication information, and assertions if implemented within the digital identity model.

## SP 800-63-2

NIST SP 800-63-2 was a limited update of SP 800-63-1 and substantive changes were made only in Sec. 5, *Registration and Issuance Processes*. The substantive changes in the revised draft were intended to facilitate the use of professional credentials in the identity proofing process, and to reduce the need to send postal mail to an address of record to issue credentials for level 3 remote registration. Other changes to Sec. 5 were minor explanations and clarifications.

## SP 800-63-3

NIST SP 800-63-3 is a substantial update and restructuring of SP 800-63-2. SP 800-63-3 introduces individual components of digital authentication assurance &mdash; AAL, IAL, and FAL &mdash; to support the growing need for independent treatment of authentication strength and confidence in an individual's claimed identity (e.g., in strong pseudonymous authentication). A risk assessment methodology and its application to IAL, AAL, and FAL has been included in this guideline. It also moves the whole of digital identity guidance covered under SP 800-63 from a single document describing authentication to a suite of four documents (to separately address the individual components mentioned above) of which SP 800-63-3 is the top-level document.

Other areas updated in 800-63-3 include:

- Renamed to _Digital Identity Guidelines_ to properly represent the scope includes identity proofing and federation, and to support expanding the scope to include device identity, or machine-to-machine authentication in future revisions.
- Changed terminology, including the use of *authenticator* in place of *token* to avoid conflicting use of the word *token* in assertion technologies.
-	Updated authentication and assertion requirements to reflect advances in both security technology and threats.
-	Added requirements on the storage of long-term secrets by verifiers.
-  Restructured identity proofing model.
-	Updated requirements regarding remote identity proofing.
-	Clarified the use of independent channels and devices as "something you have".
-	Removed pre-registered knowledge tokens (authenticators), with the recognition that they are special cases of (often very weak) passwords.
-	Added requirements regarding account recovery in the event of loss or theft of an authenticator.
-	Removed email as a valid channel for out-of-band authenticators.
-   Expanded discussion of reauthentication and session management.
-   Expanded discussion of identity federation; restructuring of assertions in the context of federation.

## SP 800-63-4

NIST SP 800-63-4 には，SP 800-63-3 からの大幅な更新と再編成がある．800-63-4 の更新内容は次のとおり．

> NIST SP 800-63-4 has substantial updates and re-organization from SP 800-63-3. Updates to 800-63-4 include:

- [Sec 2.3](sec2_introduction.ja.md#ERMreqs) は，以前の版のセキュリティとプライバシーの考慮事項の内容を拡張している．また，公平性と使いやすさの考慮事項も追加している．
- [Sec 4.1](sec4_model.ja.md#s-4-1) には，更新された非フェデレーションおよびフェデレーションデジタルアイデンティティモデルと説明が含まれている．
- [Sec 4.4](sec4_model.ja.md#Federation) は，フェデレーションアイデンティティアーキテクチャとアサーションの使用に関する有益な説明と考慮事項を 1つの章にまとめている．
- [Sec 5](sec5_DIRM.ja.md#sec5) は，以前の改訂のリスク管理の内容を拡張し，組織への影響に加えて個人やコミュニティへの影響を，組織が考慮することを具体的に義務付けている．また，リスク管理プロセス内，およびデジタルアイデンティティシステムを実装する際に，資格のあるすべての人々にサービスを提供することへの課題を含む，ミッションの提供に対するリスクを高めている．800-63-3 の 6章にあった xAL 選択フローチャートは，xAL 選択をサポートするリスク評価マトリックスの例と共に，リスク管理プロセスを詳述するテキストに置き換えられている．さらに，ガイドラインは現在，個人，コミュニティ，および組織への潜在的な影響の継続的な評価を義務付けている．

> - [Section 2.3](sec2_introduction.md#ERMreqs) expands security and privacy consideration content of previous revisions. It also adds equity and usability considerations.
> - [Section 4.1](sec4_model.md#s-4-1) includes updated non-federated and federated digital identity models and descriptions.
> - [Section 4.4](sec4_model.md#Federation) consolidates informative descriptions and considerations on the use of federated identity architectures and assertions into one section.
> - [Section 5](sec5_DIRM.md#sec5) expands upon the risk management content of previous revisions and specifically mandates that organizations take into account impacts to individuals and communities in addition to impacts to the organization. It also elevates risks to mission delivery, including challenges to the provisioning of services to all people who are eligible for and entitled to them, within the risk management process and when implementing digital identity systems. The xAL selection flowcharts, previously found in 800-63-3, section 6, have been replaced with text that elaborates the risk management process along with a sample risk assessment matrix that supports xAL selection. Additionally, the guidelines now mandate continuous evaluation of potential impacts to individuals, communities, and organizations. 
