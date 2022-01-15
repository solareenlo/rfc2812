```
Network Working Group                                            C. Kalt
Request for Comments: 2812                                    April 2000
Updates: 1459
Category: Informational
```

<h1 align="center">
Internet Relay Chat: クライアントプロトコル
</h1>

## 本メモの位置づけ

このメモは、インターネットコミュニティのための情報を提供するものです。このメモは、いかなる種類のインターネット標準も規定するものではありません。このメモの配布は無制限です。

## Copyright Notice

Copyright (C) The Internet Society (2000). All Rights Reserved.

## IESG NOTE:

IRC プロトコル自体は、クライアント間のデータ転送のいくつかの可能性を可能にし、電子メールのような他の転送メカニズムと同様に、データの受信者は、データの取り扱いについて注意しなければなりません。IRC プロトコルのセキュリティ問題については、例えば <http://www.irchelp.org/irchelp/security/> を参照してください。

## 概要

IRC（Internet Relay Chat）プロトコルは、テキストベースの会議用で、サーバに接続可能なソケットプログラムであれば、最もシンプルなクライアントとなります。

この文書では、クライアントプロトコルを定義し、読者が [IRC アーキテクチャ [IRC-ARCH]](https://solareenlo.com/rfc2810) に精通していることを想定しています。
