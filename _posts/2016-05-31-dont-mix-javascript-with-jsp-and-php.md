---
title: "JavaScriptとjsp、phpを混合してみましょう"
layout: post
tags:
  - javascript
  - php
  - jsp
---

メンテナンスを担当したコードをか見ると、すべてのjspファイルで同様のjsとcssが繰り返されていた。当然jsとcssをファイルから分離しようとした。ところが、jsファイルを分離して、ナニIDEでエラーが表示さがすごく浮かび上がった。以下のようなコードのためだった。

    var url = "http://${pageContext.request.serverName}:${pageContext.request.serverPort}/api/";

jspで`${pageContext.request.serverName}`は、URLのドメイン（domain.comなど）の部分を指す。 IP数日もありま。上記のコードをphpに変更すると、次のとおりである。

    var url = "http://<?= $_SERVER['HTTP_HOST'] ?>/api/";

このようなコードは、読みやすさを落とし、他の開発者を混乱に陥れる。悪い。事実、このような場合は、単にjsでこのように少ない場合になる。

    var url = location.origin + '/api/';

IE 10まで`window.location.origin`オブジェクトがないので、上記のコードを使用する前のどこか次のようなコードを入れてくれれば良い。

    if (!window.location.origin) {
        window.location.origin = window.location.protocol + "//" + window.location.hostname + (window.location.port ? ':' + window.location.port: '');
    }

## サーバ側データの一部をjsでもたらす使わなければならする場合

サーバ側の値を受け、jsで処理する必要がある場合は、上記のようにデフォルト値を取得して使用するのがいけない。例えば、jsで$ username値が必要であると仮定してみよう。このような場合にはHTML DOMの適切な場所に$ username値を打ち込んだ後、jsから取り出し使うようにする。どこかに「mytoryさん、ようこそ！」のようなフレーズがあるので、そこに入れるとなる。論理でもある。 HTMLは以下のようになるだろう（$ usernameをあえてエスケープ処理はいない。必要に応じての世話をすること）。

	<p>
		<span id="#username" data-username="<?= $username ?>">
			<?= $username ?>
		</span>
		さん、ようこそ！
	</p>

jQueryを使用する場合はこのようにもたらす使えばなるだろう。

    var username = $('#username').data('username');

`post_id`のようなものも同じだ。 HTML要素のどこかに残っていたが取り出さ使えば良い。以下は例示。

    var post_id = $('[name="post_id"]').val();

## サイズが大きいサーバ側資料としてjsonを作って活用する必要がある場合は、

チャートを描く場合は、サーバーただし、データにjsonを作成jsに渡す必要があります。これにより、上記のような解決策には限界がある。このような場合、ajax呼び出しをして、データをインポートする場合は、コードがすっきりになるだろう。

サーバ側のajax応答phpスクリプトは、以下のであればなるだろう。

	header('content-type: application/json; charset=utf-8');
	// $data変数の設定プロセスは省略した
	echo json_encode($data);

ajax処理は、あえてサーバーに要求をもう一度送ることになる。データが動的に変わる場合を除き、ページにjsonを薄紙てはならない理由があるか静的なページですがajax呼び出しをすると、むしろ、他の開発者がコードを見たとき混乱することもできる。

以下は妥協策である。データjsonを除くすべてのjsのコードは、別のファイルに分離して、データjsonのためだけにscriptタグを使用しているものである。

	<script>
	var data = <?= json_encode($data) ?>;
	</script>

少し気に控えめなのですが、他の開発者がコードを理解するのが難しくないだろう。これ以上のコードを混合しなければなら、本当にそう組まなければならないのか疑問で、jsのコードを利用した解決策を見つける必要があります。再び強調するが、`var data`万scriptタグの中に入れた。残りのjsは、別のファイルに入れた。

## 結論

コー​​ド量が多くjsonデータを取得し、根は例外的な場合を除けば、ほとんどの場合jsとサーバ側のスクリプトを分離することができ、そのようにしなければならないということを強調します。 jsの中にphpを入れて簡単に解決できるという考えが例えば、そうしないでください。明らかに、他の解決策がある。

目的は、コードの可読性を得るものである。今、私は絞りコードを他の開発者が見たとき、1年後、あるいは2年後の私を見たときに理解し易いである。今すぐの便利だけを追求するためのコードはだいたい悪い。