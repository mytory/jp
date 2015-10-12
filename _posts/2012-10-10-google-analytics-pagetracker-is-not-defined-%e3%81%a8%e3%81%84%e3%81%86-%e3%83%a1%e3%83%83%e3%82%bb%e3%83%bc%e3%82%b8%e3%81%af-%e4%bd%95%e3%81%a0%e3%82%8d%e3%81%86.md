---
title: '[Google Analytics] pageTracker is not defined という メッセージは 何だろう?'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/724
aktt_notify_twitter:
  - yes
categories:
  - ウェブ解析と検索
tags:
  - Google Analytics
  - Web Analytics
---
グーグル アナルリティックスで 使う ジャバスクリプト 変数は pageTracker という やつだ.

ところが 鳥 バージョンの アナルリティックス 追跡 関数では これ 変数を 使うの ない. _gaqという 変数を 使う. したがって 最新 追跡 コードを 適用した サイトなら, PDF ダウンロード ような のを 追跡しようとすれば 違う 方式の コードを 使うと する.

伝統的な 追跡 コードは 下と ようだ.

<pre class="brush:js">&lt;a href="http://mydomain.com/myPdf.pdf" onClick="javascript:pageTracker._trackPageview(&#039;/myPdf.pdf&#039;);"&gt;myPdf ダウンロード&lt;/a&gt;</pre>

ところが 鳥 バージョンの 追跡コードを 使う サイトでは 載せるように 中 食べるという ことだ. 上 コードに 大韓 説明は グーグル 公式 ヘルプ サイトでも 消えた.すなわち, 今は これ以上 作動するの ない コードだ. (新しい 方式の コードを 説明して ある ヘルプ ページは[外部 リンク][1]という 文書だ. それを 参考する 首都 ある ことだ.)

上 コードと ような 仕事を する コードは 下と ようだ.

<pre class="brush:js">&lt;a href="http://mydomain.com/myPdf.pdf" onClick="_gaq.push([&#039;_trackPageview&#039;, &#039;/myPdf.pdf&#039;])"&gt;myPdf ダウンロード&lt;/a&gt;</pre>

mail リンクを クリックするとか する 件 イベントで 追跡する 蟹 もっと 出るので 電子メール 住所を 何 番(回)や クリックしたのかを 確認しようとすれば 下のように コードを 使えば なると する. 内 考えに ツイッター 移して行くこと などを 追跡する 時 使えば コンパニオン なる の ようだ.

<pre class="brush:js">&lt;a href="mailto:hello@mydomain.com" onclick="_gaq.push([&#039;_trackEvent&#039;, &#039;name&#039;, value]);"&gt;hello@mydomain.com&lt;/a&gt;</pre>

外部 リンクに 適用しようとすれば 下のように 使えば なる の ようだ.

<pre class="brush:js">jQuery(&#039;.recommand-left21-link&#039;).click(function(){
	_gaq.push([&#039;_trackEvent&#039;, &#039;レフト21 推薦&#039;, &#039;クリック&#039;]);
});</pre>

<pre class="brush:html">&lt;a class=&#039;recommand-left21-link&#039; href=&#039;http://left21.com&#039;&gt;レフト21銀 斉家 強力お勧めする 進歩 言論です.&lt;/a&gt;</pre>

団, 上 コードは 私が 実際 適用して 本 コードは ない. 今日 適用して 実験を 始めたし,<a target="_top" href="http://stackoverflow.com/questions/3503511/google-analytics-pagetracker-is-not-defined">Google Analytics pageTracker is not defined?</a> で 本 内容を 土台で 使った ことだ.

ソーシャル ネットワーク 反応 関連 追跡 関数は 別に ある. `<a target="_top" href="http://code.google.com/intl/ko-KR/apis/analytics/docs/gaJS/gaJSApiSocialTracking.html#_gat.GA_EventTracker_._trackSocial">_trackSocial()</a>`という 関数だ.

 [1]: https://support.google.com/analytics/bin/answer.py?hl=ko&answer=1136920&topic=1136919&ctx=topic