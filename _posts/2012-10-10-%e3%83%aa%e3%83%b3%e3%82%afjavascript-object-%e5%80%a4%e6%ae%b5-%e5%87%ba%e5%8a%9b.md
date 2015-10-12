---
title: '[リンク]javascript Object 値段 出力'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/280
aktt_notify_twitter:
  - yes
categories:
  - Web publishing
tags:
  - javascript
  - plain javascript
---
<a target="_blank" href="http://bluebreeze.co.kr/398">http://bluebreeze.co.kr/398</a>  
ソースだ. リンク 付けて おいて&#8230; どこかで 汲んで 誤信 ことで したから ソース コピしても 了解して 主室 ことで 思う.  
<a target="_blank" href="http://bluebreeze.co.kr/398"> </a>

<div>
  <pre class="brush:js">dump: function(arr,level) {
	var dumped_text = "";
	if(!level) level = 0;
	
	//The padding given at the beginning of the line.
	var level_padding = "";
	for(var j=0; j &lt; level+1; j++) level_padding += "    ";
	
	if(typeof(arr) == &#039;object&#039;) { //Array/Hashes/Objects 
		for(var item in arr) {
			var value = arr[item];
			
			if(typeof(value) == &#039;object&#039;) { //If it is an array,
				dumped_text += level_padding + "&#039;" + item + "&#039; ...n";
				dumped_text += this.dump(value,level+1);
			} else {
				dumped_text += level_padding + "&#039;" + item + "&#039; =&gt; "" + value + ""n";
			}
		}
	} else { //Stings/Chars/Numbers etc.
		dumped_text = "===&gt;"+arr+"&lt;===("+typeof(arr)+")";
	}
	return dumped_text;
}
</pre>
  
  <p>
    </div>