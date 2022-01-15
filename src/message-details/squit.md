# 3.1.8 Squit

```
   Command: SQUIT
Parameters: <server> <comment>
```

SQUIT コマンドはオペレータのみ使用可能です。サーバのリンクを切断するために使用されます。また、サーバはエラー状態の時に SQUIT メッセージを生成することができます。SQUIT メッセージは、リモートサーバの接続をターゲットにすることもできます。この場合、SQUIT メッセージはオペレータとリモートサーバ間のサーバに影響を与えることなく、単にリモートサーバに送信されます。

`<comment>` は、リモートサーバに対して SQUIT を実行するすべてのオペレータによって供給されなければなりません。相手の切断を命じられたサーバは，`<comment>` を含む WALLOPS メッセージを生成し，他のユーザがこの動作の理由を知ることができるようにします。

数値返信：

```
        ERR_NOPRIVILEGES                ERR_NOSUCHSERVER
        ERR_NEEDMOREPARAMS
```

例：

```
SQUIT tolsun.oulu.fi :Bad Link ?
    ; tolson.oulu.fi の uplink に "Bad Link" というコメントで接続を終了させるコマンド。

:Trillian SQUIT cm22.eng.umd.edu :Server out of control
    ; Trillianからの "Server out of control" というコメントとともに
      "cm22.eng.umd.edu" をネットから切断するコマンド。

```
