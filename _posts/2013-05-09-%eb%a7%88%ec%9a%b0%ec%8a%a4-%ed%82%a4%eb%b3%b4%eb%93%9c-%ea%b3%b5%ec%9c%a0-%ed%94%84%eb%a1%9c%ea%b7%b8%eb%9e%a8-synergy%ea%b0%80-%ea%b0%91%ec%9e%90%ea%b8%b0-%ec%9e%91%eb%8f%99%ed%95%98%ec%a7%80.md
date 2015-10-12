---
title: マウス、キーボードを共有するプログラム、Synergyが急に動作しないときにチェックすること
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/2024
categories:
  - etc
tags:
  - Program
---
Synergyが突然動作をしなかった。正常に接続が多なった言葉だ。

log levelをdebugに変更し、logを見てから知ることができた。ログに以下のように出てきた。

<pre>locked to screen</pre>

スクリーンに閉じ込められて？なぜ？[検索してみた。出てきた。][1]

Scroll Lockキーが押されているからだった。代替のキーは何のためものであるがこのような場合にのみ人気になるよ！

ヨトンそれを一度押してくれたらよくなる。終わり！

 [1]: http://blog.ajperrins.com/2011/10/synergy-locked-to-screen.html