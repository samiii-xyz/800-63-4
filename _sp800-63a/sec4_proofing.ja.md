---
layout: default.ja
title: Identity Resolution, Validation, and Verification
navOrder: 4
navTitle: Proofing
permalink: /sp800-63a/proofing/
anchor: ipv-section
section: 4
---

# Identity Resolution, Validation, and Verification {#ipv-section}

_This section is normative._

This section provides and overview of the identity proofing and enrollment process as well as requirements to support the resolution, validation, and verification of the identity claimed by an applicant. It also provides guidelines on additional aspects of the identity proofing process.  These requirements are intended to ensure that the claimed identity exists in the real world and that the applicant is the individual associated with that identity. Collectively, the elements of the identity proofing process are designed to ensure that attacks against a CSP's identity service that affect a large number of enrolled subscribers require greater time and cost than the value of the data being protected.

Additionally, these guidelines provide for multiple methods by which resolution, validation, and verification can be completed as well as multiple types of identity evidence that may support the identity proofing process. To the extent practical, CSPs and organizations **SHOULD** enable optionality when implementing their identity proofing services and processes to promote access for those with different means, capabilities, and technology access. At a minimum, this **SHOULD** include accepting multiple types and combinations of identity evidence, supporting multiple data validation sources, enabling multiple methods for verifying identity (e.g., use of trusted referees), multiple channels for engagement (e.g., in-person, remote), and offering assistance mechanisms for applicants (e.g., applicant references). 

## Identity Proofing and Enrollment

This document describes the common pattern in which an applicant undergoes an identity proofing and enrollment process whereby their identity evidence and attributes are collected, uniquely resolved to a single identity within a given population or context, then validated and verified. See [[SP800-63]](../_sp800-63/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63"} for details on how to choose the most appropriate IAL. A CSP can then bind these attributes to an authenticator (described in [[SP800-63B]](../_sp800-63b/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63B"}).

The objective of identity proofing is to ensure, to a stated level of certainty, the applicant is who they claim to be. Identity proofing is not conducted to determine suitability or entitlement to benefits. The identity proofing process involves the presentation and validation of the minimum attributes necessary to accomplish identity proofing.  There can be many different sets of attributes that suffice as the minimum, so CSPs choose this set by considering applicants' privacy and the usability, as well as the likely attributes needed in future uses of the digital identity. For example, such attributes, to the extent they are the minimum necessary, could include:

1. Full name
2. Date of birth
3. Home address

This document also provides requirements for CSPs collecting additional information used for purposes other than identity proofing.

~~~
\clearpage
~~~
{:latex-literal="true"}

### Process Flow

_This section is informative._

[Figure 1](sec4_proofing.md#fig-1) outlines the basic flow for identity proofing and enrollment.

[Figure 1. Identity Proofing Process](sec4_proofing.md#fig-1){:name="fig-1"}
{:latex-ignore="true"}

![Illustration of steps in identity proofing and enrollment]({{site.baseurl}}/{{page.collection}}/media/ProofingProcess.png 'Identity Proofing Process'){:style="width:1074px;height:496px;;min-width: 1074px;min-height: 496px;" latex-src="ProofingProcess.png" latex-fig="1" latex-place="h"}

The following provides an example of how a CSP and an applicant might interact during a remote identity proofing process at IAL2:


1. **収集(Resolution)**
    1. CSP は，名前，住所，生年月日，電子メール，電話番号などの属性を申請者から収集する．
    2. CSP は，運転免許証やパスポートなど，1 つ以上の Enidence も収集する．

> 1. **Resolution**
>    1. The CSP collects attributes from the applicant, such as name, address, date of birth, email, and phone number.
>    2. The CSP also collects one or more pieces of identity evidence, such as a driver's license or a passport. 
    {:.letter-list}

2. **確認(Validation)**
    1．CSP は，手順 1a で取得した属性を，権威のある情報源(authoritative source)または信頼できる情報源(credible source)と照合して確認する．
    2. CSP は，提示された証拠の信頼性，正確性，および最新性を確認する．

> 2. **Validation**
>    1. The CSP validates the attributes obtained in steps 1a by checking them against authoritative or credible sources.
>    2. The CSP validates the authenticity, accuracy, and currency of the presented evidence.
    {:.letter-list}

3. **検証(Verification)**
    1. CSP は申請者(applicant)に，生きているかどうかをチェックして自分の写真を撮るように求める．
    2. CSP は，運転免許証やパスポートの写真を，前のステップでの実際の申請者(applicant)の写真と比較し，それらが一致することを判断する．
    3. CSP は，申請者(applicant)の検証済み電話番号に登録コードを送信し，申請者(applicant)は登録コードを CSP に提供し，CSP はそれらが一致することを確認し，申請者(applicant)が検証済み電話番号を所有および管理していることを確認する．
    4. 申請者(applicant)は身元確認に成功し，加入者(subscriber)アカウントが登録される．

> 3. **Verification**
>     1. The CSP asks the applicant to take a photo of themself, with liveness checks.
>     2. The CSP compares the pictures on the license and the passport to the photo of the live applicant's photo from the previous step and determines they match.
>     3. The CSP sends an enrollment code to the validated phone number of the applicant, the applicant provides the enrollment code to the CSP, and the CSP confirms they match, verifying they the applicant is in possession and control of the validated phone number.
>     4. The applicant has been successfully identity proofed and can be enrolled into a subscriber account.
    {:.letter-list}

## アイデンティティの解決 (Identity Resolution) {#resolve}

identity resolution の目標は、属性の最小セットを使用して，特定の母集団またはコンテキスト内で個人を一意に区別することである．identity resolution は，潜在的な不正行為の初期検出を含んだ，身元確認(identity proofing)プロセス全体の開始点であるが，完全で成功した身元確認(identity proofing)トランザクションを表すものではない．

> The goal of identity resolution is to use the smallest set of attributes to uniquely distinguish an individual within a given population or context. While identity resolution is the starting point in the overall identity proofing process, to include the initial detection of potential fraud, it in no way represents a complete and successful identity proofing transaction.

## アイデンティティの確認と アイデンティティEvidence の収集 (Identity Validation and Identity Evidence Collection) {#evidence-collection}

アイデンティティの確認(Validation) の目的は，申請者(Applicant)から最も適切なアイデンティティEvidenceと属性情報を収集し，それが本物で，正確で，最新であり，有効期限が切れていないことを確認することである．アイデンティティの確認(Validation) は，次の 3 つのプロセスステップで構成される．1) 適切なEvidenceの収集， 2) Evidencrが本物であることの確認， 3) Evidenceに含まれる重要なデータが有効で，最新で，実際の対象者に関連していることの確認．

> The goal of identity validation is to collect the most appropriate identity evidence and attribute information from the applicant and determine it is authentic, accurate, current, and unexpired. Identity validation is made up of three process steps: 1) collecting the appropriate identity evidence; 2) confirming the evidence is authentic; and, 3) confirming key data contained on the identity evidence is valid, current, and related to a real-life subject.

Evidenceの収集は，アイデンティティの確認(Validation) プロセスをサポートし，次の 2 つのステップで構成される．1) 身元確認(identity proofing)の申請者(Applicant)による CSP への Evidence の提示， 2) 提示された Evidence が受け入れ可能かどうかの CSP による決定．Evidence は，物理的な文書，文書のコピー，写真，スキャン，またはデジタル記録として提示できる．受け入れ可能な物的 (文書) Evidence の特性は [Sec. 4.3.1](sec4_proofing.ja.md#physical-evidence) ，受け入れ可能なデジタルEvidenceの特性は [Sec. 4.3.2](sec4_proofing.ja.md#digital-evidence) に示されている．

> Identity evidence collection supports the identity validation process and consists of two steps: 1) presentation of identity evidence by the identity proofing applicant to the CSP and 2) determination by the CSP that the presented evidence is acceptable. Evidence can be presented as a physical document or a copy, photograph, or scan of a document, or as a digital record. The characteristics for acceptable physical (documentary) identity evidence are presented in [Sec. 4.3.1](sec4_proofing.ja.md#physical-evidence) and the characteristics for acceptable digital evidence are provided in [Sec. 4.3.2](sec4_proofing.ja.md#digital-evidence).

CSPは、本セクションのEvidence特性に基づいて，身元確認(identity proofing)のために提示されたEvidenceが受け入れ可能かどうかを決定し**なければならない(SHALL)**．

> The CSP **SHALL** determine the acceptability of presented identity evidence for identity proofing based on the evidence characteristics in this section.

本セクションで示される特性は，CSP が身元確認(identity proofing)プロセスの Evidence として受け入れられるものを決定する際の指針となることを目的としており，Evidence の強度を示すものではない．CSP が特定のタイプの Evidence が受け入れ可能であると判断したら，[Sec. 4.3.3](sec4_proofing.ja.md#evidence-strength) で規定されているように，その強度について判断をする必要がある.

> The characteristics presented in this section are intended to guide CSPs in determining what is acceptable as identity evidence for the identity proofing process and are not an indication of strength of evidence. Once a CSP determines a particular type of evidence is acceptable, a determination must be made as to its strength, as provided in [Sec. 4.3.3](sec4_proofing.md#evidence-strength). 

### 受け入れ可能な 物的 Evidence の特性（Characteristics of Acceptable Physical Evidence） {#physical-evidence}

受け入れ可能な 物的 Evidence は，次のすべての特性を含んでい**なければならない(SHALL)**．

1. 提示された文書は，申請者(Applicant)の名前が印刷されている． (印刷された名前が，申請者(Applicant)が主張する身元とは異なる場合の取り扱いに関するガイダンスは [Sec. 10.1](sec10_equity.md#EquityResolve) - Equity and Resolution 参照)
2. 提示された文書は，少なくとも1つの参照番号が印刷されている．
3. 提示された文書は，文書の発行者の名前が印刷されている．
4. 文書の発行者は，文書を発行する前に，(Applicant)申請者の身元確認(identity proofing)を行っている．
5. 文書は，意図された人物に渡されたという合理的な保証がある．

> Acceptable physical evidence **SHALL** contain all of the following characteristics:

> 1.	The presented document contains the printed name of the applicant. (See [Sec. 10.1](sec10_equity.md#EquityResolve) - Equity and Resolution - for guidance on dealing with a printed name that varies from the applicant's claimed identity.)
> 2.	The presented document contains at least one printed reference number.
> 3.	The presented document contains the printed name of the issuer of the document.
> 4.	The issuer of the document performed identity proofing of the applicant prior to issuing the document.
> 5.	There is reasonable assurance that the document was delivered to the intended person.

### 受け入れ可能な デジタルEvidence の特性（Characteristics of Acceptable Digital Evidence） {#digital-evidence}

受け入れ可能な デジタル Evidence は，次のすべての特性を含んでい**なければならない(SHALL)**．

1. デジタル Evidence は，デジタル情報またはアカウントの主体として申請者(Applicant)の名前を含む． (デジタル Evidence上の名前が，申請者(Applicant)が主張する身元とは異なる場合の取り扱いに関するガイダンスは[Sec. 10.1](sec10_equity.md#EquityResolve) - Equity and Resolution 参照)
2. デジタル Evidence は，少なくとも 1つの参照 (口座番号など) またはデジタル情報を申請者(Applicant)に結び付けるのに十分な属性を含む．
3. デジタル Evidence は，デジタル情報の発行者の名前を含む．
4. デジタル Evidence の発行者は，デジタル証拠を発行する前に，申請者(Applicant)の身元確認(Identity Proofing)を行っている．
5. デジタル Evidence が配信された，または対象者がアクセスできるようになったという合理的な保証がある．
6. 該当する場合，提示されたデジタル証拠は，評価された IAL に対応する AAL または FAL での認証を通じて検証できる．

> Acceptable digital evidence **SHALL** contain all of the following characteristics:
> 
> 1.  The presented digital evidence contains the name of the applicant as the subject of the digital information or account. (See [Sec. 10.1](sec10_equity.md#EquityResolve) - Equity and Resolution - for guidance on dealing with a name on digital evidence that varies from the applicant's claimed identity.)
> 2.  The presented digital evidence contains at least one reference (e.g., account number) or sufficient attributes to bind the digital information to the applicant.
> 3.  The presented digital evidence contains the name of the issuer of the digital information.
> 4.  The issuer of the digital evidence performed identity proofing of the applicant prior to issuing the digital evidence.
> 5.  There is reasonable assurance that the digital evidence was delivered or made accessible to intended person.
> 6.  If applicable, the presented digital evidence can be verified through authentication at an AAL or FAL commensurate with the assessed IAL. 

### Evidence の強度の要件 (Evidence Strength Requirements) {#evidence-strength}

本セクションでは，各強度での identity evidence の要件を定義する．identity evidence の強度は、次の 3 つの側面によって決定される．1) 発行の厳密さ 2) 検証に信頼を与える能力（属性の正確性と完全性を含む） 3) Evidence を提示する申請者(applicant)との紐付けに信頼を与える能力．全てのレベルの強度において証拠は，最新であり，有効期限が切れていない必要がある．
> This section defines the requirements for identity evidence at each strength. Strength of identity evidence is determined by three aspects: 1) the issuing rigor; 2) the ability to provide confidence in validation, including accuracy and integrity of attributes; and 3) the ability to provide confidence in the verification of the applicant presenting the evidence. Evidence at all levels of strength must be current and unexpired. 

#### FAIR Evidence の要件（Fair Evidence Requirements）

FAIR であるには，identity evidence が次の要件を_すべて_満たさ**なければならない(SHALL)**:

1. Evidence の発行元は，身元確認プロセスを通じて主張された身元を確認済みである．
2. Evidence 発行プロセスにより，Evidence が関連する人物に引き渡されることになると合理的に想定できる．
3. Evidence には，少なくとも 1 つの参照番号，顔の肖像画，または関連する人物を一意に識別するのに十分な属性が含まれている．
4. Evidence の有効期限が切れていない，または過去 6 か月以内に期限切れになった，または有効期限が含まれていない場合は過去 6 か月以内に発行されたものである．

> In order to be considered FAIR, identity evidence **SHALL** meet _all_ the following requirements:
> 
> 1.  The issuing source of the evidence confirmed the claimed identity through an identity proofing process.
> 2.  It can be reasonably assumed that the evidence issuing process would result in the delivery of the evidence to the person to whom it relates.
> 3.  The evidence contains at least one reference number, a facial portrait, or sufficient attributes to uniquely identify the person to whom it relates.
> 4.  The evidence has not expired or it expired within the previous six (6) months, or it was issued within the previous six (6) months if it does not contain an expiration date. 

#### STRONG Evidence の要件（Strong Evidence Requirements)

STRONG であるには，identity evidence が次の要件を _すべて_ 満たさ**なければならない(SHALL)**:

1. Evidence の発行元は，その人物の実際の身元を知っていると合理的に信頼できるよう設計されている決められた手順を通じて，主張された身元を確認済みである．手順は，規制機関または公的責任機関による定期的な監視の対象となる．たとえば，the USA PATRIOT Act of 2001 または [[RedFlagsRule]](sec11_references.md#ref-rfr) に対応して確立された顧客識別プログラム（the Customer Identification Program）のガイドラインや，2003年の公正かつ正確な信用取引法（Fair and Accurate Credit Transaction Act of 2003 (FACT Act)） の第 114 条など．
2. Evidence 発行プロセスにより，Evidence が関連する人物に引き渡される可能性が高い. 
3. Evidence には，関連する人物を一意に識別する参照番号またはその他の属性が含まれている．
4. Evidence には，関連する人物の顔写真またはその他の生体特徴が含まれている．
5. Evidence には，コピーまたは複製を困難にする物理的なセキュリティ機能が含まれている．
6. Evidence には有効期限があり、有効期限が切れていない．

> In order to be considered STRONG, identity evidence **SHALL** meet _all_ the following requirements:
> 
> 1.  The issuing source of the evidence confirmed the claimed identity through written procedures designed to enable it to form a reasonable belief that it knows the real-life identity of the person. Such procedures are subject to recurring oversight by regulatory or publicly-accountable institutions. For example, the Customer Identification Program guidelines established in response to the USA PATRIOT Act of 2001 or the [[RedFlagsRule]](sec11_references.md#ref-rfr), under Sec. 114 of the Fair and Accurate Credit Transaction Act of 2003 (FACT Act).
> 2.  There is a high likelihood that the evidence issuing process would result in the delivery of the evidence to the person to whom it relates.
> 3.  The evidence contains a reference number or other attributes that uniquely identify the person to whom it relates.
> 4.  The evidence contains a facial portrait or other biometric characteristic of the person to whom it relates.
> 5.  The evidence includes physical security features that make it difficult to copy or reproduce.
> 6.  The evidence includes an expiration date and is unexpired. 

#### SUPERIOR Evidence の要件Superior Evidence Requirements

SUPERIOR であるには，identity evidence が次の要件を _すべて_ 満たさ**なければならない(SHALL)**:

1. Evidence の発行元は，情報源が対象者の実際の身元を知っていると高い信頼を得られるように設計されている決められた手順を通じて，主張された身元を確認済みである．手順は，規制機関または公的責任機関による定期的な監視の対象となる．
2. 発行元は，申請者を視覚的に識別し，その人物の存在を確認するために追加の確認を行っている．
3. Evidence 発行プロセスにより，証拠がそれに関連する人の所有物として引き渡されたことが保証されている．
4. Evidence には，関連する人物を一意に識別する少なくとも 1 つの参照番号が含まれる．
5. Evidence には，関連する人物の顔写真またはその他の生体特徴が含まれている．
6. Evidence には，暗号で署名されたデジタル情報が含まれる．
7. Evidence には，コピーや複製を困難にする物理的なセキュリティ機能が含まれている．
8. Evidence には有効期限があり、有効期限が切れていない．

> In order to be considered SUPERIOR, identity evidence **SHALL** meet _all_ the following requirements:

> 1.  The issuing source of the evidence confirmed the claimed identity by following written procedures designed to enable it to have high confidence that the source knows the real-life identity of the subject. Such procedures are subject to recurring oversight by regulatory or publicly accountable institutions.
> 2.  The issuing source visually identified the applicant and performed further checks to confirm the existence of that person. 
> 3.  The issuing process for the evidence ensured that it was delivered into the possession of the person to whom it relates.
> 4.  The evidence contains at least one reference number that uniquely identifies the person to whom it relates.
> 5.  The evidence contains a facial portrait or other biometric characteristic of the person to whom it relates.
> 6.  The evidence includes digital information that is cryptographically signed.
> 7.  The evidence includes physical security features that make it difficult to copy or reproduce.
> 8.  The evidence includes an expiration date and is unexpired.

### Identity Evidence and Attribute Validation 

The CSP **SHALL** validate all identity evidence collected to meet evidence collection requirements and all core attribute information required by the CSP identity service. 

#### Evidence Validation {#validation}

The CSP **SHALL** validate the authenticity, accuracy, and currency of presented evidence by:

- Confirming the evidence is in the correct format and includes complete information for the identity evidence type.
- Confirming the evidence is not counterfeit and that it as not been tampered with.
- Confirming any security features.

The CSP **SHALL** validate that the evidence is current through confirmation that its expiration date has not passed or that evidence without an expiration date was issued within the previous six (6) months. 

The authenticity and accuracy of identity evidence or attribute information that is cryptographically protected can be validated through verification of the digital signature on the evidence or the attribute data objects. The CSP **SHALL** use the public key of the issuing authority of the evidence to verify digitally signed evidence or attribute data objects.

#### Attribute Validation

All core attributes, whether obtained from identity evidence or applicant self-assertion, must be validated. This subsection provides guidance on acceptable methods for validating evidence and collected attributes.   

#### Evidence and Attribute Validation Methods

Acceptable methods for validating presented evidence include:

- Visual and tactile inspection by trained personnel for in-person identity proofing,
- Visual inspection by trained personnel for remote identity proofing,
- Automated document validation processes using appropriate technologies,
- Validation of attributes contained on the evidence with an authoritative or credible source.
- Verification of the digital signature protecting digital evidence or attribute data objects using the public key of the issuing authority of the evidence. 

#### Validation Sources

Core attributes that are contained on identity evidence that has been validated according to [Sec. 4.3.4.1](sec4_proofing.md#validation) can be considered validated, in which case no further validation is required.

An authoritative source is an entity that can provide or validate the accuracy of identity attribute information through one or more of the following characteristics. An authoritative source:

- Is the original source of the identity attribute(s); or 
- Is the issuer of identity evidence containing identity attribute information and the issuer confirmed the claimed identity through documented identity proofing processes that are subject to recurring oversight by regulatory or publicly accountable institutions, such as the Customer Identification Program guidelines established under the [[PatriotAct]](sec11_references.md#ref-PatriotAct); or 
- Collected and validated attribute information through an identity proofing process that can confirm the claimed identity through direct interaction with individuals (either in-person or remotely); or
- Has access to evidence and attribute information that can be traced to the issuing source of a piece of identity evidence.

A credible source is an entity that can provide or validate the accuracy of identity evidence and attribute information through one or more of the following characteristics. A credible source:

- Has access to attribute information that was validated through an identity proofing process; or
- Has access to attribute information that can be traced to an authoritative source; or 
- Maintains identity attribute information obtained from multiple sources that is checked for data correlation for accuracy, consistency, and currency.

## Identity Verification

The goal of identity verification is to confirm and establish a linkage between the claimed identity and the real-life existence of the applicant engaged in the identity proofing process.   

### Identity Verification Methods

The CSP **SHALL** verify the linkage of the claimed identity  to the applicant engaged in the identity proofing process through one or more of the following methods, depending on the IAL identity verification requirements presented in [Sec. 5](sec5_ial.md#ial-section).

- **Enrollment code verification** as specified in [Sec. 5.1.6](sec5_ial.md#EnrollCodes).
- **In-person physical comparison**. The CSP operator and applicant interact in person for the identity proofing event. The CSP operator performs a physical comparison of the facial portrait presented on identity evidence to the face of the applicant engaged in the identity proofing event. 
- **Remote (attended and unattended) physical facial image comparison**. The CSP operator performs a physical comparison of the facial portrait presented on identity evidence to the facial image of the applicant engaged in the identity proofing event. The CSP operator may interact directly with the applicant during some or all of the identity proofing event (attended) or may conduct the comparison at a later time (unattended) using a captured video or photograph and the uploaded copy of the evidence. If the comparison is performed at a later time, steps are taken to ensure the captured video or photograph was taken from the live applicant present during the identity proofing event.  
- **Automated biometric comparison**. Biometric system comparison may be performed for in-person or remote identity proofing events. The facial portrait, or other biometric characteristic, contained on identity evidence is compared by an automated biometric comparison system to the facial image photograph of the live applicant or other biometric live sample submitted by the applicant during the identity proofing event. The automated biometric comparison system uses a mathematical algorithm for the comparison.
- **Control of a digital account**. An individual is able to demonstrate control of a digital account (e.g., online bank account) or signed digital assertion (e.g., verifiable credentials) through the use of authentication or federation protocols. This may be done in person through presentation of the credential to a device or reader, but is more likely to be done during remote identity proofing sessions. 




