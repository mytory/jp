---
title: dekiwiki, Sharing violation on path /var/www/dekiwiki/bin/cache/luceneindex/default-queue/data_1.bin
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/680
aktt_notify_twitter:
  - yes
categories:
  - etc
tags:
  - TIP
---
<a target="_top" href="http://www.mindtouch.com/">デキウィキ</a>増えた 有用な ウィキ プログラムだ. FCKEditorを 使うこと だから 素人も 易しく 文を 使う 数 ある.

ところが 下と ような エラー メッセージが 出ながら ウィキ 検索が なるの なかった. 事実 エラー メッセージは ずっと 複雑だったし, そこで message 部分を 取った ことだ.

(<a title="dekiwiki 間違いと 解決策 引き続き 使う ページ" target="_top" href="http://mytory.local/archives/233">デキウィキ 間違い 関して 累積する 文</a>度 あるのに これは そのまま 文を 別に 使って 検索に つかまるように する 偏移 ましだと 思った.)

<pre>Sharing violation on path /var/www/dekiwiki/bin/cache/luceneindex/default-queue/data_1.bin</pre>

そのため <a target="_top" href="http://forums.developer.mindtouch.com/showthread.php?8065-Search-index-empty-error-after-upgrading-to-Olympic&p=41121#post41121">ググルリングウを したら 今世 解決策</a>これ 出た.

> Try this:  
> 1. Stop MindTouch  
> 2. Kill the index by deleting it. rm -rf luceneindex  
> 3. Start MindTouch and queue the rebuild

たいてい 節で 一応 マインドタッチ(デキウィキを のぼる 言葉だ)を 停止させて, luceneindex フォルダを 削除して, 再び 始めなさいという 言葉だ.

使って ある 蟹 ウブント リナックスなら 下の 命令を 順番で 打って 与えれば なる. スクリプトを 使えば良い.

<pre>/etc/init.d/dekiwiki stop
rm -rf /var/www/dekiwiki/bin/cache/luceneindex
/etc/init.d/dekiwiki start</pre>

こんなに して 管理 パネルで 入って行って Cache Management に 仮面 ルシンが 検索 インデックスを 再生性して ある ことだ. 時間は まどろみ かかる.

以上.