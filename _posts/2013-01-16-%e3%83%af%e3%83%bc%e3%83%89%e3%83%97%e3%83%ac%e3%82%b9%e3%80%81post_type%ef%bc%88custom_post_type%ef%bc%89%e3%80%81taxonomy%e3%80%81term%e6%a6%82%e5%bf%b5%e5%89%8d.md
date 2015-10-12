---
title: ワードプレス、post_type（custom_post_type）、taxonomy、term概念
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/1916
categories:
  - WordPress
tags:
  - WordPress Tip
---
ワードプレスをCMSツールとして使用するための具体ほぼ必須の高度な機能がすぐにcustom\_post\_typeとtaxonomyだ。

custom\_post\_typeだ名前だけ見ても分かるだろう。ウェブサイトを作ってみるとただ文だけから成っているウェブサイトはあまりない。出版社だけ見ても、アナウンスのpost\_typeだpostにすることができるのに、本​​までpostに処理そういえばムォハダ。書評は、postで処理すべきかreivewに処理すべきか？このような時custom\_post_typeを使用してbookというアイテムを作ることができる。

taxonomyは不慣れなのに、翻訳すると&#8221;分類&#8221;だ。各ポストゥウルどのように分類するか決めるのがtaxonomyだ。ワードプレスの公式文書を見ると、taxonomyを説明するときに本を分類する例を挙げる。以下の表に例を挙げた。

最後に、私は混乱てたのはtermというやつだった。公式文書で何の説明をまだ見られなかったからだ。コードを確認しながら、知ることになった。 termは、すぐに具体的なtaxonomyを指すものであった。

これ以下の表を見てみよう。

<table>
  <tr>
    <th>
      post_type
    </th>
    
    <th>
      taxonomy
    </th>
    
    <th>
      term
    </th>
  </tr>
  
  <tr>
    <td>
      post
    </td>
    
    <td>
      category
    </td>
    
    <td>
      ウェップサーバー
    </td>
  </tr>
  
  <tr>
    <td>
      post
    </td>
    
    <td>
      category
    </td>
    
    <td>
      ウェブクライアント
    </td>
  </tr>
  
  <tr>
    <td>
      post
    </td>
    
    <td>
      tag
    </td>
    
    <td>
      PHP
    </td>
  </tr>
  
  <tr>
    <td>
      post
    </td>
    
    <td>
      tag
    </td>
    
    <td>
      javascript
    </td>
  </tr>
  
  <tr>
    <td>
      book
    </td>
    
    <td>
      publisher
    </td>
    
    <td>
      ハンビットメディア
    </td>
  </tr>
  
  <tr>
    <td>
      book
    </td>
    
    <td>
      publisher
    </td>
    
    <td>
      しおり
    </td>
  </tr>
  
  <tr>
    <td>
      book
    </td>
    
    <td>
      author
    </td>
    
    <td>
      ツェズンでは
    </td>
  </tr>
  
  <tr>
    <td>
      book
    </td>
    
    <td>
      author
    </td>
    
    <td>
      アレックスケルリニコス
    </td>
  </tr>
</table>

これ以上詳しく説明することはあまりない。残りはワードプレスの公式文書を見ながら具体的に活用すればいいのだ。

そう覚えましょう。

post_typeは本を言い、taxonomyは様々な分類基準をいう。例えば本を分類する基準となる筆者、出版社のようなもの。製氷機の場合はメーカーを基準に分類することができるはずだ。

termは、具体的なtaxonomyをいう。筆者taxonomyのtermはチェジュンソンとアレックスケルリニコスがあるのだ。カテゴリtaxonomyのtermには、WebサーバーやWebクライアントがあるだろうし、タグtaxonomyのtermには、PHP、javascriptのようなものがあるのだ。

この程度なら理解されただろう。