---
title: Javascript路 文書 修正すること(DOM Script) 簡単 例題
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/42
aktt_notify_twitter:
  - yes
categories:
  - Web publishing
tags:
  - javascript
  - plain javascript
---
次 内容は O\`relly シリーズ 中 ひとつの <a href="http://www.insightbook.co.kr/books/programming-insight/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%99%84%EB%B2%BD-%EA%B0%80%EC%9D%B4%EB%93%9C" target="_blank">《ジャバスクリプト 完壁 ガイド》(インサイト)</a>義 韓国語版 435ページを 変容して 移した のだ. あまりにも 分かって たかった 機能なので しばらく 間 読んで ところで メモすることに 決定!

ソースを 見れば だ 卵 のなので 説明は 略する. ただ, 私 本は ジャバスクリプトを 勉強して たい 人々には 無条件 強力お勧めだ. 終り.

<pre title="code" class="brush: jscript;">&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"&gt;
&lt;html xmlns="http://www.w3.org/1999/xhtml"&gt;
 &lt;head&gt;
  &lt;title&gt;textNode Test&lt;/title&gt;
  &lt;meta http-equiv="content-type" content="text/html;charset=utf-8" /&gt;
  &lt;meta name="author" content="ahw" /&gt;
  &lt;meta name="keywords" content="textNode" /&gt;
  &lt;meta name="description" content="textNode control example." /&gt;
  &lt;script type="text/javascript"&gt;
  //これ 関数は Node nを 伝達因子で 受けて, これ ノードを HTML &lt;strong&gt; テグルを 表現する Element ノードで 入れ替った 後 既存 ノードを 鳥で 作った &lt;strong&gt; エレメントの 子で 作る.
  function emStrongly(n){
	if (typeof n == "string") n = document.getElementById(n); //ノードを 調査する.
	var s = document.createElement("strong"); //新しい &lt;strong&gt; エレメントを 生成.
	var parent = n.parentNode; //与えられた ノードの 親を 得る.
	parent.replaceChild(s, n); //与えられた ノードを &lt;strong&gt; タグで 入れ替る.
	s.appendChild(n);
  }
  &lt;/script&gt;
 &lt;/head&gt;

 &lt;body&gt;
  &lt;!-- 二 犬の サンプル 文段 --&gt;
  &lt;p id="p1"&gt;これは &lt;i&gt;文段&lt;/i&gt; 1です.&lt;/p&gt;
  &lt;p id="p2"&gt;これは &lt;i&gt;文段&lt;/i&gt; 2です.&lt;/p&gt;
  &lt;!-- emStrongly() 関数を p1という エレメントに 大海 呼び出す ボタン --&gt;
  &lt;button onclick="emStrongly2(&#039;p1&#039;);"&gt;EmStrongly&lt;/button&gt;
 &lt;/body&gt;
&lt;/html&gt;</pre>

&nbsp;