---
title: '[Google Analytics] 電子 商取引 追跡 Ecommerce Tracking'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/1616
categories:
  - ウェブ解析と検索
tags:
  - Google Analytics
  - Web Analytics
---
グーグル アナルリティックスで 実際で どうな 訪問者が いくらの 収益を 発生させたのか 確認する 数 あるという のを 分かって 驚いた. 何かを 寝る 使おうとすれば マニュアルを 充実に 見ると する. そのため 翻訳を 決めた. 原文は[Ecommerce Tracking][1]載せる. 下から 翻訳 手始め.

&#8212;&#8212;

グーグル アナルリティックスが ウェブサイトの 電子 商取引 活動を レポートする 数 あるように するためには, プロフィール セッティング ページで 電子 商取引 追跡を 活性化すると する. [Google Analytics 最新 バージョンの 場合,**管理(右側 上端) > プロフィール > プロフィール 設定 タップ > 電子商取引 設定**選択 - 緑風] そして 出て, 市場かご ページや 電子商取引 ソフトウェアに `ga.js` 電子 商取引 追跡 メソッドを 具現すると する. 商取引が 起きた 時,電子 商取引 メソッド 集合は 一緒に 作動して 使用者 それぞれの トランザクション 情報[後の 説明 参照 - 緑風]を グーグル アナルリティックスの データベースに 送る 仕事を する. こういう 方式で アナルリティックスは 転換や 購買を 特定 推薦(referral) 経路と 連結する 数 ある. 大部分の テンプレート 方式 電子 商取引 エンジンは 注文 完了 ページに これ コードを 見えるの ないように 入れる 数 ある.

[トランザクションと言う(のは) ナッナッの 行為が 集まって 一つの 構成を 成す 単位を のぼる 言葉だ. 例を 入れば '決済すること' ボタンを 押した 後, 実際 決済を 夏至 なければ '決済すること' ボタンを 押した 行為は 無意味だ. **何 犬の アイテムを 市場かごに 盛る > 決済すること ボタン クリック > 配送 情報 入力 > 決済 情報 入力 > 決済 完了**に のぼる 過程を '決済'と 割 でしょうに, これ 過程を ところで 一つの トランザクションだと 呼ぶ. - 緑風]

1.  一般的 処理 過程
2.  ガイドライン
3.  完成 例題

## 一般的 処理 過程(General Process) {#General}

グーグル アナルリティックスの 電子 商取引 追跡 基本 処理 過程は 歳 枝 メソッドで 要約される. これ メソッドたちは サイトで 電子 商取引 トランザクションを 追跡する ところ 必須な ものなどだ. これ メソッドたちは 注文で 説明される. これ メソッドたち銀匠かごや 電子 商取引 ソフトウェアで 呼んで来ると する.

1.  **トランザクション 客体を 作る**[`_addTrans()`][2]メソッドを 使って トランザクション 客体を 初期化(intialize)する. トランザクション 客体は 単一 トランザクションに 係わった あらゆる 情報を 保存する. 例を 入れば, 注文番号(order ID), 配送料, 請求書 受信 住所 ような ものなどが ある. トランザクション 客体に ある 情報は 注文番号を 通じて お互いに ヨングァンメッヌンダ. たいてい トランザクションに ある あらゆる アイテムは 注文番号が ようだと する.(The information in the transaction object is associated with its items by means of the order IDs for the transaction and all items, which should be the same ID.)
2.  **アイテムを トランザクションに 盛る**`<a href="https://developers.google.com/analytics/devguides/collection/gajs/methods/gaJSApiEcommerce#_gat.GA_Tracker_._addItem">_addItem()</a>`メソッドは 各 トランザクションに ある`orderId`フィールドを 媒介で 使用自分の考え市場かごに ある それぞれの アイテムと 彼に 関する 情報を 追跡する. [たいてい 人が 4犬の アイテムを 市場かごに 盛って 決済すること ボタンを 押したと 欠点. 注文番号(orderId)街 342番(回)だと 欠点. これ トランザクションは orderId街 342イン トランザクションで, 各 アイテムは orderId街 342イン トランザクションに 属した アイテムである のだ.] これ メソッドは 特定 アイテムの 詳細 情報を 追跡する. 例を 入れば, SKU[再考 管理 コード], 価格, カテゴリー, 数量 など.
3.  **トランザクションを アナルリティックス サーバーに 送る.`<a href="https://developers.google.com/analytics/devguides/collection/gajs/methods/gaJSApiEcommerce#_gat.GA_Tracker_._trackTrans">_trackTrans()</a>`**メソッドは 購買が 起きたという ガール 定める. そして トランザクション 客体に 盛って 置いた あらゆる データは トランザクションとして 完了する.

電子 商取引 エンジンで 情報が 検索される 数 ある 色々 方法が ある. どうな 電子 商取引 エンジンは 購買 情報を 私たちが 使う 数 ある hidden formに 入れる.[hidden form銀 <input type="hidden"> 式の コードを 言う のだ - 緑風] どうな のは 私たちが 検索する 数 ある データベースに 情報を 入れて 置く. そして どうな ものなどは 情報を クッキーに 保存する. もうちょっと 有名で, グーグル アナルリティックスを 認識する どうな 電子 商取引 エンジンは グーグル アナルリティックスを のために 注文 追跡を 簡単に 割 数 あるように モジュールを 提供して 与えたり する.

## ガイドライン {#Guidelines}

電子 商取引 追跡を 割 時 次を 念頭に 置きなさい.

*   **SKU code[再考 管理 コード]増えた トランザクションに 追加される あらゆる アイテムに 必要な 必須 パラメーターだ.**  
    もし トランザクションに 色々 アイテムが あるのに SKU街 ない アイテムが あったら, GIF 要請は SKU街 ある アイテム 中 トランザクションに 最後に 追加された のに 大韓 情報だけ 送る.\[GIF request欄, GIF イメージ ファイルを 要請する 振りをしながら 情報を 送る cross domain 通信 技法である ようだ - 緑風\](a GIF request is sent only for the last item added to the transaction for which a SKU is provided.) 付け加えて, ような SKUを 持った お互いに 違う アイテムが 物品 リストに あって, お客さんが それを 同時に 購入するように なれば, 後ほど 追加された のに 大韓 情報だけ 受けるように なる のだ. したがって, 各 アイテムには ユイルハン SKUを 付けると する.
*   **`_addTrans()`わ`_addItem()`義 因子値は 位置に 当たるように 入れる  
    **あらゆる 因子値が 咲く事は ない だから, 間違いを 避けること ためには ない 因子値に 大海は ヴィン 値段を つまんで 入れると する. 例を 入れば, 注文番号と sku, 価格, 数量だけ ある アイテムを 追加する 焚く こんなに 使う.</p> 
    <pre>_addItem("54321", "12345", "", "", "55.95", "1");</pre>

*   **`price`わ`total`パラメーターは どうな 通話 単位も 無視する.**  
    二 パラメーターの 場合, 読点や 点は 少数を 意味するように なる. したがって, 例を 入れば, もし`1,996.00`を `total`パラメーターの 値段で 入れたら, `1.996で 記録されて`, $1,996.00 路 記録されるの ない. 値段が どうな 通話とも 連携されるの ない だから, 電子 商取引 ソフトウェア 方で データを グーグル アナルリティックスで 越すこと 前に 必ず 数字を 調整すると する.
*   **もし 電子 商取引 追跡を 具現して おいたし, サードパーティー 市場かごを 使って あったら, クロス ドメイン 追跡 設定も すると 割 のだ.(If you are implementing ecommerce tracking and using a 3rd-party shopping cart, you will likely need to configure cross-domain tracking as well.)**  
    詳細な 内容は &#8220;[Cross Domain Tracking][3]&#8220;を 参考しなさい.
*   **必ず 必要な 件 ないが, もし 特定 ページと トランザクション データを 連動して たければ, 注文 完了 ページで`_trackPageview()`を 呼び出す のも 方法だ.**

## 完成 例題 {#Example}

次 例題は 三種類 メソッドを 皆 利用して 注文 完了 ページで 電子 商取引 追跡を 設定する のを 具現して ある.`_trackPageview()`を 使って &#8216;Acme 衣類 購買 領収証&#8217;という 題目の ページと トランザクションを 連関をつける.

**非同期式 文法(勧奨)**

<pre class="brush: javascript; gutter: true; first-line: 1">&lt;html&gt;
&lt;head&gt;
&lt;title&gt;Receipt for your clothing purchase from Acme Clothing&lt;/title&gt;
&lt;script type="text/javascript"&gt;

  var _gaq = _gaq || [];
  _gaq.push([&#039;_setAccount&#039;, &#039;UA-XXXXX-X&#039;]);
  _gaq.push([&#039;_trackPageview&#039;]);
  _gaq.push([&#039;_addTrans&#039;,
    &#039;1234&#039;,           // order ID - required
    &#039;Acme Clothing&#039;,  // affiliation or store name
    &#039;11.99&#039;,          // total - required
    &#039;1.29&#039;,           // tax
    &#039;5&#039;,              // shipping
    &#039;San Jose&#039;,       // city
    &#039;California&#039;,     // state or province
    &#039;USA&#039;             // country
  ]);

   // add item might be called for every item in the shopping cart
   // where your ecommerce engine loops through each item in the cart and
   // prints out _addItem for each
  _gaq.push([&#039;_addItem&#039;,
    &#039;1234&#039;,           // order ID - required
    &#039;DD44&#039;,           // SKU/code - required
    &#039;T-Shirt&#039;,        // product name
    &#039;Green Medium&#039;,   // category or variation
    &#039;11.99&#039;,          // unit price - required
    &#039;1&#039;               // quantity - required
  ]);
  _gaq.push([&#039;_trackTrans&#039;]); //submits transaction to the Analytics servers

  (function() {
    var ga = document.createElement(&#039;script&#039;); ga.type = &#039;text/javascript&#039;; ga.async = true;
    ga.src = (&#039;https:&#039; == document.location.protocol ? &#039;https://ssl&#039; : &#039;http://www&#039;) + &#039;.google-analytics.com/ga.js&#039;;
    var s = document.getElementsByTagName(&#039;script&#039;)[0]; s.parentNode.insertBefore(ga, s);
  })();

&lt;/script&gt;
&lt;/head&gt;
&lt;body&gt;

  Thank you for your order.  You will receive an email containing all your order details.

&lt;/body&gt;
&lt;/html&gt;</pre>

**旧式 文法**

<pre class="brush: javascript; gutter: true; first-line: 1">&lt;html&gt;
&lt;head&gt;
&lt;title&gt;Receipt for your clothing purchase from Acme Clothing&lt;/title&gt;
&lt;/head&gt;

&lt;body&gt;

  Thank you for your order.  You will receive an email containing all your order details.

&lt;script type="text/javascript"&gt;
  var gaJsHost = (("https:" == document.location.protocol ) ? "https://ssl." : "http://www.");
  document.write(unescape("%3Cscript src=&#039;" + gaJsHost + "google-analytics.com/ga.js&#039; type=&#039;text/javascript&#039;%3E%3C/script%3E"));
&lt;/script&gt;
&lt;script type="text/javascript"&gt;
try{
  var pageTracker = _gat._getTracker("UA-xxxxx-x");
  pageTracker._trackPageview();
  pageTracker._addTrans(
      "1234",            // order ID - required
      "Womens Apparel",  // affiliation or store name
      "11.99",           // total - required
      "1.29",            // tax
      "

		
	
		
		

</pre>

 [1]: https://developers.google.com/analytics/devguides/collection/gajs/gaTrackingEcommerce
 [2]: https://developers.google.com/analytics/devguides/collection/gajs/methods/gaJSApiEcommerce#_gat.GA_Tracker_._addTrans
 [3]: https://developers.google.com/analytics/devguides/collection/gajs/gaTrackingSite