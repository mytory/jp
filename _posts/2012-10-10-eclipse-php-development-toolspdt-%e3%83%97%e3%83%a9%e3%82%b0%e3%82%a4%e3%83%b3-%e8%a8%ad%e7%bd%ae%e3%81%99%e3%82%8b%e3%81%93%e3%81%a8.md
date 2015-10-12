---
title: '[eclipse] PHP Development Tools(PDT) プラグイン 設置すること'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/538
aktt_notify_twitter:
  - yes
categories:
  - 開発ツール
tags:
  - Eclipse
---
元々 PDT 2.1.2までは zipファイルを ダウンロードして したが 今日 イクルリブス 最新バージョンである ヘリオスを ダウンして 該当 zip ファイルで プラグインを 設置しようと するから 下のように エラー メッセージが 出ながら なるの なかった.

PHP Development Tools (PDT) Runtime Feature 2.1.2.v20090826-1027-7L7979F8NcJKhKRU19TmWA (org.eclipse.php.feature.group 2.1.2.v20090826-1027-7L7979F8NcJKhKRU19TmWA) requires &#8216;org.eclipse.dltk.core.feature.group [1.0.0,2.0.0)&#8217; but it could not be found

何 仕事か たくて 検索してから 易しい 方法を 捜すように いい.(<a href="http://wiki.eclipse.org/PDT/Installation#From_Update_Site" target="_blank">アップデート サイトを 通じて PDT 設置すること(英文)</a>)

**Help > Install new Software** メニューで PDTを 捜して そのまま 設置すれば なる のだった. 

下の 絵を 参考すれば 易しい.

<img src="http://dl.dropboxusercontent.com/u/15546257/blog/mytory/old-images/1/cfile25.uf.114EB24C4D4BC9682C3E25.png" class="aligncenter" alt="" height="729" width="580" />

さて 易しい.

勿論 上 絵を 真似るの なくて PDT アップデート サイトで 2.2 バージョンを ダウンロードして ローカル アーカイブ ファイルで 設置しても なる. ヘリオスなら 必ず 2.2を ダウンすると するという 点を 熟知すること 望む.