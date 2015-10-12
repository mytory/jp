---
title: 'crontab エディタ 間違い &#8211; /bin/sh: /usr/bin/vi: No such file or directory    crontab: &#8220;/usr/bin/vi&#8221; exited with status 127'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/560
aktt_notify_twitter:
  - yes
categories:
  - Web server
tags:
  - shell
---
crontab -e 命令で <a href="http://mytory.local/archives/601" target="_blank" title="ウブント 予約作業 管理, cron">crontabを 使用</a>しようと するから 間違いが 出た.

<img alt="" class="aligncenter" filemime="image/jpeg" filename="crontab 間違い 解決.png" src="http://dl.dropboxusercontent.com/u/15546257/blog/mytory/old-images/1/cfile24.uf.120CC73A4D632BA10A8D0F.png" height="300" width="577" />

こんなに cron 命令語を 寸だから

<pre class="brush:shell">sudo crontab -e</pre>

こんなに エラー メッセージが 浮かんだ.

<pre class="brush:plain">no crontab for root - using an empty one
/bin/sh: /usr/bin/vi: No such file or directory
crontab: "/usr/bin/vi" exited with status 127
</pre>

エラー 構文を 見たら 編集機である vi 義 位置が 過ち つかまって ある の ようだった.

そのため 何 箇所を 立ち後れてから <a href="http://www.unix.com/unix-dummies-questions-answers/773-bin-sh-usr-bin-vi-no-such-file-directory-when-doing-crontab.html" target="_blank" title="[http://www.unix.com/unix-dummies-questions-answers/773-bin-sh-usr-bin-vi-no-such-file-directory-when-doing-crontab.html]路 移動します.">解決策が 使って ある 所</a>を 見つけた.

根本的 解決策と言う よりは 臨時 方便は する. するが 一応 寝る 作動する.

上 エラー メッセージを 見れば /usr/bin/vi という ファイルや ディレクトリが ないという 言葉が 出る. 実際で なかった.

実際 vi義 位置は /bin/vi であった. 上 解決策は /bin/vi 義 シンボリック リンクを 作る 方法だ. /usr/bin/vi 路 シンボリック リンクを 作って 与えれば, こぎれいに 実行される のだ.

(シンボリック リンクが 何やら 寝る 分からない 人は そのまま 短縮 アイコンだと 思えば なる. 勿論 シンボリック リンクの 場合は シンボリック リンクを 消せば 原本まで 一緒に 削除されるので 単純な 短縮 アイコンは ない)

命令語は 下と ようだ. 管理者 権限が 必要な のだ. 私は sudoを 付けて 管理者 権限を 使った.

<pre class="brush:shell">sudo ln -s /bin/vi /usr/bin/vi</pre>

/bin/viを 実行させる /usr/bin/vi という リンクを 作りなさいという 命令語だ.(私 ような 場合は /usr/bin/vim を 連結した.)

上 命令を 行って 出れば 解決される.