---
title: 'css positon: fixed'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/36
aktt_notify_twitter:
  - yes
categories:
  - Web publishing
tags:
  - CSS
---
下の cssコードは 該当 クラスの 客体を 画面 下側に 固定させる. スクロールを しても 相変らず 彼 位置に ある. すなわち, 漂う 子たちのように なる のだ.

<pre>.クラス名前 {
	position: fixed;
	bottom: 0;
	left: 0;
}</pre>

fixed 速成は 次 特性を 持つ.(一応 今日 私が 扱いながら 分かるように なった, 分かっておけば 良い 点に 大海.)

1.top / left / right / bottom などで 位置を 指定して 与えると する.

2.位置を 指定して 主旨 なければ 客体の コード上 位置が 固定される 位置が なる.(指定するの なくて して見なさい.)

3.位置を 指定してくれれば 上位 客体を 無視した のまま 位置を 取る. (left:0 で おけば 画面 端に 位する.)

4.幅が inlineのように なる. blockのように 作って たければ widthを 指定して 与えると する. そのまま 全体 幅で して たければ 悩む の なく 100%路 しなさい. それでは 画面 横サイズが なる.(上位 客体の 横サイズを 継がれる 蟹 ないという 点が 重要だ.)