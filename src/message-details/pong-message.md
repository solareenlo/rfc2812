# 3.7.3 Pong メッセージ

```
   Command: PONG
Parameters: <server> [ <server2> ]
```

PONG メッセージは、Ping メッセージに対する応答です。パラメータ `<server2>` が指定された場合、このメッセージは指定されたターゲットに転送されなければなりません。`<server>` パラメータには，PING メッセージに応答してこのメッセージを生成したエンティティの名前を指定します。

数値返信：

```
        ERR_NOORIGIN                  ERR_NOSUCHSERVER
```

例：

```
PONG csd.bu.edu tolsun.oulu.fi
    ; csd.bu.edu から tolsun.oulu.fi への PONG メッセージ
```
