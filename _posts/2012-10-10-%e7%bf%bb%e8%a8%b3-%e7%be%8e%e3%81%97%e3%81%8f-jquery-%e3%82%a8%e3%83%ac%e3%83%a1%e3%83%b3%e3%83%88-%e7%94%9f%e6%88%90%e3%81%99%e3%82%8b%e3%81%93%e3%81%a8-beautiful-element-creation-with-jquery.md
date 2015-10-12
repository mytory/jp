---
title: '[翻訳] 美しく jQuery エレメント 生成すること Beautiful Element Creation with jQuery'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/557
aktt_notify_twitter:
  - yes
categories:
  - Web publishing
tags:
  - javascript
  - jQuery
---
原文は <a href="http://www.thenerdary.net/post/20965430596/beautiful-element-creation-with-jquery" target="_blank">Beautiful Element Creation with jQuery</a> です.

エレメント(要素), パラメーター(媒介 変数), オトリビュト(速成), オブジェクト(客体)増えた そのまま 翻訳するの なくて 使いました.

<pre class="brush:html">&lt;div class="thisClass"&gt;&lt;/div&gt;</pre>

上 コードで `div`を エレメントと します. class街 オトリビュトで, `thisClass`増えた valueと します.

パラメーターは 変数です. 変数 分からない 分は ないでしょう? `var name = "撤収"` 割 時 `name`これ 変数ですよ.

オブジェクトは よく 客体と 翻訳するのに とても 良い 翻訳は ないと 思います. もう 固まった 単語だから どうする 数 なく 使うと することは しますが. 何やらは ご存知でしょう? 説明するには 力量が 走って パスします.

カッコ()増えた 翻訳に 自分が ない 時 原文を 入れる 用途で 使いました. コックスェッグァルホ[]増えた 理解を 助け合い のために 入れた のです.

&#8212;&#8212;- 翻訳 手始め &#8212;&#8212;

<img class="aligncenter" src="http://dl.dropboxusercontent.com/u/15546257/blog/mytory/old-images/1/cfile27.uf.203A6C444D4C0D6F2EB4D6.png" alt="" height="268" width="268" />

jQuery義 鳥(ローン の ような) エレメント 生成 文法は リボンを 下げる の ような 文法だ.(jQuery&#8217;s new(ish) element creation syntax drops &#8216;bows.) 分からない 人々を のために &#8211; 私は 少し 期待して あるのに &#8211; jQuery増えた あなたたちが エレメントを 作るように して, そこに パラメーターを 追加するように する. エレメントと エレメントの オトリビュトを 生成すること のために 彼 パラメーターたちを 使う のだ.

<pre class="brush:js">//Charles the alcoholic div
$(&#039;&lt;div /&gt;&#039;, {
	id: "charles"
});</pre>

昔の バージョンの jQueryで 皆さんは こんなに 使った のだ:

<pre class="brush:js">$(&#039;&lt;div id="charles"&gt;&lt;/div&gt;&#039;)</pre>

賢明に 聞こえる これ 方法は 二 番目 オプションが もっと 明確に 現われる. そして もし 皆さんが idを 持った 簡単な divを 作って ある ことなら これは 立派な 解法だ.(Now, volume-wise it appears that the second option is clearer and if you&#8217;re creating a simple div with an ID, this is an excellent solution.) [しかし] 内 考えに オブジェクト スタイルで [エレメントを] 生成する のには 阿洲 多い 長所が ある.

## オブジェクトに イベントを 付ける 数 ある.

多分 こういう 式の オブジェクト 生成で 仮装(家長) 大きい 特徴は イベントを 付ける 数 あるという 点である ことだ. そのまま また 一つの パラメーターで 入れれば なる.

<pre class="brush:js">$(&#039;&lt;div /&gt;&#039;, {
	id: &#039;charles&#039;,
	click: function(e){
		e.preventDefault();
		$(this).animate({opacity: 0.7}); 
	}
});</pre>

上で 見たように, 私たち アルちゅう divイン charles増えた ますます もっと 太って来る ことだ.

## Git[バージョン管理 システム]で バージョン 間 差[diff]を 寝る ボール 数 ある

[バージョン管理 システムである] Git義 特別な 観点 中 一つは ライン別で 管理を するという 点だ. もし たいてい 竝びで 一部を 直したら, Git増えた 竝び 全体が 変わった ので 見えて 与える. ジャバスクリプトは 阿洲 修正が ひんぱんな(tempestuous-さわがしい,狂暴な) 言語期 だから, ライン別で [パラメーターを 入れた のに] 基盤して 作った エレメントは 微妙な 変化を 気付くこと 良い.

## 馬具 コピー[clone]割 数 ある

こういう オブジェクトは 違う jQuery オブジェクトのように 作動して 良い.

<pre class="brush:js">var anchor = $(&#039;&lt;a /&gt;&#039;, {
	className: &#039;awesome&#039;,
	href: &#039;#&#039;,
	text: "This is an anchor ",
	click: function(e){
	 	e.preventDefault();
		$(this).parent().slideToggle();
	}
});

$("li").each(function(){
	$(this).prepend(anchor.clone());
});</pre>

こんなに 一応 値段を セッティングして, 必要な 時 いつでも コピーする 数 ある. 勿論 この前 文法で 生成した エレメントでも こんなに 割 数 ある. するが いくら \_\_美しいか\_\_ 見なさい. [生成した オブジェクトを] そのまま 使うの なくて コピー(clone)する 理由は 値段が 私 一つの エレメントを 参照すること だからだ. もし コピーするの なかったら, 一つの エレメントを ページに 入れれば なる.

これが 新しい 消息(hotness)載せる. もっと 分かって たければ <a href="http://api.jquery.com/jQuery/#jQuery2" target="_blank">これ 文書</a>を 見れば なる.

&#8212;&#8212;&#8212;-

[訳者 株] 団, こんなに なさる 焚く 必ず classNameと 使うと します. classと 使えば サファリで 作動を 中 します. 勿論 key値段を 引用符で 振り回して &#8220;class&#8221;と 少なければ サファリでも 寝る 作動します. 私は そのまま 引用符を 打つ 方を 好みます. 面倒ですよ.

また, 客体 中に 客体を 入れて たい 場合には append ような メソッドを 使うと します. これ 方式で 客体を 生成する 時 {}に 入って行く 数 ある 要素はattributes, events, and methods to callと 正義されて あります. すなわち, object増えた ない ことですよ.