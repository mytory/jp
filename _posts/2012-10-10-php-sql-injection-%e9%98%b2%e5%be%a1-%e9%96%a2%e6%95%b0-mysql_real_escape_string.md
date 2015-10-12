---
title: '[PHP] sql injection 防御 関数, mysql_real_escape_string'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/563
aktt_notify_twitter:
  - yes
categories:
  - Web server
tags:
  - PHP
---
<a target="_top" href="http://www.php.net/manual/kr/function.mysql-real-escape-string.php">PHP 公式 ハングル 説明 : mysql_real_escape_string</a>

SQL インジェクション 攻撃は ID私 PASSWORD イブリョックカンに SQL門を 入れて DBを はたく のを 言う.

PHP 公式 ウェブサイトには SQL インジェクション 攻撃の 例で 下と ような のを 入って おいて ある.

<pre class="brush:php">// ユーザーが あるのか DBで チェックする クイーリー
$query = "SELECT * FROM users WHERE user=&#039;{$_POST[&#039;username&#039;]}&#039; AND password=&#039;{$_POST[&#039;password&#039;]}&#039;";
mysql_query($query);

// $_POST[&#039;password&#039;]を チェックする 数 なく なって, どうな ユーザーでも 許容するように なる. 例を 入れば:
$_POST[&#039;username&#039;] = &#039;aidan&#039;;
$_POST[&#039;password&#039;] = "&#039; OR &#039;&#039;=&#039;";

// MySQLに こういう クイーリーが 送信されるという のを 意味する:
echo $query;
//SELECT * FROM users WHERE user=&#039;aidan&#039; AND password=&#039;&#039; OR &#039;&#039;=&#039;&#039;</pre>

mysql\_real\_escape_string 関数は ところで こういう 攻撃を 阻んで 与える 関数だ.

PHP 公式 ウェブサイトには 下を 模範 例題で 入って ある.

<pre class="brush:php">if (isset($_POST[&#039;product_name&#039;]) && isset($_POST[&#039;product_description&#039;]) && isset($_POST[&#039;user_id&#039;])) {
    // 接続
    $link = mysql_connect(&#039;mysql_host&#039;, &#039;mysql_user&#039;, &#039;mysql_password&#039;);

    if(!is_resource($link)) {

        echo "サーバー 接続 失敗n";
        // ... 間違いを 適切に 記録

    } else {

        // ON仕事 場合 magic_quotes_gpc/magic_quotes_sybase 效果 除去

        if(get_magic_quotes_gpc()) {
            $product_name        = stripslashes($_POST[&#039;product_name&#039;]);
            $product_description = stripslashes($_POST[&#039;product_description&#039;]);
        } else {
            $product_name        = $_POST[&#039;product_name&#039;];
            $product_description = $_POST[&#039;product_description&#039;];
        }

        // 安全な 質の 作り
        $query = sprintf("INSERT INTO products (`name`, `description`, `user_id`) VALUES (&#039;%s&#039;, &#039;%s&#039;, %d)",
                    mysql_real_escape_string($product_name, $link),
                    mysql_real_escape_string($product_description, $link),
                    $_POST[&#039;user_id&#039;]);

        mysql_query($query, $link);

        if (mysql_affected_rows($link) &gt; 0) {
            echo "Product insertedn";
        }
    }
} else {
    echo "Fill the form propertyn";
}</pre>

上と ような 方式で 使えば なる.