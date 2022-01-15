# 3.4.3 Version メッセージ

```
   Command: VERSION
Parameters: [ <target> ]
```

VERSION コマンドは、サーバプログラムのバージョンを問い合わせるために使用します。オプションのパラメータ `<target>` は、クライアントが直接接続していないサーバプログラムのバージョンを問い合わせるために使用されます。

`<target>` パラメータには、ワイルドカードを使用できます。

数値返信：

```
        ERR_NOSUCHSERVER                RPL_VERSION
```

例：

```
VERSION tolsun.oulu.fi
    ; サーバ tolsun.oulu.fi のバージョンを確認するコマンド。
```
