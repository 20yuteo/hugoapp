---
title: "DDDにおける「値オブジェクト」とは"
date: 2022-10-17
categories:
- DDD
tags:
- DDD
- ValueObject
archives:
- 2022-10-17
keywords:
- DDD
- Value Object
comments:       false
showMeta:       true
showActions:    false
#thumbnailImage: //example.com/image.jpg
---

## 1. 初めに
「ドメイン駆動設計入門 ボトムアップでわかる！ドメイン駆動設計の基本」から値オブジェクトとは何なのかをまとめる。

## 2. 「値オブジェクト」とは？
- システム開発においてシステム固有の値を定義することが時に必要になる
  - このシステム固有の値を表現するために定義されたオブジェクトが「値オブジェクト」である

## 3. 「値」とは？
- 普段何気なく利用している数字、文字などの値は「一定の性質」を持っている
  - この性質こそが値オブジェクトを理解する鍵となる
- 「値」の性質は次の三つ
  - 不変である
  - 交換が可能である
  - 等価性によって比較できる
- 上記の「値」が持つ性質は「値オブジェクト」にそのまま適応される

## 4. 不変である
- 「値」が不変であるとの感覚は我々にはピンとこないかもしれない
- しかし、仮に可変であった場合、下記のようなことが可能になってしまう。
```javascript
"おはようございます".changeValue("こんにちは");
console.log("おはようございます"); // 2023が出力される
```
- つまり、以下のようなクラスは「値オブジェクト」としては不適切である
```javascript
const user = new User({
    name: "user name"
});
user.changeName("anothoer user name");
console.log(user.name);
```

## 5. 交換が可能である
- 不変であるが交換が可能とはどうゆうことか？
  - 我々は普段、何気なく値の交換をしてる。
```javascript
let user = new User({ name: "first user name" });
user = new User({ name: "another user name" });
```
- 上記が値の交換である。
