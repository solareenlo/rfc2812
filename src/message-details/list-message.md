# 3.2.6 List メッセージ

```
   Command: LIST
Parameters: [ <channel> *( "," <channel> ) [ <target> ] ]
```

LIST コマンドは、チャネルとそのトピックを一覧表示するために使用されます。`<channel>` パラメータを指定した場合は，そのチャネルの状態のみを表示します。

`<target>`パラメータが指定された場合、リクエストをそのサーバに転送し、そのサーバが応答を生成します。

`<target>` パラメータには、ワイルドカードを使用できます。

数値返信：

```
        ERR_TOOMANYMATCHES              ERR_NOSUCHSERVER
        RPL_LIST                        RPL_LISTEND
```

例：

```
LIST
    ; 全チャネルを一覧表示するコマンド。

LIST #twilight_zone,#42
    ; チャネル #twilight_zone と #42 をリストアップするコマンド。
```
