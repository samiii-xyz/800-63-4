---
layout: default.ja
title: はじめに
navOrder: 2
navTitle: はじめに
permalink: /sp800-63/introduction/
anchor: intro
section: 2
---

# はじめに (Introduction) {#intro}

*This section is informative.*

仮想世界と物理世界の境界線が曖昧になり，デジタルおよびインターネット対応の技術が急増して接続し続けるにつれて，開発者と消費者は，関連する機会とリスクを含んで，この変化するハイブリッドエコシステムを理解することが不可欠である．このエコシステム全体での約束(engagement)は，多くの場合，個人の能力とデジタルアイデンティティ(オンライントランザクションに従事している個人の固有の表現) を確立する意思によって決定される．

> As the line between the virtual world and physical world blurs, and as digital and internet-enabled technologies continue to proliferate and connect, it is imperative that developers and consumers alike understand this changing hybrid ecosystem - including its associated opportunities and risks. Engagement across this ecosystem is often determined by an individual's ability and willingness to establish a digital identity - the unique representation of a person engaged in an online transaction.

デジタルアイデンティティは，デジタルサービスの文脈においてはは常に一意であるものの，すべての文脈において常に個人を一意に識別するわけではない．さらに，デジタルアイデンティティは，デジタルサービスの文脈において固有の特定の意味を表す場合があるが，デジタルアイデンティティの背後にある個人の実際のアイデンティティは不明な場合がある．本刊行物の目的上，「人」は自然人のみを指す (つまり，すべての法人ではない)．

> A digital identity is always unique in the context of a digital service but does not always uniquely identify a person in all contexts. Further, while a digital identity may relay unique and specific meaning within the context of a digital service, the real-life identity of the individual behind the digital identity may not be known. For the purpose of this publication, a "person" refers to natural persons only (i.e., not all legal persons.)

デジタルアイデンティティの確立は，デジタルアイデンティティの所有者と，デジタルトランザクションの相手側の人，組織，またはシステムとの間の信頼を示すことを目的としている．ただし，このプロセスには問題が生じる可能性がある．物理的な世界での関係や取引と同様に，間違い，誤解，なりすまし，および他人のデジタルアイデンティティを不正に主張するその他の攻撃の機会が複数存在する．さらに，幅広い個人のニーズ，制約，能力，および好みを考慮して，デジタルサービスは公平性と柔軟性を念頭に置いて設計し，広範かつ永続的な参加を保証する必要がある．

> Establishing a digital identity is intended to demonstrate trust between the holder of the digital identity and the person, organization, or system on the other side of the digital transaction. However, this process can present challenges. As in relationships and transactions in the physical world, there are multiple opportunities for mistakes, miscommunication, impersonation, and other attacks that fraudulently claim another person's digital identity. Additionally, given the broad range of individual needs, constraints, capacities, and preferences, digital services must be designed with equity and flexibility in mind to ensure broad and enduring participation.

デジタルアイデンティティに関連するリスクは，企業への潜在的な影響を超えているため，企業の意思決定に組み込む必要がある． 本刊行物は，個人，コミュニティ，およびその他の組織に対するリスクをより確実かつ明確に説明するよう努めている．具体的には，このガイダンスを使用する際に，組織は，組織のサイバーセキュリティの目的を優先するデジタルアイデンティティに関連する決定が，他の目的にどのように影響するか，またはそれに対応する必要があるかを検討する必要がある．(プログラムやサービスと対話する個人の経験を中心とする，プライバシー，公平性，使いやすさ，およびミッションとビジネスパフォーマンスのその他の指標に関連するものなど)．人間中心で継続的に情報に基づいた方法でミッションを遂行することにより，組織はサービスを提供するさまざまな人々との信頼関係を徐々に構築し，顧客満足度を向上させ，問題をより迅速に特定し，効果的で文化的に適切な是正オプションを個人に提供する機会を得ることができる．

> Risks associated with digital identity stretch beyond the potential impacts to enterprises and should be incorporated into enterprise decision-making. This publication endeavors to more robustly and explicitly account for risks to individuals, communities, and other organizations. Specifically, while using this guidance, organizations should consider how decisions related to digital identity that prioritize organizational cybersecurity objectives might affect or need to accommodate other objectives, such as those related to privacy, equity, usability, and other indicators of mission and business performance that center the experiences of the individuals interacting with programs and services. By taking a human-centered and continuously informed approach to mission delivery, organizations have an opportunity to incrementally build trust with the variety of populations they serve, improve customer satisfaction, identify issues more quickly, and provide individuals with effective and culturally appropriate redress options.

本ガイドラインは，デジタルアイデンティティ管理をサポートするプロセス，ポリシー，データ，人，テクノロジーなど，デジタルアイデンティティシステムに関連するリスクを評価および管理するための，連邦政府のプログラムやその他の組織向けのモデルを示している． このモデルは，身元確認(identity proofing)，当人認証(authentication)，フェデレーションという一連のプロセスによってサポートされている．身元確認プロセスは，主体が特定の物理的な人物であることを確立する．当人認証プロセスは，デジタルアイデンティティを主張するために使用される 1つまたは複数のオーセンティケーターの有効性を判断し，主体がデジタルサービスにアクセスしようとしているという信頼を確立する．つまり，主体は，(1) 認証に使用されるテクノロジを管理しており，(2) 以前にサービスにアクセスしたのと同じ主体であるということを確認する．最後に，フェデレーションプロセスにより，システム間での認証をサポートするためにアイデンティティ情報を共有することができる．

> These guidelines lay out a model for federal programs and other organizations to assess and manage risks associated with digital identity systems, including the processes, policies, data, people, and technologies that support digital identity management. The model is supported by a series of processes: identity proofing, authentication, and federation. The identity proofing process establishes that a subject is a specific physical person. The digital authentication process determines the validity of one or more authenticators used to claim a digital identity and establishes confidence that a subject attempting to access a digital service: (1) is in control of the technologies being used for authentication, and (2) is the same subject that previously accessed the service. Finally, the federation process allows for identity information to be shared in support of authentication across systems.

SP 800-63 の初版がリリースされて以来，アイデンティティサービスの構成，モデル，および可用性は大幅に変化しており，さまざまなユーザーコミュニティに安全でプライベートで公平なサービスを展開する際の考慮事項と課題も変化している．本改訂では，これらの課題に対処すると同時に，エンティティが全体的なデジタルアイデンティティモデルの下で提供できる機能に基づいて要件を明確にすることにより，開発されたアイデンティティサービスの新しいモデルとアーキテクチャを促進する．

> The composition, model, and availability of identity services has significantly changed since the first version of SP 800-63 was released, as have the considerations and challenges of deploying secure, private, and equitable services to diverse user communities. This revision addresses these challenges while facilitating the new models and architectures for identity services that have developed by clarifying requirements based on the function an entity may serve under the overall digital identity model.

さらに，本刊行物は，クレデンシャルサービスプロバイダー (CSP)，検証者，および　Relying Party (RP) 向けの指示を提供し，組織がデジタルアイデンティティサービスを実装するために従うべき管理プロセスを説明しており，*NIST Risk Management Framework* [[NISTRMF]](sec8_references.ja.md#ref-NIST-RMF)とその構成特殊刊行物(Special Publications) を補足する．本刊行物は，公平性とユーザビリティの考慮事項をデジタルアイデンティティリスク管理プロセスに組み込む方法を概説することで NIST RMF を拡張し，企業の運用と資産だけでなく，個人や他の組織，より広義には社会に及ぼす影響を考慮することの重要性を強調している．さらに，デジタル認証は，個人情報への不正アクセスのリスクを軽減することでプライバシー保護をサポートするが，身元確認(identity proofing)，当人認証(authentication)，承認(authorization)，フェデレーションには個人情報の処理が含まれることが多いため，これらの機能はプライバシーリスクも生み出す可能性がありる．したがって，これらのガイドラインには，関連する潜在的なプライバシー リスクを軽減するのに役立つプライバシー要件と考慮事項が含まれている．

> Additionally, this publication provides instruction for credential service providers (CSPs), verifiers, and relying parties (RPs) and it describes the risk management processes that organizations should follow for implementing digital identity services and that supplement the *NIST Risk Management Framework* [[NISTRMF]](sec8_references.md#ref-NIST-RMF) and its component special publications. The publication expands upon the NIST RMF by outlining how equity and usability considerations should be incorporated into digital identity risk management processes and it highlights the importance of considering impacts, not only on the enterprise operations and assets, but also on individuals, other organizations, and, more broadly, society. Further, while digital authentication supports privacy protection by mitigating risks of unauthorized access to individuals' information, given that identity proofing, authentication, authorization, and federation often involve the processing of individuals' information, these functions can also create privacy risks. These guidelines, therefore, include privacy requirements and considerations to help mitigate potential associated privacy risks.

最後に，本刊行物は，ネットワークを介してデジタルシステムにアクセスするために主体のデジタルアイデンティティを確立，維持，および認証するための技術的要件と推奨事項を組織に提供するが，障壁と悪影響に対処し，公平性を促進し，任務の目的を首尾よく遂行するために，情報技術チームの範囲外の追加のサポートオプションを提供する必要のある場合がある．

> Finally, while this publication provides organizations with technical requirements and recommendations for establishing, maintaining, and authenticating the digital identity of subjects in order to access digital systems over a network, additional support options outside the purview of information technology teams may need to be provided to address barriers and adverse impacts, foster equity, and successfully deliver on mission objectives.

## Scope & Applicability

すべてのデジタルサービスが身元確認(identity proofing)や当人認証(authentication)を必要とするわけではない．ただし，本ガイドラインは，対象者 (市民，ビジネス パートナー，政府機関など) に関係なく，ある程度のデジタルアイデンティティが必要なすべてのオンライントランザクションに適用される．

> Not all digital services require identity proofing or authentication; however, this guidance applies to all online transactions for which some level of digital identity is required, regardless of the constituency (e.g., citizens, business partners, and government entities).

本ガイドラインは主に，公益にアクセスする市民やコラボレーションスペースにアクセスする民間部門のパートナーなど，外部ユーザーと対話する組織サービスに焦点を当てている．ただし，従業員や請負業者がアクセスする連邦システムにも適用される． **Personal Identity Verification (PIV) of Federal Employees and Contractors* 標準 [[FIPS201]](sec8_references.ja.md#ref-FIPS201) およびそれに対応する一連の特別刊行物(Special Publication)および組織固有の指示は，これらのガイドラインを連邦企業向けに拡張したものであり，Personal Identity Verification (PIV) カードを発行および管理するための追加の技術的制御とプロセスを提供し，派生した PIV クレデンシャルとして追加のオーセンティケーターをバインドし，PIV システムでフェデレーションアーキテクチャとプロトコルを使用する．

> These guidelines primarily focus on organizational services that interact with external users, such as citizens accessing public benefits or private sector partners accessing collaboration spaces. However, it also applies to federal systems accessed by employees and contractors. The *Personal Identity Verification (PIV) of Federal Employees and Contractors* standard [[FIPS201]](sec8_references.md#ref-FIPS201) and its corresponding set of special publications and organization-specific instructions, extend these guidelines for the federal enterprise, providing additional technical controls and processes for issuing and managing Personal Identity Verification (PIV) cards, binding additional authenticators as derived PIV credentials, and using federation architectures and protocols with PIV systems.

このガイダンスでカバーされていないトランザクションには，44 U.S.C. § 3542(b)(2) で定義されている国家安全保障システムに関連するトランザクションが含まれる．さまざまなデジタルアイデンティティ保証レベルを必要とするデジタルプロセスを使用する民間部門の組織および州，地方，部族政府は，必要に応じてこれらの標準の使用を検討することができる．

> Transactions not covered by this guidance include those associated with national security systems as defined in 44 U.S.C. § 3542(b)(2). Private sector organizations and state, local, and tribal governments whose digital processes require varying levels of digital identity assurance may consider the use of these standards where appropriate.

さらに，これらの技術ガイドラインは，物理アクセス (建物など) の主体のアイデンティティには対応していないが，オンライントランザクションに使用される一部のアイデンティティは物理アクセスにも使用される場合がある．さらに，本ガイドラインの本改訂版では，マシン間 (ルーター間など) 認証と呼ばれることが多いデバイスアイデンティティや，モノのインターネット (IoT) と一般的に呼ばれる相互接続されたデバイスについては明示的に対応していないが，本ガイドラインは，デバイスへの適用の可能性を残すために，可能な限り一般的な主体を参照するように書かれている．さらに，本ガイドラインは，主体に代わってアプリケーションプログラミングインターフェース (API) へのアクセスを承認することには対応していない．

> Additionally, these technical guidelines do not address the identity of subjects for physical access (e.g., to buildings), though some identities used for online transactions may also be used for physical access. Additionally, this revision of these guidelines does not explicitly address device identity, often referred to as machine-to-machine (such as router-to-router) authentication or interconnected devices, commonly referred to as the internet of things (IoT), although these guidelines are written to refer to generic subjects wherever possible to leave open the possibility for applicability to devices. Furthermore, these guidelines do not address authorization of access to Application Programming Interfaces (APIs) on behalf of subjects.

## How to Use this Suite of SPs

本ガイドラインは，デジタルアイデンティティの個々の要素を個別の構成要素に分離することにより，デジタルアイデンティティエラーによって引き起こされる悪影響の軽減をサポートする．非フェデレーションシステムの場合，政府機関は *Identity Assurance Level (IAL)* および *Authentication Assurance Level (AAL)* と呼ばれる 2つの構成要素を選択する．フェデレーションシステムの場合，3つ目の構成要素である *Federation Assurance Level (FAL)* も含む．[Sec. 5, Digital Identity Risk Management](sec5_DIRM.ja.md#sec5) では，リスク評価プロセスの詳細と，リスク評価の結果が，追加の文脈とともに，リスクと使命に基づいた IAL，AAL，FAL の組み合わせの組織の選択をどのように通知するかについて説明する．

> These guidelines support the mitigation of the negative impacts induced by a digital identity error by separating the individual elements of digital identity into discrete, component parts. For non-federated systems, agencies will select two components, referred to as *Identity Assurance Level (IAL)* and *Authentication Assurance Level (AAL)*. For federated systems, a third component, *Federation Assurance Level (FAL)*, is included. [Sec. 5, Digital Identity Risk Management](sec5_DIRM.md#sec5) provides details on the risk assessment process and how the results of the risk assessment, with additional context, inform organizational selection of IAL, AAL, and FAL combinations based on risk and mission.

ビジネス，セキュリティ，およびプライバシーの適切なリスク管理をミッションのニーズと並行して実施することにより，組織は IAL，AAL，および FAL を個別のオプションとして選択します． 具体的には，組織は，実行される各機能に対応するレベルを個別に選択する必要があります． 多くのシステムは，各 IAL，AAL，および FAL の数値レベルが同じである可能性がありますが，これは要件ではなく，組織は，特定のシステムまたはアプリケーションでそれらが同じであると想定すべきではありません．

> By conducting appropriate risk management for business, security, and privacy, side-by-side with mission needs, organizations will select IAL, AAL, and FAL as distinct options. Specifically, organizations are required to individually select levels corresponding to each function being performed. While many systems could have the same numerical level for each IAL, AAL, and FAL, this is not a requirement and organizations should not assume they will be the same in any given system or application.

本ガイドラインで詳述されている アイデンティティ保証の構成要素は次のとおり．

> The components of identity assurance detailed in these guidelines are as follows:

* **IAL** は，身元確認プロセスを指す．
* **AAL** は，当人認証プロセスを指す．
* **FAL** は，フェデレーションプロトコルを介して RP が接続されている場合のフェデレーションプロセスを指す．

> * **IAL** refers to the identity proofing process.
> * **AAL** refers to the authentication process.
> * **FAL** refers to the federation process, when the RP is connected through a federated protocol.

注記：本ガイドラインでは，一般的に，あるいは，まとめて説明する場合，IAL，AAL，FAL を ***xAL*** と表す．

> Note: When described generically or bundled, these guidelines will refer to IAL, AAL, and FAL as ***xAL***.

SP 800-63 は，次の巻で構成されている．

> SP 800-63 is organized as the following suite of volumes:

SP 800-63 *Digital Identity Guidelines*: デジタルシステムでオーセンティケーター，クレデンシャル，およびアサーションを一緒に使用するリスク評価方法と一般的なアイデンティティフレームワークの概要，および保証レベルを選択するリスクベースのプロセスを提供する．_SP 800-63 には，規範的(normative)内容と参考(informative)内容の両方が含まれている．_

> SP 800-63 *Digital Identity Guidelines*: Provides the risk assessment methodology and an overview of general identity frameworks, using authenticators, credentials, and assertions together in a digital system, and a risk-based process of selecting assurance levels. _SP 800-63 contains both normative and informative material._

[[SP800-63A]](../_sp800-63a/sec1_purpose.ja.md#purpose){:latex-href="#ref-SP800-63A"}: 3つの身元確認保証レベル (IAL) のそれぞれでリソースへのアクセスを希望する申請者の，リモートまたは対面での登録および身元確認(identity proofing)の要件を提供する．これは，加入者(subscriber)アカウントの確立と維持，および加入者(subscriber)アカウントへの認証子 (CSP 発行または加入者(subscriber)提供) のバインドに関するクレデンシャルサービスプロバイダー (CSP) の責任を詳述している．
_SP 800-63A には，規範的(normative)内容と参考(informative)内容の両方が含まれている．_

> [[SP800-63A]](../_sp800-63a/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63A"}: Provides requirements for enrollment and identity proofing of applicants, either remotely or in person, that wish to gain access to resources at each of the three identity assurance levels (IALs). It details the responsibilities of Credential Service Providers (CSPs) with respect to establishing and maintaining subscriber accounts and binding authenticators (either CSP-issued or subscriber-provided) to the subscriber account.
_SP 800-63A contains both normative and informative material._

[[SP800-63B]](../_sp800-63b/sec1_purpose.ja.md#purpose){:latex-href="#ref-SP800-63B"}: 3つの当人認証保証レベル (AAL) のそれぞれで使用できるオーセンティケーターの選択を含む，認証プロセスのタイプに関する推奨事項を提供する．また，紛失や盗難が発生した場合の無効化を含む，オーセンティケーターのライフサイクルに関する推奨事項も提供する．
_SP 800-63B には，規範的(normative)内容と参考(informative)内容の両方が含まれている．_

> [[SP800-63B]](../_sp800-63b/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63B"}: Provides recommendations on types of authentication processes, including choices of authenticators, that may be used at each of the three authentication assurance levels (AALs). It also provides recommendations on the lifecycle of authenticators, including invalidation in the event of loss or theft.
_SP 800-63B contains both normative and informative material._

[[SP800-63C]](../_sp800-63c/sec1_purpose.ja.md#purpose){:latex-href="#ref-SP800-63C"}: 認証プロセスの結果と関連するアイデンティティ情報をアプリケーションに伝達するためのフェデレーションアイデンティティアーキテクチャとアサーションの使用に関する要件を提供する．さらに，本巻では，有効な認証された主体に関する情報を共有するためのプライバシー強化手法を提供し，主体がデジタルサービスに対して仮名のままである間に強力な多要素認証 (MFA) を可能にする方法について説明する．
_SP 800-63C には，規範的資料と有益な資料の両方が含まれている．_

> [[SP800-63C]](../_sp800-63c/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63C"}: Provides requirements on the use of federated identity architectures and assertions to convey the results of authentication processes and relevant identity information to an agency application. Further, this volume offers privacy-enhancing techniques to share information about a valid, authenticated subject, and describes methods that allow for strong multi-factor authentication (MFA) while the subject remains pseudonymous to the digital service.
_SP 800-63C contains both normative and informative material._

## Enterprise Risk Management Requirements and Considerations {#ERMreqs}

Effective enterprise risk management is multidisciplinary by default and involves the consideration of a diverse set of factors and equities. In a digital identity risk management context, these factors include, but are not limited to, information security, privacy, equity, and usability. It is important for risk management efforts to weigh these factors as they relate not only to enterprise assets and operations but also to individuals, other organizations, and society more broadly.

During the process of analyzing factors relevant to digital identity, organizations may determine that measures outside of those specified in this publication are appropriate in certain contexts, for instance where privacy or other legal requirements exist or where the output of a risk assessment leads the organization to determine that additional measures or other process safeguards are appropriate. Organizations, including federal agencies, may employ compensating or supplemental controls not specified in this publication. They may also consider partitioning the functionality of a digital service to allow less sensitive functions to be available at a lower level of assurance.

The considerations detailed below support enterprise risk management efforts and encourage informed, inclusive, and human-centric service delivery. While this list of considerations is not exhaustive, it highlights a set of cross-cutting factors likely to impact decision-making associated with digital identity management.

### Security

It is increasingly important for enterprise organizations to assess and manage digital identity security risks, such as unauthorized access, availability issues, impersonation, and other types of fraudulent claims, as well as institute strong identity governance practices. As organizations consult this guidance, they should consider potential impacts to the confidentiality, integrity, and availability of information and information systems that they manage and that their service providers and business partners manage on behalf of the individuals and communities that they serve.

Federal agencies implementing these guidelines need to adhere to their statutory responsibilities, including those under the _Federal Information Security Modernization Act (FISMA) of 2014_ [[FISMA]](sec8_references.md#ref-FISMA) and related NIST standards and guidelines. NIST recommends that non-federal organizations implementing these guidelines follow equivalent standards to ensure the secure operation of their digital systems.

FISMA requires federal agencies to implement appropriate controls to protect federal information and information systems from unauthorized access, use, disclosure, disruption, or modification. The NIST RMF [[NISTRMF]](sec8_references.md#ref-NIST-RMF) provides a process that integrates security, privacy, and cyber supply chain risk management activities into the system development life cycle. It is expected that federal agencies and organizations that provide services under these guidelines have already implemented the controls and processes required under FISMA and associated NIST risk management processes and publications.

The controls and requirements encompassed by the identity, authentication, and federation assurance levels under these guidelines augment, but do not replace or alter, the information and information system controls as determined under FISMA and the RMF.

### Privacy

When designing, engineering, and managing digital identity systems, it is imperative to consider the potential of that system to create privacy-related problems for individuals when processing PII &mdash; a problematic data action &mdash; and the potential impact of the problematic data action should it occur. Additionally, by focusing on the privacy engineering objectives of predictability, manageability, and disassociability, organizations can determine the types of capabilities a given system may need to be able to demonstrate how organizational privacy policies and system privacy requirements have been implemented.

The *Privacy Act of 1974, 2010 Edition*, [[PrivacyAct]](sec8_references.md#ref-PrivacyAct) established a set of fair information practices for the collection, maintenance, use, and disclosure of information about individuals that is maintained by federal agencies in systems of records.

When designing and implementing digital identity management processes and systems, privacy risk assessments are required for PII processing under these guidelines. Such privacy risk assessments can be used to support Privacy Impact Assessments under *OMB Guidance for Implementing the Privacy Provisions of the E-Government Act of 2002* [[M-03-22]](sec8_references.md#ref-M-03-22) as well as to select controls from NIST Special Publication 800-53, *Security and Privacy Controls for Information Systems and Organizations* [[SP800-53]](sec8_references.md#ref-SP800-53). Further, each volume of 800-63 (63A, 63B, and 63C) contains a specific section providing detailed privacy requirements and considerations for the implementation of the processes, controls, and requirements presented in that volume.

### Equity

As defined in Executive Order 13985, *Advancing Racial Equity and Support for Underserved Communities Through the Federal Government* [[EO13985]](sec8_references.md#ref-EO13985), equity refers to the consistent and systematic fair, just, and impartial treatment of all individuals, including individuals who belong to underserved communities that have been denied such treatment, such as Black, Latino, and Indigenous and Native American persons, Asian Americans and Pacific Islanders, and other persons of color; members of religious minorities; lesbian, gay, bisexual, transgender, and queer (LGBTQ+) persons; persons with disabilities; persons who live in rural areas; and persons otherwise adversely affected by persistent poverty or inequality.

A person's ability to engage in an online transaction, such as accessing a critical service like healthcare, is often dependent on their ability to successfully and safely present a digital identity. Given the broad disparities that exist in the U.S. society and globally, many people are either unable to successfully present a digital identity, or they face a higher degree of burden in navigating online services than their more privileged peers, leaving them locked out of critical services or broader participation in the online world. In a public service context, this poses a direct risk to successful mission delivery. In a broader societal context, challenges related to digital access can exacerbate existing inequities and continue systemic cycles of exclusion for historically marginalized and underserved groups.

Readers of this guidance are encouraged to consider existing inequities faced by the populations they serve to identify opportunities to design or operate digital identity systems and processes in ways that best support their needs. Readers are also encouraged to consider any potential or actual impact to the experiences and outcomes of these populations, including disparities between populations, caused by the design or operation of digital identity systems.

For federal agencies implementing these guidelines, EO 13985 directs federal agencies to identify underserved communities for the programs and services that they provide and to determine and address any systemic barriers to underserved communities to provide equitable access to those programs and services. In alignment with the direction set by EO 13985, federal agencies should determine potential barriers communities and individuals may face to enrollment in and access to online benefits and services. They should also  identify whether programmatic changes may be necessary to advance equity.

### Usability

Usability refers to the extent to which a system, product, or service can be used by specified users to achieve specified goals with effectiveness, efficiency, and satisfaction in a specified context of use.

Similar to equity, usability requires an understanding of the people interacting with a digital identity system or process, as well as their unique goals and context of use. To provide an effective, efficient, and satisfactory experience, readers of this guidance should take a holistic approach to considering the interactions that each user will engage in throughout the process of enrolling in and authenticating to a service. Throughout the design and development lifecycle of a digital identity system or process, it is important to conduct usability evaluation with representative users performing realistic scenarios and tasks in appropriate context of use.

Digital identity management processes should be designed and implemented so it is easy for users to do the right thing, hard to do the wrong thing, and easy to recover when the wrong thing happens.
