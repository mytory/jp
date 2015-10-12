---
title: "$_SERVER['DOCUMENT_ROOT']わ dirname(__FILE__)"
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/13
aktt_notify_twitter:
  - yes
categories:
  - Web server
tags:
  - PHP
---
`$_SERVER['DOCUMENT_ROOT']`増えた 現在 ファイルの 絶対 経路を リターンして 与える 関数ですよ.

ところが こいつが たびたび 問題を 起こします. まともな 経路を 返すの ない 場合が ある ことですよ.

入って 見たら PHP 固守たちは `$_SERVER['DOCUMENT_ROOT']`を 使うの ないと するんですよ.(そのまま カドラです.)

`$_SERVER['DOCUMENT_ROOT']` 変数 代りに 次 変数を 使って 見れば なる の ようです.

これ 変数(?)増えた 現在 ディレクトリを リターンして 与えます.

<pre class="brush: php; gutter: true; first-line: 1; highlight: []; html-script: false">dirname(__FILE__)</pre>

それでは まともに 出力が なる のを 確認する 数 ある はずです.

`$_SERVER['DOCUMENT_ROOT']`街 なぜ まともに 作動するの ない 場合が ある のか 分かって あった 分 あったら デッグル つけて ください. 私も こいつ だから 苦労ちょっと したんですよ.

これ チップは <a href="http://jptrans.naver.net/k2j_frame.php/korean/csscreator.com/node/10972#comment-46501" target="_top"><code>$_SERVER['DOCUMENT_ROOT']</code> problem という 文に Chris..Sという 人が つけておいた デッグル</a>を 参考しました.

英語 寝る できなくて 凡そ 分かった ことけれども.

それではこれで ^^

## 追加 : 直接 入力が 仮装(家長) こぎれいな よう?

追加で まどろみ もっと 考えを して見ました. 私の 考えに 仮装(家長) こぎれいな のは 直接 入力する のだと ギョルロンネリョッスブニだ.

設置型 ブログ テキストキューブの 場合 `config` ファイルに 直接 住所たちを 入力するように します. fckeditor度 住所を 入力するように します.

どうな 場合でも エラーは 発生する 数 ある の ようで, 柔軟性を 最大で 夏期 ためには 直接 入力受けた のを 使う 蟹 最善である ようです.

config.class.phpを 一つ 作って 置いて そこに 絶対経路 ルート, 相手経路 ルート, ルート 住所を 示す URIを 入れるように すれば 残りは 易しく 解決される のだと 思います.

団, もう 作られた のを 直すと する 場合は 頭痛い 数 あります. そうな 焚く 上の チップを 使う 数 あると 見ます.