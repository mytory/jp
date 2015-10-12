---
title: '[APMSETUP 7] Request Entity Too Large &#8211; post_max_sizeと upload_max_filesize 用量を だ 育てたのに 用量 だから アップロードが 中 なると 出る 時'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/717
aktt_notify_twitter:
  - yes
categories:
  - Web server
tags:
  - apache
---
**Request Entity Too Large**

<pre>The requested resource
 /folder/
 does not allow request data with POST requests, or the amount of data provided in the request exceeds the capacity limit.</pre>

<img class="aligncenter" src="https://dl.dropbox.com/u/15546257/blog/mytory/Request-Entity-Too-Large.png" alt="" height="230" width="515" />

用量が 別に 大きくも ない ファイルを アップロードさせたが 上と ような エラー メッセージが 浮かんだ. 明確に php.ini で post\_max\_sizeと upload\_max\_filesize 義 用量を ふやしたのに そうだった.

問題は php街 なく apacheであった.

解法は <a target="_top" href="http://www.apmsetup.com/board.php?bid=513&mode=view&uid=21942">&#8220;Request Entity Too Large エラー メッセージ&#8221;</a>で 捜した.

## 解法 1. 設定 用量を ふやす

<pre>C:APM_SetupServerApacheconfextrahttpd-modsecurity.conf</pre>

上 ファイルを メモ帳や テキスト 編集機で 開いて 下の 文具を 捜す.

<pre>SecRequestBodyLimit 131072</pre>

数字を ふやす.

ところが なぜかは 分からないが, これ 方法は お勧めするの ないと する. 理由は 分からない. 分かって 判断しなさい.

## 解法2. modsecurityを 非活性化する

<pre>C:APM_SetupServerApacheconfhttpd.conf</pre>

上 ファイルを 開く. そして 下の 部分を 捜す.

<pre>Include conf/extra/httpd-modsecurity.conf</pre>

これを こんなに 直す.

<pre>#Include conf/extra/httpd-modsecurity.conf</pre>

前に #万 付けて 与えれば なる ことだ.