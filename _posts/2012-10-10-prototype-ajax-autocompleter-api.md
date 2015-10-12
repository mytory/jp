---
title: '[prototype] Ajax.Autocompleter API'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/239
aktt_notify_twitter:
  - yes
categories:
  - Web publishing
tags:
  - javascript
---
プロトタイプと スクリブタキュルロスは 勉強するの ないことに したし, jQuery江戸 これ 文を 使って いくら 中 あって <a target="_top" href="http://jqueryui.com/demos/autocomplete/">jQuery UI義 AutoComplete</a>街 登場した.

ハングルも 寝る 作動する. もう 実際で 適用して 見た.

そうだから jQuery UIを 使うのを 勧める.

&#8212;&#8212;&#8212;- 以下 元々 内容 &#8212;&#8212;&#8212;&#8211;

プロトタイプも 機会 なれば 勉強する つもりだ. プロトタイプの スクリブタキュルロスに ある <a href="http://wiki.github.com/madrobby/scriptaculous/ajax-autocompleter" target="_blank">Ajax.Autocompleter義 DOC</a>だ.

知りたかった 機能を 説明して ある 文を 捜した. 一応 リンクして : <a href="http://trend21c.tistory.com/360" target="_blank">http://trend21c.tistory.com/360</a>

必要な 部分を 掻いた. 冊題目だけ 自動完成で 検索すれば 本 関連 価格 情報 などが 自動で よって 入って来るように して たい 時 使う 方法だというのに, 正確に どうに 使うかは 知らせてくれるの なくて あるが 手がかりを 酒庫 ある.

自動検索される 内容の中で 検索語では 入れて たいでしょう ないが 追加して たい テキストが ある 場合も あります.

例を 入れば 本 題目と 価格, 出版社, 著者を 一度に 現わして シブギンしたのに

検索語では 題目だけ 入力されるように して たい時!!!!

ところで こういう 場合を のために scriptaculous増えた 次と ような 方法を 使えば なります.

<pre class="brush:html">&lt;li&gt; 冊題目 &lt;span class="informal"&gt;ゴムセックエヌンナタナジアンヌンギタゾングボ&lt;/span&gt;&lt;/li&gt;</pre>

こんなに マークアップを するように なれば(informal クラス人を 使用) informal クラス 中に ある テキストは 自動完成 キーワードが 完成される時 含まれるの ないです.