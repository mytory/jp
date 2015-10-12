---
title: '[アパッチ] (98)Address already in use: make_sock: could not bind to address [::]:80 エラー 発生の時'
author: 녹풍(綠風, Windgreen)
layout: post
permalink: /archives/685
aktt_notify_twitter:
  - yes
categories:
  - Web server
tags:
  - apache
---
今日 サーバーを 回そうと するから 下と ような エラー メッセージが 浮かんだ.

<pre>(98)Address already in use: make_sock: could not bind to address [::]:80</pre>

まどろみ 迷ったが 解決策は 簡単だった. しかし 根本的 処方かは 分からない.

<pre>netstat -nlp</pre>

ssh路 接続して これ 命令を 打つ.

それでは 現在 実行中の プロセスが 出る. 下のように 出る ことだ.

<pre class="brush:shell;highlight:[4,5,8]">Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      947/mysqld
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN      2180/apache2
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      2180/apache2
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      697/sshd
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      942/cupsd
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      2180/apache2
tcp6       0      0 :::5900                 :::*                    LISTEN      1198/vino-server
tcp6       0      0 :::22                   :::*                    LISTEN      697/sshd
tcp6       0      0 ::1:631                 :::*                    LISTEN      942/cupsd
udp        0      0 0.0.0.0:49724           0.0.0.0:*                           740/avahi-daemon: r
udp        0      0 0.0.0.0:68              0.0.0.0:*                           826/dhclient
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           740/avahi-daemon: r
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     3114     1/init              @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     4934     947/mysqld          /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     5009     822/gdm-simple-slav @/tmp/gdm-session-yPXnypLE
unix  2      [ ACC ]     STREAM     LISTENING     4424     740/avahi-daemon: r /var/run/avahi-daemon/socket
(後略...)</pre>

彼 中に apache と 使って ある 奴が 4,5,8番(回) 竝びに ある やつなのに, 2180/apache2 と 使って ある. 2180これ プロセス 番号だ.

これ やつらを 殺せば なる.

<pre>kill -9 2180</pre>

と 使って エンター. それでは apache2街 芽 死ぬ.

今 行えば 寝る なる.

ところが いったい 理解が 中 なる 件 なぜ こういう 仕事が 発生するのか する ことだ.

分かる 粉餌 あったら デッグルで 知らせて くだされば ありがたい.