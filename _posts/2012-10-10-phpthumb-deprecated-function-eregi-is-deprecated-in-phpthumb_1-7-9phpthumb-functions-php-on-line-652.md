---
title: '[phpThumb] Deprecated: Function eregi() is deprecated in /phpThumb_1.7.9/phpthumb.functions.php on line 652'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/351
aktt_notify_twitter:
  - yes
categories:
  - Web server
tags:
  - PHP
  - phpThumb()
---
phpThumb()を 設置して 機能を チェックして見た. ところが 下と ような メッセージが ズウック 浮かんだ.

&nbsp;

<pre class="brush:plain">Deprecated: Function eregi() is deprecated in /var/www/phpThumb_1.7.9/phpthumb.functions.php on line 652</pre>

&nbsp;

Deprecated増えた 今後 支援を 夏至 ない 計画なので 勧奨するの ないという 言葉だ.

上 文章を 解釈すれば eregi() 関数は 今後 支援するの ない のなので 什 ないでねと言う ことだ. すなわち, 警告 メッセージ.(実際で PHP6からは 関数が 消えると する.) PHP 5.3裏面 上 メッセージが 出ると する. 彼 以下 バージョンでは 登場するの ない よう.

整理すれば? 警告 メッセージだ エラーが なくて, 正常作動する.

それでは, 二 枝 方法が ある.

(1)私 関数を だ 直す.

(2)警告 メッセージを 出力するの ないように 作る.

他人が 作った ライブラリを いちいち 修正する 自分は ないから(勿論 <a href="http://nthinking.net/index.html#reDeprec.html" target="_blank">自動で 修正して 与える プログラム</a>度 あると する.) 警告 担ぐが 出力するの 末子.

&nbsp;

<pre class="brush:php">error_reporting(E_ALL ^E_DEPRECATED);</pre>

&nbsp;

上 コードを 実行 前に 入れて 与えれば なると する.(<a href="http://www.sitehis.com/spb3/sboard3/read.php?db=talk&cateuid=4&uid=167" target="_blank">参考した 文</a>)

定木, phpThumb.phpに ところで 上 コードを 入れれば なる ことだ.

phpThumb.phpを 開けば, マン 上側に 似ている コードが 見える.

&nbsp;

<pre class="brush:php">error_reporting(E_ALL);
ini_set(&#039;display_errors&#039;, &#039;1&#039;);</pre>

&nbsp;

12目 竝びの 上と ような コードを 捜して&#8230;

&nbsp;

<pre class="brush:php">error_reporting(E_ALL ^E_DEPRECATED);
ini_set(&#039;display_errors&#039;, &#039;1&#039;);</pre>

&nbsp;

こんなに 直して 与える.

それでは 万事 ＯＫ.

これ 次からは 上 エラーが 浮かぶの ない ことだ.

## あらゆる deprecatedに 対処して 見よう. php.iniを 直す 方法

php.iniを 直して 見よう.

今は 消えた http://bugs.php.net/23610 という 株少義ページで 対策を 捜す 数 あった.

下のように 直しなさいと言っている. 言うとおりに 日 見よう.

&nbsp;

<pre class="brush:plain">error_reporting = E_ALL & ‾E_DEPRECATED</pre>

&nbsp;

上のように 使えば エラー 報告を 全部 するが, DEPRECATED 義 場合だけ 夏至 ないでねと言う 意味が なる. 詳細な 内容は <a href="http://www.php.net/manual/en/errorfunc.configuration.php#ini.error-reporting" target="_blank">PHP サイトで</a> 見れば なる.

上のように したが 中 なる 場合 E\_ALL 代わり E\_ERRORを 使って 見よう. それでは エラーだけ 出力しなさいと する かけるから 言葉だ.

当然 痛がるのを 改めて始まって 与えると する. ウブント 使用者なら ターミナルで 下の 命令を 打つ. 零 分からなければ そのまま コムトを 再起動しなさい.

&nbsp;

<pre class="brush:plain">sudo /etc/init.d/apache2 restart</pre>

&nbsp;

そうだから 警告 メッセージが すっきり 消えた.