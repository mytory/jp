---
title: '[PHP] preg_match_all 関数 使い方'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/819
aktt_notify_twitter:
  - yes
categories:
  - Web server
tags:
  - PHP
---
一応, <a target="_top" href="http://www.php.net/manual/kr/function.preg-match-all.php">PHP.net義 preg_match_all 公式 説明</a>を 参考した.

これ 関数は 基本的に 正規式に 当たる 文字列を 配列語 入れてくれる 関数だ. どうな 方式で 入れるか オプションを 竝び 数 ある. オプションが 歳 犬なのに, 次 例題 コードに それぞれ 違う オプションを 理解する 数 あるように 日 置いた.正規式に 大韓 理解は 基本に あると 仮定する.

<pre class="brush: php; gutter: true; first-line: 1">$subject = &#039;&lt;ul&gt;
	&lt;li&gt;&lt;a href="/#issuebar"&gt;メイン記事&lt;/a&gt;&lt;/li&gt;
	&lt;li&gt;&lt;a href="/#special-article-section"&gt;特集記事&lt;/a&gt;&lt;/li&gt;
	&lt;li&gt;&lt;a class="toggle-recommand" href="/#shortcut-recommand"&gt;推薦記事&lt;/a&gt;&lt;/li&gt;
	&lt;li&gt;&lt;a href="/9_subscribe.php?from=mainNav"&gt;定期購読&lt;/a&gt;&lt;/li&gt;
	&lt;li&gt;&lt;a href="/B_support.php?from=mainNav"&gt;後援&lt;/a&gt;&lt;/li&gt;
&lt;/ul&gt;&#039;;
$pattern = &#039;/"/#(.+)"/&#039;;
preg_match_all($pattern, $subject, $matches1, PREG_PATTERN_ORDER);
preg_match_all($pattern, $subject, $matches2, PREG_SET_ORDER);
preg_match_all($pattern, $subject, $matches3, PREG_OFFSET_CAPTURE);
echo &#039;&lt;pre&gt;&#039;;
echo &#039;&lt;h1&gt;$subject : &lt;/h1&gt;&#039;;
print_r(htmlspecialchars($subject));
echo &#039;&lt;h1&gt;PREG_PATTERN_ORDER : &lt;/h1&gt;&#039;;
print_r($matches1);
echo &#039;&lt;h1&gt;PREG_SET_ORDER : &lt;/h1&gt;&#039;;
print_r($matches2);
echo &#039;&lt;h1&gt;PREG_OFFSET_CAPTURE : &lt;/h1&gt;&#039;;
print_r($matches3);
echo &#039;&lt;/pre&gt;&#039;;</pre>

こんなに コードを 入れれば 下と 一緒に 出力が なる.

配列が まどろみ 多くて 頭が 痛い でしょうに, まず 全体 正規式に マッチされた 奴は 前部に 入れて 酒庫, 正規式に 含まれた 各 カッコたちを 尻手に 入れて 与える ので 理解すれば なる. 右に出た 正規式を`/"/#(.+)"/` こんなに つまんで 入れたが, `(.+)`街 ところで 尻手 配列に 入って行った やつだ. カッコで 色々 勝ちどき 縛られて あったら 色々 犬を 返還して 与える.

`PREG_PATTERN_ORDER` 路 オプションを 与えた 焚く 一応 前の 配列に 全体 正規式に マッチングされた やつらを 一度に 入れて 酒庫, 後の 配列には カッコに 当たる 遊ぶことを また 一度に 入れて 与える. カッコが 色々 晴れなさいといえば 後に 引き続き 配列を もっと 付けて 入れて 竝び ことだ. これ 例題の 場合 全体 正規式に 当たる 奴は 3改稿, カッコは 一つだから 元素 3ケのもの 配列 2勝ちどき 入って ある のだ.

`PREG_SET_ORDER`路 すれば 全体 正規式に 当たる やつ, 各 カッコに 当たる 遊ぶことを たいてい 配列ずつ 作って 順番で 入れて 与える. これ 例題の 場合 全体 正規式に 当たる 奴は 3改稿, カッコは 一つだから 元素 2ケのもの 配列 3勝ちどき 入って ある.

`PREG_OFFSET_CAPTURE`増えた 文字列の 位置を 一緒に 入れて 返還して 与える のだ.`PREG_PATTERN_ORDER`路 結果を 返還して 与えながら 文字列の 位地図 一緒に 返還して 与えたが,`PREG_SET_ORDER` 形態で 返還受けて たければ`preg_match_all($pattern, $subject, $matches4, PREG_SET_ORDER + PREG_OFFSET_CAPTURE);` 形態で 使えば なる.

質問が あれば デッグル つけて 与えるように.

<pre class="brush: text; gutter: true">$subject : 

&lt;ul&gt;
	&lt;li&gt;&lt;a href="/#issuebar"&gt;メイン記事&lt;/a&gt;&lt;/li&gt;
	&lt;li&gt;&lt;a href="/#special-article-section"&gt;特集記事&lt;/a&gt;&lt;/li&gt;
	&lt;li&gt;&lt;a class="toggle-recommand" href="/#shortcut-recommand"&gt;推薦記事&lt;/a&gt;&lt;/li&gt;
	&lt;li&gt;&lt;a href="/9_subscribe.php?from=mainNav"&gt;定期購読&lt;/a&gt;&lt;/li&gt;
	&lt;li&gt;&lt;a href="/B_support.php?from=mainNav"&gt;後援&lt;/a&gt;&lt;/li&gt;
&lt;/ul&gt;

PREG_PATTERN_ORDER : 

Array
(
    [0] =&gt; Array
        (
            [0] =&gt; "/#issuebar"
            [1] =&gt; "/#special-article-section"
            [2] =&gt; "/#shortcut-recommand"
        )

    [1] =&gt; Array
        (
            [0] =&gt; issuebar
            [1] =&gt; special-article-section
            [2] =&gt; shortcut-recommand
        )

)
PREG_SET_ORDER : 

Array
(
    [0] =&gt; Array
        (
            [0] =&gt; "/#issuebar"
            [1] =&gt; issuebar
        )

    [1] =&gt; Array
        (
            [0] =&gt; "/#special-article-section"
            [1] =&gt; special-article-section
        )

    [2] =&gt; Array
        (
            [0] =&gt; "/#shortcut-recommand"
            [1] =&gt; shortcut-recommand
        )

)
PREG_OFFSET_CAPTURE : 

Array
(
    [0] =&gt; Array
        (
            [0] =&gt; Array
                (
                    [0] =&gt; "/#issuebar"
                    [1] =&gt; 18
                )

            [1] =&gt; Array
                (
                    [0] =&gt; "/#special-article-section"
                    [1] =&gt; 66
                )

            [2] =&gt; Array
                (
                    [0] =&gt; "/#shortcut-recommand"
                    [1] =&gt; 154
                )

        )

    [1] =&gt; Array
        (
            [0] =&gt; Array
                (
                    [0] =&gt; issuebar
                    [1] =&gt; 21
                )

            [1] =&gt; Array
                (
                    [0] =&gt; special-article-section
                    [1] =&gt; 69
                )

            [2] =&gt; Array
                (
                    [0] =&gt; shortcut-recommand
                    [1] =&gt; 157
                )

        )

)</pre>