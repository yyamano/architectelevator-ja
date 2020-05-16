---
description: 意識的な決定は優れたアーキテクチャへの大きな一歩です。
original:
  url: https://architectelevator.com/architecture/important-decisions/
---

# 最も重要なアーキテクチャ判断を知らないうちにおこなっていたのかもしれません

意識的な決定は優れたアーキテクチャへの大きな一歩です。

最近、開発者の生産性向上のための製品の選定に関して同僚と話す機会がありました。人が多い空間だったので、他にも製品があるなかでチームがどのように特定の製品を選んだのかに興味を持ちました。同僚はチームでプラットフォームの様々な部分に関してレビュー記事、レビュー、業界アナリストのレポートなどをもとにかなり調査をしたことを強調しました。チームはレビューの評価が高く、最も利用されているように見える製品を選択していました。

同僚が完璧な仕事をしたことについて防御的に説明をしたので、製品選定はチームの主要な決定事項ではなかったことに気づきました。しかしながら、まず、なぜ意思決定がアーキテクチャの非常に重要な要素であるなのかについて振り返ってみましょう。

## これはアーキテクチャですか? 意思決定を見てみましょう

全てのシステムにはアーキテクチャがありますが、意味のあるアーキテクチャ、つまりセレンディピティによるものではなくアーキテクトによって設計されたアーキテクチャは容易ではない意思決定によって方向付けられます。これらは、いくつかの最もらしい選択肢から選んだ決定であり、それぞれに検討すべき長所と短所があります。建物のアーキテクチャから借用した簡単な例がこの点を示しています。

![Two houses](https://architectelevator.com/assets/img/houses_600.png)
***意識的なアーキテクチャのない家とある家***{: style="margin-left: auto;margin-right: auto;display: block;"}

左側の家にはアーキテクチャがあります(全てに存在します)が、意識的なアーキテクチャではありません。重要な決定が欠けているからです。もちろん、ドアは地面に面していますし、窓は壁にきちんと配置されています。残念ながら、これらはアーキテクトへの支払いに値する決定ではありません。

右側の家も同じように見えますが、過度な雪の重さを避けるための屋根の傾斜のような明示的な決定があります。つまり、優れたアーキテクチャは複雑なものではなく重要で意味のある決定を行うものです。

注: オリジナルの記事が[Enterprise Integration Patterns](https://www.enterpriseintegrationpatterns.com/ramblings/86_isthisarchitecture.html)にあります。また、[私の書籍](https://architectelevator.com/book/)で改定されたバージョンを読むことができます。

## 重要な決定はすでに行われています

<p>Coming back to the discussion about selecting tools for a development platform, it occurred to me that selecting the products wasn’t the team’s  biggest decision because they had already made the main decision. They had decided to select the best tool for each component they needed. Alternatively, they could have selected a suite of  tools that could be best integrated into the overall platform.</p>

<p>The team had decided to follow the former approach, perhaps without giving it too much consideration - after all, you’d want the best tools, right? The alternative route, while not selecting the strongest tool for each individual function, could make the best overall solution. So it’s a non-trivial decision because both options are reasonable choices.</p>

<p>Both options also have ramifications. For example, choosing the “best of breed” approach likely means that their platform looks more like a <a href="/architecture/platforms-fruit-salad/">fruit basket than fruit salad</a>.</p>

<p><a href="/transformation/it-decisions/">IT’s challenges with decision making</a> is something I commented on before. Making management aware of decision trade-offs is important, so you need to be conscious of the decisions you are making in the first place.</p>

## 思い込みに気をつけて

<p>Unconscious decisions often come in the form of assumptions. Assumptions are risky because they lead to non-requirements, those requirements that exist but weren’t documented anywhere. Tacit assumptions and unconscious decisions both lead to missed expectations or surprises down the road.</p>

<p>The best way to catch yourself when making such assumptions is to take a step back and zoom out to see the bigger picture. Let’s say you’re in a store buying a sweater and are deciding between one for $100 and a nicer one for $150. Taking a step back, you realize that you already decided to buy a sweater, the place where to buy it, and the price range. Perhaps you are also favoring a specific brand. Starting a comparison matrix between these two sweaters is as meaningless as most score cards in IT that represent the end of a long decision tree, with most considerations made along the way lost. If you feel cold outside, perhaps a scarf would also do instead of a warmer sweater.</p>

## 意識的な意思決定

日常生活において直感と好みに基づく決定には何の問題もありません。しかし、ITは決定とともにはるかに長い寿命を持ちます。100ドル以上の賭けです。したがって、決定する時にはそのことを意識してください。
