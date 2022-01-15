# 3.2.5 Names メッセージ

```
   Command: NAMES
Parameters: [ <channel> *( "," <channel> ) [ <target> ] ]
```

NAMES コマンドを使用すると、ユーザが表示可能なすべてのニックネームを一覧表示することができます。見えるものと見えないものの詳細については、["Internet Relay Chat: チャネル管理" [IRC-CHAN]](https://solareenlo.com/rfc2811/) を参照してください。`<channel>` パラメータは、情報を返すチャネルを指定します。不正なチャネル名に対するエラー返信はありません。

`<channel>` パラメータが与えられない場合、すべてのチャネルとその占有者のリストが返されます。このリストの最後には、見えているがどのチャネルにも入っていない、あるいは見えているチャネルにも入っていないユーザのリストが `channel` `*` にあるとしてリストアップされます。

`<target>` パラメータが指定された場合、リクエストをそのサーバに転送し、そのサーバが応答を生成します。

`<target>` パラメータには、ワイルドカードを使用できます。

数値返信：

```
        ERR_TOOMANYMATCHES              ERR_NOSUCHSERVER
        RPL_NAMREPLY                    RPL_ENDOFNAMES
```

例：

```
NAMES #twilight_zone,#42
    ; #twilight_zone と #42 で表示可能なユーザーをリストアップするコマンド。

NAMES
    ; 表示可能なすべてのチャネルとユーザを一覧表示するコマンド。
```
