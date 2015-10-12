---
title: 'ブログのデザイン刷新 &#8211; 魔法のツリーのテーマ'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/2137
daumview_id:
  - 50004336
categories:
  - Web publishing
tags:
  - CSS
  - Web Design
---
このブログの最初の文は、2009年6月26日に書いた。 `z-index`の単一行のメモだったが、今は非公開処理されている。 内容の正確性に自信がなくて、より正確な文を翻訳するつもりで下した。 女ねじったので、今日で約4年3か月の間ブログを運営したのだ。

ブログは最初にポチオクで始めたが、それグーグルのブロガーに統合され、設置型ワードプレスに移した。 初めて使用したテーマは、ハイブリッドというシンプルなテーマであった。 次に、デフォルトのテーマであるTwentyElevenを使用し、その次にTwentyTwelveを使用した。 もちろん、私が多少手を見て使用した。 ただ使わなかった。 文を探してみると[TwentyElevenテーマを手を加えたのは記録が残っている。][1]

今回のブログの再編を見て野心的になった。 デザインを自分ですることにした。 テーマは変えるのではなく、最初から最後まで私が作成した。 約10日頃の余暇時間合間をぬって作業をして作った。

## デザインコンセプト

史上初のウェブサイトのデザインをしてみた。 結果は満足している。 トレンドに沿ってフラットなスタイルでデザインしており、テーマのコンセプトは &#8220;魔法の木&#8221;だ。 元々は魔法陣コンセプトにしようとした。 私のニックネームを &#8220;緑風（绿风）&#8221;に使用するため、緑をテーマカラーに使用しようと考えていた。

しかし、魔法陣で検索してから魔法の木がナオギルレ &#8216;magic tree &#8220;とも一度検索をしてみた。 そうだったがやめ画像かに惚れてしまった。 今のロゴで使用している[魔法の木][2]である。 有料であった。 約1万2千ウォンで購入した。 購入した画像で色が少し変えたのが今のサイトのロゴだ。

![Magic Tree Concept][3]

今のところサイトのヘッダーキャプチャして何をするかだが、後でデザインの変更と、材料となるだろう。

テーマにある変化を与えることができた。 クラスだけを変更すると、ヘッダが暗いテーマに変更するように作られていた。 後で使用する予定だが、そのテーマのコンセプトを元にファビコンとは、iPhoneのタッチアイコンを作った。 下の画像だ。

![Magic Tree Logo][4]

花札だという評価を聞いたが、満足している。

魔方陣、魔法のツリーの両方の魔法に関連するだろう。 正しい。 魔法をコンセプトにデザインをしたのだ。

魔法をコンセプトにキャッチした理由は、私が文系出身で初めてのプログラミングでは、データベースの操作をしたときに感じたのがまさにそれだったからだ。

<左21>  
で働く時だった。

中間の出版物は50以上に掲載されたすべての記事の発行日の情報が間違っていた。 だから約記事2千〜3千ガエチェウムされる量である。 2週ぐらいしまったセな仕事をして日付を正さなければならないと思っていた。 その時ちょうど私はPHPを最初に勉強していて、本の半ばを超えて行こうMySQLの説明が出てきた。 SQLステートメントをうまく利用すれば一発でという気がした。 PHP `for`文を回して、SQLステートメントを抜いてそれをもう一度丁寧にエディットプラスに持ってきた後にエラーがないかどうか、しばらく確認した後、ローカルDBのPhpMyAdminで実行してみた。 万歳！ 一発ですべてのエラーはすぐに逮捕された。 その時感じたのだ。

**&#8220;これは魔法だね&#8221;**

考えてみると、ウィザードのプログラマは同じような職種であるようだ。 ヨトン各説して&#8230;

## 使用した技術と技法、気をつけた点

最新の技術と技法を使って、少ない労力で最大の効率を出そうと努力した。 さまざまな画面サイズに対応できるようにした。 その一方で、メンテナンスしやすいようにしようと努力した。 また、何よりも使いやすさを最優先に考慮した。 ディテールもお見逃しないようにした。 だから、次のような技術やテクニックを使用した。

*   CSSのフレームワークである[inuit.css][5]を使用した。
*   CSS前処理起き[sass][6]を使用した。
*   `style.sass`には、 `@import`宣言がおき、ファイルを細かく分けて作業した。
*   マージンとパディングは、一部の例外を除いては、すべてsass変数として処理した。 変数を使用してinuit.cssが提供するリズム感のギャップをそのままにしようとした。
*   色もいくつかの例外を除いては、すべてsass変数として処理した。 これにより、一貫した色を維持しようとした。
*   [Flat UI &#8211; Free Web User Interface Kit][7]が提供するColor Swatchesの色を取って使用した。 専門家ではないのでたたんで入った。
*   `margin-top`は使用せず、 `margin-bottom`のみを使用した。 （ [Single-direction margin declarations][8] ）
*   [オブジェクト指向CSS][9]の原則に従っしようとした。
*   CSSの命名規則は、 [BEM][10]を続いた。
*   レティナディスプレイ対応はSVGにした。 SVGを認識しないブラウザはpngを提供した。 phpでブラウザ検出を優先した後、modernizrがクライアント側で再チェックするようにした。
*   SVG、CSSも適用した。
*   jsに形を変えることはしなかった。 CSS3アニメーションでは、トランジションとキーフレームを使用して、jsはクラスを離した付けただけである。 （ [SMACSS：Changing State][11] ）
*   メディアクエリを利用して反応型で作業した。
*   反応型の操作時にブレークポイントは、特定の値にしなかった。 ただ、必要な場所で適切に分けた。（ [&#8220;反応型のWebデザイン&#8221;をお勧めします。][12] ）
*   モバイル優先主義を適用しなかった。 韓国のモバイルブラウザは、99.6％以上のメディアクエリをサポートします。 （ [RWD＃3。モバイルファースト（モ ​​バイル優先株式）][13] ）
*   SNSの共有にもjsやSNSサービスで提供されるボタンを1本も使わず、すべての単純なリンクで処理した。 必然的に次のビューウィジェットが次から提供するのに使用した。
*   ツイッターやフェイスブックのロゴは、その会社が提供するロゴデザインを使用した。
*   印刷ボタンを押すと、 `body`のクラスは1つだけ付けて、印刷イメージをユーザーが見ることができる状態で、印刷に入るようにした。 `@media print`は、 &#8220;戻る&#8221;ボタンを印刷しない目的でのみ使用した。 昔からやってみたかったんだけど、今回してみた。 印刷するときに、あえ​​てCourierフォントで作成することはなかったが、明確なゴシック様式は十分にきれいだと思うからだ。
*   <a href="http://www.crystaldesigns.tk/blog/favicon/" class="broken_link">様々なサイズと形式のファビコン</a>を提供した。 [フェイスブック用の共有イメージとファームウェアのリンク][14]を提供した。 Canonicalはタグを提供した。 つまり、さまざまなメタ情報を提供するために努力した。
*   テーマ依存でない機能はプラグインで処理した。 既に持っているのは、ダウンロードして使ったし（wp-pagenavi、minifyなど）、ないものは作った。
*   画像のmax-widthを100％にくれたので、実際よりもサイズが小さくなる場合がある。 80％以下に小さくなった場合には[元の表示リンクを提供][15]するようにした。 ブラウザのサイズが変わって画像がリサイズされると、再検出します。 元の画像が見える画像の数倍なのかも教えてくれる。
*   狭い画面で横に長いコードを見て不快感を改善するために、 [新しいウィンドウでコードビュー機能][16]を作った。 ビューポートのないハイライトされたコードを見ると、ちょっとよい。 やっぱり横スクロールが発生した場合にのみ、新しいウィンドウで表示オプションが追加さており、ブラウザがリサイズされると、再検出します。
*   ワードプレスの翻訳機能を利用して日本語と英語でのテーマのメッセージをすべて翻訳しておいた。
*   アクセシビリティを維持しようとした。 成功した確認道はありません。
*   font smoothi​​ngをサポートしていない場合は、フォントをMS Pゴシックにしてしまう。 （ [私が使用しているfont-family、そしてXPの明確なゴシックぼやけて出てくる問題を回避するためのヒント][17] 、 [How to Detect Font-Smoothing Using JavaScript][18] ）そして、この場合には印刷するときにCourierフォントを追加してくれる。 （このようなコンピュータの場合には明確なゴシックがインストールされていないXPことができますので。）

## 別に文を使って説明する予定であること

書いてみると気にたくさん書いた。 私が何をしたか整理もちょっとれる。 このうち、新たに学んだことは、いくつかの共有をするのがいいだろう。

*   サブブラウザをサポートし、SVGを活用する
*   CSS3アニメーション &#8211; トランジションとキーフレームを活用する
*   jsと`iframe`ないSNSシェアボタン
*   URLを変えずに、印刷イメージを表示し、印刷する
*   画像がたくさん小さくなった場合にのみ、ソースの表示]リンクを入れサイクル
*   `pre`ブロックに水平スクロールが発生した場合、新しいウィンドウで浮かせて表示ボタンを入れサイクル
*   OOCSS、inuit.css、BEM経験の共有

個人的なプロジェクトは、時間に追われずに企画を自分でするので、一針一針精魂を込めて作ることができるという利点がある。 満足なブログリニューアルだった。

 [1]: http://translate.googleusercontent.com/translate_c?depth=1&hl=ko&ie=UTF8&prev=_t&rurl=translate.google.co.kr&sl=ko&tl=ja&u=http://mytory.local/archives/2159&usg=ALkJrhhJBGe6mDGNZALwj4B-PJx864aqVQ
 [2]: http://www.istockphoto.com/stock-illustration-3561299-magic-tree-amp-birdie.php
 [3]: http://dl.dropboxusercontent.com/u/15546257/blog/mytory/magic-tree-01.png
 [4]: http://dl.dropboxusercontent.com/u/15546257/blog/mytory/magic-tree-logo.png
 [5]: http://inuitcss.com/
 [6]: http://sass-lang.com/
 [7]: http://designmodo.com/demo/flat-ui/
 [8]: http://csswizardry.com/2012/06/single-direction-margin-declarations/
 [9]: http://translate.googleusercontent.com/translate_c?depth=1&hl=ko&ie=UTF8&prev=_t&rurl=translate.google.co.kr&sl=ko&tl=ja&u=http://mytory.local/archives/8949&usg=ALkJrhhG5GSBciCxTQQLH3DglTYKWC4T9A
 [10]: http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/
 [11]: http://smacss.com/book/state
 [12]: http://translate.googleusercontent.com/translate_c?depth=1&hl=ko&ie=UTF8&prev=_t&rurl=translate.google.co.kr&sl=ko&tl=ja&u=http://mytory.local/archives/4892&usg=ALkJrhi-S7f2gtmThF3-70d-NAiqLD1Fyw
 [13]: http://tobyyun.tumblr.com/post/58232536556/rwd-3
 [14]: http://translate.googleusercontent.com/translate_c?depth=1&hl=ko&ie=UTF8&prev=_t&rurl=translate.google.co.kr&sl=ko&tl=ja&u=http://mytory.local/archives/2186&usg=ALkJrhhKNL2K0T5QnQshDnNgrTAoNwpZmQ
 [15]: https://github.com/mytory/mytory-original-img-link
 [16]: https://github.com/mytory/mytory-code-view
 [17]: http://translate.googleusercontent.com/translate_c?depth=1&hl=ko&ie=UTF8&prev=_t&rurl=translate.google.co.kr&sl=ko&tl=ja&u=http://mytory.local/archives/9743&usg=ALkJrhiW0flgGGBFx6ircx2SqJuAVYByXw "私が使用しているfont-family。そしてXPの明確なゴシックぼやけて出てくる問題を回避するためのヒント"
 [18]: http://www.useragentman.com/blog/2009/11/29/how-to-detect-font-smoothing-using-javascript/