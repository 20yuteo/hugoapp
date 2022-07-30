---
title: "ブラウザバックを禁止したくなったら"
date: 2022-06-30
categories:
- Javascript
tags:
- Browser
archives:
- 2022-06-30
keywords:
- Javascript
- Browser
comments:       false
showMeta:       true
showActions:    false
#thumbnailImage: //example.com/image.jpg
---

## 1. これまでの経緯
お客様「ちょっとブラウザバック禁止させてくんね？」  

俺 (ブラウザバック禁止とかチョロそうなタスク来たわ)  

俺「いいっすよ！チャチャっとやっちゃいますよ！」  

この一言で僕は地獄を見ることとなりました。  
これからお話することはブラウザバック禁止対応を甘くみた私の備忘録となります。  
心して聞いてください。。。

## 2. とりあえず結論
完全なブラウザバックの禁止はできません！あきらめましょう！  

そっかぁできないのか、じゃあしょうがない！...  
とはならない人もいるかと思いますのでなぜ完全には防げないのかを解説します！

## 3. chromeではブラウザバック制御ができない
色々ブラウザバック禁止等の情報を調べていると  
javascriptのpopstateを利用して制御する方法が結構出てくると思います。

俺「めっちゃ情報あるじゃん。半日くらいで終わりそうやな。」

高を括っていた私ですがあることに気付きます。

俺「あれ。chromeで発火しねぇんだが...」

> Google working on blocking Back button hijacking in Chrome   
> https://www.zdnet.com/article/google-working-on-blocking-back-button-hijacking-in-chrome/  

2022/6/30時点での情報ですがブラウザの履歴等の操作を行うhistory APIが  
chrome側でブロックされているようです。仕様までしっかりと確認は取れていませんが  
EdgeでもhistoryAPIが動作しないことが確認できました。

## 4. 対応方法
chromeの仕様ですがページを表示しているユーザーが画面上をクリック等の  
アクションをとるとHistoryAPIが発火するようになるようです。  

ユーザビリティ等の観点から考えるとイマイチかもしれないですが必ず一度は  
画面を押下するような作りにする。遷移先でブラウザバックを検知  
(onshowpageで検知できます)することで代替することもできるかも...。  
(ただこの方法はなかなか辛いので全くおすすめしません。)  
一番はブラウザバックさせてもいいような設計にすることが一番ですので  
きちんとお客様に説明して出来るだけ断るように倒すべきかと思います。
