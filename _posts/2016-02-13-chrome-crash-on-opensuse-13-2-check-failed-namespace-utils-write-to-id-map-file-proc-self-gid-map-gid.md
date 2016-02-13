---
title: 'openSUSEの13.2クロムエラー修正(Check failed: NamespaceUtils::WriteToIdMapFile("/proc/self/gid_map", gid_))'
layout: post
categories:
  - linux
tags:
  - opensuse
---

openSUSEのアップデートをしてからこそ、突然クロムが実行されない。コマンドラインで`google-chrome`を打って実行してみると、次のようなエラーメッセージが出てきた。

    Check failed: NamespaceUtils::WriteToIdMapFile("/proc/self/gid_map", gid_)

何かの名前空間で問題が出たということだが...

以下のようクロムを実行すると、一度実行される。名前空間の機能をオフにかよりも。

    google-chrome %U --disable-namespace-sandbox

以上。

