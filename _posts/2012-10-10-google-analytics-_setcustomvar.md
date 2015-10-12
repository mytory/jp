---
title: '[Google Analytics] _setCustomVar()'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/772
aktt_notify_twitter:
  - yes
categories:
  - ウェブ解析と検索
tags:
  - Google Analytics
  - Web Analytics
---
<a title="[Google Analytics] クッキーを 利用して 管理者 トラフィックを 統計で 除くこと" target="_top" href="http://mytory.local/archives/2090">グーグル アナルリティックス(GA : Google Analytics)で 管理者が 訪問する ガール 統計で 除去</a>して たかった. そのため ヘルプを デ−ビョ 報告 探求を した. `_setVar()`という GA 関数を 使う 方法が 出て あった.

ところが `_setVar()`増えた deprecated だ. 開発者 文書は 代わり[`_setCustomVar()`][1]を 使いなさいと して あった. そのため 探求を したし, 彼 結果を そのまま 保管する. 惜しくて;;

[`_setCustomVar()`][1]増えた 何か 別に 保存する に如く 値段が ある 時 使う してした ようだ.セッティングした 価格は**潜在顧客 > オーダーメード > オーダーメード 変数(Audience > Custom > Custom Variables)**で 確認する 数 ある.

## 使用方法

<pre>//_gaq.push([&#039;_setCustomVar&#039;, index, name, value, opt_scope]);
_gaq.push([&#039;_setCustomVar&#039;, 1, &#039;User Type&#039;, &#039;admin&#039;, 1]);</pre>

indexには 1‾5 間の 値段を 入れて 与える. グーグル アナルリティックスに 入って行って 見れば 1‾5までの スロットが ある のを 確認する 数 ある ことだ. これは 辞書に 分類が イッダギ よりは 自分が 恣意的に1‾5 間の 値段を 入れて 与えれば なる ことだ. 寝るのが 分かって 1‾5 間で オーダーメード 変数を 分類しなさいという 意味で 理解すれば なる.

name科 value増えた 敢えて 説明するの なくても なる のだ.

opt_scope増えた オーダーメード 変数を どうな 範囲で 追跡する のか セッティングする のだ. 1銀 visitor レベルで 追跡, 2増えた セッション レベルで 追跡, 3銀 ページ レベルで 追跡する のだ.

Visitor レベルである 1路 設定すれば 多分 2年 間 私が いくら 瓦刀 1回だけ 追跡される のだ. セッション レベル 追跡なら セッションが 終わる 瞬間 新しい 値段が 追跡される のだ.(簡単に 言って ブラウザー 消した つければ 鳥で 追跡されるという 音) 3銀 ページが 変更される 度に 追跡されるように 設定する のだ.(簡単に 言って, F5 押す 度に 追跡されるという 音だ.)

 [1]: https://developers.google.com/analytics/devguides/collection/gajs/gaTrackingCustomVariables