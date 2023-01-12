---
layout: default.ja
title: Digital Identity Risk Management
navOrder: 5
navTitle: DIRM
permalink: /sp800-63/dirm/
anchor: sec5
section: 5
---

# Digital Identity Risk Management {#sec5}

_This section is normative._

本章では，各xALのデジタルアイデンティティリスクを評価する方法について詳しく説明する．本プロセスでは，連邦情報セキュリティ近代化法(Federal Information Security Modernization Act) [[FISMA]](sec8_references.ja.md#ref-FISMA) の要件を実装するための NIST ガイダンスの下で，情報および情報システムリスクのリスク管理プロセスを強化する．

> This section provides details on the methodology for assessing digital identity risks for each xAL. This process augments the risk management processes for information and information system risk under NIST guidance for implementing Federal Information Security Modernization Act [[FISMA]](sec8_references.md#ref-FISMA) requirements.

デジタルアイデンティティリスク管理プロセスには 4つのステップがある．

1. **初期影響評価の実施**: 本ステップでは，定義された一連の影響カテゴリ―に対して，組織はユーザー集団を評価し，保護されたアプリケーションまたはサービスのアイデンティティシステム (身元確認，当人認証，フェデレーション) の各機能の障害の影響を評価する．本ステップの結果は，文書化された一連の影響カテゴリと関連する影響レベルである．
2. **初期保証レベルの選択**: 本ステップでは，影響カテゴリと影響レベルを評価し，アプリケーションを保護するための適切な保証レベルを決定する．本ステップの結果は，該当するxALごとに特定された初期レベルである．
3. **保証レベルの決定の調整と文書化**: 本ステップでは，詳細なプライバシー，公平性，使いやすさ，および脅威の評価が実施され，最初に選択された保証レベルがアプリケーションの特定のユーザー集団と脅威環境に与える潜在的な影響が決定される．初期の保証レベルが調整され，補完または補足的なコントロールが特定され，すべての決定は文書化される．結果は，実装可能な保証レベルが定義されたデジタルアイデンティティ承認ステートメント (Digital Identity Acceptance Statement， [Sec. 5.3.4](sec5_DIRM.md#IDacceptStmt) 参照) である．
4. **継続的な評価と改善**: 本ステップでは，組織のニーズと進化する脅威ベクトルに基づいて，さまざまな要因からアイデンティティシステムのパフォーマンスに関する情報を収集する．この情報は，選択した保証レベルと制御が，ミッション，ビジネス，およびセキュリティのニーズを満たしているかどうかを判断し，発生した可能性のある意図しない損害を監視するために使用される．本ステップの結果は，パフォーマンスメトリクス，評価と是正のための文書化された透明なプロセス，および必要に応じたアイデンティティシステムの継続的な改善である．

> There are 4 steps to the digital identity risk management process:
> 
> 1.	**Conduct Initial Impact Assessment**: In this step, organizations evaluate their user population and assess the impact of a failure of each function in the identity system (i.e., proofing, authentication, and federation) for their protected application or service against a defined set of impact categories. The outcome of this step is a documented set of impact categories and associated impact levels.
> 2.	**Select Initial Assurance Levels**: In this step, the impact categories and impact levels are evaluated to determine the appropriate assurance levels to protect the application. The outcome of this step is an identified initial level for each applicable xAL.  
> 3.	**Tailor and Document Assurance Level Determinations**: In this step, detailed privacy, equity, usability, and threat assessments are conducted to determine the potential impact of the initially selected assurance level on the specific user population and threat environment of the application. The initial assurance level is tailored, compensating or supplemental controls are identified, and all decisions are documented. The outcome is a Digital Identity Acceptance Statement (see [Sec. 5.3.4](sec5_DIRM.md#IDacceptStmt)) with a defined implementable assurance level.
> 4.	**Continuously Evaluate & Improve**: In this step, information is collected on performance of the identity system across a diverse set of factors based on organization needs and evolving threat vectors. This information is used to determine if the selected assurance level and controls are meeting mission, business, and security needs and to monitor for unintended harms that may have emerged. The outcomes of this step are performance metrics, documented and transparent processes for evaluation and redress, and ongoing improvements to the identity system as needed.

「段階的な」アプローチとして提示されているが，最初のタスクの実行とタスクの再検討の間の反復サイクルの必要性など，一連の順序からの分岐が必要なプロセスの多くのポイントが存在する可能性がある．たとえば，評価の進行中に新しい規制や要件が導入された場合，組織はプロセスのステップを再検討する必要がある場合がある．さらに，新しい機能，データ使用の変更，および脅威環境の変更により，組織はいつでもデジタルアイデンティティリスク管理プロセスの手順を再検討する必要がある．

> While presented as a “stepwise” approach, there can be many points in the process that require divergence from the sequential order, including the need for iterative cycles between initial task execution and revisiting tasks. For example, the introduction of new regulations or requirements while an assessment is ongoing may require organizations to revisit a step in the process. Additionally new functionality, changes in data usage, and changes to the threat environment may at any point require an organization to revisit steps in the digital identity risk management process.

組織は，組織のプロセス，ガバナンス，および企業のリスク管理慣行との統合を満たすために，この全体的なアプローチを適応および修正する**必要がある**．少なくとも，組織は，運用アプローチや有効化ツールに関係なく，各ステップが実行され，各ステップの規範的な義務と結果が完了し，文書化されていることを確認し**なければならない(SHOULD)**．

> Organizations **SHOULD** adapt and modify this overall approach to meet organizational processes, governance, and integration with enterprise risk management practices. At a minimum, organizations **SHALL** ensure that each step is executed and the normative mandates and outcomes of each step are completed and documented regardless of operational approach and enabling tools.


## 初期影響評価の実施 (Conduct Initial Impact Assessment) {#intlAssess}

初期影響分析の目的は，RP アプリケーションまたはサービスに固有の身元確認，当人認証，およびフェデレーションにおける障害の潜在的な悪影響を特定し，保証レベルの初期セットを生み出すことである．これらの領域を個別に評価することで，組織はミッションの目的を達成するのに最適なデジタルアイデンティティサービスを開発または取得する際に最大限の柔軟性を得ることができる．

> The purpose of the initial impact analysis is to identify the potential adverse impacts of failures in identity proofing, authentication, and federation specific to an RP application or service, yielding an initial set of assurance levels. Assessing these areas separately allows organizations maximum flexibility in developing or acquiring a digital identity service that best enables them to successfully deliver on mission objectives.

影響評価には以下が含まる．

- 影響を受けるエンティティの特定
- 害が評価される一連の影響カテゴリの特定
- 影響カテゴリごとの潜在的な害の特定
- 障害が発生した場合に，これらの潜在的な害が与える影響のレベルの特定
- 各タイプの障害 (身元確認，当人認証，フェデレーション) の影響と，影響を受けるすべてのエンティティに対する影響レベルの評価

> The impact assessment includes:
> 
> - Identifying impacted entities,
> - Identifying a set of impact categories for which harms will be assessed,
> - Identifying potential harms for each of the impact categories,
> - Identifying the levels of impact those potential harms would inflict should failures occur, and
> - Assessing the impact of each type of failure (proofing, authentication, and federation) and the resulting impact level to all affected entities.

本評価の結果は，考えられる障害の種類ごとに &mdash; 高，中，低 &mdash; で定義された影響レベルである．これは，最初の保証レベル選択への主要な入力として機能する．

> The output of this assessment is a defined impact level &mdash; High, Moderate, or Low &mdash; for each possible type of failure. This serves as the primary input to the initial assurance level selection.

### 影響を受けるエンティティの特定 (Identify Impacted Entities) {#impctEnt}

影響を評価する場合，組織は検討中のアプリケーションまたはトランザクションによって影響を受けるエンティティを決定する必要がある．このガイドラインで前述したように，デジタルアイデンティティシステムの障害がもたらすさまざまなエンティティへの影響を考慮することが不可欠である．特に重要なのは，個人への潜在的な影響が企業への影響と並んで考慮されるようにすることである．

> When assessing impacts, an organization needs to determine the entities that will be impacted by the application or transaction under consideration. As mentioned earlier in this guideline, it is imperative to consider the impact on different entities resulting from a failure of the digital identity system. Of particular importance is ensuring that the potential impacts to individuals are considered alongside those of the enterprise.

したがって，影響評価には，組織自体に加えて，システムまたはアプリケーションを使用する個人を含め**なければならない(SHALL)**．さらに，組織は，ミッションパートナー，コミュニティ，および [[SP800-30]](sec8_references.ja.md#ref-SP800-30) で特定されたものなど，ミッションとビジネスのニーズに基づいて具体的に含める必要がある他のエンティティを特定する**必要がある(SHOULD)**．少なくとも，機関は，影響分析を実施する際に，影響が評価されるすべてのエンティティを文書化し**なければならない(SHALL)**．

> Accordingly, impact assessments **SHALL** include individuals using the system or application in addition to the organization itself. Additionally, organizations **SHOULD** identify other entities, such as mission partners, communities, and those identified in [[SP800-30]](sec8_references.md#ref-SP800-30), that need to be specifically included based on mission and business needs. At a minimum, agencies **SHALL** document all entities to which impacts will be assessed when conducting their impact analysis.

本項目の結果は，影響が評価される検討中のアプリケーションまたはトランザクションの対象となるエンティティのリストである．

> The outcome of this activity is a list of entities subject to the application or transaction under consideration for whom impacts will be assessed.

### 影響のカテゴリと潜在的な害の特定 (Identify Impact Categories and Potential Harms) {#impactCatHarms}

デジタルトランザクションの初期保証レベルは，少なくとも次の各カテゴリの潜在的な影響を評価することによって決定され**なければならない(SHALL)**．

   - 使命の配信への損害
   - 信頼または評判への損害
   - 機密情報の喪失
   - 経済的安定性への損害または喪失
   - 生命の損失，または安全，健康，環境の安定性への損害
   - 法律，規制，and/or 契約上の義務の不遵守

> Initial assurance levels for digital transactions **SHALL** be determined by assessing the potential impact of, at a minimum, each of the following categories:
> 
>   - Damage to mission delivery
>   - Damage to trust or reputation
>   - Loss of sensitive information
>   - Damage to or loss of economic stability
>   - Loss of life or damage to safety, health, or  environmental stability
>   - Noncompliance with laws, regulations, and/or contractual obligations

組織は，その使命に基づいて，必要に応じて追加の影響カテゴリを含める**必要がある(SHOULD)**．各影響カテゴリを文書化し，組織によって評価されたさまざまなアプリケーションに一貫して適用し**なければならない(SHALL)**．

> Organizations **SHOULD** include additional impact categories as appropriate based on their mission. Each impact category **SHALL** be documented and consistently applied across different applications assessed by the organization.

害とは，エンティティが経験するあらゆる悪影響である．それらは，影響カテゴリと，そのアプリケーションに関連付けられた特定のエンティティにどのように適用されるかをより効果的に理解する手段を提供する．機関は，定義された影響カテゴリごとに特定の害を考慮して，影響分析をより適切に通知する**必要がある(SHOULD)**．各カテゴリの危害の識別は，「エンティティの識別」プロセスで識別されたエンティティごとに行われ**なければならない(SHALL)**．

> Harms are any adverse effects that would be experienced by an entity. They provide a means to more effectively understand the impact categories and how they may apply to specific entities associated with that application. Agencies **SHOULD** consider specific harms for each of the defined impact categories to better inform their impact analysis. Identification of harms for each category **SHALL** be done for each of the entities identified during "entity identification" process.

各カテゴリに関連する害の例には，次のものが含まれるが，これらに限定されない．

> Examples of harms associated with each category include, but are not limited to:

使命の配信への損害:

   - 個人への損害には，資格のある政府のサービスまたは特典にアクセスできないことが含まれる．
   - 組織への損害には，計画されたリソースの制約内で，十分な信頼性 and/or 正確性をもって，現在のミッション/ビジネス機能を十分にタイムリーに実行できないこと，または，将来的に組織内でミッション/ビジネス機能を実行できない，または，能力が制限されていることが含まれる．

> Damage to mission delivery:
> 
>   - Harms to individuals may include the inability to access government services or benefits for which they are eligible.
>   - Harms to the organization may include an inability to perform current mission/business functions in a sufficiently timely manner, with sufficient confidence and/or correctness, within planned resource constraints, or an inability, or limited ability, to perform mission/business functions in the future.

信頼または評判への損害:

   - 個人への損害には，なりすましやイメージや評判への損害が含まれる．
   - 組織への損害には，将来の潜在的な信頼関係を含む，信頼関係，イメージ，または評判への損害が含まれる．

> Damage to trust or reputation:
> 
>   - Harms to individuals may include impersonation or damage to image or reputation.
>   - Harms to the organization may include damage to trust relationships, image, or reputation including future, potential trust relationships.

機密情報の喪失:

   - 個人への損害には，PII またはその他の機密情報の喪失が含まれ，経済的安定の喪失，生命の喪失，身体的または精神的傷害，なりすまし，個人情報の盗難，または永続的な不便などの二次的損害をもたらす可能性がある．
   - 組織への損害には，機密情報や管理された非機密情報 (CUI) などの知的財産やその他の情報資産の喪失または劣化が含まれる．

> Loss of sensitive information:
> 
>   - Harms to individuals includes loss of PII or other sensitive information, which may result in secondary harms such as loss of economic stability, loss of life, physical or psychological injury, impersonation, identity theft, or persistent inconvenience.
>   - Harms to the organization may include loss or degradation of intellectual property or other information assets such as classified materials or controlled unclassified information (CUI).

経済的安定性への損害または喪失:
   - 個人への損害には，詐欺やその他の損害，信用の毀損や喪失，実際の雇用または潜在的な雇用，収入源，and/or その他の経済的損失の結果として発生した負債または資産の損失が含まれる．
   - 組織への損害には，詐欺やその他の犯罪行為，資産の損失，価値の下落，または事業の損失に関連して発生した費用が含まれる．

> Damage to or loss of economic stability:
> 
>   - Harms to individuals may include debts incurred or assets lost as a result of fraud or other harm, damage to or loss of credit, actual or potential employment, or sources of income, and/or other financial loss.
>   - Harms to the organization may include costs incurred related to fraud or other criminal activity, loss of assets, devaluation, or loss of business.

生命の損失，または安全，健康，環境の安定性への損害:

   - 個人への損害には，死亡，身体的，精神的，または感情的な幸福への損害または喪失，環境への損害，アクセス可能で手頃な価格の住宅の喪失が含まれる．
   - 組織への損害には，組織の労働力への損害または損失，または組織を運営できなくするか，能力を低下させて運営する危険な状況の影響が含まれる．


> Loss of life or damage to safety, health, or environmental stability:
> 
>   - Harms to individuals may include death, damage to or loss of physical, mental, or emotional well-being, damage to the environment, or loss of accessible, affordable housing.
>   - Harms to the organization may include damage to or loss of the organization's workforce or the impact of unsafe conditions rendering the organization unable to operate or operating at reduced capacity.

法律，規制，and/or 契約上の義務の不遵守:

   - 個人への損害には，地方，州，および連邦の法律，規制，and/or 契約上の義務の違反による，経済的安定，安全，プライバシー，市民的自由，公平性，and/or ユーザビリティへの損害または損失が含まれる．
   - 組織への損害には，適用される法律，規制，契約上の要件，またはその他の拘束力のある合意におけるその他の要件の不遵守による，金銭的費用，制裁，責任などが含まれる．

> Noncompliance with laws, regulations, and/or contractual obligations:
> 
>   - Harms to individuals may include damage to or loss of economic stability, safety, privacy, civil liberties, equity, and/or usability due to violations of local, state, and federal laws, regulations, and/or contractual obligations.
>   - Harms to the organization may include financial costs, sanctions, liability, etc, due to noncompliance with applicable laws, regulations, contractual requirements, or other requirements in other binding agreements.

本項目の結果は，特定されたエンティティへの影響を評価するために使用される影響カテゴリと害のリストである．

> The outcome of this activity will be a list of impact categories and harms which will be used to assess impacts to identified entities.

### 潜在的な影響レベルの特定 (Identify Potential Impact Levels) {#impLvls}

デジタル トランザクションの初期保証レベルは，次の潜在的な影響値のいずれかを使用して，[Sec. 5.1.2](sec5_DIRM.ja.md#impactCatHarms) の各カテゴリにえ障害が及ぼす潜在的な影響を評価することによって決定される:

1. 影響の可能性「低: 限定的な悪影響が予想される
2. 影響の可能性「中」: 深刻な悪影響が予想される
3. 影響の可能性「高」: 重大または壊滅的な悪影響が予想される

> Initial assurance levels for digital transactions are determined by assessing the potential impact a failure would have on each of the categories from [Sec. 5.1.2](sec5_DIRM.md#impactCatHarms) using one of the following potential impact values:
> 
> 1. Low potential impact: could be expected to have a limited adverse effect
> 2. Moderate potential impact: could be expected to have a serious adverse effect
> 3. High potential impact: could be expected to have a severe or catastrophic adverse effect

注記: アイデンティティシステムの障害がカテゴリに測定可能な結果を引き起こさない場合，影響はない．

> Note: If a failure in the identity system causes no measurable consequences for a category, there is no impact.


IAL，AAL，FAL (フェデレーションアイデンティティを受け入れるか提示する場合) の各保証レベルは個別に評価し**なければならない(SHALL)**．理想的には，評価には，組織の使命を成功裏に遂行するために適用される，個人，組織，他の組織，および国への危害など，さまざまな視点が含まれる．各カテゴリの潜在的な影響の例は次のとおり．

> Each assurance level, IAL, AAL, and FAL (if accepting or asserting a federated identity) **SHALL** be evaluated separately. Ideally, any evaluation will include different viewpoints such as harm to individuals, the organization, other organizations, and the nation as applicable to successful delivery of the organization's mission. Examples of potential impacts in each of the categories include:

**使命の配信の損害:**

- **低**: 連邦政府の資金提供を受けたプログラムに参加する個人と，資格があるが参加できない個人との間にわずかな結果の格差が存在するか，組織の運営や資産，または公共の利益に限定的な悪影響が生じる．限定的な悪影響の例としては，組織がその主要な機能を実行できる範囲と期間における任務能力の低下で，有効性が著しく低下すること，または組織の資産または公共の利益に対する軽微な損害が挙げられる．
- **中**: 連邦政府が資金提供するプログラムに参加している個人と，資格はあるが参加できない個人との間で結果の格差が明らかであるか，組織の運営や資産，または公共の利益に深刻な悪影響を及ぼす．深刻な悪影響の例としては，次のようなものがある．組織がその主要な機能を実行できる範囲と期間に及ぶ重大なミッション能力の低下．または，組織の資産または公共の利益に対する重大な損害．
- **高**: 結果の格差はコミュニティ全体で持続しており，連邦政府が資金提供するプログラムへの参加に対する除外，回避，またはその他の障壁の体系的なパターン，または組織の運営や資産，または公共の利益に対する重大または壊滅的な悪影響を示している．重大または壊滅的な影響の例は次のとおり．組織がその主要な機能の 1 つまたは複数を実行できない範囲と期間に及ぶ重大な任務能力の低下または損失．または組織の資産または公共の利益に重大な損害を与える

> **Damage to mission delivery:**
> 
> - **Low**: at worst, slight outcome disparities exist between individuals that participate in federally funded programs and those that are eligible but unable to participate, or a limited adverse effect on organizational operations or assets, or public interests. Examples of limited adverse effects are: mission capability degradation to the extent and duration that the organization is able to perform its primary functions with noticeably reduced effectiveness, or minor damage to organizational assets or public interests.
> - **Moderate**: at worst, outcome disparities are evident between individuals that participate in federally funded programs and those that are eligible but unable to participate, or a serious adverse effect on organizational operations or assets, or public interests. Examples of serious adverse effects are: significant mission capability degradation to the extent and duration that the organization is able to perform its primary functions with significantly reduced effectiveness; or significant damage to organizational assets or public interests.
> - **High**: outcome disparities endure across communities, indicating a systemic pattern of exclusion, avoidance, or other barriers to participation in federally funded programs, or a severe or catastrophic adverse effect on organizational operations or assets, or public interests. Examples of severe or catastrophic effects are: severe mission capability degradation or loss to the extent and duration that the organization is unable to perform one or more of its primary functions; or major damage to organizational assets or public interests.

**信頼と評判の損害:**

- **低**: 限定的で短期的な不便，苦痛，または困惑をあらゆる当事者にもたらす．
- **中**: 深刻な短期的または限られた長期的な不便，苦痛，またはいずれかの当事者の地位または評判への損害．
- **高**: 重大または深刻な長期にわたる不便，苦痛，またはいずれかの当事者の地位または評判への損害．本項目は通常，特に深刻な影響を伴う状況，または多くの人に影響を与える可能性のある状況のために予約されている.

> **Damage to trust and reputation:**
> 
> - **Low**: at worst, limited, short-term inconvenience, distress, or embarrassment to any party.
> - **Moderate**: at worst, serious short-term or limited long-term inconvenience, distress, or damage to the standing or reputation of any party.
> - **High**: severe or serious long-term inconvenience, distress, or damage to the standing or reputation of any party. This is ordinarily reserved for situations with particularly severe effects or which potentially affect many individuals.


**機密情報の喪失:**

- **低**: [[FIPS199]] (sec8_references.ja.md#ref-FIPS199)で定義されているように，個人情報，米国政府の機密情報，または商業上の機密情報が許可されていない第三者に限定的に公開され，機密性が失われるが，わずかな影響が生じる．
- **中程度**: [[FIPS199]] (sec8_references.ja.md#ref-FIPS199)で定義されているように，個人情報，米国政府の機密情報，または商業上の機密情報が許可されていない関係者に公開され，結果として機密性が失われ，中程度の影響が生じる．
- **高**: [[FIPS199]] (sec8_references.ja.md#ref-FIPS199)で定義されているように，個人情報，米国政府の機密情報，または商業上の機密情報が許可されていない関係者に公開され，機密性が失われ，大きな影響が生じる．

> **Loss of sensitive information:**
> 
> - **Low**: at worst, a limited release of personal, U.S. government sensitive, or commercially sensitive information to unauthorized parties resulting in a loss of confidentiality with a low impact as defined in [[FIPS199]](sec8_references.md#ref-FIPS199).
> - **Moderate**: at worst, a release of personal, U.S. government sensitive, or commercially sensitive information to unauthorized parties resulting in loss of confidentiality with a moderate impact as defined in [[FIPS199]](sec8_references.md#ref-FIPS199).
> - **High**: a release of personal, U.S. government sensitive, or commercially sensitive information to unauthorized parties resulting in loss of confidentiality with a high impact as defined in [[FIPS199]](sec8_references.md#ref-FIPS199).

**経済的安定性への損害または喪失:**

- **低**: いずれかの当事者にとってささいで，取るに足らない経済的損失．
- **中**: あらゆる当事者にとって深刻な経済的損失．
- **高**: いずれかの関係者に対する重大または壊滅的な経済的損失．

> **Damage to or loss of economic stability:**
> 
> - **Low**: at worst, an insignificant or inconsequential financial loss to any party.
> - **Moderate**: at worst, a serious financial loss to any party.
> - **High**: severe or catastrophic financial loss to any party.

**人命の損失，または安全，健康，環境の安定性への損害:**

- **低**: 軽傷または自然に解決し，メンタルヘルスを含む医療や治療を必要としない急性の健康問題．プログラムの運営が行われる地域における環境への影響の限られたリスク．長期的な不便，苦痛，またはいずれかの関係者の地位または評判への損害．
- **高**: 重大または深刻な長期にわたる不便，苦痛，またはいずれかの当事者の地位または評判への損害．本項目は通常，特に深刻な影響を伴う状況，または多くの人に影響を与える可能性のある状況のために予約されている.

> **Loss of life or damage to safety, health, or environmental stability:**
> 
> - **Low**: at worst, minor injury or acute health issue that resolves itself and does not require medical, including mental health, treatment; limited risk of environmental impact in locality where program operations take place.ong-term inconvenience, distress, or damage to the standing or reputation of any party.
> - **High**: severe or serious long-term inconvenience, distress, or damage to the standing or reputation of any party. This is ordinarily reserved for situations with particularly severe effects or which potentially affect many individuals.

**法律，規制，and/or 契約上の義務の不遵守:**

- **低**: 通常は取り締まりの対象とならない性質の民事または刑事上の違反のリスク，または，ささいで取るに足らない組織の責任のリスク．
- **中程度**: 執行措置の対象となる可能性のある民事または刑事上の違反のリスク，または重大な組織の責任のリスク．
- **高**: 法執行プログラムにとって特に重要な民事または刑事上の違反，または重大または壊滅的な組織責任のリスク．

> **Noncompliance with laws, regulations, and/or contractual obligations:**
> 
> - **Low**: at worst, a risk of civil or criminal violations of a nature that would not ordinarily be subject to enforcement efforts, or at worst, an insignificant or inconsequential organization liability.
> - **Moderate**: at worst, a risk of civil or criminal violations that may be subject to enforcement efforts, or a serious organization liability.
> - **High**: a risk of civil or criminal violations that are of special importance to enforcement programs, or severe or catastrophic organization liability.

### 影響分析 (Impact Analysis) {#impAnalysis}

影響分析は，身元確認，当人認証，フェデレーションのプロセスによってどの程度リスクを軽減する必要があるかを判断するのに役立る．これらの決定は，リスク決定を推進する特定の技術に対する欲求ではなく，適用可能な技術と緩和戦略の関連する選択を推進する．

> The impact analysis helps determine the extent to which risk must be mitigated by the identity proofing, authentication, and federation processes. These determinations drive the relevant choices of applicable technologies and mitigation strategies, rather than the desire for any given technology driving risk determinations.

ユーザーが主張するアイデンティティの適切な保証レベルを決定するために，組織は潜在的なリスクを評価し，その影響を最小限に抑えるための対策を特定し**なければならない(SHALL)**．組織は，身元証明，当人認証，フェデレーションの失敗のリスクを個別に評価して，各トランザクションに必要な保証レベルを決定し**なければならない(SHALL)**．このプロセスには，[Sec. 5.1.1](sec5_DIRM.md#impctEnt) で説明されているように，デジタルアイデンティティシステムによって影響を受けるさまざまなエンティティへの潜在的にさまざまな危害の影響を考慮し**なければならない(SHALL)**．ビジネスプロセス，ポリシー，およびテクノロジは，リスクの軽減に役立つ場合がある．エンティティは，身元確認，当人認証，フェデレーションに関連する特定のモードの障害の影響を考慮する**必要がある(SHOULD)**．これには以下が含まれるが，これらに限定されない．

> To determine the appropriate level of assurance of the user's asserted identity, organizations **SHALL** assess the potential risks and identify measures to minimize their impact. Organizations **SHALL** assess the risk of identity proofing, authentication, and federation failures separately to determine the required assurance level for each transaction. This process **SHALL** include consideration of potentially varying impacts of harms to different entities impacted by the digital identity system, as described in [Sec. 5.1.1](sec5_DIRM.md#impctEnt). Business processes, policies, and technologies may help reduce risk. Entities **SHOULD** consider the impact of specific modes of failures related to identity proofing, authentication, and federation this includes, but may not be limited to:  

**身元確認:**

- 間違った主体にサービスを提供することの影響 (たとえば，攻撃者が別の人物として証明に成功するなど)．
- 身元確認のプロセス全体で主体が直面する，偏見を含む障壁のために，資格のある主体にサービスを提供しないことの影響．
- 身元確認プロセスをサポートするための過剰な情報の収集と保持の影響．

> **Identity Proofing:**
> 
> - The impact of providing a service to the wrong subject (e.g., an attacker successfully proofs as someone else).
> - The impact of not providing service to an eligible subject due to barriers, including biases, faced by the subject throughout the process of identity proofing.
> - The impact of excessive information collection and retention to support identity proofing processes.

**当人認証:**

- 間違った主体を認証することの影響 (たとえば，オーセンティケーターを侵害または盗む攻撃者)．
- 主体がオーセンティケータを提示する際に直面する，偏見を含む障壁のために，正しい主体を認証できなかった場合の影響．

> **Authentication:**
> 
> - The impact of authenticating the wrong subject (e.g., an attacker who compromises or steals an authenticator).
> - The impact of failing to authenticate the correct subject due to barriers, including biases, faced by the subject in presenting their authenticator.  

**フェデレーション：**

- 間違った主体がアプリケーション，システム，またはデータに正常にアクセスした場合の影響 (たとえば，アサーションの侵害またはリプレイ)．
- 加入者(subscriber)属性を間違ったアプリケーションまたはシステムにリリースすることの影響．

> **Federation:**
> 
> - The impact of the wrong subject successfully accessing an application, system, or data (e.g., compromising or replaying an assertion).
> - The impact of releasing subscriber attributes to the wrong application or system.

[表1](sec5_DIRM.ja.md#table-1) のようなワークシートを使用すると，組織が分析を完了するために収集した情報を編集するのに役立つ．この種の分析は，身元確認，当人認証，フェデレーションの潜在的な障害の種類ごとに行われ，デジタルアイデンティティシステムとやり取りするエンティティに対する全体的なリスクを判断する．

> Using a worksheet similar to [Table 1](sec5_DIRM.md#table-1) can assist organizations with compiling the information gathered in order to complete the analysis. This kind of analysis would be done for each type of potential failure for identity proofing, authentication, and federation to determine the overall risks to entities interacting with the digital identity system.

[表1 影響カテゴリー](sec5_DIRM.ja.md#table-1){:name="table-1"}
{:latex-ignore="true"}

| 影響カテゴリー | 個人への害 | 組織への害 | (その他の害のカテゴリー) | 総合影響レベル |
| :--- | :----: | :----: | :----: | :----: |
| 使命の配信の損害 | L / M / H | L / M / H | L / M / H |   |
| 信頼や評判の損害 | L / M / H | L / M / H | L / M / H |   |
| 機密情報の喪失 | L / M / H | L / M / H | L / M / H |   |
| 経済的安定性への損害または喪失 | L / M / H | L / M / H | L / M / H |   |
| 人命の損失，または安全，健康，環境の安定性への損害 | L / M / H | L / M / H | L / M / H |   |
| 法律，規制，and/or 契約上の義務の不遵守: | L / M / H | L / M / H | L / M / H |   |
{:latex-table="1" latex-caption="影響カテゴリー" latex-columns="p@0.20\textwidth,p@0.15\textwidth,p@0.15\textwidth,p@0.15\textwidth,p@0.15\textwidth"}

> | Impact Categories | Harm to Individuals | Harm to the Organization | (Other harm categories) | Combined Impact Level |
> | :--- | :----: | :----: | :----: | :----: |
> | Damage to mission delivery | L / M / H | L / M / H | L / M / H |   |
> | Damage to trust or reputation | L / M / H | L / M / H | L / M / H |   |
> | Loss of sensitive information | L / M / H | L / M / H | L / M / H |   |
> | Damage to or loss of economic stability | L / M / H | L / M / H | L / M / H |   |
> | Loss of life or damage to safety, health, or environmental stability | L / M / H | L / M / H | L / M / H |   |
> | Noncompliance with laws, regulations, and/or contractual obligations | L / M / H | L / M / H | L / M / H |   |
> {:latex-table="1" latex-caption="Impact Categories" latex-columns="p@0.20\textwidth,p@0.15\textwidth,p@0.15\textwidth,p@0.15\textwidth,p@0.15\textwidth"}

本ステップの出力は，身元確認，当人認証，およびフェデレーションの失敗に対する定義済みの影響レベルであり，最初の保証レベル選択への主要な入力として機能する．

> The output of this step is a defined impact level for failures of identity proofing, authentication, and federation which serve as the primary input to the initial assurance level selection.

## 初期保証レベルの選択 (Select Initial Assurance Levels)

影響分析は，身元確認，当人認証，フェデレーションの初期保証レベルを選択するプロセスへの主要なインプットとして機能する．保証レベルは，各領域における障害の潜在的な影響の分析に基づいて，これらの領域間で異なる場合がある．これらの初期保証レベルの目的は，使命の必要性，サイバーセキュリティリスク，およびデジタルアイデンティティシステムの組織とユーザーに対するその他の潜在的な影響に基づいて評価および調整される [[SP800-63A]](../_sp800-63a/sec1_purpose.md#purpose){:latex-href="#ref-SP-800-63A"}, [[SP800-63B]](../_sp800-63b/sec1_purpose.md#purpose){:latex-href="#ref-SP-800-63B"}, and [[SP800-63C]](../_sp800-63c/sec1_purpose.md#purpose){:latex-href="#ref-SP-800-63C"} の付属の巻の要件とガイドラインに反映されている，ベースラインのデジタルアイデンティティ制御とプロセスを特定することである．

> The impact analysis serves as a primary input to the process of selecting initial assurance levels for identity proofing, authentication and federation. The assurance levels may differ across these areas based on the analysis of the potential impact of failures in each area. The purpose of these initial assurance levels is to identify baseline digital identity controls and processes, reflected in the requirements and guidelines in the companion volumes of [[SP800-63A]](../_sp800-63a/sec1_purpose.md#purpose){:latex-href="#ref-SP-800-63A"}, [[SP800-63B]](../_sp800-63b/sec1_purpose.md#purpose){:latex-href="#ref-SP-800-63B"}, and [[SP800-63C]](../_sp800-63c/sec1_purpose.md#purpose){:latex-href="#ref-SP-800-63C"}, which will be assessed and tailored based on mission need, cybersecurity risk, and other potential impacts to the organization and users of the digital identity systems.

### 保証レベル (Assurance Levels)
組織の RP は，サイバーセキュリティのリスクと使命のニーズに基づいて，次の個々の初期保証レベルを選択し**なければならない(SHALL)**．

* **IAL**: 個人の身元を自信を持って判断するための身元確認プロセスの堅牢性．IAL は，潜在的な身元確認の失敗を軽減するために選択される．
* **AAL**: 当人認証プロセス自体の堅牢性，およびオーセンティケーターと特定の個人の識別子の間のバインディング．AAL は，潜在的な当人認証の失敗を軽減するために選択される．
* **FAL**: 認証および属性情報 (該当する場合) を IdP から RP に通信するために使用されるフェデレーションプロセスの堅牢性．すべてのデジタルシステムがフェデレーションアイデンティティアーキテクチャを利用するわけではないため，FAL はオプションである．FAL は，潜在的なフェデレーションの障害を軽減するために選択される．

> An organization RP **SHALL** select, based on cybersecurity risk and mission needs, the following individual initial assurance levels:
> 
> * **IAL**: The robustness of the identity proofing process to confidently determine the identity of an individual. IAL is selected to mitigate potential identity proofing failures.
> * **AAL**: The robustness of the authentication process itself, and the binding between an authenticator and a specific individual's identifier. AAL is selected to mitigate potential authentication failures.
> * **FAL**: The robustness of the federation process used to communicate authentication and attribute information (if applicable) to an RP from an IdP. FAL is optional as not all digital systems will leverage federated identity architectures. FAL is selected to mitigate potential federation failures.

### xALの詳細 (xAL Descriptions)

アイデンティティ，オーセンティケータ，およびフェデレーションの各保証レベルの概要を以下に示す．

> A summary of each of the identity, authenticator, and federation assurance levels is provided below.

本ガイドラインでは，一般的に記述されているかまとめられている場合，IAL，AAL，FAL を **_xAL_** と呼ぶ．

> When described generically or bundled, these guidelines will refer to IAL, AAL, and FAL as **_xAL_**.

#### 身元確認保証レベル (Identity Assurance Level)

**IAL1**:
IAL1 は，権威のある情報源(authoritative source) または信頼できる情報源(credible souece) に対する識別属性の検証，および申請者(applicant)の主張する身元を検証するための基本的なプロセスの使用を必要とする．

> **IAL1**:
> IAL1 requires validation of identifying attributes against authoritative or credible sources and use of basic processes to verify the claimed identity of the applicant.

**IAL2**:
IAL2 では，特定の属性が強力な証拠によって裏付けられ，権威のある情報源(authoritative source) または信頼できる情報源(credible souece) に照らして検証され，プロセスを使用して申請者(applicant)の主張する身元を検証する必要がある．

> **IAL2**:
> IAL2 requires identifying attributes to be supported by strong evidence and validated against authoritative or credible sources and use of processes to verify the claimed identity of the applicant.

**IAL3**:
IAL3 では，CSP 担当者とのインタラクティブなプロセスを使用して，物理的な文書を検査することにより，認定された CSP 担当者が識別属性を検証する必要がある．

> **IAL3**:
> IAL3 requires identifying attributes to be verified by an authorized CSP representative through examination of physical documentation using an interactive process with a CSP representative.

#### 当人認証保証レベル (Authentication Assurance Level)

**AAL1**:
AAL1 は，申請者(applicant)が加入者(subscriber)に登録されたオーセンティケーターを制御するという保証を提供する．AAL1 では，利用可能なさまざまな認証技術を使用した単一要素認証が必要である．認証を成功させるには，主張者(ckaimant)が安全な認証プロトコルを介してオーセンティケーターの所有と管理を証明する必要がある．

> **AAL1**:
AAL1 provides some assurance that the claimant controls an authenticator registered to the subscriber. AAL1 requires single-factor authentication using a wide range of available authentication technologies. Successful authentication requires that the claimant prove possession and control of the authenticator through a secure authentication protocol.

**AAL2**:
AAL2 は，申請者(applicant)が加入者(subscriber)に登録されたオーセンティケーターを制御するという高い信頼性を提供する．安全な認証プロトコルを通じて，2つの異なる認証要素の所有と管理の証明が必要である．AAL2 以上では，承認された暗号技術が必要である．

> **AAL2**:
AAL2 provides high confidence that the claimant controls authenticator registered to the subscriber. Proof of possession and control of two different authentication factors is required through a secure authentication protocol. Approved cryptographic techniques are required at AAL2 and above.

**AAL3**:
AAL3 は，申請者(applicant)が加入者(subscriber)に登録されたオーセンティケーターを制御するという非常に高い信頼性を提供する．AAL3 での認証は，フィッシング攻撃に抵抗できる暗号化認証プロトコルによる鍵の所有証明に基づいている．

> **AAL3**:
AAL3 provides very high confidence that the claimant controls authenticator registered to the subscriber. Authentication at AAL3 is based on proof of possession of a key through a cryptographic authentication protocol capable of resisting phishing attacks.

#### フェデレーション保証レベル (Federation Assurance Level)

**FAL1**:
FAL1 を使用すると，加入者(subscriber)は IdP からのアサーションを使用して RP にログインできる．このアサーションは，RP によって，IdP から送信され，特定の RP を対象としていることが検証される．アサーションは，攻撃者による変更または構築から保護されている．IdP と RP の間の信頼の合意(trust agreement)と登録は，動的に発生する可能性がある．

> **FAL1**:
FAL1 allows for the subscriber to log into the RP using an assertion from the IdP that can be verified by the RP as coming from the IdP and targeted for a specific RP. The assertion is protected from modification or construction by an attacker. The trust agreement and registration between the IdP and RP can happen dynamically.

**FAL2**:
FAL2 では，アサーションが RP でのインジェクションに対して堅牢であるという要件が追加されている．これに対応する手段の1つは，アサーションをブラウザーなどの仲介者を介して渡すのではなく，IdP から RP に直接提示することである．IdP と RP 間の信頼の合意(trust agreement)は動的に発生することはないが，特定の IdP と RP の動的登録は実行時に発生する可能性がある．

> **FAL2**:
FAL2 adds the requirement that the assertion be robust against injection at the RP. One means of this is to have the assertion presented directly to the RP from the IdP instead of passing through an intermediary like a browser. The trust agreement between the IdP and RP cannot happen dynamically, but dynamic registration of the specific IdP and RP can occur at runtime.

**FAL3**:
FAL3 は，加入者(subscriber)が認証アサーションの提示と共に，バインドされたオーセンティケーターを使用して RP に直接認証するという要件を追加する．この追加のオーセンティケーターの存在により，RP にアクセスする当事者がアサーションで識別された当事者であるという非常に高い保証が RP に提供される．信頼の合意(trust agreement)と登録を動的にすることはできない．

> **FAL3**:
FAL3 adds the requirement that the subscriber authenticate directly to the RP using a bound authenticator along with presenting the authentication assertion. The presence of this additional authenticator provides a very high assurance to the RP that the party accessing the RP is the party identified in the assertion. The trust agreement and registration cannot be dynamic.

### 初期保証レベルの選択 (Initial Assurance Level Selection)

身元確認，当人認証，およびフェデレーションプロセスにおける障害の潜在的な影響の特定と評価は，組織のデジタルアイデンティティリスク管理プロセスと，それらの領域の保証レベルの初期選択に役立る．これらの最初の選択は，主にサイバーセキュリティリスクに基づくが，使命のニーズや，組織，ユーザー，およびミッションパートナーに対するその他の潜在的な影響に基づいて調整される．

> The identification and assessment of the potential impacts of failures in identity proofing, authentication, and federation processes informs the organization's digital identity risk management process and the initial selection of assurance levels for those areas. These initial selections are primarily based on cybersecurity risk, but will be tailored, based on mission needs and other potential impacts to the organization, users, and mission partners.

組織は，デジタルアイデンティティの障害の潜在的な影響に基づいて初期保証レベルを選択するためのプロセスとガバナンスモデルを開発し，文書化し**なければならない(SHALL)**．本セクションでは，そのプロセスに含める主要な要素に関するガイダンスを提供する．

> Organizations **SHALL** develop and document a process and governance model for selecting initial assurance levels based on the potential impact of digital identity failures. This section provides guidance on the major elements to include in that process.

#### 初期IALの選択 (Selecting Initial IAL) {#IAL_CYOA}

IAL は，申請者(applicant)が主張した現実の身元を保持しているという保証のレベルを反映している．組織は，リスクベースのアプローチを使用して，RP アプリケーションに最も適切な身元確認要件を選択し**なければならない(SHALL)**．[Sec. 5.3.1](sec5_DIRM.ja.md#impLvls) で説明されている影響分析は，最初の IAL の選択に役立つ．この最初の選択は，[Sec. 5.3](sec5_DIRM.ja.md#tailor)で説明されているように，最終的な IAL を決定する前に，使命のニーズ，リスク許容度，およびプライバシー，公平性，およびユーザビリティへの潜在的な影響に基づいて調整され**なければならない(SHALL)**．

> The IAL reflects the level of assurance that an applicant holds the claimed real-life identity.  Organizations **SHALL** use a risk-based approach to select the most appropriate identity proofing requirements for their RP application. The impact analysis described in [Sec. 5.3.1](sec5_DIRM.md#impLvls) informs the selection of the initial IAL selection.  This initial selection **SHALL** be tailored, as described in [Sec. 5.3](sec5_DIRM.md#tailor), based on mission needs, risk tolerance, and potential impacts to privacy, equity, and usability, before making a final IAL determination.

身元確認は CSP の機能であるため，IAL の選択は，RP アプリケーションの所有者が自分で証明を実行する必要があるという意味ではない．

> The IAL selection does not mean the RP application owner will need to perform the proofing themselves since identity proofing is the function of the CSP.

すべての RP アプリケーションで身元確認が必要になるわけではない．RP アプリケーションがデジタルトランザクションを実行するために個人情報を必要としない場合，システムは RP アプリケーションのユーザーの身元確認なしで動作できる．個人情報が必要な場合，RP は，検証済みおよび検証済みの属性が必要かどうか，または自己提示属性が許容されるかどうかを判断する必要がある．自己提示された属性を受け入れることによる潜在的な害がわずかである場合，システムはユーザーの身元確認なしで動作することもできる．そのような場合，[[SP800-63A]](../_sp800-63a/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63A"} で説明されている身元確認プロセスはシステムに適用されない．

> Not all RP applications will require identity proofing. If the RP application does not require any personal information to execute any digital transactions, the system can operate without identity proofing users of the RP application. If personal information is needed, the RP needs to determine if validated and verified attributes are required or if self-asserted attributes are acceptable. If there are insignificant potential harms from accepting self-asserted attributes, the system may also be able to operate without identity proofing users. In such cases, the identity proofing processes described in [[SP800-63A]](../_sp800-63a/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63A"} are not applicable to the system.

身元確認が必要であると組織が判断した場合，最初の IAL は，身元確認の失敗の潜在的な影響に基づいて評価され**なければならない(SHALL)**．[Sec. 5.1](sec5_DIRM.ja.md#intlAssess)で説明されているように，RP アプリケーションの使用または操作によって生じる損害について，組織，個人，他の組織，および国家の観点から潜在的な影響を考慮し**なければならない(SHALL)**．組織が悪影響を受けることはないかもしれないが，サービスプロバイダーのビジネス慣行によってプライバシーやその他の権利が侵害された個人と同様に，ユーザーは重大な損害を受ける可能性がある． 組織は，RP アプリケーションの全体的な影響レベルを特定する際に最悪のケースを考慮する**必要がある(SHOULD)**が，異なる影響がある場合は，リスク管理プロセスを使用して最初の選択を調整することができる．

> If an organization determines that identity proofing is necessary, the initial IAL **SHALL** be assessed based on the potential impacts of identity proofing failures.  As described in [Sec. 5.1](sec5_DIRM.md#intlAssess), potential impacts **SHALL** be considered from the perspective of the organization, individuals, other organizations, and the nation, for harms incurred through the use or operation of the RP application. While the organization may not be negatively impacted, the user could be significantly harmed, as could individuals whose privacy or other rights have been violated by the business practices of a service provider. Organizations **SHOULD** consider the worst-case when identifying the overall impact level of the RP application, but may use risk management processes to tailor their initial selection when there are differing impacts.

RP アプリケーションの全体的な影響レベルを評価する場合，組織は使命の提供への影響を他の影響カテゴリとは別に考慮し**なければならない(SHALL)**．組織は，使命の遂行に害を及ぼす可能性のある身元確認プロセスの潜在的な失敗を評価して，より厳密な身元確認プロセスの実装によって関連する影響が軽減または悪化するかどうかを判断する必要がある．そのため，組織は，RP アプリケーションの全体的な影響レベルを最初に特定するときに，使命の配信のカテゴリを除外**してもよい(MAY)**．これは，これらの影響を調整プロセスで考慮する必要があるためである．

> When assessing the overall impact level of the RP application, the organization **SHOULD** consider impacts to mission delivery separately from other impact categories. Potential failures in the identity proofing process that could lead to harms in mission delivery should be assessed by the organization to determine if the associated impacts would be mitigated or exacerbated by the implementation of more rigorous identity proofing processes. As such, the organization **MAY** exclude the mission delivery category when initially identifying the overall impact level of the RP application, as these impacts will need to be considered in the tailoring process.

組織によって評価された全体的な影響レベルは，さらなる調整が行われる可能性がある IAL の予備的な選択につながる:

- 影響「低」: IAL1
- 影響「中」: IAL2
- 影響「高」: IAL3

> The overall impact level assessed by the organization leads to a preliminary selection of the IAL from which further tailoring may be done:
> 
> - Low impact: IAL1
> - Moderate impact: IAL2
> - High impact: IAL3

予備的な選択では，身元確認プロセスでの失敗の潜在的な影響は，より高い保証プロセスによって軽減されるべきであると想定している．これはよくあることだが，組織は，影響分析の一部として特定された特定の障害，影響カテゴリ，および影響を受けるエンティティを考慮して，追加の調整が必要かどうかを判断する必要がある．たとえば，正当な申請者(applicant)の登録に失敗すると，過度の損害が発生する可能性がある場合，組織は，保証の低い身元確認プロセスが適切かどうかを評価する必要がある．

> The preliminary selection assumes that higher potential impacts of failures in the identity proofing process should be mitigated by higher assurance processes. While this is often the case, organizations should consider the specific failures, impact categories, and impacted entities identified as part of the impact analysis to determine if additional tailoring is warranted. For example, if a failure to enroll a legitimate applicant could lead to excessive harm, organizations should assess whether lower-assurance identity proofing processes would be appropriate.

追加の調整を含むこのプロセスの結果は，[Sec. 5.3](sec5_DIRM.ja.md#tailor) で説明されている追加の潜在的な影響に対して評価される IAL の初期評価である．

> The result of this process, including any additional tailoring, is the initial assessment of the IAL, which will be assessed against additional potential impacts as described in [Sec. 5.3](sec5_DIRM.md#tailor).

#### Selecting Initial AAL {#AAL_CYOA}
The AAL reflects the level of assurance from the authentication process that the claimant is who they claim to be. Organizations **SHALL** use a risk-based approach to select the most appropriate authentication requirements for their RP application. The impact analysis described in [Sec. 5.1.3](sec5_DIRM.md#impLvls) informs the selection of the initial AAL selection.  This initial selection **SHALL** be tailored, as described in [Sec. 5.3](sec5_DIRM.md#tailor), based on mission needs, risk tolerance, and potential impacts to privacy, equity, and usability, before making a final AAL determination.

The AAL selection does not mean the RP application owner will need to issue authenticators themselves.

The initial AAL **SHALL** be assessed based on the potential impacts of authentication failures. As described in [Sec. 5.1](sec5_DIRM.md#intlAssess), potential impacts **SHALL** be considered from the perspective of the organization, individuals, other organizations, and the nation, for harms incurred through the use or operation of the RP application, as the level of harm from a failure could vary significantly across these entities. Organizations **SHOULD** consider the worst-case when identifying the overall impact level of the RP application, but may use risk management processes to tailor their initial selection when there are differing impacts.

When assessing the overall impact level of the RP application, the organization **SHOULD** consider impacts to mission delivery separately from other impact categories. Potential failures in the authentication process that could lead to harms in mission delivery should be assessed by the organization to determine if the associated impacts would be mitigated or exacerbated by the implementation of more rigorous authentication controls. As such, the organization **MAY** exclude the mission delivery category when initially identifying the overall impact level of the RP application, as these impacts will need to be considered in the tailoring process.

The overall impact level assessed by the organization leads to a preliminary selection of the AAL from which further tailoring may be done:

- Low impact: AAL1
- Moderate impact: AAL2
- High impact: AAL3

The preliminary selection assumes that higher potential impacts of failures in the authentication process should be mitigated by higher assurance processes. While this is often the case, organizations should consider the specific failures, impact categories, and impacted entities identified as part of the impact analysis to determine if additional tailoring is warranted. Further, organizations should consider legal, regulatory, or policy requirements that govern digital services. For example, the terms of [[EO13681]](sec8_references.md#ref-EO13681) requiring "that all organizations making personal data accessible to citizens through digital applications require the use of multiple factors of authentication," which would drive the selection of AAL2 or AAL3.

The result of this process, including any additional tailoring, is the initial assessment of the AAL, which will be as assessed against additional potential impacts as described in [Sec. 5.3](sec5_DIRM.md#tailor).

#### Selecting Initial FAL {#FAL_CYOA}
The FAL reflects the level of assurance in identity assertions that convey the results of authentication processes and relevant identity information to RP systems. Organizations **SHALL** use a risk-based approach to select the most appropriate federation requirements for their RP application. The impact analysis described in [Sec. 5.3.1](sec5_DIRM.md#impLvls) informs the selection of the initial FAL selection.  This initial selection **SHALL** be tailored, as described in [Sec. 5.3](sec5_DIRM.md#tailor), based on mission needs, risk tolerance, and potential impacts to privacy, equity, and usability, before making a final FAL determination.

The initial FAL **SHALL** be assessed based on the potential impacts of failures in the presentation or acceptance of assertions in federated identity architectures. Examples of compromise include use of assertion replay to impersonate a valid user or leakage of assertion information through the browser. As described in [Sec. 5.1](sec5_DIRM.md#intlAssess), potential impacts **SHALL** be considered from the perspective of the organization, individuals, other organizations, and the nation, for harms incurred through the use or operation of the RP application, as the level of harm from a failure could vary significantly across these entities. Organizations **SHOULD** consider the worst-case when identifying the overall impact level of the RP application, but may use risk management processes to tailor their initial selection when there are differing impacts.

When assessing the overall impact level of the RP application, the organization **SHOULD** consider impacts to mission delivery separately from other impact categories. Potential failures in federated architectures that could lead to harms in mission delivery **MAY** be assessed by the organization to determine if the associated impacts would be mitigated or exacerbated by the implementation of more rigorous controls by identity providers. As such, the organization may exclude the mission delivery impact category when initially identifying the overall impact level of the RP application, as these impacts will need to be considered in the tailoring process.

The overall impact level assessed by the organization leads to a preliminary selection of the FAL from which further tailoring may be done:

- Low impact: FAL1
- Moderate impact: FAL2
- High impact: FAL3

The preliminary selection assumes that higher potential impacts of failures in federated identity architectures should be mitigated by higher assurance processes. While this is often the case, organizations should consider the specific failures, impact categories, and impacted entities identified as part of the impact analysis to determine if additional tailoring is warranted.

The result of this process, including any additional tailoring, is the initial assessment of the FAL, which will be as assessed against additional potential impacts as described in [Sec. 5.3](sec5_DIRM.md#tailor).

## Tailor and Document Assurance Levels {#tailor}

Tailoring provides a process to modify an initially assessed assurance level or implement compensating controls based on ongoing detailed impact and risk assessments. Organizations **SHOULD** implement the assessed assurance level as defined in these guidelines. However, these guidelines provide flexibility to allow for organizations to meet specific mission needs and address unique risk appetites and considerations. Therefore, organizations **SHALL** establish and document an xAL tailoring process. At a minimum this process:

1. **SHALL** include a structured governance approach to allow for decision-making and conflict resolution.
2. **SHALL** document all decisions in the tailoring process, including the assessed xALs, modified xALs, and compensating controls in the Digital Identity Acceptance Statement (see [Sec. 5.3.4](sec5_DIRM.md#IDacceptStmt)).
3. **SHALL** justify and document all risk-based decisions or modifications to the initially assessed xALs in the Digital Identity Acceptance Statement (see [Sec. 5.3.4](sec5_DIRM.md#IDacceptStmt)).
4. **SHOULD** establish a cross-functional capability to support subject matter analysis of xAL selection impacts in the tailoring process.
5. **SHOULD** be a continuous process that incorporates real world operational data to evaluate the impacts of selected xAL controls.

The tailoring process promotes a structured means to balance risks and impacts in the furtherance of protecting systems, data, and services in a manner that enables mission success while supporting equity, privacy, and usability for individuals.

### Assess Privacy, Equity, Usability and Threats

When selecting and tailoring assurance levels for specific applications, it is critical that insights and inputs to the process extend beyond an initial, static impact assessment. When transitioning from an initial assurance level to the final xAL selection and implementation, organizations **SHALL** conduct detailed assessments of the controls defined at the assurance level to determine potential impacts in their operational environment. At a minimum, organizations **SHALL** assess impacts related to the following areas:

- **Privacy** – to determine unintended consequences to the privacy of individuals that will be subject to the controls at an assessed xAL and of individuals affected by organizational or third-party practices related to the establishment, management, or federation of a digital identity.
- **Equity** – to determine whether implementation of controls may create or maintain inequities across demographics or user groups.
- **Usability** – to determine whether implementation of the selected controls will result in challenges to end-user experience.
- **Threat** – to determine whether the defined assurance level will address specific threats based on environment, threat actors, and known tactics, techniques, and procedures (TTPs).

Additionally, organizations **SHOULD** conduct additional business specific assessments as appropriate to fully represent mission and domain specific considerations not captured here. These assessments **SHALL** be extended to any compensating or supplemental controls as defined in [Sec. 5.3.2](sec5_DIRM.md#IDCompCntls) and [Sec. 5.3.3](sec5_DIRM.md#IDSupCntrls).


### Identify Compensating Controls {#IDCompCntls}

A compensating control is a management, operational, or technical control employed by an organization in lieu of a recommended control in the defined xALs. They are intended, to the greatest degree possible, to address the same risks as the baseline control is intended to address.

Organizations **SHOULD** implement their identity services per the requirements in these guidelines for their tailored assurance level. However, where organizations are unable to implement a specific control associated with their baseline or tailored assurance level, they **MAY** select to implement a compensating control. This control **MAY** be a modification to a digital identity process as defined in these guidelines, but **MAY** also be applied elsewhere in an application, transaction, or service lifecycle. For example:

-	A federal agency could choose to use a federal background investigation and checks, as referenced by  _Personal Identity Verification_ [[FIPS201]](sec8_references.md#ref-FIPS201), to compensate for the identity evidence validation with authoritative sources requirement under these guidelines.
-	An organization could choose to implement stricter auditing and transactional review processes on a payment application where verification processes using weaker forms of identity evidence were accepted due to availability of evidence in the end-user population.

Where compensating controls are implemented, organizations **SHALL** demonstrate comparability of a chosen alternative or document residual risk incurred by deviating from normative requirements. Organizations **SHALL** implement procedures to document both the justification for any departure from normative requirements and detail the compensating controls employed. The inclusion of compensating controls does not imply that an organization must tailor to a lower xAL. The process of tailoring allows for agencies and service providers to make risk-based decisions in how they implement their xALs and provides a mechanism for documenting and communicating decisions through the Digital Identity Acceptance Statement described in [Sec. 5.3.4](sec5_DIRM.md#IDSupCntrls).

### Identify Supplemental Controls {#IDSupCntrls}

Supplemental controls are those that may be added, in addition to those specified in the organizations tailored assurance level, in order to address specific threats or attacks. Organizations **SHOULD** identify and implement supplemental controls where they identify threats that may not be addressed in baseline controls. For example:

- An organization could choose to verify an end user against additional pieces of identity evidence, beyond what is required by the assurance level, due to a high prevalence of fraudulent attempts to complete the proofing process.
- An organization could choose to implement risk-scoring analytics, coupled with re-proofing mechanisms, to confirm a user’s identity when their access attempts exhibit certain risk factors.

Where organizations implement supplemental controls, these **SHALL** be assessed for impacts based on the same factors used to tailor the organization’s assurance level.
Supplemental controls **SHALL** be documented.

### Document Results - The Digital Identity Acceptance Statement {#IDacceptStmt}

The Digital Identity Acceptance Statement documents the results of the digital identity risk management process. This includes the Impact Assessment, Initial Assurance Level Selection, and Tailoring process.

The statement **SHALL** include, at a minimum:

1.	Initial Impact Assessment Results
2.	Initially assessed xAL,
3.	Tailored xAL and rationale, if tailored xAL differs from initially assessed xAL,
4.	All compensating controls and their comparability or residual risk associated with compensating controls
5.	All supplemental controls

Federal agencies **SHOULD** include this information in the system authorization package described in [[SP800-37]](sec8_references.md#ref-SP800-37).

## Continuously Evaluate and Improve

Threat actors adapt, user expectations and needs shift, and missions evolve. As such, risk assessments and identity solutions are not to be set and forgotten. To maintain pace with the constantly shifting environment in which they operate, organizations **SHOULD** implement a continuous evaluation and improvement program that leverages input from people interacting with the identity system. These programs **SHOULD** consider feedback from application performance metrics, threat intelligence, fraud analytics, assessments of equity impacts, privacy impact analysis, and user inputs.

## Cyber, Fraud, and Identity Program Integrity

Typically, identity solutions are the front door for a critical business or service function. Accordingly, they should not operate in a vacuum. Close coordination of identity functions with cybersecurity teams, threat intelligence teams, and program integrity teams can enable a more complete protection of business capabilities, while constantly improving identity solution capabilities. For example, payment fraud data collected by program integrity teams could provide indicators of compromised subscriber accounts and potential weaknesses in identity proofing implementations. Similarly, threat intelligence teams may receive indication of new TTPs that may impact identity proofing, authentication, and federation processes. Organizations **SHOULD** establish consistent mechanisms for the exchange of information between critical security and fraud stakeholders.

Where supporting service providers, such as CSPs, are external, this may be complicated, but **SHOULD** be considered in contractual and legal mechanisms. All data collected, transmitted, or shared **SHALL** be minimized and subject to a detailed privacy and legal
assessment.
