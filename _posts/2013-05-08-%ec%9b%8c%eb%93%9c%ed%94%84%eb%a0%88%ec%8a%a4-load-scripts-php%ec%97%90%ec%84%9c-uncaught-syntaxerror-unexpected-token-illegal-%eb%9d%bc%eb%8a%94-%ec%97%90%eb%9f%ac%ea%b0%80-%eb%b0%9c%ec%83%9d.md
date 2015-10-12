---
title: '[ワードプレス] load-scripts.phpからUncaught SyntaxError：Unexpected token ILLEGALというエラーが発生する'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/2020
categories:
  - WordPress
tags:
  - WordPress Tip
---
ワードプレスのウェブサイトを構築してローカルで作業をして管理者ページに入ってからレイアウトがことごとく破れた。 Javascriptが正常に動作していないものであった。これは何かと思ってjsコンソールを開けてみるとなんとエラーメッセージが浮かんでいた。

    Uncaught SyntaxError：Unexpected token ILLEGAL

場所は、`load-scripts.php`の最初の行。何はことなのかと思ってあれこれしてみた全く受け入れられなかった。

load-scripts.phpはjsを受けて最小化（minify）をしてくれるファイルです。そこからjsファイルを受け取って根ということだ。ソースの表示をしてload-scripts.phpで検索をしてみて入ると、最小化されたjsファイルを見つけることができるのだ。しかし、入ってみると、不明な文字に化けていた。これは何&#8230;

最終的に検索をしてみると、同じ問題を経験した人がかなりいることがわかった。[解決策][1]は簡単である。キャッシュをクリアするとされる。クッキーまで消すこともない。クロムなどの場合**ツール>履歴の消去**を押して、キャッシュのみチェックし、[OK]をクリックするとされる。だから、その次からはよく出てくる。なぜキャッシュが問題になったのかは分からないがとにかく大解決。

 [1]: http://stackoverflow.com/questions/11916987/uncaught-syntaxerror-unexpected-token-illegal-load-scripts-php1