# 3.2.3 Mode メッセージ

```
   Command: MODE
Parameters: <channel> *( ( "-" / "+" ) *<modes> *<modeparams> )
```

MODE コマンドは、ユーザがチャネルの特性を照会したり変更したりするために用意されています。利用可能なモードとその用途の詳細については、["Internet Relay Chat: チャンネル管理" [IRC-CHAN]](https://solareenlo.com/rfc2811/) を参照してください。パラメータを取るモードでは、1回のコマンドで3回までしか変更できないことに注意してください。

数値返信：

```
        ERR_NEEDMOREPARAMS              ERR_KEYSET
        ERR_NOCHANMODES                 ERR_CHANOPRIVSNEEDED
        ERR_USERNOTINCHANNEL            ERR_UNKNOWNMODE
        RPL_CHANNELMODEIS
        RPL_BANLIST                     RPL_ENDOFBANLIST
        RPL_EXCEPTLIST                  RPL_ENDOFEXCEPTLIST
        RPL_INVITELIST                  RPL_ENDOFINVITELIST
        RPL_UNIQOPIS
```

以下の例は、MODE コマンドの構文を理解するためのものですが、["Internet Relay Chat: チャンネル管理" [IRC-CHAN]](https://solareenlo.com/rfc2811/) で定義されているモードを参照しています。

例：

```
MODE #Finnish +imI *!*@*.fi
    ; ホスト名が *.fi に一致するユーザが自動的に招待される、
      #Finnish チャネルをモデレートされた '招待制' にするコマンド。

MODE #Finnish +o Kilroy
    ; チャネル #Finnish の Kilroy に 'chanop' 権限を付与するコマンド。

MODE #Finnish +v Wiz
    ; WiZ が #Finnish で発言することを許可するコマンド。

MODE #Fins -s
    ; チャネル #Fins から 'secret' フラグを削除するコマンド。

MODE #42 +k oulu
    ;チャンネルキーを "ulu" に設定するコマンド。

MODE #42 -k oulu
    ; チャネル "#42" の "oulu" チャネルキーを削除するコマンド。

MODE #eu-opers +l 10
    ; チャネル "#eu-opers" のユーザ数の上限を10に設定するコマンド。

:WiZ!jto@tolsun.oulu.fi MODE #eu-opers -l
    ; ユーザ "WiZ" がチャネル "#eu-opers" のユーザ数制限を解除しました。

MODE &oulu +b
    ; チャネル "&oulu" に設定された禁止マスクをリストアップするコマンド。

MODE &oulu +b *!*@*
    ; すべてのユーザを参加させないようにするためのコマンド。


MODE &oulu +b *!*@*.edu +e *!*@*.bu.edu
    ; ホスト名が *.edu に一致するユーザが参加できないようにするコマンド。
      ただし、*.bu.edu に一致する場合は除く。

MODE #bu +be *!*@*.edu *!*@*.bu.edu
    ; *.bu.edu にマッチする場合を除き、
      *.edu にマッチするホスト名のユーザが参加できないようにするコメント。

MODE #meditation e
    ; チャネル "#meditation" に設定された例外マスクを一覧表示するコマンド。

MODE #meditation I
    ; チャネル "#meditation" に設定された招待マスクを一覧表示するコマンド。


MODE !12345ircd O
    ; "!12345ircd" のチャネル作成者が誰かを問い合わせるコマンド。
```
