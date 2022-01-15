# 4.7 Operwall メッセージ

```
   Command: WALLOPS
Parameters: <Text to be sent>
```

WALLOPS コマンドは、現在接続しているユーザのうち、自分に `w` ユーザモードを設定しているユーザ全てにメッセージを送信するために使用されます。（[3.1.5節 "ユーザーモード"](../message-details/user-mode-message.md) 参照）。

WALLOPS をユーザコマンドとして実装した後、多くの人にメッセージを送る手段として、しばしば悪用されることがわかりました。このため、WALLOPS の実装では、サーバのみを WALLOPS の発信元として許可・認識することが推奨されます。

数値返信：

```
        ERR_NEEDMOREPARAMS
```

例：

```
:csd.bu.edu WALLOPS :Connect '*.uiuc.edu 6667' from Joshua
    ; csd.bu.edu からの WALLOPS メッセージは、Joshua から受信した CONNECT メッセージに対応することを告知しています。
```
