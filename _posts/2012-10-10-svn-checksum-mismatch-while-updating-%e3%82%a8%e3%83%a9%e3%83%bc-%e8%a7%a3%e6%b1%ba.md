---
title: 'svn: Checksum mismatch while updating エラー 解決'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/556
aktt_notify_twitter:
  - yes
categories:
  - 開発ツール
tags:
  - SVN
---
<img src="http://dl.dropboxusercontent.com/u/15546257/blog/mytory/old-images/1/cfile10.uf.18329D554D4BC97130E518.png" class="aligncenter" alt="" filename="subversion_logo-384x332.png" filemime="image/jpeg" height="332" width="384" />

svnこれ ある日 アップデート 命令を 拒否した.

<pre class="brush:plain">update C:/workspace/myProject -r HEAD --force
    svn: Working copy &#039;C:workspacemyProjectcss&#039; locked; try performing &#039;cleanup&#039;
    svn: Working copy &#039;C:workspacemyProjectcss&#039; locked; try performing &#039;cleanup&#039;
cleanup C:/workspace/myProject
</pre>

ところが 私は 誰 のも たいてい 蟹 ないと! そのまま 寝る 作業してから updateを 押した だけだと!

どうする 仕事なのか? エラー メッセージを 見れば svnで ‘css フォルダが 掛かったから cleanupを 日 見ます’ と したから, <a target="_blank" href="http://wiki.kldp.org/wiki.php/SubversionBook/GuidedTour#svn-ch-3-sect-7.1">cleanup 命令</a>を 下って 見た.&nbsp;

作業を 行ってから 問題が 生じた 時 cleanupを 行えば 中断した 作業を 再び 行うように なる. それでは 掛かった ファイルも 解けて 何 そんな ことだ.(svn銀 作業を 割 時 対象 ファイルを 閉ざす. カーミット中の 子を 修正すれば 滅びるから )

定木, cleanup 命令を 下ったから 再び アップデートを させた.

<pre class="brush:plain">update C:/workspace/myProject -r HEAD --force
    Restored C:/workspace/myProject/css/index.css
    svn: Checksum mismatch while updating &#039;C:workspacemyProjectcss.svntext-baseindex.css.svn-base&#039;; expected: &#039;1bdfe3f4fe587005aa0562c465ad54ad&#039;, actual: &#039;null&#039;
    svn: Checksum mismatch while updating &#039;C:workspacemyProjectcss.svntext-baseindex.css.svn-base&#039;; expected: &#039;1bdfe3f4fe587005aa0562c465ad54ad&#039;, actual: &#039;null&#039;
</pre>

そうしよう 今度には 米? ‘index.css.svn-base を アップデートするのに <a href="http://jp.mytory.local/archives/96" target="_blank" title="[http://mytory.local/72]路 移動します.">Checksum</a>これ 中 当たる’と する.&nbsp;

寝ることは どうして ゾチォゴを 期待したが 私の 作業本は null載せなさいと言っている.

ウシャング どうしなさいと!

## 解決策: 作業本 削除

前に 何 番(回) 載せろと言った 焚く 作業本 全体を 削除して 全部 再び ダウンした.

今は そうに 無識な 仕業を 夏至 ない. 問題が なった フォルダは css フォルダだ. そのため あいつだけ 消した.

これは svnで 消しなさいという 蟹 なく そのまま **探索器 行って del ボタン 押しなさいという 音**だ.&nbsp;

イクルリブス 使う 方々 あったら, 李クリップ須恵書 消すの 以外に 探索器や ノーチラスで 消すのを.

刺字. そうして 出て updateすれば 寝る なる.

どうすれば 私 index.css 万 問題である 首都 ある. あいつだけ 消しても なる 指導 分からない. ところが そうに 日 本 少ない ないから パス!