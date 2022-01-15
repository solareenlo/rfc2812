# 3.4.10 Info コマンド

```
   Command: INFO
Parameters: [ <target> ]
```

INFO コマンドは、サーバのバージョン、コンパイル日、パッチレベル、起動日、その他関連すると思われる雑多な情報など、サーバに関する情報を返すことが要求されます。

`<target>` パラメータには、ワイルドカードを使用できます。

数値返信：

```
        ERR_NOSUCHSERVER
        RPL_INFO                      RPL_ENDOFINFO
```

例：

```
INFO csd.bu.edu
    ; csd.bu.edu からの INFO 応答を要求します。

INFO Angel
    ; Angel が接続しているサーバに情報を要求します。
```
