# 3.2.7 Invite メッセージ

```
   Command: INVITE
Parameters: <nickname> <channel>
```

INVITE コマンドは、ユーザをチャネルに招待するために使用します。パラメータ `<nickname>` には、対象のチャネル `<channel>` に招待する人のニックネームを指定します。ターゲットユーザが招待されるチャネルが存在すること、または有効なチャネルであることは要求されていません。ただし、チャネルが存在する場合、そのチャネルのメンバのみが他のユーザを招待することができます。チャネルに招待専用フラグが設定されている場合、チャネルオペレータのみが INVITE コマンドを発行できます。

招待の通知は、招待したユーザと招待されたユーザのみが受け取ります。他のチャネルメンバには通知されません。（これは MODE 変更と異なり、時々ユーザを悩ませる原因となっています。）

数値返信：

```
        ERR_NEEDMOREPARAMS              ERR_NOSUCHNICK
        ERR_NOTONCHANNEL                ERR_USERONCHANNEL
        ERR_CHANOPRIVSNEEDED
        RPL_INVITING                    RPL_AWAY
```

例：

```
:Angel!wings@irc.org INVITE Wiz #Dust
    ; WiZ が Angel からチャネル #Dust に招待されたときのメッセージ。


INVITE Wiz #Twilight_Zone
    ; WiZ を #Twilight_zone に招待するコマンド
```
