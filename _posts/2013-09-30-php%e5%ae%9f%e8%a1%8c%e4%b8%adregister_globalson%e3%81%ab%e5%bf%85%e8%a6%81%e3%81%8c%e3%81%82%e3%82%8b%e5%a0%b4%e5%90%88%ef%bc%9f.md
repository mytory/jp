---
title: PHP実行中register_globals=Onに必要がある場合？
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/2211
categories:
  - Web server
tags:
  - PHP
  - TIP
---
ローカルの開発環境を備えて開発するとき、 `register_globals = Off`にしておいて作業する。その習慣をべきだと思うからだ。

しかし、すでにそのように処理しておいて`register_globals = On`にする必要が修正作業を行うことができる場合がある。完全に近道であり、推奨しない適切な方法であるが、そんな時はこうすれば解決される。

<pre>extract($_REQUEST);</pre>

分かるだろう、 `extract`は、配列の値をすべて引き出してくれる関数と、 `$_REQUEST` `$_GET`の値と`$ _POST`の値の両方を持っている配列です。すべてのページの先頭に`include`するファイルに加え、上記のコードを挿入すると、 `php.ini`ファイルに触れることなく、 `register_globals`を`On`に作成されたのと同じ効果を出すことができる。

もちろん、私は絶対にお勧めできません。避けられない場合にのみ使って必ず仕事が終わった後は、コードを削除しなければならない。意のままにドゥェジンだろうがね。少なくとも、以下のようにも書かなければならない。

<pre>if($_SERVER['REMOTE_ADDR'] == 127.0.0.1){
  extract($_REQUEST);
}</pre>

以上です。