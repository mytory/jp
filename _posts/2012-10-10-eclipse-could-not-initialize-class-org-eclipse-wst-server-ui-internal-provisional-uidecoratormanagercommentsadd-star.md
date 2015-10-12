---
title: 'Eclipse: Could not initialize class org.eclipse.wst.server.ui.internal.provisional.UIDecoratorManagerCommentsAdd Star'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/216
aktt_notify_twitter:
  - yes
categories:
  - 開発ツール
tags:
  - Eclipse
---
横で 片付けて おけば 以上作動する ないが 人を 非常に かんしゃくが起こるように 作る エラー, Could not initialize class org.eclipse.wst.server.ui.internal.provisional.UIDecoratorManagerCommentsAdd Star これを 解決する 方法を まどろみ 集めることに した.

自主 起きる バグと するのに, 明確な 解決策が ある 件 なくて 多様な 方法が あると する.

一応 第一 簡単な かける イクルリブス アイコン 速成で 入って行って 実行命令 後に -cleanを 付けて 与える ことだ.( <a href="http://54321.textcube.com/7" target="_blank">http://54321.textcube.com/7</a>&nbsp;) プラグインを 初期化する ことと する. ところが 私は これで 中 いい.

中 なれば 右側 上端に ある perspective アイコンで Java EE perspectiveを 見えるように して イクルリブスを 消した つけなさいと する. 私は これでも 解決されるの なかった.( <a href="http://d.hatena.ne.jp/falkenhagen/20091030/1256868650" target="_blank">http://d.hatena.ne.jp/falkenhagen/20091030/1256868650</a>&nbsp; )

<p style="text-decoration: line-through;">
  違う 解決策を 分かる 人は デッグル 残して 週期 望む.
</p>

<meta http-equiv="content-type" content="text/html; charset=utf-8" />


エラー人を 見れば WST義 UI 関連 クラスが 問題を 起こす の ようなのに 言葉だ.

<p style="font-weight: bold;">
  2010.2.18 追加
</p>

上 二 枝 措置を して いくら 中 あって これ 症状が 消えた. 正確が どうな の おかげさまで これ 症状が 消えた のかは 分からない;; とにかく 上 二 枝 措置を 日 見れば 私のように 音うわさなしに 解決される 首都&#8230;