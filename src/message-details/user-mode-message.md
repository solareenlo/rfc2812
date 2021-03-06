# 3.1.5 User Mode メッセージ

```
   Command: MODE
Parameters: <nickname>
            *( ( "+" / "-" ) *( "i" / "w" / "o" / "O" / "r" ) )
```

ユーザモードは通常、クライアントが他者からどのように見られるか、またはクライアントがどのような "追加" メッセージを送信するかに影響する変更です。

ユーザモードのコマンドは、メッセージの送信者とパラメータとして与えられたニックネームの両方が同じである場合にのみ受け入れられなければなりません。もし他のパラメータが与えられなければ、サーバはニックネームに対する現在の設定を返します。

使用可能なモードは以下の通りです。

```
        a - ユーザが不在であることを示すフラグが立てられる。
        i - ユーザを非表示とマークする。
        w - ユーザが Wallops を受け取る。
        r - ユーザ接続を制限する。
        o - オペレータフラグ。
        O - ローカルオペレータフラグ。
        s - サーバ通知を受信するユーザをマークする。
```

後日、追加のモードも用意される予定です。

MODE コマンドでフラグ `a` をトグルしてはならず、AWAY コマンドでトグルします。

ユーザが `+o` または `+O` フラグを使用して自分自身をオペレータにしようとした場合、OPER コマンドの認証メカニズムをバイパスすることができるため、その試みは無視されるべきです。しかし、（`-o` または `-O` を使って）自分自身を "脱落" させることについては、何ら制限はありません。

一方、ユーザが `-r` フラグを使って無制限化しようとした場合、その試みは無視されるべきです。しかし、（`+r` を使って）自分自身を "停止" させることについては、何の制限もありません。このフラグは、通常、管理上の理由から、接続時にサーバによって設定されます。どのような制限を加えるかは実装次第ですが、制限されたユーザがニックネームを変更したり、チャネルオペレータのステータスをチャネルで使用したりすることを許可しないのが一般的です。

フラグ `s` は廃止されましたが、まだ使用できるかもしれません。

数値返信：

```
        ERR_NEEDMOREPARAMS              ERR_USERSDONTMATCH
        ERR_UMODEUNKNOWNFLAG            RPL_UMODEIS
```

例：

```
MODE WiZ -w
    ; WiZ が WALLOPS メッセージの受信をオフにするコマンド。

MODE Angel +i
    ; Angel からの、自分を非表示にするコマンド。

MODE WiZ -o
    ; WiZ の "デオッピング"（オペレータの地位を取り除くこと）。
```
