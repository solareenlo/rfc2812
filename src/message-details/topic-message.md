# 3.2.4 Topic メッセージ

```
   Command: TOPIC
Parameters: <channel> [ <topic> ]
```

TOPIC コマンドは、チャネルのトピックを変更または表示するために使用されます。`<topic>` が指定されていない場合は、チャネル `<channel>` のトピックが返されます。`<topic>` パラメータが指定された場合、そのチャネルのトピックが変更されます（要求したユーザがこの操作を許可している場合）。`<topic>` パラメータが空の文字列である場合、そのチャネルのトピックは削除されます。

数値返信：

```
        ERR_NEEDMOREPARAMS              ERR_NOTONCHANNEL
        RPL_NOTOPIC                     RPL_TOPIC
        ERR_CHANOPRIVSNEEDED            ERR_NOCHANMODES
```

例：

```
:WiZ!jto@tolsun.oulu.fi TOPIC #test :New topic
    ; ユーザ Wiz がトピックを設定します。

TOPIC #test :another topic
    ; #test のトピックを "another topic" に設定するコマンド。

TOPIC #test :
    ; #test のトピックを消去するコマンド。

TOPIC #test
    ; #test のトピックを確認するコマンド。
```
