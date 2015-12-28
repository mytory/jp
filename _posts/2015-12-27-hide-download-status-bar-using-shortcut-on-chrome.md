---
layout: post
title: "クロム、ダウンロードステータスバーなくすキーボードショートカット"
categories:
- etc
tag:
- TIP
---

私は、Webブラウジングするときに、マウスをよく使用していない。 私は手が弱くグランジわからなくても、検知関節が痛いからである。 だから[Vimium](https://chrome.google.com/webstore/detail/vimium/dbepggeogbaibhgnhhndojpepiihcmeb)ような拡張を使用して、マウスなしでWebブラウジングをする。

ところが、クロムで何かをダウンロード受けたときの下部にダウンロードの状態バーに残っているのはちょっと迷惑である。 ダウンロードする時だ状態を知ることができますので、良い。 ところが、ダウンロードが終わった後も継続残っファイルを示しているのである。 マウスではxを押し下がるが面倒である。 キーボードから手を離す嫌いだ。

これを削除する方法を見つける通った、[Always Close Downloads](https://chrome.google.com/webstore/detail/always-clear-downloads/cpbmgiffkljiglnpdbljhlenaikojapc)拡張以外星がない。 ところが、Always Close Downloads拡張は、ダウンロードが終了したことを認知しにくく作ってあまりだった。

[マックでマクロを作成する方法](http://rocketink.net/2013/06/close-google-chrome-downloads.html)もあったが、私はマックがない。

ところが、意外に簡単に発見した。 方法は、まさに、<kbd>Ctrl</kbd> + <kbd>j</kbd>を押すだろう。 これにより、全ダウンロードリストタブが開かれる。 それとともにダウンロード状態バー消える。 すごい〜今再び、<kbd>Ctrl</kbd> + <kbd>w</kbd>を押してダウンロードリストタブを閉じると、元のタブに戻る。

結論。

<pre>Ctrl + j、Ctrl + w</pre>