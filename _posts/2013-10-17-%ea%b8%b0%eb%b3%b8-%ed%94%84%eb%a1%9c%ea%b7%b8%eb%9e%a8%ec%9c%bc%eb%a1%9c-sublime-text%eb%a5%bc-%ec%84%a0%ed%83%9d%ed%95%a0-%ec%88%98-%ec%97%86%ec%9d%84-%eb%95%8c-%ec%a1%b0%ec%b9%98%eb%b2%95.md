---
title: 基本的なプログラムにsublime textを選択することができない場合措置法
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/2215
categories:
  - etc
tags:
  - Program
---
64ビットsublime textをインストールした後からsublime textを既定のプログラムとして選択することができなかった。

面倒であるが検索して解決策を探した。

1.  ` Window+ Rを押した後<code> regedit`と書いてエンター。その後、レジストリエディタを実行します。</code>
2.  `コンピュータ/HKEY_CLASSES_ROOT/Applications`に入った後、` sublime_text.exe`を見つけて削除します。

その後、再び指定をすることができるようになる。

ところでは消去し再び敷いてもされるそういえばいたよ。