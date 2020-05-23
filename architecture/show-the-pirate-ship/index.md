---
description: アーキテクチャ図にはシステムの主要な目的が描かれるのではなく、個々の部品全てが描かれる傾向があります。これを逆にすると、よりよく表現された図になるだけでなく、意思決定も改善されます。
original:
  url: https://architectelevator.com/architecture/show-the-pirate-ship/
---

# 良い意思決定のために海賊船を見せよう

アーキテクチャ図にはシステムの主要な目的が描かれるのではなく、個々の部品全てが描かれる傾向があります。これを逆にすると、よりよく表現された図になるだけでなく、意思決定も改善されます。

## 教えることは最高の教師です

ちょうど、[アーキテクトエレベーターにの乗ろう](https://architectelevator.com/workshops)という二日間の楽しく実例の多く含まれた二日間のワークショップが終わったところです。ワークショップの冒頭で、
講師である自分自身もワークショップに参加していることを参加者に強調して伝えます。私にとってもワークショップは素晴らしい学びの機会だからです。説明することは理解するための最善の方法です。また、演習や議論から得るものも多いのです。参加者の幅広いXXXコンテキストXXXから様々な事例を得ることができるからです。最後に、要旨と話の流れが洗練されます。何十人もの優れたアーキテクトが質問するより良いロジックのテストは存在しません。

つまり、正しい教育は二車線道路なのです。トレーニングコースに参加すると講師が教えるだけなのか、あるいは学んでもいるのかがすぐにわかります。後者の方が役に立つと思います。

## 海賊船を見せよう

ワークショップの演習の一つは、[私の本](https://leanpub.com/37things)の中の「海賊船を子供達に見せよう」を元にしています。このアドバイスは典型的なLegoの箱の参照です。箱の外には小さな部品全てが表示されて入るわけではありません。海賊船(あるいは部品から作れるもの)が表示されています。製品の最終的な形を見ると子供達は興奮し、中に入って入る部品の実際の目的を理解します。

残念ながら、ITには正反対のことを行う傾向があります。全ての小さな部品を極端に詳細に見せたがりますが、そこから出来上がる海賊船を見せることを忘れています。これが、ビジネスにとってITが多くのお金が入っていき、出てくるものはほとんどない謎の「ブラックボックス」のままである理由の一つです。

## Monitoring architecture

ワークショップでは、参加したアーキテクトがシステムの構造を描きます。この演習の目的は、参加者の多くがよく理解しているシステムのアーキテクチャを記述する様々な方法を見ることです。したがって、アプリケーションの状態を監視し、もし何かおかしければアラートを通知する抽象的なモニタリングシステムを題材にしました。モニタリングシステムの良いところは、ほとんどのエンジニアが関係せざるを得ないことです。

演習の一環として小さなカードの束をアーキテクト達のチームに渡しす。チームのタスクは、それら小さな部品を全て組み込んだ「良い」アーキテクチャ図を描くことです。小さなチームに分かれて行うので、結果を比較し、批評することができます。

![Monitoring architecture team exercise](https://architectelevator.com/assets/img/monitoring_exercise.jpg)

カードにはブラックボックスモニタリング、ホワイトボックスモニタリング、ログ集約、時系列データベース、トリガー、アラートなどみんなが知っているモニタリングシステムの要素が含まれています。

この演習をかなり楽しいものです。約10分のディスカッションの後、カードを並べ替え、フリップチャートにアーキテクチャ図を描きます。だいたいこのような図が出来上がります。

![Drawing a monitoring architecture](https://architectelevator.com/assets/img/monitoring_sketch_1.jpg)

通常、アーキテクチャ図には、アプリケーションからセンサー、ログ、ログ集約、時系列データベース、アラート、オペレータへの連絡に至るクリーンなデータフロー、制御フローが描かれます。ほとんどの場合、図はきちんと構造化されており、基盤となるシステムのセマンティクスを表現するビジュアル言語で書かれています。

## 目的を考える

スケッチの発表と議論の後、いつも「このシステムの目的は何ですか」と無邪気に質問します。最初は、ほとんどの参加者は最初はシステムの目的を異常や停止を検出し、誰かに通知することだと考えます。ちょっとした指摘をすると、参加したアーキテクトは「ズームアウト」し、*システムの可用性を最大化する*ことが真の目的だと認識します。もし、可用性が問題にならないのであれば、モニタリングの必要はありません。システムのダウンタイムを認識し、迅速に復旧することでシステムの可用性は最大化されます。

## ループを閉じる

次に「海賊船を見せる」ために画像を拡大することに挑戦してみましょう、。このケースの場合、*海賊船*はダウンタイムを最小化し、システムの可用性を最大化することです。オペレータからアラートによって発生した課題につながった線を描き、文字通りループを閉じます。

![Showing the pirate ship](https://architectelevator.com/assets/img/monitoring_sketch_2.jpg)

*テスト対象システムからアラートと解決までのループを図に書けば、システムの目的を視覚的に強調できます。問題が発生してから解決するまでの時間を最小化することです。これは、システムの平均復旧時間(MTTR)です。ループの途中にこれを思い切って描きます。

## より良い意思決定をおこなう

目的とシステム全体が明確になれば、つまり「全体像」を描くことができれば、より良い意思決定が可能になります。MTTRは停止を検出するのにどれくらい時間がかかり、問題を解決するのにどれくらい時間がかかりますかという二つの要素で構成されていることがわかりました。

この側面が明確になることにより、企業がより良いモニタリングシステムに投資すべきかどうかを判断できます。例えば、停止を検知するのにかかる時間を30分から数分に減らす良いセンサーや賢い分析機能を提供するモニタリングシステムへの投資は良いアイデアに見えます。

Once you consider, though, that resolving an outage takes several hours, the picture changes. Investing let’s say half a million Dollars to reduce the MTTR from 4.5 hours to 4.1 hours doesn’t look that great anymore. Instead, you’d be looking to reduce the time spent resolving outages, e.g. by better transparency across systems or higher levels of automation that can quickly roll back the deployed software to an earlier, stable version. Drawing a better picture has helped us make better decisions.</p>

## 教師を教育する

確かに、システムの「モニタリング」側を説明するカードだけを手渡し参加者を少し引っ掛けました。しかし、同時に欠けている部分を発見し、全体像を描くために「ズームアウト」する能力は、アーキテクトにとって重要な能力です。

<p>The most valuable part for me is that the exercise didn’t start out this way. Originally it was just a way to draw a few architectures and compare them. Through the dialog with attendees it evolved into combining it with the <em>Pirate Ship</em> and decision making, drawing multiple elements of the class into a single exercise. Teaching really is the best way to learn.</p>
