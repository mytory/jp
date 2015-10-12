---
title: '[jQuery plugin] 오른쪽 위에 반투명 메세지 박스 띄우는 플러그인 jgrowl'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/616
aktt_notify_twitter:
  - yes
categories:
  - Web publishing
tags:
  - javascript
  - jQuery
---
時間がなくて使い方を詳しく紹介はしませんが′とても簡である。

一動をごか。

<p style="text-align: center;">
  <div class="video-container">
    <div class="video-container__inner">
    </div>
  </div>
</p>

コドは以下の通りです。サンプル1から5まで簡に知ることができる。

<pre>/ / Sample 1 - ただ使用する
$.jGrowl（ "Hello world!"）;
/ / Sample 2 - 中消えて
$.jGrowl（ "Stick this!",{sticky：true}）;
/ / Sample 3 - メッセジにタイトル盛り上げる
$.jGrowl（ "A message with a header",{header： &#039;Important&#039;}）;
/ / Sample 4 - 時間を決める（下記は10秒）
$.jGrowl（ "A message that will live a little longer。",{life：10000}）;
/ / Sample 5 - 表示されるアニメションの設定,オフ時に行するの設定（ただし,手動でオフにすると動作しません。）
$.jGrowl（ "A message with a beforeOpen callback and a different opening animation",{
    beforeClose：function（e,m）{
        alert（ &#039;About to close this notification! "）;
    },
    animateOpen：{
        height： &#039;show&#039;
    }
}）;</pre>

ちょっと見て見たところでは一cssファイルを配置する必要がある。シンプルだ。

jQuery UIを使用することもできるようだが′具的には′何に使うのかよく分からない。

オプションは開かれる速度′最大何個までのメッセジを開くように許可するかどうか′消滅するか′ユザが任意にオフになるまでつけておくかなどがある。どこ浮かぶするかどうかの位置も指定することができる。ツイッタを受けて浮かび上がることもできる。（不思議不思議）

今のプロジェクトに適用してみよう。ふふふ