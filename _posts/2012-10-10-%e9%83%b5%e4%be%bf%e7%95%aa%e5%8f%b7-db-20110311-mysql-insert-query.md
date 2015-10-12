---
title: 郵便番号 DB 20110311 mysql insert query
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/397
aktt_notify_twitter:
  - yes
categories:
  - Web server
tags:
  - MySQL
---
<a title="郵便局の 郵便番号 APIを 利用して 郵便番号 検索 サービスを 作って 見よう (1) サーバー団" target="_top" href="http://mytory.local/archives/1284">郵便局で 提供する オープン API</a>街 あるが, 気難しくて, 活用すること 大変な 部分図 ある.

ところが <a href="http://www.zipfinder.co.kr/zipcode/index.html" target="_blank">郵便番号 DBを 提供する ところ</a>西 ダウンを 受ければ, 今度には 卵生 初め 見る dbf ファイルで なって ある. 勿論 これ ファイルは エクセルで 寝る 開かれる. それでは こいつを どうに mysqlに 入れようか&#8230;

初めには エクセルで 違う 名前で 保存を 選択した 後 cvs路 変えた 次,(それでは テキスト ファイルが なる.) エディット プラスで 開いて いちいち 探し 変えるのを した. とても 面倒だったし, 結局 だ したが 間違いが 出た. シャング.

今度は phpmyadmin義 import メニューを 寝る よく見た. Format of imported file 項目が あったし, CVS 形式が あった. エクセルで CVS路 保存した 次 ここ 入れた. 大成功!

勿論, 設定は 必要だった. 下のように 言葉だ. (多分 クリックすれば 拡がる ことだ.)

<img class="aligncenter" src="http://dl.dropboxusercontent.com/u/15546257/blog/mytory/old-images/1/cfile30.uf.1249464E4D4BC8F9262EF9.jpg" alt="" height="189" width="580" />

うん. 一応 フィールド 仕分け者を 読点で 変えたし, フィールド くるむのを 消した. 竝び 仕分け者は そのまま オートで した.

といったところ 成功的に 入って行った. ナイス!(勿論, DBわ フィールドは あらかじめ 生成して 置いた.)

そして また 活用して 食べようと 出すのを した. 私が 使った 奴は フィールド 六つ ケのもの やつだ. 必要な 方々は ダウンして 使いなさい. 私も 引き続き 作り 面倒で 必要ならば ダウンして 使おうと する.

[2011年 3月 11日付け 郵便番号 mysql export ファイル ダウンロード  
][1]

 [1]: https://docs.google.com/leaf?id=0B1y-xjZYE3AqMzFhNzEzYWUtMWY1OC00MGIyLWI5NGYtZmQ1YzY5YWZmZDVi&hl=ko