# 3.4.7 Connect メッセージ

```
   Command: CONNECT
Parameters: <target server> <port> [ <remote server> ]
```

CONNECT コマンドは、他のサーバとの新しい接続を直ちに試みるようにサーバに要求するために使用することができます。CONNECT は特権的なコマンドであり、IRC オペレータのみが使用できるようにすべきです。 `<remote server>` が与えられ、そのマスクが解析サーバの名前と一致しない場合、CONNECT の試行は最初に一致したリモートサーバに送られます。それ以外の場合は、リクエストを処理するサーバによって CONNECT が試行されます。

リモート CONNECT コマンドを受信したサーバは、リクエストのソースとターゲットを記述する WALLOPS メッセージを生成する必要があります。

数値返信：

```
        ERR_NOSUCHSERVER              ERR_NOPRIVILEGES
        ERR_NEEDMOREPARAMS
```

例：

```
CONNECT tolsun.oulu.fi 6667
    ; ローカルサーバから tolsun.oulu.fi のポート6667への接続を試行するコマンド。
```
