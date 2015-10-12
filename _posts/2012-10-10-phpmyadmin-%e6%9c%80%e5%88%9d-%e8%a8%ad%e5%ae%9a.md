---
title: phpMyAdmin 最初 設定
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/378
aktt_notify_twitter:
  - yes
categories:
  - Web server
tags:
  - PHP
---
ところどころ 散らばって ある 説明は 別に 巻くに 入るの ない. 説明が まちまちで 彼 方法 でなく 違う 方法が ない ように 説明する 蟹 巻くに 中 入る. 勿論 私も そんな 式で 説明する 時が あるという ガール 分かる. するが phpMyAdmin ような 大衆的な プログラムは もうちょっと 正確な 説明が 必要なの ないが たい.

そして 核心は, プログラム ホームページに 行って <a href="http://www.phpmyadmin.net/documentation/" target="_blank">document 項目</a>を 見る のだ. そこに 基礎 説明が なって ある. 応用は 分かって する のだが, 基礎が なければ 応用も まともに 割 数 ないという のは 数学時間にだけ 当たる 言葉は ない. プログラミングも ようだ.

ヨトンガンに, <a href="http://www.phpmyadmin.net/" target="_blank">phpMyAdmin</a>を 敷く 度に ブログで 設定方法を 捜して 報告 たまに 中 なって 迷う 場合も あって したが 今日は そのまま phpMyAdmin ホームページの 説明を 捜して 見た. 振作に 捜して ボール ガール する 考えが 入った. 

ヨトン, 必要が すぐ 急な 人は 下の ファイルを 使えば なる. 児, 内 phpMyAdmin バージョンは 3.3.2だ.

<a target="_top" href="http://dl.dropboxusercontent.com/u/15546257/blog/mytory/old-images/1/cfile23.uf.147962544D4BC8F21FA64E" class="aligncenter"></a>cfile23.uf.147962544D4BC8F21FA64E

私が ここ 引用した 部分は <a href="http://www.phpmyadmin.net/documentation/#quick_install" target="_blank">Quick Install 部分</a>載せる. これ 方法を 使って config.inc.php ファイルを 作れば 私たちが よく 向い合う phpMyAdmin 画面を ボール 数 ある. ウェブ ログイン 窓だ.

<img src="http://dl.dropboxusercontent.com/u/15546257/blog/mytory/old-images/1/cfile29.uf.142A68484D4BC8F2299277.jpg" class="aligncenter" alt="" height="393" width="409" />

受動で config.inc.php ファイルを 作って 下の 内容を 満たして 入れれば なると なって ある. config.sample.inc.php ファイルを 使う 首都 あると 使って ある. ヨトン 下の コードが 核心だ.

<pre class="brush:php">$cfg[&#039;blowfish_secret&#039;] = &#039;ba17c1ec07d65003&#039;;  // 誰か 満たして 入れれば なる.

$i=0;
$i++;
$cfg[&#039;Servers&#039;][$i][&#039;auth_type&#039;]     = &#039;cookie&#039;;
</pre>

上で $cfg['blowfish_secret'] に 入って行く のは 誰か 入れれば なる. 私も 誰か 入れた. 例えば こういう こと 言葉だ. T^UIGHF^R^r76uygt87y8 ハングルで しても なるかは 中 して見た;;

これ 内容を 満たして phpMyAdmin フォルダの ルートに 頭面 なる. 簡単だ.

次, 敢えて ログイン 過程を 経るの ないように 作る 方法も ある. これ 方法は 当然, 管理者 ログイン ような 蟹 なって ある 時だけ config.inc.php を 読む 数 あるように セッション チェックを すると 割 ことだ. 中 それでは DBを 満天下に 公開する 蟹 なったら 言葉だ.

ヨトン 下のように 万たち 首都 ある.

<pre class="brush:php">$i=0;
$i++;
$cfg[&#039;Servers&#039;][$i][&#039;user&#039;]          = &#039;アイディー&#039;;
$cfg[&#039;Servers&#039;][$i][&#039;password&#039;]      = &#039;パスワード&#039;; // ここ パスワードを 入れなさい
$cfg[&#039;Servers&#039;][$i][&#039;auth_type&#039;]     = &#039;config&#039;;
</pre>

簡単だ.

今まで 設定のために 苦労した こと 思えば こっそり 腹立つ. これ 外にも 多様な 設定法が ある. 必要ならば 使うように なる 側で, 使えば 説明も 少ないように する. すぐ なるのは ない ことだ.

以上.