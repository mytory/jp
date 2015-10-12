---
title: '[JAVA] HTMLEntities クラス &#8211; PHP義 htmlspecialchars 機能'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/585
aktt_notify_twitter:
  - yes
categories:
  - Web server
tags:
  - JAVA
---
JAVAで <を <で 変更すると する 仕事が 生じた.

PHPには こいつが 基本機能(htmlspecialchars)で あるが, JAVAには 基本 機能で あるの ない.

したがって クラスを 使うと する.

それを のために ある 蟹 ところで HTMLEntities クラスだ. java.netで オープンソースで 開発される 遊ぶことだ.

*   <a target="_top" href="http://www.tecnick.com/public/code/cp_dpage.php?aiocp_dp=htmlentities">HTMLEntities Class 紹介</a>
*   <a target="_top" href="http://sourceforge.net/projects/htmlentities/">HTMLEntities Class ダウンロード</a> : ダウンし Zip ファイルで www フォルダに ある jarを 使えば なる.

使い方は 簡単だ.

一応 importを すると するのに, インポート 経路は com.tecnick.htmlutils.htmlentities.* 路 すれば なる.

コードは 下のように 使う.

<pre class="brush:java">String str = HTMLEntities.htmlentities(str);</pre>

何 枝 メソドが もっと ある. 圧縮 解けば 出る ファイルたち 中 doc フォルダで index.htmlを 開けば 文書が 寝る 整理されて あるから それを 見れば なる.