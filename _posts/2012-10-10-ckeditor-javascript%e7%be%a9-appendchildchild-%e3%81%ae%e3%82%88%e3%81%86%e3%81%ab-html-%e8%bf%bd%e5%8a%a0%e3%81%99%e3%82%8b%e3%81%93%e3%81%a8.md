---
title: ckeditor, javascript義 appendChild(child) のように html 追加すること
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/154
aktt_notify_twitter:
  - yes
categories:
  - Web server
tags:
  - 'FCKEditor &amp; CKEditor'
---
<a href="http://mytory.textcube.com/entry/ckeditor-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EB%A1%9C-%EB%82%B4%EC%9A%A9-%EC%A7%91%EC%96%B4%EB%84%A3%EA%B8%B0%EC%A0%84%EC%B2%B4-%EB%82%B4%EC%9A%A9-%EB%B0%94%EA%BE%B8%EA%B8%B0" target="_blank">ckeditor, ジャバスクリプトで 内容 入れること(全体 内容 変えること)</a>で 全体 内容を 変えるの なくて htmlを 追加する 方法が 知りたいと 使ったが, API万 立ち後れてから シャベルですくい出した の ようだ. ckeditorを ダウンロードすれば 基本に 提供する samplesに 基本的に 使う 数 ある API街 あった. コードは 下と ようだ.

<pre class="brush:js">function InsertHTML()
{
	// 願う エディタの インストンスを 持って来る.
	var oEditor = CKEDITOR.instances.editor1;
	var value = &#039;入れて たい テキスト&#039;;

	// Check the active editing mode.
	if ( oEditor.mode == &#039;wysiwyg&#039; )
	{
		// Insert the desired HTML.
		oEditor.insertHtml( value );
	}
	else
		alert( &#039;WISIWIG モードだと 可能です!&#039; );
}
</pre>

思ったより 休んだ.

上 コードどおり すれば 大きくては ある 所に value街 入って行くように なる.

value増えた そのまま テキストでも なって, html引き継いでも なる. 

html裏面 html路 入って行って, text面 分かって html処理を たいてい 次 入って行く. 

選択領域が あれば 選択領域を 取り替えながら 入って行く. すなわち, エディタに 内容を 満たす 時 載せるように 核心だ.

したがって 色々 枝で テストして 表示 望む.