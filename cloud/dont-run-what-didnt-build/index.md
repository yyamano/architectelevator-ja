---
description: 最新のクラウド技術の多くはコンテナを利用しています。しかしながら、それなりの数の企業アプリケーションがコンテナ上では簡単に動きません。この難しい問題に対する回答は、一歩下がって根本的な問題について考えることにより得られます。
original:
  url: https://architectelevator.com/cloud/dont-run-what-didnt-build/
---

# なぜ自分達で作っていないソフトウェアを動かすのか

最新のクラウド技術の多くはコンテナを利用しています。しかしながら、それなりの数の企業アプリケーションがコンテナ上では簡単に動きません。この難しい問題に対する回答は、一歩下がって根本的な問題について考えることにより得られます。

[GoogleのCloud Services Platform](https://cloud.google.com/solutions/cloud-services-platform/)のような最新のクラウドプラットフォームは、アプリケーションとサービスの一貫性のあるデプロイメントと運用のための中核技術として[コンテナ](https://en.wikipedia.org/wiki/Operating-system-level_virtualization)を利用しています。従来のIT組織とコンテナ技術について議論した時によくある反応は「多くの私たちの企業アプリケーション、特に市販の商用ソフトウェアはコンテナ上では動きません。少なくとも、ベンダーのサポートがなければ」。確かにその通りです。しかし、この難問への回答は面白いことに、一歩下がって、より根本的な問題について考えることにより得られます。

## 企業のIT =  他人の作ったソフトウェアを動かす

企業のITは主に他の誰かが作ったソフトウェアを動かします。これは、企業のITが自分達でソフトウェアを構築するより購入することを好むからであり、実際にそうしています。時が経つにつれて、他の人が作ったソフトウェアを動かすことはITの基本前提となりました。ITはソフトウェアとハードウェアを調達し、ソフトウェアをハードウェアにインストール、設定、統合、そして運用します。

これにより、ITはかなり過負荷な状態になっています。

![Is your IT overloaded?](https://architectelevator.com/assets/img/overloaded_teaser.jpg)

もし、あなたのITがこのような状態であれば、スリム化すべき時です。

## 他人のソフトウェアを動かすのは本当は高い買い物

よく考えると、他の誰かが作ったソフトウェアを動かすのは実のところ高くつきます。

- **ハードウェアは有料です**。より最悪なのは、パフォーマンスの課題を説明するよりハードウェアを購入してもらうほうが簡単なため、ベンダーのサイジング要件は保守的になりがちです。
- **インストールは厄介です**。インストールに関する全ての問題は顧客の環境が原因だと言うベンダーがいました。それに対する私の返事は、あなたたちのソフトウェアを私たちの環境で動かすことがインストールの目的でしょう。
- **何かが動かなくなった時、無実が証明されるまでは有罪です**。そうです。陶器屋さんと一緒です。壊したら払わないといけません。この場合は、サポート費用を払うことになります。そして、何かがうまく動かない場合、環境のせいではないことをサポートに納得させる必要があります。
- **必要な時に変更できません**。これだけの努力にもかかわらず、新しい機能が必要な場合、次のリリースまで待たなければなりません。ただし、必要な機能がベンダーの機能リストに乗っている場合の話です。そうでなければ、非常に長い時間待つことになるでしょう。

そうです。自分達が作ったのではないソフトウェアを動かすのは、実のところそれほど良いことではありません。企業のITがこのモデルに慣れてしまい、多くの人が疑問を持たなくなっているのにはびっくりさせられます。

## SaaS - Software as a Service

幸運なことに、クラウドの世界は新しい選択肢をもたらしてくれました。Software-as-a-service (SaaS)を使うと、ベンダーが顧客のためにアプリケーションを動かしてくれます。パッチをあて、アップグレードし、拡張し、壊れたハードウェアを交換してくれもします。ずいぶんましになりました。

興味深いことに、Salesforceは2005年頃にこのモデルを採用した本当に最初の会社でしたが、現在は他の会社もこのモデルを採用しています。[Google G Suite](https://gsuite.google.com)(2006年にGoogle Apps for Your Domainとして始まりました)のおかげで、全てのコミュニケーションとドキュメントをクラウド上で扱うことができます。そして、[SAP SuccessFactors](https://www.successfactors.com)による人事と業績管理、[SAP Cloud ERP](https://www.sap.com/sea/products/erp/erp-cloud.html)によるERP、[ServiceNow](https://www.servicenow.com/)によるサービス管理、[Mulesoft CloudHub](https://www.mulesoft.com/platform/saas/cloudhub-ipaas-cloud-based-integration)によるそれら全ての統合が可能です。(注: これは単なる例であり、これらの企業と提携しているわけではありません。G Suiteについて言及するかどうかにかかわらず、Googleは給与を払ってくれます :-)

## しかし…

当然ですが、企業ITは長い「しかし」のリストを持っていることが多いので、いくつか見てみましょう。ゴールはこれらの懸念事項を却下することではなく、何が変わるのかを認識してもらい、懸念を減らす(あるいは無くす)ことです。

- **セキュリティ**: オンプレミスに置くことが安全を意味する時代は終わりました。例えばマイクロプロセッサーの脆弱性([Spectre](https://en.wikipedia.org/wiki/Spectre_(security_vulnerability))や[Meltdown](https://en.wikipedia.org/wiki/Meltdown_(security_vulnerability)))、大規模なDoS攻撃、国家による攻撃などの攻撃ベクター(いくつか例をあげただけです)により、大規模なクラウドプロバイダーの規模と運用の自動化無しでは、IT資産を守ることはほぼ不可能になりました。しかも、オンプレミスは実際には施設(premise)内に存在しないことが多いのです。単なる別のデータセンターです。
- **遅延**: 遅延は単に距離の問題ではありません。ホップ数とパイプのサイズの問題でもあります(ネットワークの飽和は遅延の増加、あるいはサービス停止も招きます)。ほとんどの顧客とパートナーはインターネット経由でサービスにアクセスするので、多くの場合、クラウドはISPやデータセンターより顧客に近い場所にあります。
- **管理**: 管理とは現実と指示したことが一致することです。多くの企業では人手による処理が管理の制約となっています。誰かが要求を出し、それが承認され、人手によって処理されます。承認されたことと実際のアクションが一致することを誰が保証するのでしょうか? 踏み台サーバーとセッションの記録でしょうか?
- **費用**: 規模の経済と高いレベルの自動化のおかげで、ほとんどの企業はクラウドへの移行によりコストを削減しています。
- **統合**: 誰かが統合に関わる全てについて本を書くかもしれません。[あー、ちょっと待った](https://www.enterpriseintegrationpatterns.com)。当然ですが、ソフトウェアのインストールで重要なのは、ソフトウェアを動くようにするだけではなく、他のシステムと接続することです。SaaSモデルによりこの作業が全く無くなるわけではありませんが、APIと組み込みのインターフェース(例えば[SalesforceとGSuite](https://www.salesforce.com/campaign/google/))によってかなり簡単になっています。このような観点からは、SalesforceがMulesoftを買収したのは驚くべきことではありません。

## 自分達で作ったソフトウェアはどうなのでしょうか

当然ですが、自分達で作りたいソフトウェアもあります。例えば、他社との競争で優位に立つためのものです。そのようなソフトウェアにおいては、デリバリーの速さ、可用性、そしてスケーラビリティが重要な基準です。幸い、[クラウドは単なるインフラストラクチャではありません](https://www.linkedin.com/pulse/cloud-infrastructure-topic-gregor-hohpe/)。CI/CDパイプラインやコンテナオーケストレーション、例えばKubernetes、あるいは[Google Kubernetes Engine](https://cloud.google.com/kubernetes-engine/)のようなマネージドサービスを組み合わせたPlatform-as-a-Serviceとして提供されます。　

## 戦略 = ベクトル

全てのオンプレミス上のソフトウェアが明日なくなることはありません。しかし、戦略は方向性であり、目の前の現実ではありません。自分たちで作っていないソフトウェアを動かさないことは、ITのスリム化のための現実的なIT戦略になったと確信しています。