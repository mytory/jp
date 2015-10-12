---
title: '[翻訳] 客体 志向 CSS(OOCSS) 紹介'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/1872
categories:
  - Web publishing
tags:
  - CSS
---
スマッシュマガジンの<a title="Read 'An Introduction To Object Oriented CSS (OOCSS)'" href="http://coding.smashingmagazine.com/2011/12/12/an-introduction-to-object-oriented-css-oocss/" rel="bookmark">An Introduction To Object Oriented CSS (OOCSS)</a>を翻訳した文だ. [ルイスラザリス][1]が使った.

私は普段再使用性の高い CSSが開発速度を高めてくれると思って来た. そしてそうしようとすればコンテナに独立的なスタイルを使った方が良くないかと思う考えをしていた. ところでなぜか! 初めから客体志向 CSSという開発方法論があった! ワウ! 楽しみがわいてすべて読んで翻訳した. 役に立ってほしい.

&#8212;&#8212;

**&#8220;コンテンツが生命だ&#8221; 言うことを聞いて見たのか? ウェブ開発者として私たちはコンテンツ生産に係わる事をよくするようになる. コンテンツが生命という言葉は確かに濫用されて来たが, サイト訪問者には真実だ.**

しかし, ウェブ開発者観点では, 論争の余地はあるが[速度が生命][2]である. 私はますますもっとこの立場(入場)を支持するようになった. 最近何年間経験あるフロントエンドエンジニア多数が速度向上に使用者経験を改善することができるという [立場を受け入れた.][3]

不幸にも, 速度改善領域でCSSは看過されて来た. 多くの開発者たちは (良い理由で) ジャバスクリプト速度と[違う領域たち][4]に主に焦点を合わせて来た.

この文で, 私はよく看過される領域を扱うでしょう.**客体志向 CSS(Object Oriented CSS, OOCSS)**概念を紹介して, これがウェブページの速度と維持補修容易性を二つとも改善する方法という点を知らせてくれる.

## OOCSSの原則

他の客体基盤コーディング方法論のように, OOCSSの目的もコード再使用性を高めて, 窮極的には, もっと早くて效率的で何か追加しやすくて維持補修すること容易いスタイルシーツを作るのだ.

<p style="text-align: center;">
  <img class="aligncenter" alt="OOCSS" src="http://dl.dropbox.com/u/15546257/blog/mytory/intruduce-oocss/oocss-splash1.jpg" />
</p>

[OOCSS GitHubのウィキページ][5]から説明するように, OOCSSは二つの原則に基礎している.

### 表現で構造を分離すること

スタイルを加えたウェプページのほとんどすべての要素たちは脈絡によって模様が違う. (表現)ウェブサイトのコンセプトを考えて見よう. 色, グラデ−オントの纎細な使用, または見える線たち. 一方, 他の見えない要素たちは似ているように繰り返される. (構造)

この他の要素たちをクラス基盤モジュールに抽象化すれば, **再使用が可能になって** どんな要素にも適用することができるし, 基本的に一貫された模様を期待することができるようになる. コードを整える前と整えた後を比べて見よう. 私が何の話をするのか分かることができるでしょう.

OOCSS 原則を適用する前にはこんな CSSを作成するのだ.

<pre class="brush: css">#button {
	width: 200px;
	height: 50px;
	padding: 10px;
	border: solid 1px #ccc;
	background: linear-gradient(#ccc, #222)
	box-shadow: rgba(0, 0, 0, .5) 2px 2px 5px;
}

#box {
	width: 400px;
	overflow: hidden;
	border: solid 1px #ccc;
	background: linear-gradient(#ccc, #222)
	box-shadow: rgba(0, 0, 0, .5) 2px 2px 5px;
}

#widget {
	width: 500px;
	min-height: 200px;
	overflow: auto;
	border: solid 1px #ccc;
	background: linear-gradient(#ccc, #222)
	box-shadow: rgba(0, 0, 0, .5) 2px 2px 5px;
}</pre>

上の三つの要素にはそれぞれ独立的なスタイルがある. そしてスタイルを適用するために ID 選択者(selector)を使っている. ID 選択者は再使用することができない. 共通スタイル(common styles)は雰囲気を掲げるがデザインを一貫されるように維持するために存在する. <a class="simple-footnote" title="The common styles might exist for branding purposes or consistency of design." id="return-note-1872-1" href="#note-1872-1"><sup>1</sup></a>

少しだけ計画を立てて考えを先にすれば, 共通スタイル(common styles)を抽象化することができる. そうすれば CSSは下のようになるでしょう.

<pre class="brush: css">.button {
	width: 200px;
	height: 50px;
}

.box {
	width: 400px;
	overflow: hidden;
}

.widget {
	width: 500px;
	min-height: 200px;
	overflow: auto;
}

.skin {
	border: solid 1px #ccc;
	background: linear-gradient(#ccc, #222)
	box-shadow: rgba(0, 0, 0, .5) 2px 2px 5px;
}</pre>

このようにすれば, すべての要素たちはクラスを二つ以上使うようになる. しかし共通スタイルと再使用可能な &#8220;表現&#8221;竜スタイルを結合して使いながら不必要な繰り返しは消える. 私たちはただすべての要素たちに &#8220;表現&#8221; クラスを適用すれば良い. それでは初めて例題で作ったことと等しい結果物を見られる. **コードが減ったという点と、再利用の可能性が増えたという点抜いた言葉だ。**

### コンテナとコンテンツを分離すること

OOCSS Github ウィキページが説明する二番目原則は, コンテナをコンテンツで分離するのだ. 次の CSSを見ればこれがどうして重要か分かる.

<pre class="brush: css">#sidebar h3 {
	font-family: Arial, Helvetica, sans-serif;
	font-size: .8em;
	line-height: 1;
	color: #777;
	text-shadow: rgba(0, 0, 0, .3) 3px 3px 6px;
}</pre>

このスタイルは `#sidebar` 要素の子要素である 3段階題目(h3)に適用するでしょう. しかし字大きさと影だけ変えて残りは完全に同じなスタイルでプトの h3に適用したければ?

それではこんな式にしなければならないつもりだ.

<pre class="brush: css">#sidebar h3, #footer h3 {
	font-family: Arial, Helvetica, sans-serif;
	font-size: 2em;
	line-height: 1;
	color: #777;
	text-shadow: rgba(0, 0, 0, .3) 3px 3px 6px;
}

#footer h3 {
	font-size: 1.5em;
	text-shadow: rgba(0, 0, 0, .3) 2px 2px 4px;
}</pre>

それとも, もっとこんな式でもっと悪くすることもできる.

<pre class="brush: css">#sidebar h3 {
	font-family: Arial, Helvetica, sans-serif;
	font-size: 2em;
	line-height: 1;
	color: #777;
	text-shadow: rgba(0, 0, 0, .3) 3px 3px 6px;
}

/* other styles here.... */

#footer h3 {
	font-family: Arial, Helvetica, sans-serif;
	font-size: 1.5em;
	line-height: 1;
	color: #777;
	text-shadow: rgba(0, 0, 0, .) 2px 2px 4px;
}</pre>

結局, 私たちは **不必要な重複スタイル**を作っているし, 多分それを見抜くことができないはずだ. (それとも気を使わないとか.) OOCSSではさまざまな要素で共通された部分を捜し出して, それをどこででも再使用することができるようにモジュール化するとか, 客体で作る.

一番の上の例題のように階層化した選択者を使ってスタイルを宣言すれば, **再使用することができなくなる.** <a class="simple-footnote" title="訳者註 &#8211; #sidebar h3 同じ式で使ったこと" id="return-note-1872-2" href="#note-1872-2"><sup>2</sup></a> 特定コンテナにゾングソックドエギのためだ. (この場合にはサイドバやプトに属した.)

OOCSSのクラス基盤モジュールを構築することでスタイルがどんなコンテナにも属しないようにできる. これは構造的脈絡を気を使わないで, クルレスルルムンソの **どこでも再使用**できるようになるということを意味する.

## 実際事例

OOCSS 使い方をもうちょっと説明するため, [私のサイトを最近再デザイン][6]しながら使ったことと似ていることを見せてくれるようにする.私のサイトでヘッダー中の要素をコーディングした後, ヘッダー中の基本救助用スタイルをページの他の要素で再使用することができるということを悟った.

下は私のサイトのヘッダーを構える時使ったコードだ.

<pre class="brush: css">.header-inside {
	width: 980px;
	height: 260px;
	padding: 20px;
	margin: 0 auto;
	position: relative;
	overflow: hidden;
}</pre>

`.header-inside`要素にだけ必要なことはとても少しで, 残りは再使用可能なモジュールで作ることができる. それで私は救助用スタイルを再使用可能なクラスに抽象化した. それで出た結果物だ.

<pre class="brush: css">.globalwidth {
	width: 980px;
	margin: 0 auto;
	position: relative;
	padding-left: 20px;
	padding-right: 20px;
	overflow: hidden;
}

.header-inside {
	padding-top: 20px;
	padding-bottom: 20px;
	height: 260px;
}</pre>

`.globalwidth`クラスが含むものなど :

*   固定幅
*   マージンを利用して中で位置させること : `auto`
*   絶対位置を使う子要素を制御するための `position: relative`
*   左右 20px ペディング
*   clearfixのための `overflow: hidden` <a class="simple-footnote" title="clearfixと言う(のは) float 要素をコンテナがまともにくるむようにすることを言う." id="return-note-1872-3" href="#note-1872-3"><sup>3</sup></a>

このようにすれば同じ特性が必要な場合ただ望む要素にクラスだけ付与することで同じスタイルを適用することができる. CSSを１行も追加しないで言葉だ.

私のサイトで, 飛ぶこの救助用スタイルたちを主要コンテンツ要素とプト中要素に再使用した. デザインによって, このスタイルは多分ヘッダーとコンテンツの間に入って行く水平ナビゲーション要素に適用されることもできるでしょう. あるいはページの中来なければならない固定幅要素に使うこともできるでしょう.

&#8220;globalwidth&#8221; スタイルをこの要素たちに追加した後, HTML マークアップはこんなに変わった.

<pre class="brush: css">&lt;header&gt;
	&lt;div class="header-inside globalwidth"&gt;
	&lt;/div&gt;
&lt;/header&gt;

&lt;div class="main globalwidth"&gt;
&lt;/div&gt;

&lt;footer&gt;
	&lt;div class="footer-inside globalwidth"&gt;
	&lt;/div&gt;
&lt;/footer&gt;</pre>

ある人々はこんな式のスタイル抽象画が HTMLを汚なくして表現でマークアップを分離する原則を違反すると思うでしょう.

しかしマークアップに及ぶ影響に関する論争を無視すれば, この抽象画が特定スタイルを **追跡して** 上の構造的要素たちに **使われた共通スタイルを修正するもっと易しくしてくれる**はところ誰も疑問を申し立てることができないだろう.

## メディア客体(Media Object)

OOCSS 運動の開拓者の中で一つは [ニコルソリバン][7]である. ニコルソリバンは[ メディア客体][8]という再使用可能なモジュールを作った. ニコルの説明を見れば, このモジュールを使って[コード分量を大幅に減らすことができる.][9]

<p style="text-align: center;">
  <img class="aligncenter" alt="OOCSS" src="http://dl.dropbox.com/u/15546257/blog/mytory/intruduce-oocss/oocss-splash1.jpg" />
</p>

メディア客体は OOCSSの力強さを見せてくれる立派な例だ. コンテンツ左側にサイズに構わずにメディアヨソルルベチすることができるようにしてくれるからだ. 内側コンテンツに適用する多くのスタイルが そしてメディア要素自分の大きさすら 変わることができるが, メディア客体自体は不必要な重複を避けるようにしてくれる共通スタイルに基盤する.

## OOCSSの利得

私はもう OOCSSの何種類長所に対して言った. もうちょっと拡張をして見る.

### もっと早いウェブサイト

OOCSSを使えば, 速度側面で利得が明確だ. 再使用をたくさんしてスタイルがほとんどない CSSなら, **ファイルサイズが小さいだろうし**, それではダウンロード速度が早くなるでしょう.

マークアップがちょっと汚なくなって, それで HTML ファイルサイズがちょっと大きくなったりするでしょう. しかし多い場合に, マークアップのため遅くなるよりスタイルシーツのため早くなるのがもっと大きいだろう.

肝に銘ずるもう一つの概念は OOCSS ウィキにある **性能チップ**(performance freebies)だ. これは再使用を通じて CSS １行なしに新しい要素にスタイルを適用することができるということを見せてくれる. 大規模トラフィックの大きなプロジェクトでこれ &#8220;チップ&#8221;は [性能を通じて決定的な利得][10]を得ることができるようにしてくれる. <a class="simple-footnote" title="these “freebies” could bea crucial performance gain." id="return-note-1872-4" href="#note-1872-4"><sup>4</sup></a>

#### 維持補修しやすいスタイルシーツ

OOCSSを使えば, ずっと増えるスタイルシーツ代わり, 自然に自らの役割をしながらも**維持補修しやすいモジュールセット**が生ずるでしょう. <a class="simple-footnote" title="内容と関係なくて翻訳しにくい部分一部を略した.With OOCSS, instead of a constantly growing stylesheet full of specificity wars, you’ll have aneasy to maintain set of moduleswhere the natural cascade plays an important role." id="return-note-1872-5" href="#note-1872-5"><sup>5</sup></a>

既存サイトに何かを追加する時, 普通スタイルシーツもっぱら下にスタイルを追加するでしょう. 前に何があるのか気を使いながらね. もうそうでなくてもなる. 代りに既存スタイルを再使用するようになるはずで, 既存規則セットを基盤でスタイルを確張するようになるでしょう.

考えから先にすることで, とても少ない CSSだけで全体ページを作ることができる. 既存 CSS モジュールの中でどれでも新しいページに使うことができる. それでは新しくできる CSSは最小化されるでしょう. どんな場合には CSSを１行も作成しないで完全にスタイルを加えたページを作ることができるでしょう.

この維持補修容易性という利得はスタイルシーツの健康することで拡張される. スタイルがモジュール化されているから, OOCSSに基盤したページは新しい開発者も易しく適応することができる.

## 注目するに値する価値があること

OOCSSはコミュニティで多くの討論を誘発したし, いくつかの論難を起こした. ここでいくつかの誤解を払拭させて見る.

### 相変らず IDを使うことができる

OOCSS 規則を完全に守りながら作業する事にしたら, 主に CSS クラスに基盤してスタイルを加えるようになるはずで, IDを使ってスタイルを加えなくなるでしょう.

このために, 多くの人々が OOCSSが IDを全然使わないと過ち主張して来た. しかしこれは事実ではない.

IDを避けなさいという規則は, もっと具体的に言えば, **IDを選択者で使わない**と言うのだ. よって **HTMLで****ジャバスクリプトイベント(hook)としおり(**fragment identifiers**) 用で IDを使うこと**は OOCSS 規則に完全に符合するのだ.

勿論, もう要素に IDが適用された状況であることができる. その要素がページで唯一ののであることができる. <a class="simple-footnote" title="訳者註 &#8211; IDは唯一のやつにだけ適用するのだから." id="return-note-1872-6" href="#note-1872-6"><sup>6</sup></a> クラス代わりに ID 選択者を使って何バイトを節約することはできるでしょう.しかしこの場合, 後で特定問題にぶつからなければクラスを使うのがもっと安全だ.

#### もっと小さなプロジェクトを扱うこと

小規模サイトとエブで OOCSSが過剰(overkill)の場合が確かにあるでしょう. だからこの文がどんな環境でも OOCSSを使わなければならないと主張することで受け入れるな. プロジェクトによって多様な状況があり得る.

そうだが, 最小限, すべてのプロジェクトで OOCSS 規則で思考することは良いことだ. 一番(回)そんなことができるようになれば, ファックシルハンイドックがイッヌンド大きいプロジェクトで OOCSSで作業するのがもっと易しくなるでしょう. 壮語する.

## 具現ガイドライン

OOCSSを始めようとすれば時間が少しかかるはずだ. 私は相変らず努力している. それでこの領域で私がすべての答を持っているとかすべての経験をしたと言うことはできない.

しかし OOCSS モードに入って行きたければ役に立つに値するものなどを何種類知らせてくれる.

*   階層的選択者を避けなさい. (例えば,`.sidebar h3`同じことを使わないでね.)
*   ジャバスクリプトイベントをかける IDにスタイルを加えないでね.lt;/li>
*   スタイルシーツクラスに HTML タグ適地ないでね.(例えば`div.header`,`h1.title`)
*   本当に珍しい場合を外には`!important`を使わないでね.
*   [CSS Lint][11]を利用してCSSを検査しなさい. (オプションと [間違い種類][12]ルルイックヒョだと.)
*   [CSS グリッド][13]を使いなさい.

後でこの規則の中で一部が割れることもできる. しかし全体的にこの規則たちは良い習慣でスタイルシーツをもっと小さくて維持補修しやすく作ってくれるでしょう.

## ニコルソリバンの作業をよく見なさい

OOCSSをずっと学ぼうとすれば, 連関結ぶ一番重要な人は [ニコルソリバン][7]である.

ニコルは自分のブログに OOCSSに対する文を定期的にあげる.またスライドショーを活用した発表をたくさんした. 下は見物な発表資料だ.

*   [Object Oriented CSS (客体志向 CSS)][14](Slideshow)
*   [High Performance Websites: Nicole Sullivan (高性能ウェブサイト)][15](Video)
*   [Our Best Practices Are Killing Us (ベストプラクティスが私たちを殺している)][16](Slideshow)
*   [CSS Bloat (CSS 過剰)][17](Slideshow)

## 結論

多くの人々が OOCSSを憚る. 私たちが &#8220;ベストプラクティス&#8221;と学んで来たものなどを違反することのように見えるからだ. しかし **OOCSSの長期的利得**を一度理解してからは, 多くの開発者たちが転向すると確信する.  
全般的に私は OOCSSが CSS 開発の明るい未来のaaと思う. そして OOCSSはすべての開発者たちがウェブページをもっと早くて效率的で維持補修しやすく作るのためにプロジェクトに ゾックオドミョッミョッ段階では 適用しなければならない概念だ.

[翻訳者注] OOCSSに関心が持てたら[&#8220;[翻訳] OOCSS（オブジェクト指向CSS）とSassを結合することが最高のCSSコーディング方法である（OOCSS + Sass = The best way to CSS）&#8221;][18] <a class="simple-footnote" title="原文 : OOCSS+ Sass= The best way toCSS" id="return-note-1872-7" href="#note-1872-7"><sup>7</sup></a> も一度検討してみるのが良いだろう。 OOCSSは、HTMLのメンテナンスに苦労しているためOOCSSモジュールの概念を基にSass3.2の`@ extendを使用すると、最もという主張だ。`

<div class="simple-footnotes">
  <p class="notes">
    Notes:
  </p>
  
  <ol>
    <li id="note-1872-1">
      The common styles might exist for branding purposes or consistency of design. <a href="#return-note-1872-1">&#8617;</a>
    </li>
    <li id="note-1872-2">
      訳者註 &#8211; <code>#sidebar h3</code> 同じ式で使ったこと <a href="#return-note-1872-2">&#8617;</a>
    </li>
    <li id="note-1872-3">
      clearfixと言う(のは) <code>float</code> 要素をコンテナがまともにくるむようにすることを言う. <a href="#return-note-1872-3">&#8617;</a>
    </li>
    <li id="note-1872-4">
      these “freebies” could be<a href="http://www.svennerberg.com/2008/12/page-load-times-vs-conversion-rates/">a crucial performance gain</a>. <a href="#return-note-1872-4">&#8617;</a>
    </li>
    <li id="note-1872-5">
      内容と関係なくて翻訳しにくい部分一部を略した.With OOCSS, instead of a constantly growing stylesheet full of specificity wars, you’ll have an<strong>easy to maintain set of modules</strong>where the natural cascade plays an important role. <a href="#return-note-1872-5">&#8617;</a>
    </li>
    <li id="note-1872-6">
      訳者註 &#8211; IDは唯一のやつにだけ適用するのだから. <a href="#return-note-1872-6">&#8617;</a>
    </li>
    <li id="note-1872-7">
      原文 : <a href="http://ianstormtaylor.com/oocss-plus-sass-is-the-best-way-to-css">OOCSS+ Sass= The best way toCSS</a> <a href="#return-note-1872-7">&#8617;</a>
    </li>
  </ol>
</div>

 [1]: http://coding.smashingmagazine.com/author/louis-lazaris/?rel=author
 [2]: http://www.stevesouders.com/blog/2009/10/06/business-impact-of-high-performance/
 [3]: http://www.stevesouders.com/blog/
 [4]: http://developer.yahoo.com/performance/rules.html
 [5]: https://github.com/stubbornella/oocss/wiki
 [6]: http://www.impressivewebs.com/rolled-new-design/
 [7]: http://www.stubbornella.org/
 [8]: https://github.com/stubbornella/oocss/wiki/Content
 [9]: http://www.stubbornella.org/content/2010/06/25/the-media-object-saves-hundreds-of-lines-of-code/
 [10]: http://www.svennerberg.com/2008/12/page-load-times-vs-conversion-rates/
 [11]: http://csslint.net/
 [12]: https://github.com/stubbornella/csslint/wiki/Rules
 [13]: http://www.stubbornella.org/content/2011/01/22/grids-improve-site-performance/
 [14]: http://www.slideshare.net/stubbornella/object-oriented-css
 [15]: http://developer.yahoo.com/blogs/ydn/posts/2009/03/website_and_webapp_performance/
 [16]: http://www.slideshare.net/stubbornella/our-best-practices-are-killing-us
 [17]: http://www.slideshare.net/stubbornella/css-bloat
 [18]: http://jp.mytory.local/archives/1881 "[翻訳] OOCSS（オブジェクト指向CSS）とSassを結合することが最高のCSSコーディング方法である（OOCSS + Sass = The best way to CSS）"