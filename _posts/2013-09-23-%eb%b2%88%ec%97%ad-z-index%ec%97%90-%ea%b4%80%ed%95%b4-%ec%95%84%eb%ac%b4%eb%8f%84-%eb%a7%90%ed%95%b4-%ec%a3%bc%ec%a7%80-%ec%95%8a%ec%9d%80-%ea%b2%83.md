---
title: '[翻訳] z-indexについて誰も教えていないこと'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/2144
daumview_id:
  - 50052823
categories:
  - Web publishing
tags:
  - CSS
---
IEでメガメニューのサブメニューz-indexが問題を引き起こしているので、頭を腐ったことがあった。どのように解決はしたが、より正確に知る必要があると考えた。その後、z-indexに関する信頼性の高い記事を見たのは、Twitterであった。誰が推薦されたのか記憶はないのに、[&#8216;What no one told you about z-index&#8217;][1]という文があった。いつか翻訳すべきだと思っていたが今になっている。

翻訳中[]内は理解を助けるために私が追加した内容です。 Stacking Context、Stacking Orderは、Mozilla韓国ブログの用例に沿って&#8217;サトイム点&#8221;と&#8221;サトイム順&#8221;と翻訳した。

翻訳開始である。

&#8212;

z-indexの問題は、それが実際に動作するかを理解する人があまりにも少ないのである。 z-indexが複雑ではない。しかし、スペックを読んだことがない場合は、間違いなくそこには、あなたが全く知らない決定的な側面がある。

わからないときは、一度この問題を解いてみてください。

## 問題

3つの<div>要素を含むHTMLがある。各<div>は<span>要素が一つずつある。各<span>要素に背景色がある。背景色はそれぞれ赤、緑、青である。各<span>は、すべてのドキュメントの左上近くに、他の<span>要素と軽く重ねて置かれている。だから、何より前にいるのか、どのように積まれていることを知ることができる。最初の<span>は、z-indexが1である。他の二つの<span>にはz-indexがない。

HTMLと基本的なCSSは次のとおりである。下部には、完全なCSSと実際の動作デモ（[Codepen][2]）を配置していた。

    <div>
      <span>Red</span>
    </div>
    <div>
      <span>Green</span>
    </div>
    <div>
      <span>Blue</span>
    </div>
    

    .red, .green, .blue {
      position: absolute;
    }
    .red {
      background: red;
      z-index: 1;
    }
    .green {
      background: green;
    }
    .blue {
      background: blue;
    }
    

<pre class="codepen"data-height="268"data-type="result"data-href="ksBaI"data-user="philipwalton"data-safe="true"><code></code><a href="http://codepen.io/philipwalton/pen/ksBaI">Check out this Pen!</a></pre>

**これが問題だ**：赤い<span>を、下のルールを壊すことなく、青と緑<span>要素の下に行かせてみてください。

*   HTMLマークアップをどのような方法に触れるいけない。
*   いくつかの要素にもz-indexを追加したり、変更してはいけない。
*   いくつかの要素のpositionプロパティを追加または変更してはいけない。

してみるつもりであれば、上記のコードのペンで行ってちょっとしてみてください。成功した場合、以下のように示さなければならない。

**注意**：次の例の[CSS]タブをクリックしないでください。クリックすると、答えがすぐに見られる。

<pre class="codepen"data-height="268"data-type="result"data-href="dfCtb"data-user="philipwalton"data-safe="true"><code></code><a href="http://codepen.io/philipwalton/pen/dfCtb">Check out this Pen!</a></pre>

## 解決策

解決策は、最初の<div>（赤い<span>の親）にopacityを1より小さくてくれるのだ。これが上記のコードのペンに追加されたCSSです。

    div:first-child {
        opacity: .99;
    }
    

要素のサトイム順（Stacking Order）にopacityが影響を及ぼすことに衝撃を受け、頭をかきむしっている場合は、歓迎する。私が最初にこの問題にかかった時私も似たよう衝撃を受けた。

## サトイム順(Stacking Order)

z &#8211; indexは非常に簡単に見える。 z &#8211; indexが高いのがz &#8211; indexが低いことよりも前に出てくる。そうではないか？うーん、実際にはありません。これはz &#8211; indexの問題の一つだ。して簡単に見えて、非常に多くの開発者は規約を読んでいないということだ。

HTML文書のすべての要素は、他の要素の前出たり後ろに入ることができる。みんなこれをサトイム順（ stacking order ）として知られている。この順序を定める規則は、仕様に非常に明確に定義されている。しかし、私は先に述べたように、ほとんどの開発者がそれを完全に理解していない。

z &#8211; indexとpositionプロパティがないときは、規則が非常に単純である。基本的にサトイム順序は、 HTMLで表示される順序と同じである。 （右、実際にはそれより[も少し複雑ですが、][3]我々はinline要素をカバーするために負のマージンを使用していない以上、このような例外的場合に会うことはないだろう。 ）

positionプロパティを要素に使用する場合、 positionプロパティを持つすべての要素（とその子要素）は、 positionプロパティが存在しない要素の前に現れる。 （ positionプロパティがということは、 staticではなくpositionプロパティがあるということだ。例えば、 relative 、 absoluteのようなもの。 ）

最後に、 z &#8211; indexが関連付けされると、もっと複雑になる。最初は、 z &#8211; indexの値がより高い要素が前面に来ると、 z &#8211; indexの要素はz &#8211; indexがない要素よりも前に来ると仮定するのが自然だ。しかし、それはそう簡単ではない。まず、 z &#8211; indexは唯一のpositionプロパティを持つ要素でのみ動作します。 positionプロパティが指定されていない要素のz &#8211; indexを付けてみると、何もない起こる。第二に、 z &#8211; indexの値はサトイムコンテキスト（ stacking contexts ）を作成することができる。そして今、簡単に見えていたのが急に信じられないほど複雑になる。

## サトイム点（ Stacking Contexts ）

同じ親の下にあってサトイムの順序で一緒に前後に一度に移動することができる要素のグループはサトイムコンテキスト（ stacking context ）と呼ばれるものを作る。サトイム文脈を完全に理解することがz &#8211; indexとサトイム順序が動作する方法を真に理解するための鍵である。

すべてのサトイムコンテキストには、根（ root ）の要素であるHTML要素がある。いくつかの要素からサトイム点が新たに作成されると、そのサトイム点は、子要素がサトイム順で特定の範囲を超えないように制限を定めることになる。 [ ref ] When a new stacking context is formed on an element 、 that stacking context confines all of its child elements to a particular place in the stacking order [/ref ]これは、一番後ろのサトイムコンテキストの要素は、それより前のサトイム文脈の要素よりも前に出ることができないことを意味する。 z &#8211; indexを十万を与えても効果がない。 [ ref ] That means that if an element is contained in a stacking context at the bottom of the stacking order 、 there is no way to get it to appear in front of another element in a different stacking context that is higher in the stacking order 、 even with a z &#8211; index of a billion ！ [/ref ]

サトイム点は、次の三つのいずれかに属している場合作られる。

要素が文書のルート要素である場合（つまり、 <html>要素）  
要素のpositionの値がstaticではないながら、 z &#8211; indexもautoがない場合  
要素のopacityの値が1より小さいとき  
[モバイルWebKitのとクロム22以上では、 position ： fixedは無条件に新しいサトイムコンテキストを作成します。 z - indexが" auto "であってもだ。 （[この記事参照][4]） ]  
サトイムコンテキストが作成された最初の二つ目の方法は、理解しやすく、 Web開発者たちもよく知っている（何呼ぶかどうかはわからないとしてもだ） 。

## サトイム順（ Stacking Order ）での要素の位置を決定する

（線、背景、文字ノードなどを含めて）すべてのページ要素の全体サトイム順（ global stacking order ）を実際に決めるのは非常に非常に複雑で、この記事の範囲を超えます。 （もう一度、仕様書をお勧めします。 ）

しかし、ほとんどの場合は[サトイム]順（ the order ）の基礎的理解があれば、多くの助けになるものであり、予測可能なCSS開発をしていくのに役立ちます。だから[サトイム]順（ the order ）を発見、それぞれのサトイムコンテキストに入ってみよう。

## の[ステップの]サトイム文脈でサトイム順

したサトイム文脈でサトイム順序を定める基本ルールは以下のとおり（ [次の順序]後ろから前へ[蓄積] ） 。

サトイムコンテキストの根（ root ）の要素。  
positionの値があり、 z &#8211; indexの値が負の要素（と子供たち） 。 （ z &#8211; indexの値が高い要素が前に置かれる。値が同じであればHTMLに表示される順序で表示されます。 ）  
positionの値がない要素（ HTMLで表示される順序に続く） 。  
positionの値があり、 z &#8211; indexの値がautoな要素（とその子たち） 。 （ HTMLで表示される順序で）  
positionの値があり、 z &#8211; indexの値が正の要素（とその子たち） 。 （ z &#8211; indexの値が高い要素が前に置かれる。値が同じであればHTMLに表示される順序で表示されます。 ）  
注意： z &#8211; indexが負の値とし、positionプロパティを持つ要素は、サトイム点でまず第一に蓄積される。つまり、他のすべての要素よりも後ろになる。ので、珍しいことがボルオジヌンデ、同じサトイム脈絡の中にある自分の親よりも後ろに置くことができるようになる。これは、その要素の親が同じサトイム脈絡の中にある場合にのみ機能します。 [もちろん、その要素も]サトイムコンテキストのルート要素よりも後ろに行くことはできない。これに関する良い例は、ニコラスゲルラホ（ Nicolas Gallagher ）の[イメージのないCSSドロップシャドウだ。][5]

## 全体サトイム順（ Global Stacking Order ）

いつどのように新しいサトイムコンテキストが作成されるかの強固な理解、サトイム文脈の中でのサトイム順序の明確な理解と、特定の要素が全体サトイム順でどのように表示されるかを理解するのも悪くない。

間違いを避ける鍵は、いつ新しいサトイムコンテキストが作成されるか知ることができるのである。 z &#8211; indexの値を十万を与えたのに[その要素が]サトイム順で先がない場合、その祖先のツリーを見ながら、親がサトイムコンテキストを作成していないか確認してみてください。そのような要素があれば、 z &#8211; indexの値十万も要らない。

## 包む（ Wrapping Up ）

元の問題に戻りましょう。各タグにサトイム順序を示すコメントを追加しました。この手順は、元のCSSをベースにしたものだ。

    <div><!-- 1 -->
      <span><!-- 6 --></span>
    </div>
    <div><!-- 2 -->
      <span><!-- 4 --><span>
    </div>
    <div><!-- 3 -->
      <span><!-- 5 --></span>
    </div>
    

我々は、1枚目の<div>にopacityルールを追加したとき、サトイム順序は次のように変更しました。

    <div><!-- 1 -->
      <span><!-- 1.1 --></span>
    </div>
    <div><!-- 2 -->
      <span><!-- 4 --><span>
    </div>
    <div><!-- 3 -->
      <span><!-- 5 --></span>
    </div>
    

span.redの順序は6であったが、1.1に変わった。私は新しいサトイム点が生じたことを表示するためにドット（.）を使用し、span.redは、その新しいサトイム文脈では、現在、最初の要素である。

今赤いボックスがなぜ他のものの後ろに行ったのかもっと明確に理解できるようになられた方だろう。元の例では、サトイム点が2つしかなかった。根（root）の要素とspan.redで作られたのだ。私たちはspan.redの親要素のopacityを与えた時、我々は第三サトイムコンテキストを作成したものであり、その結果、span.redのz-indexは、唯一の新しいサトイムコンテキスト内でのみ適用されるようになった。最初の<div>（私たちはopacityを付けたやつ）とその兄弟要素にpositionやz-indexの値がなかったので、そのサトイム点[つまり、根の要素（root）と<div>が属しているサトイムコンテキスト]の中のすべての要素は、HTMLソースの順序でサトイム順序が決定されたので、最初の<div>とのサトイムコンテキスト内のすべての要素が2番目と3番目の<div>の後ろに描かれたのだ。

## より読み物

*   [Elaborate description of Stacking Contexts][3]
*   [The stacking context][6]
*   [The Z-Index CSS Property: A Comprehensive Look][7]

 [1]: http://philipwalton.com/articles/what-no-one-told-you-about-z-index/
 [2]: http://codepen.io/
 [3]: http://www.w3.org/TR/CSS2/zindex.html
 [4]: http://updates.html5rocks.com/2012/09/Stacking-Changes-Coming-to-position-fixed-elements
 [5]: http://nicolasgallagher.com/css-drop-shadows-without-images/demo/
 [6]: https://developer.mozilla.org/en-US/docs/CSS/Understanding_z-index/The_stacking_context
 [7]: http://coding.smashingmagazine.com/2009/09/15/the-z-index-css-property-a-comprehensive-look/