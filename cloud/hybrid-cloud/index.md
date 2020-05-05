---
description: 企業はハイブリッドクラウドを無視できません。そこに到達するための八つの方法について説明します。
original:
  url: https://architectelevator.com/cloud/hybrid-cloud/
---

# ハイブリッドクラウド象の分割

シンプルかつ示唆に富む意思決定モデルにより、エレベーターアーキテクトはより良い意識的な決定を行うことができます。ハイブリッドクラウドはこのための良いテストケースです。

[ハイブリッドマルチクラウドに関する以前の記事](/cloud/hybrid-multi-cloud/)で説明したように、ハイブリッドクラウドは、少なくとも暫定的な状態としてあらゆる企業のクラウドシナリオにあらわれます。理由は単純です。ある日、全てのワークロードがデータセンターから魔法のようになくなったことに気がつくことはありえません。いくつかのアプリケーションはすでにクラウドにあり、他のアプリケーションはいまだにオンプレミスにあります。そして、これら二つの場所にデプロイされたアプリケーションは協調して動作する必要があるでしょう。

つまり、*ハイブリッド*は流行語として真っ当なものと言えるでしょう。とはいえ、アーキテクチャ思考を適用することには大きなメリットがあります。それでは、前回の定義から始めてみましょう。

> *ハイブリッドクラウド*アーキテクチャはワークロードをクラウドとオンプレミス環境に分割します。一般的に、これらのワークロードは何かを行うために協調して動作します。

![Hybrid and multi](https://architectelevator.com/assets/img/hybrid_multi.png){: style="margin-left: auto;margin-right: auto;display: block;"}


真っ当なクラウドコンピューティング戦略を定義しようとすると十分な複雑さを扱う必要があるので、単純な定義が一番役にたちます。単純な定義は、さまざまな人々がコンセプトや決定にアクセスするのを助けます。しかし、それだけではなく、何からできているかに焦点を当てるかわりに、どのように利用されるのかを強調します(構造ではなく*意図*に焦点を合わせるのはパターンの著者の傾向なのかもしれません)。

残念ながら、定義することは最初の一歩にすぎません。それを実行可能なものにするためには、何か具体的なものに発展させる必要があります。そのために、*アーキテクトエレベータ*に乗って数階降りて、重要なニュアンスを理解し、分類してみましょう。

## 二つに分離された環境はハイブリッドではない 

いくつかのワークロードをクラウドにそして残りをオンプレミスに置くのは、残念ながら、単に別のコンピューティング環境をポートフォリオに追加することにすぎません。複雑さを求めているCIOはいません。つまり、これは良い計画ではないように思えます。

> 複雑さを求めているCIOはいません。クラウドを別のデータセンターにしてはいけません。

したがって、何かをハイブリッドと呼ぶためには環境全体の統合管理が必要です。ハイブリッドカーの例で考えてみましょう。ハイブリッドカーを作る時に難しいのは、バッテリーと電気モーターをガソリン車に組み込むことではありませんでした。二つのシステムをシームレスに調和のとれた方法で機能させることが難しかったのです。これが、トヨタプリウスが*ハイブリッド*カーと呼ばれる理由です。

先ほどの定義を見直しましょう。

> *ハイブリッドクラウド*アーキテクチャはワークロードをクラウドとオンプレミス環境に分割します。一般的に、これらのワークロードは何かを行うために協調して動作します。両方の環境は統合管理されます。

![Hybrid Cloud](https://architectelevator.com/assets/img/hybrid.png){: style="margin-left: auto;margin-right: auto;display: block;"}

さまざまな環境の統合管理は簡単ではありません。しかし、いくつかの方法があります。

- オンプレミス上にクラウド環境のようなものを構築する。例えば、[AWS Outposts](https://aws.amazon.com/outposts/)や[Azure Stack](https://azure.microsoft.com/en-in/overview/azure-stack/)を利用します。
- 既存のオンプレミス環境をクラウド上にコピーする。例えば、[VMWare Cloud](https://azure.microsoft.com/en-in/overview/azure-stack)を使います。
- 両方の環境に統合されたランタイムと管理レイヤーを拡張します。例えば、コンテナ、Kubernetes、Google Anthosのような管理レイヤーを使用します。
- クラウド上のデータをオンプレミス環境から簡単に利用できるようにします。例えば、[AWS Storage Gateway](https://aws.amazon.com/storagegateway/features/?nc=sn&loc=2&dn=1)、あるいはNetApp SnapMirrorのようなストレージレプリケーションソリューションを使います。
- アイデンティティ管理とアクセス管理を統合します。例えば、クラウドアカウントをActive Directoryに統合します。

これらの判断には別の記事にするに十分なボリュームであることは想像できるでしょう。この記事では、ハイブリッドクラウドにおける基本的な判断について考えてみましょう。

## ハイブリッドの分割 - 31種類の味

ハイブリッドクラウドの重要なアーキテクチャ上の決定事項はワークロードの分割方法です。つまり、ITシステムのどの部分をクラウドに移行し、どの部分をオンプレミスに残すかです。この決定は、ITシステムの*つなぎ目*を見つけるという考え方に密接に関係しています。Mike Feathersは彼の古典と言える[Working Effectively with Legacy Code](https://www.informit.com/articles/article.aspx?p=359417&seqNum=3)(日本語訳は[レガシーコード改善ガイド](https://www.shoeisha.co.jp/book/detail/9784798116839))の中で(知る限り)はじめてつなぎ目について説明しました。つなぎ目は分割による依存関係があまり増えずに、パフォーマンスの低下のような実行時に問題を引き起こさない場所です。

ワークロードを分割する31の方法を記述することはできないと思うので、興味をひくタイトルをつけたことを謝っておきます。とはいえ、できる限りカタログ化したいと思います。これはいくつかの点で役に立ちます。

- 何を選択したのか、そしてその理由を簡単に伝えることができるので、共通の語彙は意思決定を透明にします。
- また、このリストを使うことにより選択肢を見落としていないかどうか確認することもできます。特に法的規制への懸念やデータ保存の要件により、クラウドへ移行できない環境では、便利なプレイブックを使いクラウドに移行するための選択肢すべてを検討したかどうかを確認できます。
- 最後に、選択肢を明確にすることにより、各選択肢の適用可能性、長所、短所を矛盾なく検討しやすくなります。また、ある選択肢を選択するときに注意すべき点も明確です。

## クラウド象の分割方法

企業がハイブリッド環境にまたがってワークロードを分割する方法は少なくとも八つあります。もっとあるかもしれません。

![Ways to split hybrid cloud](https://architectelevator.com/assets/img/hybrid_splits.png)

この一覧の主な目的は、誰も知らない新しい選択肢を見つけることではありません。基本的な確認に便利なように一般的な選択肢を集めたものです。それぞれのアプローチをもう少し詳しく見てみましょう。

### 層: フロントとバック (Tier: Front vs. Back)

![Separating by tier](https://architectelevator.com/assets/img/hybrid_tier.png){: style="float:right;max-width:50%;padding-left:10px;padding-top:1em"}

顧客やエコシステムに面しているコンポーネント、別名「フロントエンドシステム」、あるいは「エンゲージメントシステム」をクラウドに移行し、バックエンドシステムを維持するのは一般的な戦略です。

私は[2スピードアーキテクチャは好きではありません](https://architectelevator.com/transformation/shifting_gears_clutch/#2-speed-it-burns-the-clutch)が、理由によってはこのアプローチが当然の選択になります。

- フロントエンドコンポーネントはインターネットに公開されているので、インターネットからクラウドにトラフィックを直接ルーティングすることにより、遅延や企業ネットワークのトラフィックの輻輳を減らすことができます。
- 激しくトラフィックが変動しがちなフロントエンドコンポーネントにとって、エラスティックスケーリングは価値があります。
- フロントエンドシステムは最新のツールチェーンとアーキテクチャを使用して開発される可能性が高いため、クラウドに適しています。
- フロントエンドシステムが個人を特定可能な情報や機密情報を保存する可能性が低くなります。これは、データが通常バックエンドに渡されるからです。企業の方針がこのようなデータのクラウドへの保管を禁止している環境では、フロントエンドシステムがクラウドへの移行の候補となります。

これらのわかりやすい利点に加えて、次の注意すべき点を除くと、アーキテクチャはそれほど興味深いものではありません。

- フロントエンドがエラスティックスケーリングの恩恵を受けたとしても、ほとんどのバックエンドはそれに
伴う負荷の急激な増加を処理することができません。したがって、キャッシュやキューの利用や計算コストの高い処理のクラウドへの移行ができない場合は、エンドツーエンドのアプリケーションのスケーラビリティを改善できないでしょう。
- 同様に、アプリケーションが信頼性に悩まされている場合、半分だけをクラウドに移行しても問題は解決しません。
- 多くのフロントエンドはバックエンド、あるいは特にデータベースと「おしゃべり」に通信します。これは、これらのシステムが近い環境向けに構築されているからです。フロントエンドに対する一つのリクエストは数十、時には数百のリクエストをバックエンドに発行します。このようなおしゃべりなチャネルをクラウドとオンプレミスに分割するとエンドユーザの遅延が増加します。

「2スピードIT」の興奮が消え去ったとしても、このアプローチは依然として良い中間状態です。ただし、長期的な戦略と混同してはいけません。

### 世代: 新しいものと古いもの (Generation: New vs. Old)

![Separating by generation](https://architectelevator.com/assets/img/hybrid_generation.png){: style="float:right;max-width:50%;padding-left:10px;padding-top:1em"}

密接な関係があるのは、*新しいもの*と*古いもの*の分割です。すでに説明したように、新しいシステムは一般的にスケーラブル、かつ独立してデプロイできるように設計されているため、クラウドが住処であることが多いでしょう。また、新しいシステムは比較的小規模で、*クラウドネイティブ*と呼ばれるにふさわしいものです。クラウドネイティブという言葉はクラウドへの移行(移住)を禁じているように見えるので好きではありませんが。

<p>Again, several reasons speak for this type of split:</p>

<ul>
  <li>Modern components are more likely to use modern tool chains and architectures, such as micro-services, continuous integration (CI), automated tests and deployment, etc. Hence they can take better advantage of cloud offerings.</li>
  <li>Modern components are more likely to run in containers and can thus utilize higher-level cloud services like managed Kubernetes or serverless environments.</li>
  <li>Modern components are more likely to be well-understood and tested, reducing the migration risk.</li>
</ul>

<p>Again, there are a few things to consider:</p>

<ul>
  <li>Splitting by <em>new</em> vs <em>old</em> may not align well with the existing systems architecture, meaning it isn’t hitting a good <em>seam</em>. For example, splitting highly cohesive components across data center boundaries will likely result in poor performance.</li>
  <li>Unless you are in the process of replacing all components over time, this strategy doesn’t lead to a “100% in the cloud” outcome.</li>
</ul>

<p>Overall this is a good approach if you are developing new systems - ultimately <em>new</em> will replace <em>old</em>.</p>

### 重要度: 重要でないものと重要なもの (Criticality: Non-critical vs. Critical)

![Separating by criticality](https://architectelevator.com/assets/img/hybrid_criticality.png){: style="float:right;max-width:50%;padding-left:10px;padding-top:1em"}

<p>Many enterprises prefer to first dip their toe into the cloud water before going all out. They are likely to try the cloud with a few simple applications that can accommodate the initial learning curve and the inevitable mistakes. “Failing fast” and learning along the way makes sense:</p>

<ul>
  <li>Skill set availability is one of the main inhibitors of moving to the cloud - stuff is never as easy as shown in the vendor demos. Therefore, starting small and getting rapid feedback builds much needed skills in a low-risk environment.</li>
  <li>Smaller applications benefit from the cloud self-service approach because it reduces or eliminates the fixed overhead common in on-premise IT.</li>
  <li>Small applications also give you timely feedback and allow you to calibrate your expectations.</li>
</ul>

<p>While moving non-critical applications out to the cloud is a good start, it also has some limitations:</p>

<ul>
  <li>Cloud providers generally offer <em>better</em> uptime and security than on-premises environments, so you’ll likely gain more by moving <em>critical</em> workloads.</li>
  <li>While you can learn a lot from moving simple applications, they may not have the same security, up-time, and scalability requirements as subsequent workloads. You therefore need to be cautious to not under-estimate the effort of a full migration.</li>
</ul>

<p>Overall it’s a good “tip your toe into the water” strategy that certainly beats a “let’s wait until all this settles” approach.</p>


### ライフサイクル: 開発と本番 (Lifecycle: Development vs. Production)

![Separating by lifecycle](https://architectelevator.com/assets/img/hybrid_lifecycle.png){: style="float:right;max-width:50%;padding-left:10px;padding-top:1em"}

<p>There are many ways to slice the proverbial elephant (eggplant for vegetarians like me). Rather than just considering splits across run-time components, a whole different approach is to split by application lifecycle. For example, you can run your tool chain, test, and staging environments in the cloud while keeping production on premises, e.g. due to regulatory constraints.</p>

<p>Shifting build and test environments into the cloud is a good idea for several reasons:</p>

<ul>
  <li>Build and test environments rarely contain real customer data, so most concerns around data privacy and locality don’t apply.</li>
  <li>Development, test, and build environments are temporary in nature, so being able to set them up when needed and tearing them back down leverages the elasticity of the cloud and can cut infrastructure costs by a factor of 3 or more: the core working hours make up less than a third of 168 hours in a week. Functional test environments may even have shorter duty cycles, depending on how quickly they can spin up.</li>
  <li>Many build systems are failure tolerant, so you can shave off even more Dollars by using <em><a href="https://cloud.google.com/preemptible-vms/" target="_blank">preemptible</a></em> / <em><a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-spot-instances.html" target="_blank">spot</a></em> compute instances.</li>
</ul>

<p>You might have guessed that architecture is the business of trade-offs, so once again we have a few things to watch out for:</p>

<ul>
  <li>Splitting your software lifecycle across cloud and on-premises results in a test environment that’s different from production. This is risky as you might not detect performance bottlenecks or subtle differences that can cause bugs to surface only in production.</li>
  <li>If your build chain generates large artifacts you may face delays or egress charges when deploying those to your premises.</li>
</ul>

<p>This option may be most popular for development teams that are restrained from running production workloads in the cloud but still want to take as much advantage of it as possible.</p>

<hr />

### データの分類: 機密性の高くないものと機密性の高いもの (Data Classification: Non-sensitive vs. Sensitive)

![Separating by data classification](https://architectelevator.com/assets/img/hybrid_classification.png){: style="float:right;max-width:50%;padding-left:10px;padding-top:1em"}

<p>The compute aspect of hybrid cloud is comparatively simple because code can easily be re-deployed into different environments. Data is a different story: data largely resides in one place and needs to be migrated or synchronized if it’s meant to go somewhere else. If you move your compute and keep the data on premises, you’ll likely incur a heavy performance penalty. Therefore, it’s the data that often prevents the move to the cloud.</p>

<p>As data classification can be the hurdle for moving apps to the cloud, a natural split would be to move non-sensitive data to the cloud while keeping sensitive data on premises. Doing so has some distinct advantages:</p>

<ul>
  <li>It complies with common internal regulations related to data residency as sensitive data will remain on your promises and isn’t replicated into other regions.</li>
  <li>It limits your exposure in case of a possible cloud data breach.</li>
</ul>

<p>However, the approach is rooted in assumptions that don’t necessarily hold true for today’s computing environments:</p>

<ul>
  <li>Protecting on premises environments from sophisticated attacks and low-level exploits has become a difficult proposition. For example, CPU-level exploits like <a href="https://en.wikipedia.org/wiki/Spectre_(security_vulnerability)" target="_blank">Spectre</a> and <a href="https://en.wikipedia.org/wiki/Meltdown_(security_vulnerability)" target="_blank">Meltdown</a> were corrected by some cloud providers before they were announced - something that couldn’t be done on premises.</li>
  <li>Malicious data access and exploits don’t always access data directly but often go through many “hops”. Having some systems in the cloud while your sensitive data remains on premises doesn’t automatically mean your data is secure. For example, one of the biggest data breaches, the <a href="https://en.wikipedia.org/wiki/Equifax#May%E2%80%93July_2017_data_breach" target="_blank">Equifax Data Breach</a> that affected up to 145 million customer records had data stored on premises.</li>
</ul>

<p>Hence, while this approach may be suitable to getting started in face of regulatory or policy constraints, use it with caution as a long-term strategy.</p>

<hr />

### データの鮮度: バックアップと稼働中 (Data Freshness: Back-up vs. Operational)

![Separating by data freshness](https://architectelevator.com/assets/img/hybrid_freshness.png){: style="float:right;max-width:50%;padding-left:10px;padding-top:1em"}

<p>Not all your data is accessed by applications all the time. In fact, in many enterprises a vast majority of data is “cold”, meaning it’s accessed rarely. That’s the case for example for historical records or back-ups. Cloud providers offer appealing options for data that’s rarely accessed. <a href="https://aws.amazon.com/glacier/" target="_blank">Amazon’s Glacier</a> was one of the earliest offerings to specifically target that use case while other providers have special tiers for their storage service, e.g. <a href="https://azure.microsoft.com/en-us/services/storage/archive/" target="_blank">Azure Storage Archive Tier</a> and <a href="https://cloud.google.com/storage/docs/storage-classes" target="_blank">GCP Coldline Cloud Storage </a>.</p>

<p>Archiving data in the cloud makes good sense:</p>

<ul>
  <li>Backing up and restoring data usually occurs separate from regular operations, so it allows you to take advantage of the cloud without having to migrate or re-architect applications.</li>
  <li>For older applications, data storage cost can make up a significant percentage of the overall operational costs, so moving some of this to the cloud can give you instant cost savings.</li>
  <li>For archiving purposes, it’s good to have data in a location separate from your usual data center.</li>
</ul>

<p>Alas, it also has limitations:</p>
<ul>
  <li>Data recovery costs can be high, so you’d only want to move data that you rarely need.</li>
  <li>The data you’d want to back up likely contains customer or other proprietary data, so you might need to encrypt or otherwise protect that data, which can interfere with optimizations such as data de-duplication.</li>
</ul>

<p>Still, using cloud backup is a good way for enterprises to quickly start benefiting from the cloud.</p>

<hr />

### 稼働状況: 災害時と通常時 (Operational State: Disaster vs. BAU)

![Separating by operational state](https://architectelevator.com/assets/img/hybrid_bau.png){: style="float:right;max-width:50%;padding-left:10px;padding-top:1em"}

<p>Lastly, one can split workloads by the nature of the system’s operational state. The most apparent division in operational state is whether things are going well (“business as usual”) or whether the main compute resources are unavailable (“disaster”). While you or your regulator may have a strong preference for running systems on premises, when these systems have become unavailable, it may be better to have a running system at all, even if it’s located in the cloud.</p>

<p>This approach to slicing workload is slightly different from the others as the same code would run in both environments, but under different circumstances:</p>

<ul>
  <li>No workloads run in the cloud under normal operational conditions.</li>
  <li>Cloud usage is temporary, making good use of the cloud’s elastic billing approach.</li>
</ul>

<p>However, life isn’t quite that simple:</p>

<ul>
  <li>In order to run emergency operations from the cloud, you need to have your data synchronized into a location that’s both accessible from the cloud and unaffected by the outage scenario that you are planning for. More likely than not, that location may be the cloud, at which point you might consider running the system from the cloud in any case.</li>
  <li>Using the cloud just for emergency situation deprives you of the benefits of operating in the cloud in the vast majority of the cases.</li>
</ul>

<p>So, this approach may be most suitable for compute tasks that don’t require a lot of data. For example, for an e-commerce site you could allow customers to place orders even if the main site is unavailable by picking from a (public) catalog and storing orders until the main system comes back up. It’ll like beat a cute 404 or 500 page.</p>

<hr />

### ワークロードの需要: バーストと通常 (Workload Demand: Burst vs Normal Operations)

![Separating by workload demand](https://architectelevator.com/assets/img/hybrid_burst.png){: style="float:right;max-width:50%;padding-left:10px;padding-top:1em"}

<p>Last, but not least, we may not have to conjure an outright emergency to occasionally shift some workloads into the cloud while keeping it on premise under normal circumstances. An approach that used to be frequently cited is bursting into the cloud, meaning you keep a fixed capacity on premises and temporarily extend into the cloud when additional capacity is needed.</p>

<p>Again, you gain some desirable benefits:</p>

<ul>
  <li>The cloud’s elastic billing model is ideal for this case as short bursts are going to be relatively cheap.</li>
  <li>You retain the comfort of operating on premises for most of the time.</li>
</ul>

<p>But there’s reasons that people don’t talk about this option quite as much anymore:</p>

<ul>
  <li>Again, you need access to data from the cloud instances . That means you either replicate the data to the cloud, which is likely what you tried to avoid in the first place, or your cloud instances need to operate on data that’s kept on premises, which likely implies major latency penalties.</li>
  <li>You need to have an application architecture that can run on premises and in the cloud simultaneously under heavy load – not a small feat.</li>
</ul>

<p>This option likely works best for compute-intensive workloads, e.g. simulations. It’s also a great fit for one-time compute tasks where you rig up machinery in the cloud just for one time. For example, this worked very well for the <a href="https://www.nytimes.com/2018/11/10/reader-center/past-tense-photos-history-morgue.html" target="_blank">New York Times digitizing 6 million photos</a>  or for <a href="https://www.theverge.com/2019/3/14/18265358/pi-calculation-record-31-trillion-google" target="_blank">calculating <em>pi</em> to 31 trillion digits</a>.</p>

## 実践してみよう

<p>For most enterprises hybrid cloud is inevitable, so you better have a good plan for how to make the best use of it. Because there are quite a few options to slice your workloads across the cloud and your on-premises compute environments, cataloging these options helps you make well-thought-out and clearly communicated decisions. It also keeps you from wanting to proclaim that “one size fits all” – all aspects of being a better architect.</p>

<p>Happy slicing and migrating!</p>

<!-- 
What do the seams look like? 
 -->

<p>ps: if you haven’t seen it yet, have a look at  <a href="https://twitter.com/swardley/status/908031162668474368" target="_blank">Simon Wardley’s humorous take on hybrid cloud</a></p>

<p><em>More thoughts on cloud strategy:</em></p>

<ul>
  <li><a href="/cloud/hybrid-multi-cloud/">Multi-hybrid Cloud: An Elevator Architect’s View</a></li>
  <li><a href="/cloud/dont-run-what-didnt-build/">Don’t run software you didn’t build</a></li>
  <li><a href="https://www.linkedin.com/pulse/can-increasing-your-run-budget-good-thing-gregor-hohpe/">Increasing your “Run” budget may be a good thing</a> [Linkedin]</li>
  <li><a href="https://www.linkedin.com/pulse/cloud-infrastructure-topic-gregor-hohpe/">Cloud computing isn’t an infrastructure topic</a> [LinkedIn]</li>
</ul>

<p><br /><em>NOTE: As a devout vegetarian, I certify that no elephants were harmed in the production of this article nor any related cloud migrations.</em></p>
