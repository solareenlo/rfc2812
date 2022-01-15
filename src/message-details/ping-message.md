# 3.7.2 Ping メッセージ

```
   Command: PING
Parameters: <server1> [ <server2> ]
```

PING コマンドは、接続の相手側にアクティブなクライアントまたはサーバが存在するかどうかをテストするために使用されます。サーバは、接続から他のアクティビティが検出されない場合、一定の間隔で PING メッセージを送信します。接続が一定時間内に PING メッセージに応答しない場合、その接続は閉じられます。PING メッセージは、接続がアクティブであっても送信されることがあります。

PING メッセージを受信したら、できるだけ早く適切な PONG メッセージを `<server1>`（PING メッセージを発信したサーバ）に返信する必要があります。`<server2>` が指定されている場合は、PING の送信先を表し、メッセージはそこに転送されます。

数値返信：

```
        ERR_NOORIGIN                  ERR_NOSUCHSERVER
```

例：

```
PING tolsun.oulu.fi
    ; サーバに PING メッセージを送信するコマンド。

PING WiZ tolsun.oulu.fii
    ; WiZ からサーバ "tolsun.oulu.fi" への PING メッセージ送信コマンド

PING :irc.funet.fi
    ; サーバ "irc.funet.fi" から送信された Ping メッセージ。
```
