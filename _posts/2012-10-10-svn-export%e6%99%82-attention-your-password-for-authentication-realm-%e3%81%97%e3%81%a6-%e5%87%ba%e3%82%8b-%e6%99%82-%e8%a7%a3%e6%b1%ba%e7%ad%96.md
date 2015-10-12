---
title: svn export時 ATTENTION! Your password for authentication realm して 出る 時 解決策
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/655
aktt_notify_twitter:
  - yes
categories:
  - 開発ツール
tags:
  - SVN
---
[緑風] もっと ましな 解決策を 見つけて 内容を 追加した 後 再発行する.

<pre>ATTENTION! Your password for authentication realm:

Subversion Repositories

can only be stored to disk unencrypted! You are advised to configure
your system so that Subversion can store passwords encrypted, if
possible. See the documentation for details.

You can avoid future appearances of this warning by setting the value
of the &#039;store-plaintext-passwords&#039; option to either &#039;yes&#039; or &#039;no&#039; in
&#039;/home/hahaite/.subversion/servers&#039;.
-----------------------------------------------------------------------
Store password unencrypted (yes/no)? yes
Please type &#039;yes&#039; or &#039;no&#039;: yes
Please type &#039;yes&#039; or &#039;no&#039;: y
Please type &#039;yes&#039; or &#039;no&#039;: &#039;yes&#039;
Please type &#039;yes&#039; or &#039;no&#039;: no
Please type &#039;yes&#039; or &#039;no&#039;: 18
Please type &#039;yes&#039; or &#039;no&#039;:</pre>

yes入った no入った 中 食われて そのまま 止める.

## 解決策1

[解決策1銀 2011-08-05に 追加した 内容だ. - 緑風]

<a target="_top" href="http://firejune.com/1682">firejune様 ブログで 見つけた 内容</a>載せる.

> ここで しばらく シャベルですくい出してから あきらめる ポン しました. localeこれ ハングルで なっているのが 原因ですね. &#8220;例&#8221; または &#8220;いいえ&#8221;路 入力すると なります.

## 解決策2

これ 解決策は <a target="_top" href="http://kldp.org/node/109560">gnome keyring manager 使って見た 分や, SVN で アムホファアンドエン パスワード 処理法 分かる 分‾</a> を 参考した.

初めから 命令語に 暗号化されるの ない パスワードを 入力する 方法だ. コマンドライン マン 後に `--password myPassword` して 入力して 与える のだ.

こういう 食餌 なる のだ. 暗号を 1234路 仮定しよう.

<pre>svn export svn://192.168.0.100/myProject/trunk . --password 1234</pre>

こういえば 解決される. 別に 良い 方法は ない の ようだ. 暗号を 平問で 入力すると 夏期 だからだ.

そのまま 割 焚く 上官 ないのに, 自動で exportを 回すと 割 焚く シェル スクリプトに 暗号を 平問で 打ちこむと したら まどろみ 気まずい.

もっと ましな 解決策は <a target="_top" href="http://www.linuxforu.com/previews/subversion-16-security-improvements-illustrated/">Subversion 1.6: Security Improvements Illustrated[翻訳: サーブバージョン 1.6 保安 改善 例題]</a>で 捜してみる 数 ある ようだ. 定石どおり 勉強して たい 分は これ 文を 読む 偏移 良い のだ.