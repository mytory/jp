---
title: jquery $.getおこるが $.post義 callback 関数 中で this
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/275
aktt_notify_twitter:
  - yes
categories:
  - Web publishing
tags:
  - javascript
  - jQuery
---
下の ような コードだった.

<pre class="brush:js">$(&#039;button.delete&#039;).click(function(){
  $.get(&#039;url&#039;,{a:1,b:2}, function(data){
    $(this).parent().remove(); //問題は ところで ここ
  });
});
</pre>

私が 意図した のは ボタンの 親 客体を 飛ばす のだった. 削除 ボタンだったので 言葉だ. ところが 中 飛ぶ の .

しばらく 迷ってから ファイアバグの js ディバッグ 機能を 利用して $(this).parent().remove(); コードが ある 竝びで スクリプトを 止めて 客体たちを 確認した.

凡そ格. this増えた ajaxで 使う 客体だった. xhrこれ 彼 中に ある ので BoA xhr銀 ない の ようで. 下の 絵を 見れば this義 正体を 確認する 数 ある.

<img src="http://dl.dropboxusercontent.com/u/15546257/blog/mytory/old-images/1/cfile23.uf.160C66494D4BC8A4261149.png" class="aligncenter" alt="" height="444" width="567" />

そのため 解決した 方法は, $.get これ 出ること 前に $(this).parent()を var widgetに 入れて 活用した.

変数を 少なく 使う 蟹 能は ない よう.