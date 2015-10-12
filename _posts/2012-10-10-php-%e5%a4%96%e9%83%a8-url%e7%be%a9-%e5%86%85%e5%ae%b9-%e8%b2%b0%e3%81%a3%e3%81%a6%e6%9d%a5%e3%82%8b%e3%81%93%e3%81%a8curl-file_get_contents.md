---
title: '[PHP] 外部 URL義 内容 貰って来ること(cURL, file_get_contents)'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/452
aktt_notify_twitter:
  - yes
categories:
  - Web server
tags:
  - PHP
---
<pre class="brush: php">header(&#039;Content-Type: text/xml&#039;);
  $curl = curl_init();
  $timeout = 5; // 0で すれば 時間制限が ない.
  $url = &#039;http://feedproxy.feedburner.com/jquery/&#039;;
  curl_setopt($curl, CURLOPT_URL, $url);
  curl_setopt($curl, CURLOPT_RETURNTRANSFER, 1);
  curl_setopt($curl, CURLOPT_CONNECTTIMEOUT, $timeout);
  print curl_exec($curl);
  curl_close($curl);</pre>

何 cURLを 利用した コードは 上と ようだ.

print curl_exec($curl) すれば 内容を 出力するように なる.

団, cURLこれ 設置されて あると する. ウブントでの 設置方法は <a href="http://mytory.textcube.com/entry/PHP-%EA%B5%AC%EA%B8%80-%EC%95%84%EB%82%A0%EB%A6%AC%ED%8B%B1%EC%8A%A4-%ED%86%B5%EA%B3%84-%EA%B7%B8%EB%9E%98%ED%94%84%EB%A5%BC-%ED%99%88%ED%8E%98%EC%9D%B4%EC%A7%80%EC%97%90-%EB%8B%AC%EA%B8%B0" target="_blank">これ 文</a>義 中間位に 出る.(ウィンドウ 側は 設置方法は なくて, 設置する 数 ある ホームページに 行って 直接 察して 見ると 割 ことだ. cURL路 検索すれば 多く 出る ことで, APM Setup 7 からは cURLを サーバー 設定で チェックして 与えれば ともる.)

下は file\_get\_contents 関数を 利用した ことなのに, 簡便だが, 阻んでおいた 所が 多いと する.

<pre class="brush: php">// file_get_contents() 街 サーバーで ともって あったら, 
  // 載せるように 可能な 仮装(家長) 短い コードだ.
  header(&#039;Content-Type: text/xml&#039;);
  print file_get_contents(&#039;http://jquery.com/blog/feed&#039;);</pre>

以上の コードは 皆 <a href="http://wikimain.cafe24.com/wiki/Wiki.jsp?page=Jquery13" target="_blank">《jQuery 1.3 &#8211; 作故 力強い ジャバスクリプト ライブラリ》</a>義 9章 例題で 持って来た のだ.<del>(圧縮を 解けば 出る の 中 news/feed.php ファイルだ.)</del> ハングル ソースコードは ウェブサイトが 飛んだ ようで, 願書 ソースコードには 9章 コードが 抜けて ある. 何だ;;