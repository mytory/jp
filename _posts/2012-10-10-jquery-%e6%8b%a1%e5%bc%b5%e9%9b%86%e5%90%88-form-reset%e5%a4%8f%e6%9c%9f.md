---
title: jQuery 拡張集合 form reset夏期
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/261
aktt_notify_twitter:
  - yes
categories:
  - Web publishing
tags:
  - javascript
  - jQuery
---
jQueryで 次と ような コードは エラーが 出る.</p> 

<pre class="brush:js">$(&#039;#myfomr&#039;).reset()</pre></p> 

明確に <a target="_blank" href="http://www.w3schools.com/jsref/met_form_reset.asp">reset()銀 標準 メソッド</a>のに 言葉だ.

たぶん 拡張集合が 配列のように 取り扱いされる ところ 原因が ある ようだ.

こんなに 使えば 解決される.

<pre class="brush:js">$(function(){
  //方法1 - 一つだけ リセット
  $(&#039;#myForm&#039;)[0].reset();
  //方法2 - 文書に ある あらゆる formを リセット
  $(&#039;form&#039;).each(function(){
    this.reset();
  });
});
</pre>

簡単な 解決策が あった. これ のために 退屈せぬよう 苦労したが. やっぱり ググルリングが 力だ.

(もし 拡張集合と言う(のは) 言葉が 疎い 人を のために 言わば, jQuery in Action義 翻訳本 &#8216;プログラミング jQuery&#8217;で $(&#8216;#myId&#8217;) のように $路 くるんだ 子たちを 呼ぶ 言葉(何やらは 分からない;;)を 翻訳した 単語だ.)