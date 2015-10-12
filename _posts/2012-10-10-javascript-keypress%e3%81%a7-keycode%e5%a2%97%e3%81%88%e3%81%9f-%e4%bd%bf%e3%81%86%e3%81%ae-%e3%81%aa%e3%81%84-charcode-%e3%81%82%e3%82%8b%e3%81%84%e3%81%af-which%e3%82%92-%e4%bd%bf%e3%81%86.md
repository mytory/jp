---
title: '[javascript] keypressで keyCode増えた 使うの ない. charCode あるいは whichを 使う.'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/459
aktt_notify_twitter:
  - yes
categories:
  - Web publishing
tags:
  - javascript
  - plain javascript
---
例えば 英文 背たちは そのまま キーコードが 0で 出る. すなわち, 設定されて あるの ない ことだ. <div>
  keypressを 使ったら, event.charCode私 event.which を 使うと する.
</div>

<div>
  keypress増えた 入力 自体を 阻むと 割 時 使う. keyupで 入力を 検査したら もう 入力された 後日 敷地だから 言葉だ.<br />下の コードを 掻いて テストして 見れば なる ことだ. 数字が それとも 入力を 阻む コードだ.
</div>

<pre class="brush:html">&lt;script src="scripts/jquery.js" type="text/javascript"&gt;&lt;/script&gt;
&lt;script type="text/javascript"&gt;
$(function(){
	$(&#039;.quantity input&#039;).keypress(function(event) {
	alert(event.charCode);
	  if (event.which && (event.which &lt; 48 || event.which &gt; 57)) {
		event.preventDefault();
	  }
	})
});
&lt;/script&gt;

&lt;div class="quantity"&gt;
  &lt;input type="text"/&gt;
&lt;/div&gt;
</pre>