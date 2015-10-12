---
title: アパッチ 仮想ホスト 作動 中 割 時 _default_ VirtualHost overlap on port 80, the first has precedence
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/555
aktt_notify_twitter:
  - yes
categories:
  - Web server
tags:
  - apache
---
英語で なって あるが ここが 寝る 説明されて ある :&nbsp;<a href="http://www.cyberciti.biz/faq/warn-_default_-virtualhost-overlap-port80-first-hasprecedence/" target="_blank" title="[http://www.cyberciti.biz/faq/warn-_default_-virtualhost-overlap-port80-first-hasprecedence/]路 移動します.">Apache: [warn] _default_ VirtualHost overlap on port 80, the first has precedence Error and Solution</a>

要旨は, <a href="http://mytory.local/archives/13" target="_blank">仮想 ホストを 付ける 時</a> 仮想ホスト 設定を 少なくて 準 部分に NameVirtualHost と 少なくて 与えると するという ことなのに, これ 時 まともに 少なくて 与えると するという ことだ. 例を 見よう.(出処は <a href="http://www.cyberciti.biz/faq/warn-_default_-virtualhost-overlap-port80-first-hasprecedence/" target="_blank" title="[http://www.cyberciti.biz/faq/warn-_default_-virtualhost-overlap-port80-first-hasprecedence/]路 移動します.">上 リンク</a>)

<pre class="brush:plain"># My Virtual Hosts Config File for Two Domains
NameVirtualHost *:80

&lt;VirtualHost *:80&gt;
    ServerAdmin webmaster@theos.in
    DocumentRoot "/usr/local/docs/theos.in"
    ServerName www.theos.in
    ServerAlias theos.in
    ErrorLog "/var/log/theos.in-error_log"
    CustomLog "/var/log/theos.in-access_log" common
&lt;/VirtualHost&gt;

&lt;VirtualHost *:80&gt;
    ServerAdmin webmaster@nixcraft.com
    DocumentRoot "/usr/local/docs/nixcraft.com"
    ServerName www.nixcraft.com
    ServerAlias nixcraft.com
    ErrorLog "/var/log/nixcraft.com-error_log"
    CustomLog "/var/log/nixcraft.com-access_log" common
&lt;/VirtualHost&gt;
</pre>

ここで 注目する 部分は ところで *:80載せる. 仮想 ホストの フォトと `NameVirtualHost`義 フォトを 合わせて 与えると する.

もし IP路 仕分けを したら *街 なく IPを 少なくて 与えると すると する.

`NameVirtualHost 192.168.0.99:80` する 式で 言葉だ.

## 応用!

定木, ところが 私の 場合には あのように しても 作動が 中 いい. なぜだったろうか?

virtualHost 正義 ファイルが 色々 犬 あった 蟹 原因だ. 私 ような 場合は ウブントを 使う. ウブントは `/etc/apache2/sites-enabled` フォルダに ある シンボリック リンク<sub>(リンクを 消せば 原本まで 消される 恐ろしい リンク!)</sub>街 ところで 仮想 ホストを 定義する ファイルなのに, 下の 絵を 紫.

<img alt="" class="aligncenter" filemime="" filename="cfile8.uf.175D704D4D4BC970289B63.png" src="http://dl.dropboxusercontent.com/u/15546257/blog/mytory/old-images/1/cfile8.uf.175D704D4D4BC970289B63.png" height="393" width="550" />

default 外にも <a href="http://www.mindtouch.com/" target="_blank" title="[http://www.mindtouch.com/]路 移動します.">dekiwiki</a> という 奴が 見える. こいつも ところで 仮想ホストを 定義して あった のだ! こいつは <a href="http://www.mindtouch.com/" target="_blank" title="[http://www.mindtouch.com/]路 移動します.">dekiwiki</a>を 設置すれば 自動で 生成される やつだ だから 気づくの できなかった のだ. OTL;;

定木, これ ファイルを 剥いて 見れば これ 仮想ホストは 下のように 始める.

<pre class="brush:plain">&lt;VirtualHost *&gt;</pre>

すなわち, そうするので 違う 仮想 ホストたちも 手始め 部分を&nbsp;

<meta content="text/html; charset=utf-8" http-equiv="content-type" />


<VirtualHost \*:80> これ なく&nbsp;<VirtualHost \*>路 設定を 日 酒庫, 仮想ホスト 正義 ファイル マン 前に&nbsp;

<pre class="brush:plain">NameVirtualHost *
&lt;VirtualHost *&gt;
</pre>

と 少なくて 与えると する のだ.

私が 勧奨する のは 仮想 ホスト 敍情 ファイル 以外に httpd.conf に 少なくて 与える のだ. 仮想 ホスト 設定ファイルを 痛がら 読み取り 前に 私 NameVirtualHost * を 読むと 夏期 だからだ.

こんなに あらゆる ガール 終わらせれば あらゆる 仮想ホストが まともに 帰ること 始めた.

もし 直したのに [warn] NameVirtualHost *:80 has no VirtualHosts なんか エラーが 出れば どこかに NameVirtualHostを 少なくて 置いた のだ. 捜して 来書 消して 走者.