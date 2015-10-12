---
title: '[翻訳] グーグル アナルリティックス PHP ClassGoogle Analytics API class for PHP'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/630
aktt_notify_twitter:
  - yes
categories:
  - Web server
tags:
  - PHP
---
[訳者 株] ウェブサイト 管理者モードで 統計を 報告 たい. ところが グーグル アナルリティックスは 統計 グラフ APIを 提供するの ない. 泡が いっぱい 立ち込めた ページビューを 露出して たくは なくて, もうちょっと 正確な グーグル アナルリティックスで 管理者 モードで 統計を 見えて 酒庫 たいのに 制約が 多かった. そのため グーグル アナルリティックス API ウェブサイトを 立ち後れて 見たが 徒労.

ところが 今日 検索を してから 良い 文を 見つけた. なぜ この前には くぎ 報告 度が外れた のか? 私が この前に <a title="[PHP] グーグル アナルリティックス 統計 グラフを ホームページに つけること" target="_top" href="http://mytory.local/archives/629">グーグル アナルリティックス グラフ ライブラリ</a>を 紹介した 少なく あったが, 彼 API増えた あまり 制限的な のだけ 知らせて 与えた だから 結局 使うの ないように なった. 今日 再び 良くて 見える ガール 見つけて 一応 翻訳から 日 見る. そして もうちょっと 使ってから jQuery ような こと 付けて グラフも 描いて 報告 割 つもりだ. 翻訳を だ して 出て 入る 所感は, &#8216;利子式 最高だ&#8217; する ことだ.

これから 翻訳 手始めだ. 原文は<a target="_top" href="http://www.askaboutphp.com/63/google-analytics-api-class-for-php.html">Google Analytics API class for PHP</a> だ.

(蛇足を つけようとすると 今 <a title="ワードプレス 3.2を 紹介する. 自分 PHP バージョンを 確認しなさい." target="_top" href="http://mytory.local/archives/1431">ワードプレス 3.2に 鳥で 追加された 機能</a>イン 全体 画面 編集 機能を 使って あるのに これ 書き込み 良い )

# Google Analytics API class for PHP

<img class="alignleft" src="http://dl.dropbox.com/u/15546257/blog/mytory/ga-marbles.jpg" alt="" height="184" width="277" />

たいてい 月 私はほど <a target="_top" href="http://analytics.blogspot.com/2009/04/attention-developers-google-analytics.html">グーグルが アナルリティックス API サービスを 開場</a>した. [訳者 株: これ 文は 2009年 5月 29仕事に 被せられた.] あらゆる アナルリティックス ユーザーに 言葉だ. APIを 利用すれば 開発者が GA[訳者株: グーグル アナルリティックス - 以下 全部 GA路 表記] 報告書を 自分の オプルリゲイションや ウェブサイトに 統合する 数 ある. はなはだしくは 携帯電話でも 呼んで来る 数 ある!

私が 触る サイトに これ APIを どうに 統合して, 機能を 進める 数 あるか まどろみ 悩みを した. するが アイディアを 出すこと(kicking off) 前に, 私は API 使い方と アクセス バングボブウルチァッよ 内野(find out)万 した. 私は ついに PHP クラスを 作った. これ 奴が APIを 呼び出す かんしゃくが起こる 仕事を 皆 処理して 竝び のだ. あなたは 団地 報告書の パラメーターだけ 提出すれば なる. それでは PHP クラスが アナルリティックス データが 入った 配列を リターンして 竝び のだ.

## 始めること

定木, なによりも まず, GA 勘定が あると する. 当然 ログインも すると する. そして 出て 内 文 マン 終わり 部分に ある 内 PHP クラスを ダウンロードすると する.

APIを アクセスする のは 基本的に 二 段階を 経るように なる. 先に グーグルに 自分 自分の 勘定で ログインを すると する. それでは 資格証明 コードを 得る 数 ある. それでは 資格証明 コードを 利用して GA プロフィールに 登録されて ある ウェブサイト データを 呼んで来る 数 ある.

グーグル アナルリティックス PHP クラス

これは ページビューと 訪問数を 呼んで 来る コードだ. 日付と 国家別で 分類を たいてい 後, &#8216;Austrailia&#8217;万 持って来るように フィルターを 適用した. ページビューが 高い 遊ぶことから 出力するように した.

<pre class="brush:php">// グーグル アナルリティックス PHP クラス include
include "googleanalytics.class.php";
try {
	// 自分の GA email IDわ パスワードを 使って GA クラスの インストンスを 生成する. [下の 電子メールと 1234増えた 自分の ので 変更する.]
	$ga = new GoogleAnalytics(&#039;email@company.com&#039;,&#039;1234&#039;);

	// 呼んで来るのを 願う GA プロフィールを セッティングする. 形式は &#039;ga:123456&#039; 載せる. [コード 下側に 何を 掻けば なるのか 説明されて ある.]
	$ga-&gt;setProfile(&#039;{GA Profile ID}&#039;);

	// 日付を セッティングする. フォーマットは YYYY-MM-DD
	$ga-&gt;setDateRange(&#039;2009-04-01&#039;,&#039;2009-04-07&#039;);

	// 国家と 日付別で 報告書を 持って 来る. Australia路 国家を ピルトリングして ページビューと 訪問数を 見えて 与えるように する.
	$report = $ga-&gt;getReport(
		array(&#039;dimensions&#039;=&gt;urlencode(&#039;ga:date,ga:country&#039;),
			&#039;metrics&#039;=&gt;urlencode(&#039;ga:pageviews,ga:visits&#039;),
			&#039;filters&#039;=&gt;urlencode(&#039;ga:country=@Australia&#039;),
			&#039;sort&#039;=&gt;&#039;-ga:pageviews&#039;
			)
		);

	//$report 配列を 出力する.
	print_r($report);

} catch (Exception $e) {
	print &#039;Error: &#039; . $e-&gt;getMessage();
}</pre>

私が 望む 件, 説明 オブで コード 自体が 自分が 何を するのか 現わす ことだ. `setProfile()`には 自分の ウェブサイト プロフィール id 番号が 必要だ. プロフィール id 番号を 得ようとすれば GA ダッシュボードに 行って 願う ウェブサイトの &#8216;報告書 表示&#8217;を 押す. そして URLを 察して 見る ことだ. そこに &#8216;id=xxxxxx&#8217; という 文字列が ある. それが 自分の id 番号だ. それを `setProfile()`に &#8216;ga:xxxxxxx&#8217; 形式で セッティングを 日 与えると する.

<p style="text-align: center;">
  <img class="aligncenter" src="http://dl.dropbox.com/u/15546257/blog/mytory/ga-url.jpg" alt="" height="29" width="507" />
</p>

それとも クラス 中に ある `getWebsiteProfiles()` 関数を 使っても なる. 資格証明を 得た 後 これ 関数を 呼び出せば, 自分の 勘定に 登録されて ある ウェブサイト プロフィール 配列を 得る 数 ある. そこにも id 番号を 捜す 数 ある.

注意を 傾けると する ユイルハン 関数は ところで `getReport()` 関数だ. 願う 結果を 得ること ためには これ 関数に 各種 パラメーターを 寝る 設定して 与えると する.

もし GAに 人慣れしたら, GA街 基本的に 二 枝 フィールド タイプを 土台で 作動するという ガール 分かって ある ことだ. それは ところで dimensions(寸法?) わ metrics(統計?) だ. 簡単に 言って, metrics 増えた GA 報告書の コラムで, dimensions 増えた 行で 思えば なる.

グーグルは APIで <a target="_top" href="http://code.google.com/apis/analytics/docs/gdata/gdataReferenceDimensionsMetrics.html">使う 数 ある dimensions わ metrics リスト</a>を 提供して ある.

[訳者 株: 配列に 入れる 各種 変数は <a target="_top" href="http://code.google.com/intl/ko-KR/apis/analytics/docs/gdata/v3/reference.html" class="broken_link">Core Reporting API - Reference Guide</a>西 参考すれば なる.]

`getReport()` 関数を 利用して 基本的に GA義 オーダーメード 報告書と ような 仕事を 割 数 ある. どうな dimensions わ metrics を 使う のか 決めれば, API街 データを リターンして 与える.

`getReport()` 関数を 利用して 得る 数 ある 結果は 下と ようだ.

<pre>Array
(
    [20090401‾‾Australia] =&gt; Array
        (
            [ga:pageviews] =&gt; 6
            [ga:visits] =&gt; 3
        )

    [20090402‾‾Australia] =&gt; Array
        (
            [ga:pageviews] =&gt; 4
            [ga:visits] =&gt; 3
        )

    [20090407‾‾Australia] =&gt; Array
        (
            [ga:pageviews] =&gt; 4
            [ga:visits] =&gt; 4
        )

    [20090403‾‾Australia] =&gt; Array
        (
            [ga:pageviews] =&gt; 3
            [ga:visits] =&gt; 3
        )

    [20090405‾‾Australia] =&gt; Array
        (
            [ga:pageviews] =&gt; 3
            [ga:visits] =&gt; 3
        )

    [20090406‾‾Australia] =&gt; Array
        (
            [ga:pageviews] =&gt; 3
            [ga:visits] =&gt; 3
        )

    [20090404‾‾Australia] =&gt; Array
        (
            [ga:pageviews] =&gt; 2
            [ga:visits] =&gt; 2
        )
)</pre>

配列を シンプルに 維持すること のために, 私は 基本的に dimensions を 始めて 番目 配列 することに 使った. 二 番目 dimensions やっぱり &#8216;‾‾&#8217;路 区分して 配列 することに 入れた. 必要ならば パッシングして 使いなさい. metrics 増えた 配列 中の 配列で 入って行く. これ 配列を metrics を することに 真書 自分の 値段を 入って ある.

あらゆる dimension これ metric 科 対応する ない. グーグルは <a target="_top" href="http://code.google.com/apis/analytics/docs/gdata/gdataReferenceDimensionsMetrics.html#explore2Pair">該当 dimension 科 metric 組合が 正しいか 判断する 数 ある 比較表</a>を 提供して ある.

[訳者 株: dimension科 metric 外に 入って行く 変数は<a target="_top" href="http://code.google.com/apis/analytics/docs/gdata/v3/reference.html#parameters_table">Parameters</a>を 参考しなさい.]

これ クラスは PHPで cURL 関数を 使う. 普通は サーバーで 使う 数 あるように なって あるのに, もし そうなの なければ <a target="_top" href="http://www.wallpaperama.com/forums/how-to-find-out-if-php-is-compiled-with-curl-extension-installed-enabled-t1576.html">ここ cURL を 使用 可能に 作る 方法</a>を 参考しなさい.

以上 基本的な 説明が 終わった. これ クラスを いくらでも ダウンロードしても 良い. 肝に銘ずると 割 のは 載せるように &#8216;常用&#8217;で 使う 位に 準備が なって ある クラスは ないという 点だ. [訳者 株: これ 次は まだ 準備が ダル いい. 時間が もっと あれば 何を する こういう 蟹 説明されて あって, 中 竝びが 引かれて ある.] これ クラスは アップデート いい. 何 枝 例外 処理を 追加した. そのため 問題に 直面するように なる 場合 もうちょっと 意味が ある メッセージを 出力して 竝び のだと 思う.

原文の ダウンロード リンク: <a target="_top" href="http://www.askaboutphp.com/wp-post-images/63/googleanalytics.class.zip">googleanalytics.class.zip</a>

訳者が 提供する ダウンロード リンク: [googleanalytics.class.zip][1]

報告書を 呼んで 来る 例示を 何 犬 もっと 見えて くれる.

<pre class="brush:php">// ブラウザーが 何やら
$report = $ga-&gt;getReport(
	array(&#039;dimensions&#039;=&gt;urlencode(&#039;ga:browser&#039;),
		&#039;metrics&#039;=&gt;urlencode(&#039;ga:visits&#039;),
		&#039;sort&#039;=&gt;&#039;-ga:visits&#039;
		)
	);

// 上位 到着 ページと サイトに とどまった 時間
$report = $ga-&gt;getReport(
	array(&#039;dimensions&#039;=&gt;urlencode(&#039;ga:landingPagePath,ga:pageTitle&#039;),
		&#039;metrics&#039;=&gt;urlencode(&#039;ga:entrances,ga:timeOnPage&#039;),
		&#039;sort&#039;=&gt;&#039;-ga:entrances&#039;
		)
	);

// ページビューで 上位 検索 キーワードは 何か?
$report = $ga-&gt;getReport(
	array(&#039;dimensions&#039;=&gt;urlencode(&#039;ga:searchKeyword&#039;),
		&#039;metrics&#039;=&gt;urlencode(&#039;ga:pageview&#039;),
		&#039;sort&#039;=&gt;&#039;-ga:pageviews&#039;
		)
	);</pre>

2009-07-15に 付け足し: グーグルは GA義 新しい APIを 出市した. リターン受ける データ 羊に 制限が 生じたし, dimensions わ metrics 組合に 緩い 制約が 生じた.

 [1]: https://docs.google.com/leaf?id=0B1y-xjZYE3AqYzJmZTdjMzItNTdlOC00ODJiLWFkMGItMDgyOTA3OGJiZGNk&hl=ko