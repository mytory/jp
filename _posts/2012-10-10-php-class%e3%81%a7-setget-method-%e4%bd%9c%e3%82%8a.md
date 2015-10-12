---
title: PHP classで set/get method 作り
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/24
aktt_notify_twitter:
  - yes
categories:
  - Web server
tags:
  - PHP
---
javaで set/get メソッドを 作って見た 人々なら, phpでも ような のを 捜す のだ.(たぶん)

本 見れば 出ているが, 常に 使う 子供は ないのに, 必ず 必要な 場合が 生ずる これ 子供達を, php路 classを 作る ガール 今 幕 始めた 私 ような 人は しきりに 度忘れするように なる.

そのため ここ 少なくて おく. 下の ソースを そのまま 掻けば なる.

<pre class="brush: php;" title="code">public function __get($name){
        return $this-&gt;$name;
    }

    public function __set($name, $value){
        $this-&gt;$name=$value;
    }</pre>

どうです? さて 易しいでしょう?