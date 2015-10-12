---
title: '[翻訳:phpThumb] phpThumb FAQ(2)'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/336
aktt_notify_twitter:
  - yes
categories:
  - Web server
tags:
  - PHP
  - phpThumb()
---
<div class="box">
  <p>
    これ 文は ソムネである 生成 プログラムである <a href="http://phpthumb.sourceforge.net/" target="_blank">phpThumb()</a>義 <a href="http://phpthumb.sourceforge.net/demo/docs/phpthumb.faq.txt" target="_blank">FaQ</a> 尻手を 翻訳した のだ. <a href="http://mytory.textcube.com/entry/%EB%B2%88%EC%97%ADphpThumb-phpThumb-FAQ1" target="_blank">前部 翻訳も これ ブログで ボール 数 ある.</a> 当然 誤役が ある 数 ある. &#8211; 緑風
  </p>
</div>

**Q: configで (w/h/fltr[] ような) パラメーターを 設定して URLを 変える 蟹 不可能になるように 割 数 あるんですか?**

A: phpThumb.config.php義 マン 下側に ある `$PHPTHUMB_DEFAULTS`を 見てください. こんなに 変えれば なります. 

<pre class="brush:php">$PHPTHUMB_DEFAULTS_GETSTRINGOVERRIDE = false</pre>

こんなに する のも なります.

<pre class="brush:php">$PHPTHUMB_DEFAULTS_DISABLEGETPARAMS = true</pre>

もっと 研究するのを バラなら

<pre class="brush:php">$PHPTHUMB_CONFIG[&#039;high_security_enabled&#039;] = true</pre>

(高い 保安 モードで イメージを 呼び出す 方法を 分かって たければ phpThumb.config.php義 マン 下側に ある 例題を 見てください.) 

**Q: **`<b>phpThumb()</b>`** 客体を 利用して URLに イメージ 位置 ような ガール パラメーターで 見せてくれる 仕事 なく ソムネイルを 生成する 方法が あるんですか?**

A: /demo/phpThumb.demo.object.phpに そんな デモが あります. これを あなたが 使う ファイルに 当たって 直す 数 あるが, ファイルに パラメーターを 越すと するという 問題は 残ります. それが phpThumb.php入った `phpThumb()` 客体でも 間に ね. 斉家 提示する 方法は, できるだけ 阿洲 多い パラメーターを phpThumb.config.php義 `$PHPTHUMB_DEFAULTS` 下の 入れて そんな パラメーターたちを それぞれの イメージには 伝達するの ない のです. もし 人々が パラメーターを 変更する 蟹 嫌いだったら, `$PHPTHUMB_CONFIG['high_security_enabled']`を つけてください. そして 暗号を 設定してください.(phpThumb.config.php義 マン 下側に ある `phpThumbURL()` [関数で] イメージを 作ると 割 はずです.) もし, 人々が 原本 イメージに 全然 近付くの できないように 作って たければ, 原本 イメージたちを サーバーの DOCUMENT_ROOT 外に 置いてください.(団, phpThumb/PHP増えた 彼 ディレクトリを 読む 数 あると します.) 違う オプションは, 原本 イメージを MySQL データベースに 入れて, `$PHPTHUMB_CONFIG['mysql_query']`わ phpThumb.config.php義 係わった パラメーターを 設定して, 原本 イメージを データベースで 抜いて 使う のです. これ 方法は phpThumb.phpを 通じる の 外には イメージを 扱う 方法が なく 作ります. そして もし 高い 保安モードが ともって あったら, パラメーターを 直して 何を 見る 件 不可能です. 汚職 あなたが 見せてくれるように たいてい のだけ 見える はずです. 結論的に, 当たります. あなた 自分の 客体を 作って 使う のは 可能です. &#8212; たいてい 枝 気を付ける 点は, phpThumb.php街 あらゆる キャッシュを 制御すること だから, 客体を 万たち 場合には [キャッシュを] 自ら 扱うと するという 点です.

**Q: ファイルで 使うとか ブラウザーに うつ こと 以外に, ソムネイルを データベースに 直接 使う 数 ある 方法は ないんですか?**

A: /demo/phpThumb.demo.object.phpを 見てください. 基本的に `this->GenerateThumbnail()` を 呼び出した 次, `$this->RenderOutput()` を すれば, 出力された そのままの イメージ データは `$this->outputImageData` で 捜す 数 あります.

**Q: (私の サーバーに あるの ない) HTTP ソース イメージを 扱う 時, まるで イメージ キャッシュが 中 なる ように phpThumb街 あまり 遅く 帰ります. どうに すれば 早くなりましょうか?**

A: 

<pre class="brush:php">$PHPTHUMB_CONFIG[&#039;cache_source_filemtime_ignore_remote&#039;] = true;
</pre>

もし true路 設定されて あれば, 遠隔 ソース イメージ 修正 日付を チェックするの ない ので, キャッシュされた イメージが あったら それを 使うように なる はずです. 原本 イメージが 変わったとか 消えても ね.

**Q: &#8220;cache\_default\_only_suffix&#8221; 設定 オプションは 何をする 遊ぶことですか?**

A: キャッシュ ファイルは 普通 &#8220;phpThumb\_cache\_www.example.com\_src1a482c2c760463795ff18faf073b389f\_par3e099041c2f4a73041a7f5d7e7fc481a_dat1119952152.jpeg&#8221;のように ものすごく 変な 名前で 生成されます. するが もし `cache_default_only_suffix`街 ともって あれば キャッシュ ファイル名は (例えば) &#8220;pic_thumb.jpg&#8221; ような 式で シンプルに 変わります. 問題は ソムネイルが 汚職 たいてい 枝 バージョンだけ 保存されるという 点です. 違う サイズや フィルター などを [キャッシュで] 再び 呼び出す 蟹 不可能になります. 一般的には そうに なる ガール 願うの ないが いくつか 人々は これを 要求すること だから あります.

**Q: 回転された イメージは なぜ 回転されること 戦意 イメージより 小さい んですか?**

A: phpThumb増えた 回転された イメージを 横(`w`) 縦(`h`) 大きさに 合わせます. `w` パラメーターを 設定するの 巻いてください : 

<pre class="brush:plain">phpThumb.php?src=file.png&ra=15</pre>

そうに すれば イメージが 回転されるの ない イメージ サイズどおり 維持されます.(事実, こんなに 合わせれば カンバス サイズ 自体は もっと 大きくなります.)

**Q: phpThumb.demo.check.phpを 行うから 安全 モード(Safe Mode)街 マスター(Master)では off故, ローカルでは onと します. php.iniを チェックして 見たら もう off路 なって あります. セーフ モードを 消そうとすれば どうに します?**

A: 多分 PHP街 Apache モジュールで 設置された の ようです. そうだったら, ドメイン セッティングで 

<pre class="brush:plain">php_admin_value sage_mode "Off"</pre>

こんなに 設定すると します.(普通は httpd.conf義 <virtualhost> タグ 間に あります.) 設定して 出れば 痛がるのを 改めて始まると します.

**Q: 原本 イメージを 消した 時 キャッシュ ファイルは どうに 消します?**

A: phpThumbに 内蔵した キャッシュ 除去 方法を 使って(phpThumb.config.phpを 見てください) そんな 效果を おさめる 首都 あって, 削除を のために 原本 イメージを 受動で ずっと 扱いて, マッチ(match)なる キャッシュ ファイルを 捜して 消す 首都 あります : 

<pre class="brush:php">if ($dh = opendir($sourcedir)) {
       while ($file = readddir($dh)) {
         if ($file == $WhatIwantToDelete) {
           $md5 = md5_file($sourcedir.&#039;/&#039;.$file);
           unlink($phpthumb_cache_dir.&#039;/phpThumb_cache_www.example.com_src&#039;.$md5.&#039;*.*&#039;);
         }
       }
       closedir($dh);
     }
</pre></p> 

**Q: キャッシュ ファイルを 消しても なるんですか?**

A: はい. キャッシュ ディレクトリや ファイル 締める 消しても 構わないです. phpThumb増えた 必要ならば 自動で キャッシュを 再び 生成する はずです. また, 自動 キャッシュ 掃除を のために phpThumb.config.phpに 設定されて ある &#8220;cache_max*&#8221;を 確認して 見てください.

**Q: phpThumb.php街 特定の イメージに 大海 使う ファイル名を 卵 数 ある 方法が あるんですか?**

A: キャッシュ ファイル名を 分かる 件 易しくは ないです. phpthumb.class.php ファイルの `SetCacheFilename()` 中で [ファイル名を] 計算する メソッドを ボール 数 ある のです.(大略 2991-3090ライン 間に あります.) イメージが どこで レンダリングされるのか 知りたかったら, それは もうちょっと 易しいのに, phpThumb 客体を 呼び出して あなた 自分の キャッシュを 設定すれば なります. /demo/phpThumb.demo.object.simple.phpで 例題を 見てください.

**Q: PDF ソムネイルを 生成する 首都 あるんですか?**

A: ImageMagick科 GhostScript街 設置されて あったら 可能です. GhostScript AFPL バージョンが GNU バージョンより もっと 寝る 作動する ことで 見えます.(少なくても 斉家 見るには そうです.)  
<a href="http://www.imagemagick.org/" target="_blank">http://www.imagemagick.org</a>  
<a href="http://www.cs.wisc.edu/‾ghost/" target="_blank">http://www.cs.wisc.edu/‾ghost/</a>  
ソムネイルを 生成する ページを 指定すること ためには &#8220;`sfn`&#8220;(Source Frame Number) パラメーターを 使うと します.

**Q: ウェプページの ソムネイルを 生成する 数 ありますか?**

A: たぶん そうな はずです. するが 易しいでしょう ないです. 理論的には html2ps, GhostScript, ImageMagickこれ 皆 設置されて あれば 可能ですが, 斉家 テストして 本 少ない ないです. ウェプページの ソムネイルを 作る 違う プロジェクトが あります : <a href="http://www.boutell.com/webthumb/" target="_blank">http://www.boutell.com/webthumb/</a>

**Q: 動く GIF路 ソムネイルを 生成したら 原本 ファイルより ソムネイルの ファイル サイズが もっと 大きくなりました. &#8212; なぜ そんな ことですよ?**

A: 動く GIF増えた 時間的, 空間的に 多様な 圧縮 テクニックを 使います. 原本 GIF増えた たぶん 阿洲 寝る 最適化されて ある のです. するが それぞれの フレームが リサイズされた 時, いくつか 望ましい 圧縮 プロパティーは 否定的な 影響を 及ぶ 数 あります.(色数が 増加する 数 あります; デ−ドリング 領域は 満たされた(solid) 領域の 色に 比べて 阿洲 下手に 圧縮されます.) ImageMagick また ファイルサイズを 最適化した 動く GIFを 万たち 数は ないです.

**Q: パラメーターで 成り立った イメージ スクリプトが あります.(ような サーバーに ある 首都 あって 違う サーバーに ある 首都 あります.) 例えば: http://sourceforge.net/sflogo.php?group_id=106407&type=5 こういう 式で ね.(これ 住所は 210&#215;62 サイズの PNG イメージを 見せてくれます.) これを 使って [切ってす] イメージを 万たち 数 あるんですか?  
**

A: はい. phpThumbを 利用して そうに 割 数 あります. 原本 イメージが 違う サーバーに あったら, `$PHPTHUMB_CONFIG['nohotlink_valid_domains']`に ソース ドメインを 含むと します. [例えば, sourceforge.net] もし ソース ドメインが 何 犬 位なら ね. それとも `$PHPTHUMB_CONFIG['nohotlink_enabled']`を false路 設定してください. それでは どうな ドメイン/IPに ある イメージでも 間に 原本 イメージで 使う 数 あります.

また, イメージ ソースを (PHP義 rawurlencode 関数を 利用して) 多分 はっきりと エンコードしてくれると 割 はずです. :   
/phpThumb.php?src=http%3A%2F%2Fsourceforge.net%2Fsflogo.php%3Fgroup_id%3D106407%26type%3D5&w=100

**Q: phpThumb増えた 世界 最高の ソフトウェアです. 後援して たいですが.**

A: 簡単です. http://phpthumb.sourceforge.net 義 マン 上に ある &#8220;Support this project&#8221; ボタンを 押して 過程を よって してください.(それでは SourceForge江戸 5%を 私に なります.), それとも PayPalを 利用して 直接 出す 方法も あります. info@silisoftware.com 路 後援すれば なります.

**Q: これ スクリプト/プログラム/ライブラリの 正確な 名前は 何ですか?**

A: 公式 名称は &#8220;phpThumb()&#8221;です. するが 短く 使う 焚く(あるいは カッコが 許容されるの ない 場合) 簡単に &#8220;phpThumb&#8221;と 使います. 大小文字を 区分するの ない 環境では &#8220;phpthumb&#8221;と 使ったり します. 次 場合は 誤った 形式です : PHPthumb; phpThumbs; phpthump; phpthumbnailer; phpThumbnail; PHP Thumb; Phpthumb; など