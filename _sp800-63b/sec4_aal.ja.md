---
layout: default.ja
title: Authentication Assurance Levels
navOrder: 4
navTitle: AAL
permalink: /sp800-63b/aal/
anchor: AAL_SEC4
section: 4
---

# Authentication Assurance Levels {#AAL_SEC4}

_This section is normative._

特定の AAL の要件を満たし，加入者(subscriber)として認識されるために，要求者(claimant)は，その強度がそのレベルの要件以上のプロセスで認証され**なければならない(SHALL)**．認証プロセスの結果は，識別子であり，加入者(subscriber)がその RP に対して認証するたびに使用し**なければならない(SHALL)**．識別子は仮名であっ**てもよい(MAY)**. 加入者(subscriber)識別子は，別の対象者に再利用し**てはならない(SHALL NOT)**が，以前登録した対象者が CSP によって再登録された場合は再利用し**なければならない(SHALL)**．加入者(subscriber)を一意の対象者として識別する他の属性も提供され**てもよい(MAY)**. 
> To satisfy the requirements of a given AAL and be recognized as a subscriber, a claimant **SHALL** be authenticated with a process whose strength is equal to or greater than the requirements at that level. The result of an authentication process is an identifier that **SHALL** be used each time that subscriber authenticates to that RP. The identifier **MAY** be pseudonymous. Subscriber identifiers **SHOULD NOT** be reused for a different subject but **SHOULD** be reused when a previously enrolled subject is re-enrolled by the CSP. Other attributes that identify the subscriber as a unique subject **MAY** also be provided.

各 AAL でのオーセンティケーターと検証者の詳細な規範的(normative)要件は，[Sec. 5](#AAL_SEC5)に記載されている．
> Detailed normative requirements for authenticators and verifiers at each AAL are provided in [Sec. 5](#AAL_SEC5).

最適な AAL を選択する方法の詳細については，[[SP800-63]](../_sp800-63/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63"} 参照．
> See [[SP800-63]](../_sp800-63/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63"} Sec. 5 for details on how to choose the most appropriate AAL.

[[FIPS140]](references.md#ref-FIPS140) の要件は、FIPS 140-3 以降のリビジョンで満たされている．
> [[FIPS140]](references.md#ref-FIPS140) requirements are satisfied by FIPS 140-3 or newer revisions.

身元確認中およびその後に収集された個人情報は，デジタルアイデンティティービスによって加入者(subscriber)に提供され**てもよい(MAY)**. 連邦政府機関による PII またはその他の個人情報の公開またはオンラインでの利用可能性は，自己主張か検証済みかにかかわらず，[[EO13681]](references.md#ref-EO13681) に従って多要素認証を必要とする．したがって，連邦政府機関は，PII またはその他の個人情報がオンラインで利用可能になる場合，最低限の AAL2 を選択**なければならない(SHALL)**．
> Personal information collected during and subsequent to identity proofing **MAY** be made available to the subscriber by the digital identity service. The release or online availability of any PII or other personal information, whether self-asserted or validated, by federal government agencies requires multi-factor authentication in accordance with [[EO13681]](references.md#ref-EO13681). Therefore, federal government agencies **SHALL** select a minimum of AAL2 when PII or other personal information is made available online.

## Authentication Assurance Level 1

AAL1 は，申請者(applicant)が加入者(subscriber)アカウントにバインドされたオーセンティケータを制御するという保証を提供する．AAL1 では，利用可能なさまざまな認証技術を使用した単一要素認証または多要素認証が必要である．認証を成功させるには，要求者(claimant)が安全な認証プロトコルを介してオーセンティケータの所有と管理を証明する必要がある．

> AAL1 provides some assurance that the claimant controls an authenticator bound to the subscriber account. AAL1 requires either single-factor or multi-factor authentication using a wide range of available authentication technologies. Successful authentication requires that the claimant prove possession and control of the authenticator through a secure authentication protocol.

### 許可されているオーセンティケータの種類（Permitted Authenticator Types）

AAL1 認証は，[Sec. 5](sec5_authenticators.md#AAL_SEC5) で定義されている次のオーセンティケータのいずれかを使用して行わ**なければならない(SHALL)**．
> AAL1 authentication **SHALL** occur by the use of any of the following authenticator types, which are defined in [Sec. 5](sec5_authenticators.md#AAL_SEC5):

* Memorized secret ([Sec. 5.1.1](sec5_authenticators.md#memsecret))
* Look-Up secret ([Sec. 5.1.2](sec5_authenticators.md#lookupsecrets))
* Out-of-band device ([Sec. 5.1.3](sec5_authenticators.md#out-of-band))
* Single-factor one-time password (OTP) device ([Sec. 5.1.4](sec5_authenticators.md#singlefactorOTP))
* Multi-factor OTP device ([Sec. 5.1.5](sec5_authenticators.md#multifactorOTP))
* Single-factor cryptographic software ([Sec. 5.1.6](sec5_authenticators.md#sfcs))
* Single-factor cryptographic device ([Sec. 5.1.7](sec5_authenticators.md#sfcd))
* Multi-factor cryptographic software ([Sec. 5.1.8](sec5_authenticators.md#mfcs))
* Multi-factor cryptographic device ([Sec. 5.1.9](sec5_authenticators.md#mfcd))

### Authenticator and Verifier Requirements {#aal1req}
AAL1 で使用される暗号認証は，承認された暗号を使用し**なければならない(SHALL)**．オペレーティングシステムのコンテキスト内で動作するソフトウェアベースの認証システムは，該当する場合，それらが実行されているユーザーエンドポイントの侵害 (マルウェアなどによる) の検出を試み**てもよく(MAY)**，そのような侵害が検出されたときに操作を完了し**てはならない(SHALL NOT)**．
> Cryptographic authenticators used at AAL1 **SHALL** use approved cryptography. Software-based authenticators that operate within the context of an operating system **MAY**, where applicable, attempt to detect compromise (e.g., by malware) of the user endpoint in which they are running and **SHOULD NOT** complete the operation when such a compromise is detected.

要求者(claimant)と検証者の間の通信は，認証された保護されたチャネルを介して行われ**なければならなず(SHALL)**，認証出力の機密性と中間者 (AitM) 攻撃への耐性を提供する．

> Communication between the claimant and verifier **SHALL** be via an authenticated protected channel to provide confidentiality of the authenticator output and resistance to adversary-in-the-middle (AitM) attacks.

AAL1 で連邦政府機関によって，または連邦政府機関に代わって運営される検証者は，[[FIPS140]](references.md#ref-FIPS140-2) レベル 1 の要件を満たすために検証され**なければならない(SHALL)**．
> Verifiers operated by or on behalf of federal government agencies at AAL1 **SHALL** be validated to meet the requirements of [[FIPS140]](references.md#ref-FIPS140-2) Level 1.

### Reauthentication {#aal1reauth}

Periodic reauthentication of subscriber sessions **SHALL** be performed as described in [Sec. 7.2](sec7_session.md#sessionreauthn). At AAL1, reauthentication of the subscriber **SHOULD** be repeated at least once per 30 days during an extended usage session, regardless of user activity. The session **SHOULD** be terminated (i.e., logged out) when this time limit is reached.

### Security Controls

The CSP **SHALL** employ appropriately tailored security controls from the baseline security controls defined in [[SP800-53]](references.md#ref-SP800-53) or equivalent federal (e.g., [[FEDRAMP]](references.md#ref-FEDRAMP)) or industry standard that the organization has determined for the information systems, applications, and online services that these guidelines are used to protect. The CSP **SHALL** ensure that the minimum assurance-related controls for the appropriate systems, or equivalent, are satisfied.

###  Records Retention Policy {#aal1records}

The CSP **SHALL** comply with its respective records retention policies in accordance with applicable laws, regulations, and policies, including any National Archives and Records Administration (NARA) records retention schedules that may apply. If the CSP opts to retain records in the absence of any mandatory requirements, the CSP **SHALL** conduct a risk management process, including assessments of privacy and security risks, to determine how long records should be retained and **SHALL** inform the subscriber of that retention policy.

## Authentication Assurance Level 2

AAL2 は，申請者(applicant)が加入者(subscriber)アカウントにバインドされたオーセンティケーターを制御するという高い信頼性を提供する．安全な認証プロトコルを通じて，2つの異なる認証要素の所有と管理の証明が必要である．AAL2 以上では，承認された暗号技術が必要である．

> AAL2 provides high confidence that the claimant controls authenticators bound to the subscriber account. Proof of possession and control of two distinct authentication factors is required through secure authentication protocols. Approved cryptographic techniques are required at AAL2 and above.

### 許可されているオーセンティケータの種類（Permitted Authenticator Types）{#aal2types}

AAL2 では，認証は，多要素オーセンティケータまたは 2つの単一要素オーセンティケータの組み合わせのいずれかを使用して行われ**なければならない(SHALL)**．多要素認証システムでは，単一の認証イベントを実行するために 2つの要素が必要である．たとえば，デバイスのアクティブ化に必要な生体認証センサーが統合された，暗号的に安全なデバイスなど．Authenticator の要件は，[Sec. 5](sec5_authenticators.md#AAL_SEC5)で指定されている．

> At AAL2, authentication **SHALL** occur by the use of either a multi-factor authenticator or a combination of two single-factor authenticators. A multi-factor authenticator requires two factors to execute a single authentication event, such as a cryptographically secure device with an integrated biometric sensor that is required to activate the device. Authenticator requirements are specified in [Sec. 5](sec5_authenticators.md#AAL_SEC5).

多要素認証を使用する場合，次のいずれかを使用し**てもよい(MAY)**：
> When a multi-factor authenticator is used, any of the following **MAY** be used:

* Multi-Factor Out-of-Band Authenticator ([Sec. 5.1.3.4](sec5_authenticators.md#mfooba))
* Multi-Factor OTP Device ([Sec. 5.1.5](sec5_authenticators.md#multifactorOTP))
* Multi-Factor Cryptographic Software ([Sec. 5.1.8](sec5_authenticators.md#mfcs))
* Multi-Factor Cryptographic Device ([Sec. 5.1.9](sec5_authenticators.md#mfcd))

2 の単一要素オーセンティケータの組み合わせが使用される場合，その組み合わせには，次のリストの記憶秘密によるオーセンティケータ([Sec. 5.1.1](sec5_authenticators.md#memsecret)) と 1つの物理オーセンティケータ (「持っているもの」など) を含め**なければならない(SHALL)**．
> When a combination of two single-factor authenticators is used, the combination **SHALL** include a Memorized Secret authenticator ([Sec. 5.1.1](sec5_authenticators.md#memsecret)) and one physical authenticator (i.e., "something you have") from the following list:

* Look-Up Secret ([Sec. 5.1.2](sec5_authenticators.md#lookupsecrets))
* Out-of-Band Device ([Sec. 5.1.3](sec5_authenticators.md#out-of-band))
* Single-Factor OTP Device ([Sec. 5.1.4](sec5_authenticators.md#singlefactorOTP))
* Single-Factor Cryptographic Software ([Sec. 5.1.6](sec5_authenticators.md#sfcs))
* Single-Factor Cryptographic Device ([Sec. 5.1.7](sec5_authenticators.md#sfcd))

注記: 生体認証が [Sec. 5.2.3](sec5_authenticators.md#biometric_use) の要件を満たす場合，生体認証の一致に加えて，デバイスも認証する必要がある．バイオメトリクスの特徴は要素として認識されるが，それ自体はオーセンティケーターとしては認識されない．したがって，生体認証を行う場合，関連付けられたデバイスは「持っているもの」として機能し，生体照合は「自身であること」として機能するため，2つのオーセンティケーターを使用する必要はない．

> Note: When biometric authentication meets the requirements in [Sec. 5.2.3](sec5_authenticators.md#biometric_use), the device has to be authenticated in addition to the biometric match. A biometric characteristic is recognized as a factor, but not recognized as an authenticator by itself. Therefore, when conducting authentication with a biometric characteristic, it is unnecessary to use two authenticators because the associated device serves as "something you have," while the biometric match serves as "something you are."

### Authenticator and Verifier Requirements {#aal2req}

AAL2 で使用される暗号認証は，承認された暗号を使用し**なければならない(SHALL)**．連邦政府機関によって調達されるオーセンティケータは，[[FIPS140]](references.md#ref-FIPS140-2) レベル 1 の要件を満たすことを検証され**なければならない(SHALL)**．オペレーティングシステムのコンテキスト内で動作するソフトウェアベースの認証システムは，該当する場合，実行されているプラットフォームの侵害 (マルウェアなどによる) を検出しようとする．そのような侵害が検出された場合，操作を完了し**てはならない(SHALL NOT)**．AAL2 で使用される少なくとも 1 つのオーセンティケータは， [Sec. 5.2.8](sec5_authenticators.md#replay). で説明されているように，リプレイ耐性が**なければならない(SHALL)**．AAL2 での認証は，[Sec. 5.2.9](sec5_authenticators.md#intent) で説明されているように，少なくとも 1 つのオーセンティケーターから認証の意図を示さ**なければならない(SHALL)**．

> Cryptographic authenticators used at AAL2 **SHALL** use approved cryptography. Authenticators procured by federal government agencies **SHALL** be validated to meet the requirements of [[FIPS140]](references.md#ref-FIPS140-2) Level 1. Software-based authenticators that operate within the context of an operating system **MAY**, where applicable, attempt to detect compromise (e.g., by malware) of the platform in which they are running. They **SHOULD NOT** complete the operation when such a compromise is detected. At least one authenticator used at AAL2 **SHALL** be replay resistant as described in [Sec. 5.2.8](sec5_authenticators.md#replay). Authentication at AAL2 **SHOULD** demonstrate authentication intent from at least one authenticator as discussed in [Sec. 5.2.9](sec5_authenticators.md#intent).

要求者(claimant)と検証者の間の通信は，認証された保護されたチャネルを介して行われ，認証出力の機密性と AitM 攻撃への耐性を提供し*なければならない(SHALL)**．
> Communication between the claimant and verifier **SHALL** be via an authenticated protected channel to provide confidentiality of the authenticator output and resistance to AitM attacks.

AAL2 で連邦政府機関によって，または連邦政府機関に代わって運営される検証者は，[[FIPS140]](references.md#ref-FIPS140-2)  レベル 1 の要件を満たすと検証され**なければならない(SHALL)**．
> Verifiers operated by or on behalf of federal government agencies at AAL2 **SHALL** be validated to meet the requirements of [[FIPS140]](references.md#ref-FIPS140-2) Level 1.

AAL2 での認証にバイオメトリック要素が使用される場合，[Sec. 5.2.3](sec5_authenticators.md#biometric_use) に記載されているパフォーマンス要件を満たさ**なければならず(SHALL)**，検証者は，バイオメトリックセンサーとその後の処理がこれらの要件を満たしていると判断し**なければならない(SHALL)**．
> When a biometric factor is used in authentication at AAL2, the performance requirements stated in [Sec. 5.2.3](sec5_authenticators.md#biometric_use) **SHALL** be met, and the verifier **SHOULD** make a determination that the biometric sensor and subsequent processing meet these requirements.

OMB Memorandum [[M-22-09]](references.md#ref-M-22-09) は，連邦政府機関に対し，AAL2 のパブリックユーザーに少なくとも 1つのフィッシング耐性認証オプションを提供することを要求している．[Sec. 5.2.5](sec5_authenticators.md#verifimpers) で説明されているようなフィッシング耐性は，一般に AAL2 での認証には必要ないが，フィッシングは重大な脅威ベクトルであるため，検証者は，実用的な場合はいつでも AAL2 でのフィッシング耐性のあるオーセンティケーターの使用を推奨し**なければならない(SHALL)**．
> OMB Memorandum [[M-22-09]](references.md#ref-M-22-09) requires federal government agencies to offer at least one phishing-resistant authenticator option to public users at AAL2. While phishing resistance as described in [Sec. 5.2.5](sec5_authenticators.md#verifimpers) is not generally required for authentication at AAL2, verifiers **SHOULD** encourage the use of phishing-resistant authenticators at AAL2 whenever practical since phishing is a significant threat vector.

### Reauthentication {#aal2reauth}

加入者(subscriber)セッションの定期的な再認証は，[Sec. 7.2](sec7_session.md#sessionreauthn)で説明されている通りで**なければならない(SHALL)**．AAL2 では，ユーザのアクティビティに関係なく，延長された使用セッション中に少なくとも 12 時間に 1 回，加入者(subscriber)の認証を繰り返さ**なければならない(SHALL)**．加入者(subscriber)の再認証は，30 分以上続く非アクティブ期間の後に繰り返さ**なければならない(SHALL)**．これらの時間制限のいずれかに達した場合，セッションは終了 (つまり，ログアウト)し **なければならない(SHALL)**．

> Periodic reauthentication of subscriber sessions **SHALL** be performed as described in [Sec. 7.2](sec7_session.md#sessionreauthn). At AAL2, authentication of the subscriber **SHALL** be repeated at least once per 12 hours during an extended usage session, regardless of user activity. Reauthentication of the subscriber **SHALL** be repeated following any period of inactivity lasting 30 minutes or longer. The session **SHALL** be terminated (i.e., logged out) when either of these time limits is reached.

制限時間にまだ達していないセッションの再認証には，記憶されたシークレットまたはまだ有効なセッションシークレットと組み合わせたバイオメトリクスのみ必要とし**てもよい(MAY)**．検証者は，非アクティブタイムアウトの直前にアクティビティを発生させるようにユーザーに促し**てもよい(MAY)**．
> Reauthentication of a session that has not yet reached its time limit **MAY** require only a memorized secret or a biometric in conjunction with the still-valid session secret. The verifier **MAY** prompt the user to cause activity just before the inactivity timeout.

### Security Controls

CSP は，[[SP800-53]](references.md#ref-SP800-53) または同等の連邦政府 (例: [[FEDRAMP]](references.md#ref-FEDRAMP)) で定義されているベースラインセキュリティコントロール，またはこれらのガイドラインが保護されるために使用される情報システム，アプリケーション，オンラインサービスに対して組織が決定した業界標準から，適切に調整されたセキュリティコントロールを採用し**なければならない(SHALL)**．または CSP は，適切なシステムまたは同等のシステムに対する最小限の保証関連のコントロールが満たされていることを保証し**なければならない(SHALL)**．
> The CSP **SHALL** employ appropriately tailored security controls from the baseline security controls defined in [[SP800-53]](references.md#ref-SP800-53) or equivalent federal (e.g., [[FEDRAMP]](references.md#ref-FEDRAMP)) or industry standard that the organization has determined for the information systems, applications, and online services that these guidelines are used to protect. The CSP **SHALL** ensure that the minimum assurance-related controls for the appropriate systems, or equivalent, are satisfied.

### Records Retention Policy {#aal2records}

CSP は，適用される可能性のある NARA 記録保持スケジュールを含む，適用される法律，規制，およびポリシーに従って，それぞれの記録保持ポリシーを遵守し**なければならない(SHALL)**．CSP が必須要件がない場合に記録を保持することを選択した場合，CSP は，プライバシーおよびセキュリティリスクの評価を含むリスク管理プロセスを実施して，記録を保持する期間を決定し，加入者(subscriber)にその保持ポリシーを通知し**なければならない(SHALL)**．
> The CSP **SHALL** comply with its respective records retention policies in accordance with applicable laws, regulations, and policies, including any NARA records retention schedules that may apply. If the CSP opts to retain records in the absence of any mandatory requirements, the CSP **SHALL** conduct a risk management process, including assessments of privacy and security risks to determine how long records should be retained and **SHALL** inform the subscriber of that retention policy.

## Authentication Assurance Level 3 {#aal3}

AAL3 は，要求者(claimant)が加入者(subscriber)アカウントにバインドされたオーセンティケーターを制御するという非常に高い信頼性を提供する．AAL3 での認証は，暗号化プロトコルによる鍵の所有証明に基づいている．AAL3 認証は，ハードウェアベースのオーセンティケーターと，フィッシング耐性を提供するオーセンティケーターを使用し**なければならない(SHALL)**．同じデバイスがこれらの要件の両方を満たし**てもよい(MAY)**．AAL3 で認証するために，要求者(claimant)は，安全な認証プロトコルを通じて，2 つの異なる認証要素の所有と管理を証明し**なければならない(SHALL)**．承認された暗号技術が必要である．
> AAL3 provides very high confidence that the claimant controls authenticators bound to the subscriber account. Authentication at AAL3 is based on proof of possession of a key through a cryptographic protocol. AAL3 authentication **SHALL** use a hardware-based authenticator and an authenticator that provides phishing resistance — the same device **MAY** fulfill both these requirements. In order to authenticate at AAL3, claimants **SHALL** prove possession and control of two distinct authentication factors through secure authentication protocols. Approved cryptographic techniques are required.

### Permitted Authenticator Types {#aal3types}

AAL3 authentication **SHALL** occur by the use of one of a combination of authenticators satisfying the requirements in [Sec. 4.3](#aal3). Possible combinations are:

* Multi-Factor Cryptographic Device ([Sec. 5.1.9](sec5_authenticators.md#mfcd))
* Single-Factor Cryptographic Device ([Sec. 5.1.7](sec5_authenticators.md#sfcd)) used in conjunction with a Memorized Secret ([Sec. 5.1.1](sec5_authenticators.md#memsecret))
* Multi-Factor OTP device (software or hardware) ([Sec. 5.1.5](sec5_authenticators.md#multifactorOTP)) used in conjunction with a Single-Factor Cryptographic Device ([Sec. 5.1.7](sec5_authenticators.md#sfcd))
* Multi-Factor OTP device (hardware only) ([Sec. 5.1.5](sec5_authenticators.md#multifactorOTP)) used in conjunction with a Single-Factor Cryptographic Software ([Sec. 5.1.6](sec5_authenticators.md#sfcs))
* Single-Factor OTP device (hardware only) ([Sec. 5.1.4](sec5_authenticators.md#singlefactorOTP)) used in conjunction with a Multi-Factor Cryptographic Software Authenticator ([Sec. 5.1.8](sec5_authenticators.md#mfcs))

### Authenticator and Verifier Requirements {#aal3req}

Communication between the claimant and verifier **SHALL** be via an authenticated protected channel to provide confidentiality of the authenticator output and resistance to AitM attacks. At least one cryptographic authenticator used at AAL3 **SHALL** be phishing resistant as described in [Sec. 5.2.5](sec5_authenticators.md#verifimpers) and **SHALL** be replay resistant as described in [Sec. 5.2.8](sec5_authenticators.md#replay). All authentication and reauthentication processes at AAL3 **SHALL** demonstrate authentication intent from at least one authenticator as described in [Sec. 5.2.9](sec5_authenticators.md#intent).

Multi-factor authenticators used at AAL3 **SHALL** be hardware cryptographic modules validated at [[FIPS140]](references.md#ref-FIPS140-2) Level 2 or higher overall with at least [[FIPS140]](references.md#ref-FIPS140-2) Level 3 physical security. Single-factor cryptographic devices used at AAL3 **SHALL** be validated at [[FIPS140]](references.md#ref-FIPS140-2) Level 1 or higher overall with at least [[FIPS140]](references.md#ref-FIPS140-2) Level 3 physical security.

Verifiers at AAL3 **SHALL** be validated at [[FIPS140]](references.md#ref-FIPS140-2) Level 1 or higher.

Verifiers at AAL3 **SHALL** be verifier compromise resistant as described in [Sec. 5.2.7](sec5_authenticators.md#verifier-secrets) with respect to at least one authentication factor.

Hardware-based authenticators and verifiers at AAL3 **SHOULD** resist relevant side-channel (e.g., timing and power-consumption analysis) attacks.

When a biometric factor is used in authentication at AAL3, the verifier **SHALL** make a determination that the biometric sensor and subsequent processing meet the performance requirements stated in [Sec. 5.2.3](sec5_authenticators.md#biometric_use).

### Reauthentication {#aal3reauth}

Periodic reauthentication of subscriber sessions **SHALL** be performed as described in [Sec. 7.2](sec7_session.md#sessionreauthn). At AAL3, authentication of the subscriber **SHALL** be repeated at least once per 12 hours during an extended usage session, regardless of user activity, as described in [Sec. 7.2](sec7_session.md#sessionreauthn). Reauthentication of the subscriber **SHALL** be repeated following any period of inactivity lasting 15 minutes or longer. Reauthentication **SHALL** use both authentication factors. The session **SHALL** be terminated (i.e., logged out) when either of these time limits is reached. The verifier **MAY** prompt the user to cause activity just before the inactivity timeout.

### Security Controls

The CSP **SHALL** employ appropriately tailored security controls from the baseline security controls defined in [[SP800-53]](references.md#ref-SP800-53) or equivalent federal (e.g., [[FEDRAMP]](references.md#ref-FEDRAMP)) or industry standard that the organization has determined for the information systems, applications, and online services that these guidelines are used to protect. The CSP **SHALL** ensure that the minimum assurance-related controls for the appropriate systems, or equivalent, are satisfied.

### Records Retention Policy {#aal3records}

The CSP **SHALL** comply with its respective records retention policies in accordance with applicable laws, regulations, and policies, including any NARA records retention schedules that may apply. If the CSP opts to retain records in the absence of any mandatory requirements, the CSP **SHALL** conduct a risk management process, including assessments of privacy and security risks, to determine how long records should be retained and **SHALL** inform the subscriber of that retention policy.

## Privacy Requirements {#aal_privacy}

The CSP **SHALL** employ appropriately tailored privacy controls defined in [[SP800-53]](references.md#ref-SP800-53) or equivalent industry standard.

If CSPs process attributes for purposes other than identity proofing, authentication, or attribute assertions (collectively "identity service"), related fraud mitigation, or to comply with law or legal process, CSPs **SHALL** implement measures to maintain predictability and manageability commensurate with the privacy risk arising from the additional processing. Measures **MAY** include providing clear notice, obtaining subscriber consent, or enabling selective use or disclosure of attributes. When CSPs use consent measures, CSPs **SHALL NOT** make consent for the additional processing a condition of the identity service.

Regardless of whether the CSP is an agency or private sector provider, the following requirements apply to a federal agency offering or using the authentication service:

1. The agency **SHALL** consult with their Senior Agency Official for Privacy (SAOP) and conduct an analysis to determine whether the collection of PII to issue or maintain authenticators triggers the requirements of the *Privacy Act of 1974* [[PrivacyAct]](references.md#ref-PrivacyAct) (see [Sec. 9.4](sec9_privacy.md#agency-privacy)).
2. The agency **SHALL** publish a System of Records Notice (SORN) to cover such collections, as applicable.
3. The agency **SHALL** consult with their SAOP and conduct an analysis to determine whether the collection of PII to issue or maintain authenticators triggers the requirements of the *E-Government Act of 2002* [[E-Gov]](references.md#ref-E-Gov).
4. The agency **SHALL** publish a Privacy Impact Assessment (PIA) to cover such collection, as applicable.

## Summary of Requirements

[Table 1](sec4_aal.md#table-1) provides a non-normative summary of the requirements for each of the AALs.

[Table 1 AAL Summary of Requirements](sec4_aal.md#table-1){:name="table-1"}
{:latex-ignore="true"}

Requirement | AAL1 | AAL2 | AAL3
------------|-------|-------|-------
**Permitted authenticator types** | Memorized Secret; Look-up Secret; Out-of-Band; SF OTP Device; MF OTP Device; SF Crypto Software; SF Crypto Device; MF Crypto Software; MF Crypto Device  | MF Out-of-Band; MF OTP Device; MF Crypto Software; MF Crypto Device; or Memorized Secret plus: Look-up Secret, Out-of-Band, SF OTP Device, SF Crypto Software, SF Crypto Device  | MF Crypto Device; SF Crypto Device plus Memorized Secret; SF OTP Device plus MF Crypto Device or Software; SF OTP Device plus SF Crypto Software plus Memorized Secret
**FIPS 140 validation** | Level 1 (Government agency verifiers) | Level 1 (Government agency authenticators and verifiers) | Level 2 overall (MF authenticators) Level 1 overall (verifiers and SF Crypto Devices) Level 3 physical security (all authenticators)
**Reauthentication** | 30 days | 12 hours or 30 minutes inactivity; one authentication factor | 12 hours or 15 minutes inactivity; both authentication factors
**Security controls**|[[SP800-53]](references.md#ref-SP800-53) Low Baseline (or equivalent)|[[SP800-53]](references.md#ref-SP800-53) Moderate Baseline (or equivalent)|[[SP800-53]](references.md#ref-SP800-53) High Baseline (or equivalent)
**AitM resistance** | Required | Required | Required |
**Phishing resistance** | Not required | Recommended | Required |
**Verifier-compromise resistance** | Not required | Not required | Required |
**Replay resistance** | Not required | Required | Required |
**Authentication intent** | Not required | Recommended | Required |
{:latex-table="1" latex-caption="AAL Summary of Requirements" latex-columns="p@0.20\textwidth,p@0.22\textwidth,p@0.22\textwidth,p@0.25\textwidth"}
