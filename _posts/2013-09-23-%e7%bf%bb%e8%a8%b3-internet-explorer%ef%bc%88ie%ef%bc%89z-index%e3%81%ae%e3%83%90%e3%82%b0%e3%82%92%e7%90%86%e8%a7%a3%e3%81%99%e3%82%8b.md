---
title: '[翻訳] Internet Explorer（IE）z-indexのバグを理解する'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/2202
categories:
  - etc
  - Web publishing
tags:
  - CSS
  - IE：インターネット·エクスプローラ
---
一度この記事は、 [&#8216;Squish the Internet Explorer Z-Index Bug &#8220;][1]を翻訳したものである。 ところで文翻訳に入る前に、参考にことが一つあって引用して開始します。

> ### IE And The z-index Property
> 
> もしIE6やIE7で位置指定された構成要素にz-indexを使用する場合は、インデックススタッキング['stacking index'、すなわち、z-indexの値 - 녹풍(綠風)]は0に設定される。 これは、 [レンダリングエラー][2]を誘発する。 bakerという人が言った[解決策][2]は、親要素の[子要素よりも - 녹풍(綠風)]より高いz-indexを与えるものである。 どのような場合には、親要素がposition：relativeに割り当てる必要がありかもしれない。

上の段落は、 [&#8220;IE6のカンニングペーパー：IE6のバグ25 +解決する方法&#8221;][3] （ [原文][4] ）から引用したものである。

z-indexの理解が少しあるのがいいだろう、最近私が翻訳した[&#8216;z-indexについて誰も教えてくれなかったこと&#8221;][5] （ [原文][6] ）を参照すると便利だ。

それでは、 &#8220;Internet Explorerのz-indexのバグポ皆既 &#8216;（Squish the Internet Explorer Z-Index Bug）翻訳開始である。

* * *

## 問題

最近のウェブサイトを作っていたある日だった。 IEのチェックを試みるまで、すべてが順調だった。 通常は、IE7でもよく戻る。 ところが、この場合には致命的な問題があった。 absoluteポジションを与えたdivを浮かべたのがあった（hoverメニュー）、その下には透過PNGを使用して、やはりabsoluteに打ち込んでおいた画像があった。 これ以下のように見えた。

![IE z-index 버그][7]

### 解決策

absoluteを与えたdivのz-indexの値は1000であった。 しかし、 [@ jorenrapini][8]がIEのz-indexを正しく使用していないと指摘した。 私は欠陥を詳細に説明している[qurksmode.orgのこの記事][2]を偶然に発見した。

> Internet Explorerのpositionの値を持つ要素は、新しいサトイムコンテキスト（stacking context）を作成するときにz-indexを0にする。 このため、z-indexはもう正常に機能しない。

上の文は、対策をすぐに含んでいるわけではありませんが、このような問題を経験した人がコメントを残した。

> 親要素より高いz-indexの値を与えると、バグが修正される。

[親 - 子の関係で子要素を持つz-indexの値よりも高いz-indexを親に与えなさいという話だ。 - 녹풍(綠風)]

これは、サイトに次のコードを適用した。

<pre>&lt;div style="position: relative; z-index: 3000"&gt;
  &lt;div style="position:absolute;z-index:1000;"&gt;
    &lt;a href="#"&gt;Page&lt;/a&gt;
    ...
  &lt;/div&gt;
&lt;/div&gt;
&lt;img style="position:absolute" src="myimage.png" /&gt;</pre>

そのようにしたらこのような結果が出た。

![IE z-index bug fix][9]

なぜ解決したのかは聞かないでください。 どうかして解決された。

 [1]: http://www.brenelz.com/blog/squish-the-internet-explorer-z-index-bug/
 [2]: http://www.quirksmode.org/bugreports/archives/2006/01/Explorer_z_index_bug.html
 [3]: http://translate.google.co.kr/translate?sl=auto&tl=ja&js=n&prev=_t&hl=ko&ie=UTF-8&u=http%3A%2F%2Fwww.clearboth.org%2Fultimate-ie6-cheatsheet-how-to-fix-25-internet-explorer-6-bugs%2F&act=url
 [4]: http://www.virtuosimedia.com/dev/css/ultimate-ie6-cheatsheet-how-to-fix-25-internet-explorer-6-bugs
 [5]: http://jp.mytory.local/archives/2144
 [6]: http://philipwalton.com/articles/what-no-one-told-you-about-z-index/
 [7]: http://dl.dropboxusercontent.com/u/15546257/blog/mytory/ie-z-index-bug-1.png
 [8]: http://twitter.com/jorenrapini
 [9]: http://dl.dropboxusercontent.com/u/15546257/blog/mytory/ie-z-index-bug-2.png