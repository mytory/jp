---
title: fckeditor竜 code syntax highlighter 使うこと
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/25
aktt_notify_twitter:
  - yes
categories:
  - Web server
tags:
  - 'FCKEditor &amp; CKEditor'
---
私は ブルログルを プログラミング 係わった 文で 満たして ある. 私にも コンパニオン なって 違う 人々にも コンパニオン なるから 言葉だ. そのため プログラミング コードを 多く 使う 便だ.

ところが コードを 使う 見れば イクルリブスや エディットプラス ような エディタたちで 日 与える 文法 ハイライト 機能が ない 蟹 惜しかった. そうだと いちいち 手で 色を 入れる 土方は 夏期 嫌いだったし&#8230;

私が 自主 見ている ブルログドルには 下と 一緒に 色が 入って行った コードが 多く 目に たたえた. そのため 100% 何か プラグインが ある のだと 確信した. そして 今日 捜した.

簡単な 設置 方法を 説明する. 一応 これ 製品は, 文 使う 焚く fckeditor街 必要だ. fckeditorを 利用して 生成した コードだけ あれば どこでも コード ハイライト 機能を 利用する 数 ある.

fckeditorに プラグインで 付けて 生成した コードを, コード ハイライト 機能を 利用して 見ようとすれば 見る ページに jsわ cssファイルを 連結すると する. 二 部分で 分けて 説明する.

## code syntax highlighter 2を fckeditorに 設置すること

### 1.

ダウンする : <a href="http://alexgorbatchev.com/SyntaxHighlighter/download/" target="_blank">code syntax highlighter ダウンロード</a> (現在 バージョンが 3これ いい. そのため 作動を するか 分からない : 2012-05-19)

(付け加えて 言わば, 次 リンクには fckeditor義 多様な プラグインが 集まって ある : <a href="http://sourceforge.net/tracker/?group_id=75348&atid=737639" target="_blank">fckeditor プラグイン 集め</a>)

### 2.

事実 ダウンした 次に そこに ある 説明どおり すれば なる. 英語 マニュアルに 恐怖感を 持って ある 人が ないなら じっくりと 読んで 真似る 蟹 もっと 治るかも 分からない. ヨトン, 私も それなりに 説明して 見る.

<img class="alignleft" src="http://dl.dropboxusercontent.com/u/15546257/blog/mytory/old-images/1/cfile22.uf.150AF7564D4BC8632F83C7.jpg" alt="" height="358" width="301" />左側 絵のように フォルダに 設置する. ダウンした ことで 圧縮 解けば 出る ファイルたち だ 入れる. <span style="text-decoration: underline;"><strong><span style="color: #ff0000;">フォルダ人は 必ず syntaxhighlight2</span></strong></span>与・野党 する. 違うように すれば 作動 中 する.

団, アブツックプルなら fckconfig.js度 一緒に 入っているのに, これは アップロードする 必要 負う.

### 3.

元々 fckeditorに 入っている fckconfig.jsを 開いて 下の コードを 追加して 与える.

<div style="clear: both; color: white;">
  .
</div>

<pre class="brush: jscript;gutter: false; ">FCKConfig.Plugins.Add( &#039;syntaxhighlight2&#039;, &#039;en&#039;) ;</pre>

FCKConfig.Plugins.Addという 関数が 被せている 所が ある. 捜して 彼 近くに 入れてくれれば なる のだ.

### 4.

そして, やっぱり fckconfig.jsに ある ツールバー セット 設定を 触れると する.

FCKConfig.ToolbarSets["Default"]私 FCKConfig.ToolbarSets["Basic"] 中に 自分が 使う のが 何やら 分かって ある 蟹 良い のだ. ボタンが 多い ことなら Default故 ボタンが 少なければ Basic載せる. 一応 言葉だ.

Customで 設定して 使う 人も 勿論 ある. Customを 触れる 竝び 分かる 分は 敢えて 説明 中 しても なる のだから 信じる.

Code Syntax Highlight2義 ボタン名前は <span style="color: #ff0000;"><strong>SyntaxHighLight2</strong></span>だ. これも 綴字 違えば 中 なる. 控え目に 付けて 入れる. 付けて入れた 結果 例示を 見せてくれれば 次と ようだ. これは <span style="color: #ff0000;"><strong>例示</strong></span>という ガール 肝に銘ずること 望む. とにかく, 分かって 寝る 入れなさいという 言葉だ.(!)

<pre class="brush: jscript;gutter: false; ">FCKConfig.ToolbarSets["Basic"] = [
	[&#039;Bold&#039;,&#039;Italic&#039;,&#039;-&#039;,&#039;OrderedList&#039;,&#039;UnorderedList&#039;,&#039;SyntaxHighLight2&#039;,&#039;-&#039;,&#039;Link&#039;,&#039;Unlink&#039;,&#039;-&#039;,&#039;About&#039;]
] ;</pre>

### 5.

ここまで すれば 一応 完了した. それでは fckeditor路 入って行って プラグインが 作動するのか 調べよう.

一応 <span style="color: #ff0000;"><strong>ウェッブブラウザーの キャッシュを 削除する.</strong></span> 中 すれば 中 変わる 確率が 高い. 派幅なら 個人情報 初期化で キャッシュを 消せば なって, エクスプローラなら インターネット オプションで 検索記録を 削除する.

fckeditor 編集画面で 下みたいな ボタンが 出て, 押した 時 下みたいな 画面が 出れば 一応 成功した のだ.

<img class="aligncenter" src="http://dl.dropboxusercontent.com/u/15546257/blog/mytory/old-images/1/cfile9.uf.120B09534D4BC86307C697.png" alt="" height="578" width="478" />

## fckeditor街 生成した コードで Code Syntax Highlighter2 作動させること

これを 捜すために かなり 迷った. どうこうでも 英語は 付く;;

コード シンタックス ハイライト プロジェクト サイトで ダウンすると する.

<p style="text-align: center;">
  <a title="[http://alexgorbatchev.com/SyntaxHighlighter/]路 移動します." href="http://alexgorbatchev.com/SyntaxHighlighter/" target="_blank">鼻</a><a title="[http://alexgorbatchev.com/SyntaxHighlighter/]路 移動します." href="http://alexgorbatchev.com/SyntaxHighlighter/" target="_blank">ド シンタックス ハイライト ページ</a>
</p>

ダウンして 圧縮を 解けば test.htmlイラン 子供が あって, src, scripts, stylesという フォルダが ある.

script, src, styles フォルダを ぜんぶ 自分の 勘定に アップロードする. textcubeに jsファイルを あげる 数は なく なって あるので, 自分が ファイルを アップロードする 数 ある 勘定が あると する.

test.html義 コードを 開いて head 間に ある script コードと style コードを だ 掻こう. <span style="color: #ff0000;"><strong>srcわ href義 経路は 自分が ファイルを アップロードした 勘定に 当たるように 寝る 修正して 与えると する.</strong></span>

<pre class="brush: xhtml;">&lt;script type="text/javascript" src="scripts/shCore.js"&gt;&lt;/script&gt;
	&lt;script type="text/javascript" src="scripts/shBrushBash.js"&gt;&lt;/script&gt;
	&lt;script type="text/javascript" src="scripts/shBrushCpp.js"&gt;&lt;/script&gt;
	&lt;script type="text/javascript" src="scripts/shBrushCSharp.js"&gt;&lt;/script&gt;
	&lt;script type="text/javascript" src="scripts/shBrushCss.js"&gt;&lt;/script&gt;
	&lt;script type="text/javascript" src="scripts/shBrushDelphi.js"&gt;&lt;/script&gt;
	&lt;script type="text/javascript" src="scripts/shBrushDiff.js"&gt;&lt;/script&gt;
	&lt;script type="text/javascript" src="scripts/shBrushGroovy.js"&gt;&lt;/script&gt;
	&lt;script type="text/javascript" src="scripts/shBrushJava.js"&gt;&lt;/script&gt;
	&lt;script type="text/javascript" src="scripts/shBrushJScript.js"&gt;&lt;/script&gt;
	&lt;script type="text/javascript" src="scripts/shBrushPhp.js"&gt;&lt;/script&gt;
	&lt;script type="text/javascript" src="scripts/shBrushPlain.js"&gt;&lt;/script&gt;
	&lt;script type="text/javascript" src="scripts/shBrushPython.js"&gt;&lt;/script&gt;
	&lt;script type="text/javascript" src="scripts/shBrushRuby.js"&gt;&lt;/script&gt;
	&lt;script type="text/javascript" src="scripts/shBrushScala.js"&gt;&lt;/script&gt;
	&lt;script type="text/javascript" src="scripts/shBrushSql.js"&gt;&lt;/script&gt;
	&lt;script type="text/javascript" src="scripts/shBrushVb.js"&gt;&lt;/script&gt;
	&lt;script type="text/javascript" src="scripts/shBrushXml.js"&gt;&lt;/script&gt;
	&lt;link type="text/css" rel="stylesheet" href="styles/shCore.css"/&gt;
	&lt;link type="text/css" rel="stylesheet" href="styles/shThemeDefault.css"/&gt;
	&lt;script type="text/javascript"&gt;
		SyntaxHighlighter.config.clipboardSwf = &#039;scripts/clipboard.swf&#039;;
		SyntaxHighlighter.all();
	&lt;/script&gt;</pre>

これを だ 掻いて, 文 見せてくれる ページに 入れる.

私は textcubeを 使うので 当然 スキン編集に 入って行って skin.htmlエッダ 私 コードを 入れたが, 作動するの なかった. ソース表示を するから コードが 消えていた. そのため ウィジェットで 入って行った 次 html コード ウィジェットに 私 コードを ぜんぶ 入れた.

それでは 設置 終りだ.