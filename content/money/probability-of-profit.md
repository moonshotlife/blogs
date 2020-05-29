+++
title = "Probability of Profit"
author = ["gram"]
date = 2020-05-28T23:08:00-07:00
lastmod = 2020-05-28T23:17:25-07:00
tags = ["options"]
categories = ["Money"]
draft = false
+++

オプションはexpiration dateのときにIMTになる確率(Probability of Profit, or POP)を統計学的に求めることができるので、OTMのオプションを売ることにより50%の確率より有利な確率で利益を得ることが期待できる。ただしOTMなので確率が上がるに従って利益幅は小さくなる。大数の法則(The law of large numbers)より、高確率のトレードを数多くこなすことにより確率50%前後しかない株式(極論すると上がるか下がるか)よりリスクを抑えて利益を上げることが期待できる。

と、ここまではTastytradeやOptions Alphaの受け売りであるが、実際の確率については根拠をあげて詳しく説明してくれるページがあまり見つからなかった。deltaがPOPであるとか、spreadのときは1 - credit (strike widthが$1のとき)であるとか、さらっと書いてあるだけ。deltaで近似できることについては、Tastytradeの[このセグメント](https://www.tastytrade.com/tt/shows/the-skinny-on-options-math/episodes/probability-of-profit-08-06-2015)が数式を交えて説明していてなるほどと納得した。

vertical spreadのPOPについては、自分で考えてみた。Strike width wのcreditがcのとき、POP pは

-   max profit = c
-   max loss = w - c

であるので、

\\[c \* p - (w - c) \* (1 - p) >= 0\\]

のpを求めればいい。数式を解いていくと、

\\[c \* p - (w - w \* p - c + c \* p) >= 0\\]
\\[c \* p - w + w \* p + c - c \* p >= 0\\]
\\[p \* w - w + c >= 0\\]
\\[p >= (w - c) / w\\]
となる。合ってるかな〜。

でも、オプション価格(premium)って絶えず変わるから、確率ってあくまでopen時の確率に過ぎない。だからopen時にPOPが80%あったとしても、credit価格の推移をちゃんとチェックし続けないとってことだ。
