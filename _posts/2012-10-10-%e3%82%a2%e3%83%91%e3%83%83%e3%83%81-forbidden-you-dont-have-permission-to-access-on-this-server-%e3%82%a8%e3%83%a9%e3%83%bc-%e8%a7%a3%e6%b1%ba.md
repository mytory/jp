---
title: 'アパッチ Forbidden  You don&#8217;t have permission to access / on this server. エラー 解決'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/801
aktt_notify_twitter:
  - yes
categories:
  - Web server
tags:
  - apache
---
<a title="メックブック アパッチ 仮想ホスト 活性化を ためには ‘ウェブ 共有’を つけると する" target="_top" href="http://mytory.local/archives/3135">メックブックで アパッチ 仮想ホスト 設定</a>に 成功したが 今度は `Forbidden` エラーを ふいた.

<pre>Forbidden
 You don&#039;t have permission to access / on this server.</pre>

エラー ログを 見れば 下のように セングギョモックオッダ.

<pre>client denied by server configuration : フォルダ 経路</pre>

こういう エラーが 出る 理由は apache 設定で `/` 下位に 接続する ガール 全部 阻んで 置いた だからだ. `/` 下位を 皆 阻んで, 開いておく 所だけ 指定する 形式だ. そのため 私は `/etc/apache2/extra/vhost.conf`に 下と ような 設定を 追加した.

もし 仮想ホストを 使うの なかったら `/etc/apache2/httpd.conf`に 入れれば なる.

<pre class="brush: xml; gutter: true; first-line: 1">&lt;Directory /Users/mytory/workspace&gt;
   Options FollowSymLinks
   AllowOverride None
   Order deny,allow
   Allow from all
&lt;/Directory&gt;</pre>

私は`/Users/mytory/workspace`義 下位 フォルダたちで 作業を 夏期 だから こんなに 使った ことで, 各自 適当に 使って 与えれば なる.

## パーミッション

エラー ログを 見たが パーミッションが ないと 出れば パーミッションを 与えれば なる. 私は ローカルで 作業する 用途で 設定した ことの だから 誰 心配なしに 下のように 命令を 下った.

<pre class="brush: bash; gutter: true; first-line: 1">sudo chomd -R 755 .</pre>

するが サーバーを 実際で 回したら あらゆる ファイルの パーミッションは 基本に `644`(持ち主は 読み取り/書き取り 可能, グループは 読み取り 可能, ゲスト 読み取り 可能)与・野党 割 ことだ 多分.

こんなに して 痛がるのを 改めて始まれば 終り!

<pre class="brush: bash; gutter: true; first-line: 1">sudo apachectl restart</pre>