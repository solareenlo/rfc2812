# 3.2.2 Part メッセージ

```
   Command: PART
Parameters: <channel> *( "," <channel> ) [ <Part Message> ]
```

PART コマンドは、メッセージを送信したユーザを、パラメータ文字列で指定されたすべてのチャネルのアクティブメンバリストの対象から除外します。もし "Part メッセージ" が指定された場合、デフォルトメッセージであるニックネームの代わりにこれが送信されます。このリクエストはサーバによって常に許可されます。

サーバは、ターゲットのリスト形式で引数を解析できなければなりませんが、クライアントに PART メッセージを送信する際には、リストを使用すべきではありません。

数値返信：

```
        ERR_NEEDMOREPARAMS              ERR_NOSUCHCHANNEL
        ERR_NOTONCHANNEL
```

例：

```
PART #twilight_zone
    ; Command to leave channel "#twilight_zone"
    ; チャネル "#twilight_zone" を抜けるコマンド。

PART #oz-ops,&group5
    ; "&group5" と "#oz-ops" の両チャネルを抜けるコマンド。

:WiZ!jto@tolsun.oulu.fi PART #playzone :I lost
    ; "I lost" というメッセージとともにチャネル "#playzone" を去るユーザ WiZ。
```
