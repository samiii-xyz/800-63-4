---
layout: default.ja
title: Session Management
navOrder: 7
navTitle: Session
permalink: /sp800-63b/session/
anchor: sec7
section: 7
---

# Session Management {#sec7}

_This section is normative._

認証イベントが発生すると，加入者(subscriber)が認証イベントを繰り返さなくても，後続の複数の対話でアプリケーションを使用し続けることができるようにすることが望ましい場合がよくある．この要件は，[[SP800-63C]](../_sp800-63c/sec1_purpose.ja.md#purpose){:latex-href="#ref-SP800-63C"} で説明されているフェデレーションシナリオに特に当てはまる．認証イベントには，ネットワーク全体で調整する複数のコンポーネントとパーティが必然的に含まれる．

> Once an authentication event has taken place, it is often desirable to allow the subscriber to continue using the application across multiple subsequent interactions without requiring them to repeat the authentication event. This requirement is particularly true for federation scenarios — described in [[SP800-63C]](../_sp800-63c/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63C"} — where the authentication event necessarily involves several components and parties coordinating across a network.

この動作を容易にするために，認証イベントに応答して *セッション* を開始し，セッションが終了するまでセッションを継続し**てもよい(MAY)**．セッションは，非アクティブタイムアウト，明示的なログアウトイベント，またはその他の手段を含むがこれらに限定されない，さまざまな理由で終了する場合がある．セッションは，[Sec. 7.2](sec7_session.md#sessionreauthn)に説明されているように，加入者(subscriber)が最初の認証イベントの一部またはすべてを繰り返し，それによってセッションを再確立することで再認証イベントを通じて継続される場合がある．

> To facilitate this behavior, a *session* **MAY** be started in response to an authentication event, and continue the session until such time that it is terminated. The session **MAY** be terminated for any number of reasons, including but not limited to an inactivity timeout, an explicit logout event, or other means. The session **MAY** be continued through a reauthentication event — described in [Sec. 7.2](sec7_session.md#sessionreauthn) — wherein the subscriber repeats some or all of the initial authentication event, thereby re-establishing the session.

セッション管理は，資格情報の継続的な提示よりも推奨される．継続的な提示の使いやすさの悪さは，アクティベーション要素のキャッシュ，認証の意図の無効化，認証イベントの鮮度の不明瞭化などの回避策のインセンティブを作成することが多いためである．

> Session management is preferable over continual presentation of credentials as the poor usability of continual presentation often creates incentives for workarounds such as caching of activation factors, negating authentication intent and obscuring the freshness of the authentication event.

## Session Bindings

加入者(subscriber) が実行しているソフトウェア間（ブラウザ，アプリケーション，オペレーティングシステムなど (つまり，セッションサブジェクト) ）および，加入者(subscriber)がアクセスしている RP または CSP (つまり，セッションホスト)の間では，セッションが発生する．セッションシークレットは，加入者(subscriber)のソフトウェアとアクセスされるサービスの間で共有され**なければならない(SHALL)**．このシークレットは，セッションの両端をバインドし，加入者(subscriber)が時間の経過とともにサービスを使用し続けることを可能にする．シークレットは，加入者(subscriber)のソフトウェアによって直接提示され**なければならない(SHALL)**．またはシークレットの所有が暗号化メカニズムを使用して証明され**なければならない(SHALL)**．

> A session occurs between the software that a subscriber is running &mdash; such as a browser, application, or operating system (i.e., the session subject) &mdash; and the RP or CSP that the subscriber is accessing (i.e., the session host). A session secret **SHALL** be shared between the subscriber's software and the service being accessed. This secret binds the two ends of the session, allowing the subscriber to continue using the service over time. The secret **SHALL** be presented directly by the subscriber's software or possession of the secret **SHALL** be proven using a cryptographic mechanism.

認証されたセッションの継続性は，認証時に検証者によって発行され，オプションでセッション中に更新されるセッションシークレットの所有に基づいてい**なければならない(SHALL)**．セッションの性質は，次のようにアプリケーションによって異なる．

* 「セッション」Cookie を使用した Webブラウザセッション
* セッションシークレットを保持するモバイルアプリケーションのインスタンス

> Continuity of authenticated sessions **SHALL** be based upon the possession of a session secret issued by the verifier at the time of authentication and optionally refreshed during the session. The nature of a session depends on the application, such as:
> 
> * a web browser session with a "session" cookie, or
> * an instance of a mobile application that retains a session secret.

セッションシークレットは永続的であっ**てはならない(SHALL NOT)**． (関連するアプリケーションの再起動またはホストデバイスの再起動後も保持される)

> Session secrets **SHALL NOT** be persistent (retained across a restart of the associated application or a reboot of the host device).

セッションバインディングに使用されるシークレットは，認証イベントに直接応答してセッションホストによって生成され**なければならない(SHALL)**．セッションは，その作成をトリガーした認証イベントの AAL プロパティを継承する**必要がありまる(SHOULD)**．セッションは，認証イベントよりも低い AAL であると見なされ**てもよい(MAY)**が，認証イベントよりも高い AAL であると見なされ**てはならない(SHALL NOT)**．

> The secret used for session binding **SHALL** be generated by the session host in direct response to an authentication event. A session **SHOULD** inherit the AAL properties of the authentication event which triggered its creation. A session **MAY** be considered at a lower AAL than the authentication event but **SHALL NOT** be considered at a higher AAL than the authentication event.

セッションバインディングに使用されるシークレットは，次のすべての要件を満たさ**なければならない(SHALL)**:

1. シークレットは，対話中にセッショ ホストによって生成される．通常，認証の直後に生成される．
2. シークレットは承認されたランダムビットジェネレータ [[SP800-90Ar1]](references.ja.md#ref-SP800-90Ar1) によって生成され，少なくとも 64 ビットのエントロピーが含まれる.
3. 加入者(subscriber)がログアウトすると，シークレットはセッションサブジェクトによって消去または無効化される.
4. シークレットは，認証され保護されたチャネルを使用してデバイスとの間で送受信される.
5. [Sections 4.1.3](sec4_aal.ja.md#aal1reauth)，[4.2.3](sec4_aal.ja.md#aal2reauth)，[4.3.3](sec4_aal.ja.md#aal3reauth) で指定された時間が経過すると，シークレットはタイムアウトになり，AALに応じて受け入れらない．
6. ホストと加入者(subscriber)のエンドポイント間の安全でない通信では，シークレットは使用できない.

> Secrets used for session binding **SHALL** meet all of the following requirements:
>
> 1. Secrets are generated by the session host during an interaction, typically immediately following authentication.
> 2. Secrets are generated by an approved random bit generator [[SP800-90Ar1]](references.md#ref-SP800-90Ar1) and contain at least 64 bits of entropy.
> 3. Secrets are erased or invalidated by the session subject when the subscriber logs out.
> 4. Secrets are sent to and received from the device using an authenticated protected channel.
> 5. Secrets will time out and are not accepted after the times specified in [Sections 4.1.3](sec4_aal.md#aal1reauth), [4.2.3](sec4_aal.md#aal2reauth), and [4.3.3](sec4_aal.md#aal3reauth), as appropriate for the AAL.
> 6. Secrets are not made available to insecure communications between the host and subscriber's endpoint.

さらに，セッションバインディングに使用されるシークレットは，加入者(subscriber)がログアウトするとき，またはシークレットの有効期限が切れたと見なされるときに，加入者(subscriber)エンドポイントで消去する**必要がある(SHOULD)**．ローカル ストレージがクロスサイト スクリプティング (XSS) 攻撃にさらされる可能性があるため，HTML5 ローカル ストレージなどの安全でない場所に配置し**てはならない(SHALL NOT)**．

> In addition, secrets used for session binding **SHOULD** be erased on the subscriber endpoint when they log out or when the secret is deemed to have expired. They **SHOULD NOT** be placed in insecure locations such as HTML5 Local Storage due to the potential exposure of local storage to cross-site scripting (XSS) attacks.

認証されたセッションは，認証後，https から http などの安全でないトランスポートにフォールバックし** てはならない(SHALL NOT)**．

> Authenticated sessions **SHALL NOT** fall back to an insecure transport, such as from https to http, following authentication.

URL または POST コンテンツには，クロスサイトリクエストフォージェリから保護するためにセッション識別子が含まれてい**なければならず(SHALL)**，RP によって検証され**なければならない(SHALL)**．

> URLs or POST content **SHALL** contain a session identifier that **SHALL** be verified by the RP to protect against cross-site request forgery.

時間の経過とともにセッションを管理するためのメカニズムがいくつかある．次のセクションでは，さまざまな例を，各テクノロジ例に固有の追加の要件と考慮事項と共に示す．追加の有益なガイダンスは，OWASPの *セッション管理チートシート(Session Management Cheat Sheet)* [[OWASP-session]](references.ja.md#ref-OWASP-session) にある．
> There are several mechanisms for managing a session over time. The following sections give different examples along with additional requirements and considerations particular to each example technology. Additional informative guidance is available in the OWASP *Session Management Cheat Sheet* [[OWASP-session]](references.md#ref-OWASP-session).

### ブラウザクッキー (Browser Cookies)

ブラウザ Cookie は，サービスにアクセスする加入者(subscriber)のためにセッションを作成および追跡するための主要なメカニズムである．Cookie はオーセンティケーターではないんが，短期間のシークレット (セッション期間のみ利用) として適している．

> Browser cookies are the predominant mechanism by which a session will be created and tracked for a subscriber accessing a service. Cookies are not authenticators, but they are suitable as short-term secrets (for the duration of a session).

セッションの管理に使用される Cookie は，次のすべての要件を満たさ**なければならない(SHALL)**．

1. Cookie は，安全な (HTTPS) セッションでのみアクセスできるようにタグ付けされている．
2. Cookie は，最小限の実用的なホスト名とパスのセットにのみアクセスできる．

> Cookies used for session maintenance **SHALL** meet all of the following requirements:
> 
> 1. Cookies are tagged to be accessible only on secure (HTTPS) sessions.
> 2. Cookies are accessible to the minimum practical set of hostnames and paths.

さらに，セッションを管理する Cookie は，JavaScript (HttpOnly) 経由でアクセスできないようにタグ付けする**必要がある(SHOULD)**．不透明な文字列 (セッション ID など) のみを含める**必要があり(SHOULD)**，平文の PII を含める**べきではない(SHOULD NOT)**．それらは，セッションの有効期間またはその直後に期限切れになるようにタグ付けする**必要がある(SHOULD)**．この後者の要件は，Cookie の蓄積を制限することを目的としているが，セッションタイムアウトを強制するために依存し**てはならない(SHALL NOT)**．

> In addition, session maintenance cookies **SHOULD** be tagged to be inaccessible via JavaScript (HttpOnly). They **SHOULD** contain only an opaque string (such as a session identifier), and **SHOULD NOT** contain cleartext PII. They **SHOULD** be tagged to expire at, or soon after, the session's validity period. This latter requirement is intended to limit the accumulation of cookies, but **SHALL NOT** be depended upon to enforce session timeouts.

### アクセストークン (Access Tokens)

アクセス トークン (OAuth など) は，アプリケーションが認証イベントに続いて加入者(subscriber)に代わって一連のサービスにアクセスできるようにするために使用される．OAuth アクセストークンの存在は，他のシグナルがない場合，RP によって加入者(subscriber)の存在として解釈され**てはならない(SHALL NOT)**．OAuth アクセストークンと関連するリフレッシュトークンは，認証セッションが終了し，加入者(subscriber)がアプリケーションを離れた後もずっと有効であっ**てもよい(MAY)**．
> An access token — such as found in OAuth — is used to allow an application to access a set of services on a subscriber's behalf following an authentication event. The presence of an OAuth access token **SHALL NOT** be interpreted by the RP as presence of the subscriber, in the absence of other signals. The OAuth access token, and any associated refresh tokens, **MAY** be valid long after the authentication session has ended and the subscriber has left the application.

### デバイスの識別 (Device Identification)

安全なデバイス識別のその他の方法（相互TLS，トークンバインディング，またはその他のメカニズムを含むが，これらに限定されない）は，加入者(subscriber)とサービスの間のセッションを制定するために使用され**てもよい(MAY)**．
> Other methods of secure device identification &mdash; including but not limited to mutual TLS, token binding, or other mechanisms &mdash; **MAY** be used to enact a session between a subscriber and a service.

## Reauthentication {#sessionreauthn}

セッションの定期的な再認証は，認証されたセッションに加入者(subscriber)が引き続き存在する(つまり，加入者(subscriber)がログアウトせずに離れていない）ことを確認するために実行し**なければならない(SHALL)**．

> Periodic reauthentication of sessions **SHALL** be performed to confirm the continued presence of the subscriber at an authenticated session (i.e., that the subscriber has not walked away without logging out).

セッションは，セッションシークレットのみの提示に基づいて，セクション[4.1.3](sec4_aal.ja.md#aal1reauth)，[4.2.3](sec4_aal.ja.md#aal2reauth)，[4.3.3](sec4_aal.ja.md#aal3reauth) (AALによる) のガイドラインを超えて拡張され**てはならない(SHALL NOT)**．セッションの有効期限が切れる前に，[表2](sec7_session.ja.md#table-2) で指定された認証要素を加入者(subscriber)に求めることにより，再認証の時間制限を延長し**なければならない(SHALL)**．

> A session **SHALL NOT** be extended past the guidelines in Sections [4.1.3](sec4_aal.md#aal1reauth), [4.2.3](sec4_aal.md#aal2reauth), and [4.3.3](sec4_aal.md#aal3reauth) (depending on AAL) based on presentation of the session secret alone. Prior to session expiration, the reauthentication time limit **SHALL** be extended by prompting the subscriber for the authentication factors specified in [Table 2](sec7_session.md#table-2).

タイムアウトまたはその他のアクションによりセッションが終了した場合，加入者(subscriber)は，再度認証して新しいセッションを確立し**なければならない(SHALL)**．
> When a session has been terminated, due to a time-out or other action, the subscriber **SHALL** be required to establish a new session by authenticating again.

[表2 AAL ごとの再認証要件](sec7_session.ja.md#table-2){:name="table-2"}
{:latex-ignore="true"}

|AAL|要件|
|----|----|
|1|いずれか1要素|
|2|記憶シークレットあるいは生体認証|
|3|全ての要素|
{:latex-table="2" latex-caption="AAL Reauthentication Requirements"}

> |AAL|Requirement|
> |----|----|
> |1|Presentation of any one factor|
> |2|Presentation of a memorized secret or biometric|
> |3|Presentation of all factors|

注記: AAL2 では，セッションシークレットは *持っているもの(something you have)* であり，セッションを続行するには追加の認証要素が必要であるため，物理的なオーセンティケーターではなく，記憶シークレットまたは生体認証が必要である．

>Note: At AAL2, a memorized secret or biometric, and not a physical authenticator, is required because the session secret is *something you have*, and an additional authentication factor is required to continue the session.

### Reauthentication from a Federation or Assertion

[[SP800-63C]](../_sp800-63c/sec1_purpose.ja.md#purpose){:latex-href="#ref-SP800-63C"} で説明されているように，フェデレーションプロトコルと アイデンティティプロバイダー (IdP) を使用して RP で認証する場合，セッション管理と再認証に特別な考慮事項が適用される．フェデレーションプロトコルは，アサーションを使用して IdP での認証イベントを RP に伝達し，RP はこのアサーションの検証の成功に基づいて認証済みセッションを開始する．IdP と RP はセッションを別々に管理し，フェデレーションプロトコルは IdP と RP の間のセッション管理を接続しないため，IdP と RP での加入者(subscriber)のセッションの終了は互いに独立している．同様に，複数の異なる RP での加入者(subscriber)のセッションは，互いに独立して確立および終了される．

> When using a federation protocol and Identity Provider (IdP) to authenticate at the RP as described in [[SP800-63C]](../_sp800-63c/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63C"}, special considerations apply to session management and reauthentication. The federation protocol communicates an authentication event at the IdP to the RP using an assertion, and the RP then begins an authenticated session based on the successful validation of this assertion. Since the IdP and RP manage sessions separately from each other and the federation protocol does not connect the session management between the IdP and RP, the termination of the subscriber's sessions at an IdP and at an RP are independent of each other. Likewise, the subscriber's sessions at multiple different RPs are established and terminated independently of each other. 

したがって，RP セッションが期限切れになり，RP が再認証を必要とする場合，IdP でのセッションが期限切れになっておらず，加入者(subscriber)を明示的に再認証することなく IdP でこのセッションから新しいアサーションが生成される可能性は十分にある．IdP は認証イベントの時間と詳細を RP に伝えることができるが，再認証要件が満たされているかどうかを判断するのは RP である． [[SP800-63C]](../_sp800-63c/sec5_federation.ja.md#federation-session){:latex-href="#ref-SP800-63C"} の セクション 5.3 では，フェデレーションコンテキスト内でのセッション管理に関する追加の詳細と要件を提供する．

> Consequently, when an RP session expires and the RP requires reauthentication, it is entirely possible that the session at the IdP has not expired and that a new assertion could be generated from this session at the IdP without explicitly reauthenticating the subscriber. The IdP can communicate the time and details of the authentication event to the RP, but it is up to the RP to determine if reauthentication requirements have been met. Section 5.3 of [[SP800-63C]](../_sp800-63c/sec5_federation.md#federation-session){:latex-href="#ref-SP800-63C"} provides additional details and requirements for session management within a federation context.
