---
title: ckeditor義 checkDirty()わ resetDirty()増えた 何か?
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/155
aktt_notify_twitter:
  - yes
categories:
  - Web server
tags:
  - 'FCKEditor &amp; CKEditor'
---
<a href="http://mytory.textcube.com/entry/ckeditor-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EB%A1%9C-%EB%82%B4%EC%9A%A9-%EC%A7%91%EC%96%B4%EB%84%A3%EA%B8%B0%EC%A0%84%EC%B2%B4-%EB%82%B4%EC%9A%A9-%EB%B0%94%EA%BE%B8%EA%B8%B0" target="_blank">ckeditor, ジャバスクリプトで 内容 入れること(全体 内容 変えること)</a>で <a href="http://ckeditor.com/download" target="_blank">ダウン</a>受ければ 出る _samples義 APIを 見れば いくつか API増えた 易しく ボール 数 あると 使った.

ckeditor/_samples/api.html 街 ところで 彼 API ページだ. ここには checkDirtyわ resetDirtyという ボタンが ある.

これは ムォンゴしたら, 簡単だ. ページに 変化が あったのか なかったのか チェックする のだ. 変化が あったら true, なかったら falseを 返還する. 修正しに 入って来てから 誰 のも 修正するの なくて 帰ったら 敢えて submit割 必要が ない 側だから そうな 時 使う の ないか? それとも ajaxAutoSave ような ガール 万たち 時 使うとか.

各 ボタンに バインドドエン 関数 コードは 下と ようだ.

<pre class="brush:js">function CheckDirty()
{
	// 願う エディタ インストンスを 選ぶ.
	var oEditor = CKEDITOR.instances.textarea_id;
	alert( oEditor.checkDirty() );
}

function ResetDirty()
{
	// 願う エディタ インストンスを 選ぶ.
	var oEditor = CKEDITOR.instances.textarea_id;
	oEditor.resetDirty();
	alert( &#039;IsDirty 状態が リセットされました.&#039; );
}
</pre>

ResetDirtyを して 出て CheckDirtyを すれば, 何も 変わるの なかったという 意味で falseと 出る.

アザックス オート セーブ ような ガール たいてい 次 ResetDirty 関数を 行えば 使用者たちが 自分 データが 保存されたのか 中 なったのか 卵 数 ある のだ.