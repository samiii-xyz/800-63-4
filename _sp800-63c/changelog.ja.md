---
layout: default.ja
title: Changelog
navOrder: 14
navTitle: Changelog
permalink: /sp800-63c/changelog/
anchor: changelog
section: A
---

# Changelog {#changelog}

_This appendix is informative._ It provides an overview of the changes to SP 800-63C since its initial release.

* 公平性(equity)に関する考慮事項と要件の追加．

* フェデレーションプロセスの個別のステップとして信頼の合意(trust agreement)と登録を確立．

* すべての FAL に信頼の合意(trust agreement)の形成と登録に関する要件を設定．

* FAL の定義から暗号化要件を撤廃．暗号化は FAL に関係なく，信頼できない当事者を介してアサーションで PII を渡す際に必要となる．

* FAL2 にはインジェクション保護が必要．

* FAL3 では，従来の holder-of-key に加えて，より一般的な bound authenticator（RP 管理の authenticatorなど）が許容された．

* IAL/AAL/FALの伝達が必須．

* より包括的になるように language を更新．

* RP 加入者(subscriber)アカウントの定義と説明を追加．

* 属性プロビジョニングモデルと説明を追加．

> * Added discussion of equity considerations and requirements.
> 
> * Established trust agreements and registration as discrete steps in the federation process.
> 
> * All FALs have requirements around establishment of trust agreements and registration.
> 
> * FAL definitions no longer have encryption requirements; encryption is triggered by passing PII in an assertion through an untrusted party regardless of FAL.
> 
> * FAL2 requires injection protection.
> 
> * FAL3 allows more general bound authenticators including RP-managed authenticators, in addition to classical holder-of-key.
> 
> * Communication of IAL/AAL/FAL required.
> 
> * Updated language to be more inclusive.
> 
> * Added definition and discussion of RP subscriber accounts.
> 
> * Added attribute provisioning models and discussion.
