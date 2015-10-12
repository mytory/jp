---
title: phpMyAdmin 3.5.2で import割 時 Character set of the fileに euc-krこれ なければ
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/806
aktt_notify_twitter:
  - yes
categories:
  - Web server
tags:
  - PHP
---
要約 : `phpMyAdmin/libraries/config.default.php` ファイルを 開いて`$cfg['AvailableCharsets']` 配列に &#8216;`euc-kr`&#8216;を 追加して 与える.

`phpMyAdmin 3.5.2`を 使って ある. 本当 カルサムする. ところが `euc-kr`路 なった sql バックアップ ファイルを インポートしようと するから エラーが 出た. 察して 見たらCharacter set of the fileを `euc-kr`路 選択して 与えると エラーが 中 ナッジ たかった. マイグレイションする デ−ビは 当然 `utf-8`を 使って あった だからだ.

ところが 荒唐,Character set of the file 項目に `euc-kr`これ ない ことだ. `cp949`度 なくて.

<div style="width: 588px" class="wp-caption aligncenter">
  <img src="http://dl.dropbox.com/u/15546257/blog/mytory/phpmyadmin3.5.2-import-encoding.png" alt="" height="233" width="578" /><p class="wp-caption-text">
    これ セレクト ボックス リストに <code>euc-kr</code>これ なかった.
  </p>
</div>

どっちみち `phpMyAdmin`度 内部では `iconv` ような `PHP` 関数を 使う 側だから 問題になる こと ないだろう たくて セレクト メニューだけ 直す つもりで コア ファイルたちを 捜して 見た.何 番(回) シャベルですくい出し 終りに`phpMyAdmin/libraries/config.default.php` ファイルに インポートする 時の 文字 エンコード リストが 入っているという ガール 分かるように いい.

ファイルを 開いて `euc-jp`路 検索を した. `euc-jp`増えた 項目に あった だからだ. 見るから やっぱり 配列で 入って行って ある. 見るから 配列 変数人は `$cfg['AvailableCharsets']` だ.配列 項目に `euc-kr`を 追加して 与えた. そうだから 寝る 入って行く. 終り!