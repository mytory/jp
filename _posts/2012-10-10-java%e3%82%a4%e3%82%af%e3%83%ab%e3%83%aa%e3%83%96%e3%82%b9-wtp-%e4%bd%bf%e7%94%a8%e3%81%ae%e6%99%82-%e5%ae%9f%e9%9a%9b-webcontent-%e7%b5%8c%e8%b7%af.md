---
title: '[java]イクルリブス WTP 使用の時 実際 WebContent 経路'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/525
aktt_notify_twitter:
  - yes
categories:
  - Web server
tags:
  - JAVA
---
私は 初めに マイ 李クリップスロー ジャバを 学んだ だから tomcat フォルダに 実際 クラス ファイルたちが 入って行く ところ 慣れた. ところが 李クリップ須恵 WTPを 付けて 使うから それが なかった. tomcat フォルダは 卑語 ある のだった. ハル‾

そのため クラス ロジッグ 中に 現在 駆動中の ファイルの 実際 経路を 取る コードを 書き入れた 次には クラスファイルたちが 実際 どこで 入って行くかどうかを 確認する 数 あった.(すなわち, イクルリブスの サーバー 項目で publishを した 時 ファイルたちが 入って行く 経路 言葉だ.)

ところで 下と ような 経路だった.(ワークスペース 経路を /home/mytory/workspace 路 仮定する.)

<pre class="brush:shell">/home/mytory/workspace/.metadata/.plugins/org.eclipse.wst.server.core/tmp0/wtpwebapps/
</pre>

あの 仮面 クラス ファイルたちと 実際 FTPに アップロードする 数 ある ファイルたちを 捜す 数 ある.

定木, 次では jsp ファイルたちを 解釈した java ファイルの 経路だ. jsp街 java路 解釈された 後 class街 なるという のは みんな 分かって ある のだ. 次 経路で jsp ファイルを 解釈した java ファイルを 捜す 数 ある.

<pre class="brush:shell">/home/mytory/workspace/.metadata/.plugins/org.eclipse.wst.server.core/tmp0/work/Catalina/localhost/_/org/apache/jsp</pre>

最後に たいてい 枝 チップを 与えようとすると, .plugins増えた 隠し フォルダだ. .で 始める 名前は リナックスでは 隠しファイルが なる. こいつを 見えるように するためには ノーチラス(リナックス用 探索器)で Ctrl+Hを 押して 与えれば なる.