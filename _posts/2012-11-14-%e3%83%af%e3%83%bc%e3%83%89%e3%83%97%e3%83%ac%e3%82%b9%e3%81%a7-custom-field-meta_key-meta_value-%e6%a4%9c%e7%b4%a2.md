---
title: ワードプレスで Custom Field(post_meta)でポスト検索
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/1816
categories:
  - WordPress
tags:
  - WordPress Tip
---
ワードプレスの Custom Field(コードでは 走路 `post_meta`と 表現)増えた 立派な 概念だ. ポストには あらゆる 文に 通用する 共通の 情報のみを 入れて, 彼 そらんずる Custom Fieldに 入れて 自由に Post義 その他 情報を 扱う 数 あるように 日 与えたら 言葉だ. ゼロボード などで columnを 余分で 10犬ほど おいて 置いて それを 使うように した のに 比べれば ずっと もっと 柔軟な 構造と 割 数 ある.

一応 Custom Fieldに 大海は 分かると 仮定して, ところが これを 使うから Custom Fieldを 土台で Postを 呼んで 来ると する 状況で 支えて 捨てた. 方法だ 当然 捜せば あるの. ところが 簡単に なる 件 ないから 言葉だ. 特に! ワードプレスに そんな コードが あったのか? する 考えが 入った ことだ. 使った コードという 蟹 `get_post()` 何 こういう かけるから 言葉だ.

ヨトン, これ 場合には 本の 徳を 見た. ウェブアクチュアル里ブックスで 出た <a target="_top" href="http://books.webactually.com/digwp/?page_id=2">《ワードプレス まともに 破棄》</a>街 方法を 知らせて 与えた. ワードプレスでは `WP_Query` クラスが DBで 持って来る 役目を するのに, そこ `$args`路 入れて 与える 方法を ところで 私 本が 知らせてくれたし, ワードプレス 公式 マニュアルで 彼 部分を 捜した.

<a target="_top" href="http://codex.wordpress.org/Class_Reference/WP_Query#Custom_Field_Parameters">WP_Query マニュアルの Custom Field Parameters</a> 部分だ. リンクを クリックして 入って行って パラメーター 使い方と 例題を 皆 見れば 理解が なる ことだ. 以上.