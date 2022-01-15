# 3.4.2 Lusers メッセージ

```
   Command: LUSERS
Parameters: [ <mask> [ <target> ] ]
```

LUSERS コマンドは、IRC ネットワークのサイズに関する統計を取るために使用されます。パラメータが与えられない場合、ネット全体についての返答があります。`<mask>` が指定された場合、そのマスクに一致するサーバによって形成されたネットワークの一部分に関する情報のみが返信されます。最後に、`<target>` パラメータが指定された場合、リクエストは応答を生成するサーバに転送されます。

`<target>` パラメータには、ワイルドカードを使用できます。

数値返信：

```
        RPL_LUSERCLIENT                 RPL_LUSEROP
        RPL_LUSERUNKOWN                 RPL_LUSERCHANNELS
        RPL_LUSERME                     ERR_NOSUCHSERVER
```
