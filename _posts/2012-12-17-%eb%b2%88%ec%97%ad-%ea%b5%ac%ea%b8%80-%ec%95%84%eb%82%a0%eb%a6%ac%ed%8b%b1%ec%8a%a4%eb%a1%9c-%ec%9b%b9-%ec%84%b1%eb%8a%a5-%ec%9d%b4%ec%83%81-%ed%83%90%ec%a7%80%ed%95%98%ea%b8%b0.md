---
title: '[翻訳] Googleあ飛ばしティクスでWebパフォーマンスの異常検出する'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/1855
categories:
  - ウェブ解析と検索
tags:
  - Google Analytics
  - Web Analytics
---
原文は [&#8216;Web Performance Anomaly Detection with Google Analytics&#8217;][1]である. 翻訳手始めだ.

&#8212;&#8212;

<img class="left alignleft" alt="" src="http://dl.dropbox.com/u/15546257/blog/mytory/GA-detect-anomaly/ga-alert.png" width="208" height="129" />

第一, すべてのものをモニタリングしなさい. 第二, データ分析, 通察得ること, **繰り返し的に** 測定するのをモニタリングして最適化することに分析時間と資源の 90%を集中しなさい.しかし一つ小さな問題がある. **機械が生産し出す大量のデータが私たちの分析能力, モニタリング能力, 数値を連関をつけて解釈する能力を追い越す場合だ.**

まさにこの地点が[異常探知アルゴリズム][2]  <a class="simple-footnote" title="anomaly detection algorithm-捜してみるから異常探知, アブノーマル探知などに翻訳されていたよ.公認された訳語があるようではなかった." id="return-note-1855-1" href="#note-1855-1"><sup>1</sup></a> この立つ席だ. このアルゴリズムはとても有用なデータに近付く立派な統計エンジンに裏付される. このエンジンは完璧な必要はないが一般的ではない状況が感知された時私たちに知らせてくれるべきである. もう入って来たお知らせや, メールするにある知らせることを土台で私たちは調査が必要か判断することができる.

<div class="video-container">
  <div class="video-container__inner">
  </div>
</div>

## グーグルアナルリティックスの知能型イベント

良い消息がある. あなたがグーグルアナルリティックスを使っていたら, 力強い異常もらうことだエンジンがもうあるのだ. まさに [知能型イベント][3]だ.なによりも, これは既存データ, 設定されたセグメント, そして他のコストマイジングしたものなどを皆カバーする. そして価格がとてもぴったりだ. 無料だ.

> アナルリティックスは意味ある統計的数値たちを感知するためにウェブサイトトラフィックをモニタリングする.そして気を使わなければならない数値を感知すれば自動でお知らせや知能型イベントを生成する. 異常数値を徹底的に観察することで, そのようにしなかったら逃した事が当然な通察を得ることができる. 例えば, 特定都市やサイトで急に流入が多くなるとか一場合言葉だ.

事実, 少し手数を入れてコストマイジングをすれば, **知能型イベントを利用して手軽くサイト性能をモニタリングすることができる!**引導から来た訪問者のページローディング時間が変だ? 問題を感知することができる自動化されたツールがあるのだ.

<img class="center" style="max-width: 691px; width: 100%;" alt="" src="http://dl.dropbox.com/u/15546257/blog/mytory/GA-detect-anomaly/wplt-alert.png.pagespeed.ic.png" width="691" height="184" />

錦上花を添えるで, 例示で入った報告書を見れば分かるが, 知らせることがどうして生成されたのか, 引導チェンナイから来た訪問者と連関をつけて説明しているという点だ. 引導チェンナイから来た訪問者たちがページローディング時間がよほど長かったことで確認された.こんなに情報を手に握ることで, 私たちは根本原因を極めることができる.

## ウェブ性能異常探知

グーグルアナルリティックスは <a href="http://w3c-test.org/webperf/specs/NavigationTiming/" class="broken_link">W3C ナビゲーションタイミング</a> APIを支援するブラウザーの場合 [ページローディング時間性能データを測定][4]する. この APIは次を測定する : リデ−レックトと DNS 時間, TCP 確立, サーバー回答時間, onload 時間同じ DOM レベル測定する. 多様な測定しある. それぞれの測定する使用者が実際にサイトに接続するのにかかった時間を記録する. 言い換えれば, これは実使用者測定(Real User Measurement (RUM))だ. 人工データではない.

[サイトの中も報告書][5]エイックスックしなければ, 学びやすい所がある. 詳しく分かりたければ [この GDL エピソード][6]を見なさい. <a class="simple-footnote" title="GDL &#8211; Google Developers Live" id="return-note-1855-2" href="#note-1855-2"><sup>2</sup></a> ところで, 私たちは一段階もっと出るはずだ.**それぞれのネイゲイションタイミング測定するのを知能型イベントにモニタリングすることができる!**オーダーメード知らせることを作って, イベントを発生させる基準店位だけ設定してくれれば良い.

<img class="center" style="max-width: 638px; width: 100%;" alt="" src="http://dl.dropbox.com/u/15546257/blog/mytory/GA-detect-anomaly/walert-segment.png.pagespeed.ic.png" width="638" height="275" />

私たちサイト性能お知らせのためのアイディア :

*   全世界あるいは特定地域の** DNS 解釈時間追跡**
*   すべての訪問者, あるいはそれぞれ異なるバージョンのサイトにコストマイジングした **サーバー回答時間追跡**
*   誤作動する CSS, スクリプトや他の資源を感知する **onload 時間追跡.**

## パウォチップ : 高級セグメントを使いなさい!

サイト全体に対して特定数値に対するお知らせを設定することは良い手始めだ. しかし, グーグルアナルリティックスで [高級セグメント][7]を使って見た事がなければ, うわっつらをなめたのだ. アジアモバイル訪問者あるいは特に東京のページローディング時間や DNS 時間をモニタリングする必要があったら? 問題ない. 新しい高級セグメントを作さえすればよい.

<img class="center" style="max-width: 684px; width: 100%;" alt="" src="https://dl.dropbox.com/u/15546257/blog/mytory/GA-detect-anomaly/wmobile-asia-segment.png.pagespeed.ic.png" width="684" height="460" />

高級セグメントは, 一度作るだけで, グーグルアナルリティックスのどんな報告書にでも適用することができる. 知能型お知らせでも使うように設定することができる! 特定市場, 特定使用者類型, 特定トラフィックみたいなことを観察しなければならないとして見よう. オーダーメードセグメントを作れば知らせることをそれほど合わせることができる.

## 測定, 最適化, 繰り返し

異常探知エンジンは道具だ. そして力強い道具だ. **しかし設定するのは私たち自分の責任だ. 自分のサイトに当たるように繰り返し的にセグメントとお知らせ基準店を改善しなければならない.**益体もない知らせることもたくさん受けるようになるつもりだ.しかしデータモニタリングの急流の中では絶対見つけることができなかった問題も引き上げるようになるでしょう.

<div class="simple-footnotes">
  <p class="notes">
    Notes:
  </p>
  
  <ol>
    <li id="note-1855-1">
      <a href="http://en.wikipedia.org/wiki/Anomaly_detection">anomaly detection algorithm</a>-捜してみるから異常探知, アブノーマル探知などに翻訳されていたよ.公認された訳語があるようではなかった. <a href="#return-note-1855-1">&#8617;</a>
    </li>
    <li id="note-1855-2">
      <a href="https://developers.google.com/live/">GDL &#8211; Google Developers Live</a> <a href="#return-note-1855-2">&#8617;</a>
    </li>
  </ol>
</div>

 [1]: http://www.igvita.com/2012/11/30/web-performance-anomaly-detection-with-google-analytics/
 [2]: http://en.wikipedia.org/wiki/Anomaly_detection
 [3]: http://support.google.com/analytics/bin/answer.py?hl=ja&answer=1320491&topic=1032994&ctx=topic
 [4]: http://www.igvita.com/2012/04/04/measuring-site-speed-with-navigation-timing/
 [5]: http://support.google.com/analytics/bin/answer.py?hl=ja&answer=1205784
 [6]: http://www.youtube.com/watch?v=NCFVEuKQgBM&list=PL1B4F4863AEE2B122&index=1
 [7]: http://support.google.com/analytics/bin/answer.py?hl=ja&answer=1033017