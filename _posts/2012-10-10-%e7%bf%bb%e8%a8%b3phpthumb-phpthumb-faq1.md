---
title: '[翻訳:phpThumb] phpThumb FAQ(1)'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/333
aktt_notify_twitter:
  - yes
categories:
  - Web server
tags:
  - PHP
  - phpThumb()
---
これ 文は phpThumb() ホームページの <a href="http://phpthumb.sourceforge.net/demo/docs/phpthumb.faq.txt" target="_blank">phpthumb.faq.txt</a> 義 前部 半分を 翻訳した 文だ. 尻手は 引き続き 視訳中だ.

## phpThumb(), 自主 する 質問

<p style="font-weight: bold;">
  Q: 知りたい 蟹 あるのに ここ 返事が ない 場合 どうに 支援受ける 数 あるんですか?
</p>

A: <a href="http://support.silisoftware.com/" target="_blank">http://support.silisoftware.com</a> を 訪問して 質問, 提案, バグ 申告 ような ガール 割 数 あります.

<p style="font-weight: bold;">
  Q: バグを 見つけた の ようなのに 仮装(家長) 先に すると 割 仕事は?
</p>

A: 最新 バージョンを 使用中なのか 確認して 見てください. 運が 良ければ [最新 バージョン円では] バグが もう 直ったかも 分からないです. そして 出て 最新 バージョンと 一緒に 再び テストして 見てください. バグ 報告を 夏期 前に ね.

<p style="font-weight: bold;">
  Q: phpThumb街 考えどおり 作動するの ないですね. サーバー 設定 だからである の ようです. どうに チェックする 数 あるんですか?
</p>

A: /demo/demo.check.php を 回して 見てください. 推薦 サーバー 設定 提案と 性能 改善を のために 割 ものなどを 捜す 数 あります.

<p style="font-weight: bold;">
  Q: GPL銀 何ですか? 商業用 サイトで これを 使う 数 あるんですか?
</p>

A: GPL FAQを 見てください.(<a href="http://www.gnu.org/licenses/gpl-faq.html" target="_blank">http://www.gnu.org/licenses/gpl-faq.html</a> [そのまま <a href="http://www.gnu.org/licenses/gpl-faq.ko.html#DoesTheGPLAllowMoney" target="_blank">ここ</a>を 見なさい 商業的に 利用 可能だと 使って ある. しかし 多様な 環境に 置かれる 時 複雑な 条件たちが ある. そうだから 商業的 活用を 真剣に 割 つもりなら き帳面に GPLを 察して 表示 望む.]) 一般的に, もし あなたが <img src=&#8221;phpThumb.php?src=pic.jpg&w=100&#8243;> のように 標準で phpThumb.phpを 呼び出すのを 願ったら 問題が ない. あなた サイトが 商業的でも なくても, あなた コードが どうな 著作権 方針を よっても 間に 上 方式を 使う 件 自由です.

もし あなたが phpThumb()を 客体で 呼び出して 使ったら, ライセンス イシューを 気を使うと します. それでは 上に 紹介した FAQわ GPLを き帳面に よく見ること(consult) 望みます.

phpThumb()を 商業的に 使っても なくても 間に, お金を 支払う 必要は ない. しかし 後援(donation)銀 いつも 歓迎だ. 後援は <a href="http://phpthumb.sourceforge.net/" target="_blank">http://phpthumb.sourceforge.net</a> で 割 数 ある.

<p style="font-weight: bold;">
  Q: ソムネである 生成が 寝る なる イメージも あって, 中 そんな のも あります.(代りに 原本 サイズ イメージが そのまま 出力されます.)
</p>

A: PHP街 許容する メモリー サイズが 十分なの なくて, ImageMagick度 サーバーに 設置されるの ない 場合です. PHP メモリーは イメージ ピクセル 獣医 5滲む なると します.

例えば,

<pre class="brush:plain">640x480x5	= 1.5MB
	1600x1200x5	= 9.2MB</pre>

PHP メモリー サイズは php.iniで 調節する 数 あります.(サーバー 管理 権限が あったら ね.) あるいは (今のところは もっと ましな 方法なのに) サーバーに ImageMagickを 設置してください. それでは メモリー 制約 問題を 避ける 数 あります. もし 上の 二 枝 方法 中 どうな のも 割 数 なければ PHP街 制御する 数 ある メモリー 中方へ イメージ サイズを リサイズする 数 あります. 受動で ね. (あなたが 愛用する イメージ エディタを 使えば なります.) そして/あるいは 内臓 EXIF ソムネイルが ある イメージで 再び 保存する 数 あります.(ポトシャブ ような ガール 利用して ですね.) それでは phpThumb街 原本 イメージで それを 使う 数 あります.(勿論, イメージ 水っぽい 落ちるが ない よりは ましです.)

<p style="font-weight: bold;">
  Q: ソムネイルを 生成しながら 新しい 高さと 幅を 決める 方法が ありますか?(img タグに widthと heightを 指定する 数 あるのか)
</p>

A: 問題は phpThumb街 イメージを リターンするという はずです. width/height ような 追加的 情報を 送ってくれる 数 ある 方法は ないです. しかし こういう 式で 割 数 あります.

<pre class="brush:php">require_once(&#039;phpthumb.functions.php&#039;);
$pic = &#039;picture.jpg&#039;;
list($source_w, $source_h) = GetImageSize($pic);
$max_w = 375;
$max_h = 400;
list($newW, $newH) = phpthumb_functions::ProportionalResize($source_w, $source_h, $max_w, $max_h);
$url = &#039;phpThumb.php?src=&#039;.$pic.&#039;&w=&#039;.$max_w.&#039;&h=&#039;.$max_h;
echo "&lt;img src=""$url"" width=""$newW"" height=""$newH""&gt;&#039;;</pre>

<p style="font-weight: bold;">
  Q: こういう エラー メッセージが 出ました.
</p>

Failed: RenderToFile(<filename>) failed because !is\_resource($this->gdimg\_output)

A: RenderToFile()おこるが OutputThumbnail 前に GenerateThumbnail()を 呼び出す ガール 漏らした だからです.

例題 ページ /demo/phpThumb.demo.object.php を 参考してください.

<p style="font-weight: bold;">
  Q: インターネット エクスプローラで phpThumb街 作った イメージを 保存しようと するから BMP フォーマットで 保存されます. なぜ そんな ことですよ?
</p>

A: phpThumb せいが いいえ. IEに 関する 論議を 見てください.

<a href="http://support.microsoft.com/default.aspx?scid=kb;en-us;810978" target="_blank">http://support.microsoft.com/default.aspx?scid=kb;en-us;810978</a>

<a href="http://support.microsoft.com/default.aspx?scid=kb;en-us;260650" target="_blank">http://support.microsoft.com/default.aspx?scid=kb;en-us;260650</a>

<p style="font-weight: bold;">
  Q: 透明 領域が ある PNGで 透明 部分が 灰色 背景で 出ます.
</p>

A: インターネット エクスプローラは 去る 10年 間 割れた アルファ チャンネル ディスプレーを 持って ありました. そのため これは 修正される 数 ないです. 違う 主要 ブラウザーたちは 一般的に アルファ チャンネルを 寝る 制御します. PNG アルファ チャンネルが まともに 見えるように 日 与える IE 核は <a href="http://www.silisoftware.com/png_alpha_transparency/" target="_blank">http://www.silisoftware.com/png_transparency/</a> わ <a href="http://www.silisoftware.com/png_alpha_transparency/" target="_blank">http://www.koivi.com/ie-png-transparency/</a> を 見れば 出ます. (訳者 株 : どうする 仕事なのか 二 ページが 皆 消えたし, 追跡して 見たら 結局は ような ページを 示すように なって 捨てた.)

<p style="font-weight: bold;">
  Q: ファイルが 存在するにも &#8220;<filename> does not exist&#8221;[ファイルが 存在するの ないです.] という メッセージが 出ます.
</p>

A: phpThumb.config.php に 二 枝 値段が あるのか, あったら 正確に あるのか チェックして 見てください.(バージョン 1.6.0を 基準で 説明します.)

$PHPTHUMB\_CONFIG\['allow\_src\_above\_docroot'\] (基本値=false)

$PHPTHUMB\_CONFIG\['allow\_src\_above\_phpthumb'\] (基本値=true)

イメージが DOCUMENT\_ROOT 外に ある ことなら(イメージ アップロード フォームが あったら 含まれて ある 建国大, 普通 イメージは &#8220;/tmp/<file>&#8221; 式の ディレクトリに アップロードされる) それでは &#8216;allow\_src\_above\_docroot&#8217;を true路 設定すると 割 はずです.

必ず ウェップサーバーが ファイルと ディレクトリを 読む 数 あるように パーミッション 設定を すると します.

<p style="font-weight: bold;">
  Q: 客体で 使う 時 phpThumb.phpわ phpThumb() 中 何を 使うと しましょうか?
</p>

A: 基本的 機能だけ 使ったら phpThumb.php街 (少ない コーディングで) もっと 使うこと 易しいです. phpThumb.php街 あらゆる キャッシュを 調整します; 客体を 使えば 自分ばかりの キャッシュ用 コードが 必要です. もし 存在する イメージの ソムネである コードを 見せてくれる のだけ 望んだら, phpThumb.phpを 使ってください. もし ソムネイルを ファイルで 保存して たければ, (例えば アップロードする 間) 客体 モードを 使う のが 適切です. また, phpThumb.config.php銀 phpThumb.phpでばかり 使います. そうするので もし あなたが 客体 インストンスを 生成したら あらゆる 設定を 受動で すると します. phpThumb.config.php街 [客体には] 誰 影響も 及ぶの ない だからです. そのため, 繰り返そうとすると:

\*\*客体が 必要な 蟹 ないなら 常に phpThumb.phpを 使ってください\*\*

<p style="font-weight: bold;">
  Q: ソムネイルが ある ページに 初め 入って行けば ソムネイルは 中 見えて イメージ フレームだけ 見えます.(あるいは イメージが 中 見えます.) 改めることを 押せば あらゆる ソムネイルが 瞬く間に 浮かびます.
</p>

A: こんなに 日 見れば 寝る 作動する 首都 あります.

<span style="white-space: pre;"> </span>$PHPTHUMB\_CONFIG['cache\_force_passthru'] = false;

するが つけるように 基本 設定でも 寝る 作動します.

お知らせ: 1.7.9 以前 バージョンでは たぶん いくつか 正義されるの ない 変数が あって こういう 増税が 現われる 首都 あります. [ところが] もし バージョン 1.7.9私 それより もっと 高い バージョンでも こういう 症状が 発生したら info@silisoftware.comで 電子メールを 送って ください.

<p style="font-weight: bold;">
  Q: phpThumb()に フロント-エンド(使用者) グラフィック インターフェースが あるんですか?
</p>

A: /demo/readme.demo.txtを 見てください.

<p style="font-weight: bold;">
  Q: phpThumb義 /に 関する 保安 争点が ありますか?
</p>

A: <a href="http://secunia.com/product/5199/" target="_blank">http://secunia.com/product/5199/</a>

<p style="font-weight: bold;">
  Q: phpThumb()路 出力された イメージは なぜ フラッシュで 作動するの ないんですか?
</p>

A: フラッシュは プログレッシブ JPEG科 上声が 中 当たります. こんなに 設定してください:

&nbsp;

<pre class="brush:php">$PHPTHUMB_CONFIG[&#039;output_interlace&#039;] = false;</pre>

&nbsp;

<p style="font-weight: bold;">
  Q: イメージ 水っぽく とても 良いでしょう ないです. なぜ そうでしょうか?
</p>

A: GD 1.x バージョンを 使って あったら 方法が ないです. GD 2.x バージョンで アップグレード してください.

<p style="font-weight: bold;">
  Q: イメージ 水っぽく 激 中 良いです. ピクセルが だ 見えます. なぜ そうです?
</p>

A: 原本 イメージが PHPメモリー 許容値より もっと カーソルー, phpThumb街 EXIF ソムネイルを 原本 イメージ 代わり 使った だから そんな のである 数 あります. EXIF ソムネイルは 普通 160&#215;120 位 なります.(そのため それを 640&#215;480で リサイズすれば 激 中 良くて 見える ことですよ.) php.iniで 勧奨 メモリー 用量を 計算しようとすれば イメージ ピクセル 数に 5を 掛けてください:

例えば, 1600&#215;1200 = 1600 \* 1200 \* 5 = 9600000 = 10M

[これより もっと] 易しい 解決策は ImageMagickを 設置する のです.

<p style="font-weight: bold;">
  Q: 生成した ソムネイルを ファイルで 保存する 数 あるんですか?
</p>

A: はい. 何 枝 方法が あります. 仮装(家長) 良い 方法は phpThumb 客体を 生成して RenderToFile()を 呼び出す のです. [これを 利用して] 願う ファイル名で 保存すれば なります.

/demo/phpThumb.demo.object.phpに 例題が あるから 見てください.

違う 方法は &#8216;file&#8217; パラメーターを 利用する のです. (/docs/phpthumb.readme.txtを 見てください.) するが これ パラメーターは これ以上 支援するの なくて 1.7.5 バージョン 以後 作動するの ないです.

<p style="font-weight: bold;">
  Q: &#8220;Off-server[違う サーバーに ある ファイルを 利用した] ソムネである 作るのが 許容されるの ないです(Off-server thumbnailing is not allowed)&#8221; &#8212; どうに すれば 可能に 作ります?
</p>

A: 基本的に, phpThumb()増えた ような ドメインに ある イメージの ソムネイルだけ 生成する 数 あります. 違う ドメインに ある イメージで ソムネイルを 万たち 数 あるように するためには, (phpThumb.config.phpに) こういう 式で ドメインを 追加して ください:

<pre class="brush:php">$PHPTHUMB_CONFIG[&#039;nohotlink_valid_domains&#039;] = array(
  @$_SERVER[&#039;HTTP_HOST&#039;], &#039;example.com&#039;, &#039;www.example.com&#039;,
  &#039;subdomain.example.net&#039;, &#039;example.org&#039;);

//To disable off-server thumbnail blocking, just set:
  $PHPTHUMB_CONFIG[&#039;nohotlink_enabled&#039;] = false;</pre>