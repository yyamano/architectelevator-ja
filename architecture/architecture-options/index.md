---
description: アーキテクチャの価値をビジネス利害関係者にどのように説明しますか? ノーベル経済学賞を受賞したブラックとショールズへの遅延はびっくりするほどうまくいきます。
original:
  url: https://architectelevator.com/architecture/architecture-options/
---

# アーキテクチャ: オプションの販売
      
アーキテクチャの価値をビジネス利害関係者にどのように説明しますか? ノーベル経済学賞を受賞したブラックとショールズへの遅延はびっくりするほどうまくいきます。

しばしばアーキテクチャの価値に関して質問されます。時には実際の興味に基づく質問ですが、時には(歓迎すべき)挑戦です。この質問に対し良い回答ができることはシニアアーキテクトにとって重要なスキルだと考えており、[トランスフォーメーションワークショップ](https://architectelevator.com/workshops/)において同様の演習をおこなっています。この無邪気な質問に対して、技術に詳しくない人々に簡潔で説得力のある回答をすることがどれほど困難なのかを理解しています。XXX

## 決定の遅延の価値は何でしょうか

<p>A colleague once suggested that my KPI should be how many decisions I make. I had a gut feeling that this isn’t what I am after but was unable to intelligently articulate it at the time. However, my gut feel triggered a thought that the inverse, being able to postpone decisions, adds value. This thought led me to a new way of articulating the value I bring as chief architect: I sell options.</p>

## オプション: 決定の遅延

<p>In the financial world, an option is well-known as the right, but not the obligation, to buy or sell a financial instrument at a future point in time (or over a future time span for American-style options). An option is therefore a way to defer a decision: instead of deciding to buy or sell a stock today, you have the right to make that decision in the future, at a known price.</p>

<p>Any person involved in the financial industry knows that options aren’t free: there’s a whole market for buying and selling options and other derivatives. If there was any doubt, it was cleared out by Fischer Black and Myron Scholes, who managed to compute the value of an option with their famous Black-Scholes Formula (see <a href="http://en.wikipedia.org/wiki/Black%E2%80%93Scholes_model" target="_blank">Wikipedia</a>). One important parameter in establishing the value of the option is the <em>strike price</em>, i.e. the price at which the stock can be purchased in the future. The lower this strike price, the higher the value of the option.</p>

## ITオプション

<p>Translating the formula to IT architecture, selling options gives the business and IT a way to defer decisions. What size of server do you need to purchase for a system? If your application is architected to be horizontally scalable, this decision can be deferred: additional servers can be purchased later, at a known unit cost. What authentication mechanism should an application use? An architecture that properly separates concerns allows you to change that decision late in the project or even after go-live, at a nominal cost.</p>

<p>Just as with financial options, it’s important that the right to exercise the option in the future is tied to a known price. In the world of IT architecture this means that a future change or addition to the system can be made at the same or similar cost as doing it today. Following Black-Scholes, options whose strike price is higher than the stock’s current price still have value. So it’s OK if exercising the (architecture) option in the future has a slightly higher price than today. The value of the option originates from being able to defer the decision until you have more information while fixing the price.</p>

## オプションとボラリティ

<p>When I once shared my “option” metaphor with a head of asset management, he not only grasped it immediately, but even took it to a new level: knowing Black-Scholes very well, he immediately concluded that with high volatility (denoted by the letter Sigma, σ, in the formula above) the value of the option increases. Therefore, in times of technological uncertainty, as we are facing them today, the value of the options that architecture sells increases. Businesses should therefore buy more options, i.e., invest more into architecture.</p>

<p>Isn’t it fantastic when a person not from your field adopts your metaphor and takes it to a level that you had not considered yourself?</p>
