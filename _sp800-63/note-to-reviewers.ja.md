---
layout: default.ja
title: "Note to Reviewers"
description: "Note to Reviewers"
navOrder: 0.5
navTitle: Reviewers
permalink: /sp800-63/reviewers/
anchor: reviewers
---

# Note to Reviewers {#reviewers}
{: .no_toc}

過去数年間のオンライン サービスの急速な普及により，信頼性が高く，公平で，安全で，プライバシーが保護されたデジタル ID ソリューションの必要性が高まっています．

> The rapid proliferation of online services over the past few years has heightened the need for reliable, equitable, secure, and privacy-protective digital identity solutions. 

NIST SP 800-63 のリビジョン4，デジタルアイデンティティガイドラインは，最後の主要なリビジョンが 2017 年に発行されて以来，出現した変化するデジタルランドスケープに対応することを意図している &mdash; オンラインリスクの現実世界への影響を含む．このガイドラインは，身元確認(identity proofing)，認証(authentication)，フェデレーション(federation)のデジタルアイデンティティ管理保証レベルを満たすためのプロセスと技術的な要件を示している．これには，セキュリティとプライバシーの要件，およびデジタルアイデンティティソリューションとテクノロジの公平性と使いやすさを促進するための考慮事項が含まれる．

> Revision 4 of NIST Special Publication 800-63, Digital Identity Guidelines, intends to respond to the changing digital landscape that has emerged since the last major revision of this suite was published in 2017 &mdash; including the real-world implications of online risks. The guidelines present the process and technical requirements for meeting digital identity management assurance levels for identity proofing, authentication, and federation, including requirements for security and privacy as well as considerations for fostering equity and the usability of digital identity solutions and technology.

[2020年6月のドラフト前のコメント募集](https://csrc.nist.gov/publications/detail/sp/800-63/4/archive/2020-06-08)にて提供されたフィードバックを考慮して，およびガイドラインの実際の実装，市場の革新，現在の脅威環境について実施された調査に加えて，このドラフトは次のことを目指している．

> Taking into account feedback provided in response to our [June 2020 Pre-Draft Call for Comments](https://csrc.nist.gov/publications/detail/sp/800-63/4/archive/2020-06-08), as well as research conducted into real-world implementations of the guidelines, market innovation, and the current threat environment, this draft seeks to: 

1. **更なる公平性:** このドラフトは，以前の改訂のリスク管理の内容を拡張することを目指しており，組織への影響に加えて，個人やコミュニティへの影響を説明することを機関に明確に義務付けている．また，リスク管理プロセス内およびデジタルアイデンティティシステムの実装時に，ミッションの提供に対するリスクを高める．これには，資格のあるすべての人にサービスを提供するという課題が含まれる．さらに，ガイダンスは現在，人口統計全体にわたる，潜在的な影響の継続的な評価を義務付けており，生体認証のパフォーマンス要件，および顔認識を利用するものなどの生体認証ベースの技術の責任ある使用のための追加のパラメーターを提供している．

> 1. **Advance Equity:** This draft seeks to expand upon the risk management content of previous revisions and specifically mandates that agencies account for impacts to individuals and communities in addition to impacts to the organization. It also elevates risks to mission delivery – including challenges to providing services to all people who are eligible for and entitled to them – within the risk management process and when implementing digital identity systems. Additionally, the guidance now mandates continuous evaluation of potential impacts across demographics, provides biometric performance requirements, and additional parameters for the responsible use of biometric-based technologies, such as those that utilize face recognition. 

2. **消費者の選択性と選択肢の強調:** 顔認識技術を利用するものや利用しないものを含む，追加のスケーラブルで公平で便利な身元確認オプションを促進および調査するために，このドラフトは，さまざまな手段，動機，および背景を持つ個人にサービスを安全に提供するための新しいメカニズムを提供するための身元確認の代替手段として許容可能なリストを拡大する．この改訂では，多様な消費者のニーズに対応し，アカウントを安全に復元するために，デジタルアイデンティティサービスが複数の認証オプションをサポートする必要性も強調している．

> 2. **Emphasize Optionality and Choice for Consumers:** In the interest of promoting and investigating additional scalable, equitable, and convenient identify verification options, including those that do and do not leverage face recognition technologies, this draft expands the list of acceptable identity proofing alternatives to provide new mechanisms to securely deliver services to individuals with differing means, motivations, and backgrounds. The revision also emphasizes the need for digital identity services to support multiple authenticator options to address diverse consumer needs and secure account recovery.

3. **詐欺と高度な脅威の抑止:** このドラフトは，新しい攻撃に対応するためにリスクと脅威のモデルを更新し，フィッシング耐性のある認証のための新しいオプションを提供し，登録プロセスに対する自動化された攻撃を防止するための要件を導入することにより，第3版の詐欺防止対策を強化する．また，モバイル運転免許証(mDL)や verifiable credentials などの新しいテクノロジーへの扉も開く．

> 3. **Deter Fraud and Advanced Threats:** This draft enhances fraud prevention measures from the third revision by updating risk and threat models to account for new attacks, providing new options for phishing resistant authentication, and introducing requirements to prevent automated attacks against enrollment processes. It also opens the door to new technology such as mobile driver’s licenses and verifiable credentials. 

4. **実装で学んだ教訓への対処:** このドラフトでは，実装の経験から，ガイドラインを効果的に運用するために追加の明確さや詳細が必要であることが示された領域に対処している．これには，フェデレーションの保証レベルの見直し，Trusted Referee に関する詳細の提供，属性の検証ソースに関するガイドラインの明確化，アドレス確認要件の改善が含まれる．

> 4. **Address Implementation Lessons Learned:** This draft addresses areas where implementation experience has indicated that additional clarity or detail was required to effectively operationalize the guidelines. This includes re-working the federation assurance levels, providing greater detail on Trusted Referees, clarifying guidelines on identity attribute validation sources, and improving address confirmation requirements. 

NIST は，次のトピックに関するコメントと推奨事項に特に関心がある．
> NIST is specifically interested in comments on and recommendations for the following topics:

**身元確認と登録 (Identity Proofing and Enrollment)**

- NIST は，セキュリティと利便性を提供するが，顔認識を必要としない，無人で完全にリモートの Identity Assurance Level (IAL) 2 の身元確認のワークフローを含める必要があると考えている．NIST は次の質問について意見を求めている．
     - 現在の IAL2 プロセスと同じリスクを明らかに軽減するリモートの無人での IAL2 の身元確認プロセスを定めるために，どのような技術または方法を適用できるか?
     - それらの技術は，既存または新たな技術標準によってサポートされているか?
     - それらの技術には，パフォーマンスの評価とユーザー集団全体の影響の理解を可能にするための測定基準とテスト方法が確立されているか (人工知能のバイアスなど)?
- デジタル evidence (モバイル運転免許証(mDL)，Verifiable Credentialsなど) をさまざまな身元保証レベルでの身元確認に適用するための方法はあるか?
- CSP が不正の検出，対応，および通知機能を確立および維持するための一連の要件を指定することの影響，利点，およびリスクは何か?
     - ベースラインの規範的要件として組み込む必要のある既存の不正チェック (例: 死亡日) または不正防止技術 (例: デバイスのフィンガープリンティング) はあるか? あるのであれば，それらはどのような保証レベルで適用できるか?
     - 不正分析やリスクスコアリングなどの新たな手法は，今後どのようにさらに研究，標準化，測定，およびガイダンスに統合される可能性があるか?
     - これらの方法に加えて，付随するプライバシーと公平性についてどのような考慮事項に対処する必要があるか?
- liveness 検出とプレゼンテーション攻撃検出のための現在のテストプログラムは，実装とテクノロジのパフォーマンスを評価するのに十分か?
- 身元確認のために提案された生体認証性能要件は，生体認証技術の実際の実装にどのような影響を与えるか?

> - NIST sees a need for inclusion of an unattended, fully remote Identity Assurance Level (IAL) 2 identity proofing workflow that provides security and convenience, but does not require face recognition. Accordingly, NIST seeks input on the following questions: 
>     - What technologies or methods can be applied to develop a remote, unattended IAL2 identity proofing process that demonstrably mitigates the same risks as the current IAL2 process?
>     - Are these technologies supported by existing or emerging technical standards?
>     - Do these technologies have established metrics and testing methodologies to allow for assessment of performance and understanding of impacts across user populations (e.g., bias in artificial intelligence)?
> - What methods exist for integrating digital evidence (e.g., Mobile Driver’s Licenses, Verifiable Credentials) into identity proofing at various identity assurance levels?
> - What are the impacts, benefits, and risks of specifying a set of requirements for CSPs to establish and maintain fraud detection, response, and notification capabilities? 
>     - Are there existing fraud checks (e.g., date of death) or fraud prevention techniques (e.g., device fingerprinting) that should be incorporated as baseline normative requirements? If so, at what assurance levels could these be applied?
>     - How might emerging methods such as fraud analytics and risk scoring be further researched, standardized, measured, and integrated into the guidance in the future? 
>     - What accompanying privacy and equity considerations should be addressed alongside these methods?
> - Are current testing programs for liveness detection and presentation attack detection sufficient for evaluating the performance of implementations and technologies?  
> - What impacts would the proposed biometric performance requirements for identity proofing have on real-world implementations of biometric technologies? 


**リスク管理 (Risk Management)**

- デジタルアイデンティティのリスクをエンタープライズリスク管理と統合するために，どのような追加のガイダンスまたは指示を提供できるか?
- 公平性，プライバシー，およびユーザビリティへの影響を，保証レベルの選択プロセスとデジタルアイデンティティのリスク管理モデルにどのように統合できるか?
- リスク分析と詐欺軽減技術を，さまざまなアイデンティティ保証レベルの選択にどのように統合できるか? 全体的な アイデンティティのリスクを軽減する能力をどのように評価または定量化できるか?

> - What additional guidance or direction can be provided to integrate digital identity risk with enterprise risk management?
> - How might equity, privacy, and usability impacts be integrated into the assurance level selection process and digital identity risk management model?
> - How might risk analytics and fraud mitigation techniques be integrated into the selection of different identity assurance levels? How can we qualify or quantify their ability to mitigate overall identity risk?


**認証とライフサイクル管理 (Authentication and Lifecycle Management)**

- FIDOパスキー，Verifiable Credentials，モバイル運転免許証(mDL)などの新しい認証モデルと技術は，ガイドラインによって適切に対処され，対応されているか? 関連する潜在的なセキュリティ，プライバシー，およびユーザビリティの利点とリスクは何か?
- AAL2 および AAL3 の認証のガイドラインで定義されているフィッシング耐性の制御は明確かつ十分か?
- セッション管理のしきい値と再認証要件は，機関や組織によってどのように実装されているか? NIST は，アプリケーション，ユーザー，およびミッションのニーズに基づいて，しきい値を提供するか，またはセッションの長さを機関に任せるべきか?
- この巻で提案されている生体認証性能要件は，生体認証技術の実際の実装にどのような影響を与えるか?

> - Are emerging authentication models and techniques – such as FIDO passkey, Verifiable Credentials, and mobile driver’s licenses – sufficiently addressed and accommodated, as appropriate, by the guidelines? What are the potential associated security, privacy, and usability benefits and risks?
> - Are the controls for phishing resistance as defined in the guidelines for AAL2 and AAL3 authentication clear and sufficient?
> - How are session management thresholds and reauthentication requirements implemented by agencies and organizations? Should NIST provide thresholds or leave session lengths to agencies based on applications, users, and mission needs? 
> - What impacts would the proposed biometric performance requirements for this volume have on real-world implementations of biometric technologies? 


**フェデレーションとアサーション (Federation and Assertions)**

- これまでガイドラインで議論されていなかったアイデンティティおよびプロビジョニングAPI の使用を説明するために，どのような追加のプライバシーの考慮事項 (同意の取り消し，使用の制限など) が必要になる可能性があるか?
- 更新されたテキストと「bound authenticators」の導入は、フェデレーション保証レベル (FAL) 3 のトランザクションの実用的な実装を可能にするのに十分明確か? 更新されたガイダンスに基づいて，どのような混乱や課題が予想されるか?

> - What additional privacy considerations (e.g., revocation of consent, limitations of use) may be required to account for the use of identity and provisioning APIs that had not previously been discussed in the guidelines?
> - Is the updated text and introduction of “bound authenticators” sufficiently clear to allow for practical implementations of federation assurance level (FAL) 3 transactions? What complications or challenges are anticipated based on the updated guidance?

**全体 (General)**

- このガイダンスに欠けている，または拡張できると思われる要素はあるか?
- ガイダンスに分かりにくい，または理解しにくい文言はあるか? 任意の言語に，定義または追加のコンテキストを追加する必要があるか?
- ガイダンスはプライバシーに十分に対処しているか?
- ガイダンスは公平性に十分に対応しているか?
     - 身元確認技術またはプロセスの結果として生じる可能性のあるさまざまな影響を防止または検出する際に組織をより適切にサポートするために，どのような公平性評価方法，影響評価モデル，または指標を参照できるか?
- どの特定の実装ガイダンス，リファレンスアーキテクチャ，メトリック，またはその他のサポートリソースが，デジタルアイデンティティガイドラインの今回および将来の反復においてより迅速な採用と実装を可能にするか?
- アイデンティティ市場とこれらのガイドラインの進歩に最大の影響を与える応用研究と測定の取り組みは何か?

> - Is there an element of this guidance that you think is missing or could be expanded?
> - Is any language in the guidance confusing or hard to understand? Should we add definitions or additional context to any language?
> - Does the guidance sufficiently address privacy? 
> - Does the guidance sufficiently address equity? 
>     - What equity assessment methods, impact evaluation models, or metrics could we reference to better support organizations in preventing or detecting disparate impacts that could arise as a result of identity verification technologies or processes?
> - What specific implementation guidance, reference architectures, metrics, or other supporting resources may enable more rapid adoption and implementation of this and future iterations of the Digital Identity Guidelines?
> - What applied research and measurement efforts would provide the greatest impact on the identity market and advancement of these guidelines?

レビュアーは，NIST SP 800-63-4 の 4 つのドラフトボリュームすべてのテキストにコメントし，変更を提案することをお勧めする．コメントの締め切りは 2023年3月24日の午後11時59分(東部時間)である．コメント送信先は <mailto:dig-comments@nist.gov>．NIST はすべてのコメントを確認し，[NIST Identity and Access Management website](https://www.nist.gov/identity-access-management)で確認できるようにする．コメントは、 [NIST Computer Security Resource Center website](https://csrc.nist.gov/publications/detail/sp/800-63c/4/draft) で提供されているコメントテンプレートを使用することをお勧めする.
> Reviewers are encouraged to comment and suggest changes to the text of all four draft volumes of of the NIST SP 800-63-4 suite. NIST requests that all comments be submitted by 11:59pm Eastern Time on March 24, 2023. Please submit your comments to <mailto:dig-comments@nist.gov>. NIST will review all comments and make them available at the [NIST Identity and Access Management website](https://www.nist.gov/identity-access-management). Commenters are encouraged to use the comment template provided on the [NIST Computer Security Resource Center website](https://csrc.nist.gov/publications/detail/sp/800-63/4/draft).
