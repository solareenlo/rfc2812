# 3.2.8 Kick コマンド

```
   Command: KICK
Parameters: <channel> *( "," <channel> ) <user> *( "," <user> )
            [<comment>]
```

KICK コマンドは、チャネルからユーザを強制的に削除することを要求するために使用します。これは `<user>` を `<channel>` から強制的に PART させます。メッセージが構文的に正しいものであるためには、1つのチャネルパラメータと複数のユーザパラメータ、またはユーザパラメータと同数のチャネルパラメータがなければなりません。"comment" が指定された場合、デフォルトメッセージの代わりに、KICK を発行したユーザのニックネームが送信されます。

サーバは、複数のチャネルまたはユーザを含む KICK メッセージをクライアントに送信してはなりません。これは、古いクライアントソフトウェアとの後方互換性を維持するために必要なことです。

数値返信：

```
        ERR_NEEDMOREPARAMS              ERR_NOSUCHCHANNEL
        ERR_BADCHANMASK                 ERR_CHANOPRIVSNEEDED
        ERR_USERNOTINCHANNEL            ERR_NOTONCHANNEL
```

例：

```
KICK &Melbourne Matthew
    ; &Melbourne から Matthew を追い出す指令

KICK #Finnish John :Speaking English
    ; "Speaking English" を理由（コメント）に #Finnish から John を追い出すコマンド。

:WiZ!jto@tolsun.oulu.fi KICK #Finnish John
    ; チャネル #Finnish から John を外すという WiZ からの KICK メッセージ。
```
