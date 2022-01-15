# 3.4.1 Motd メッセージ

```
   Command: MOTD
Parameters: [ <target> ]
```

MOTD コマンドは、指定されたサーバ（`<target>` が省略された場合は現在のサーバ）の "今日のメッセージ" を取得するために使用されます。

`<target>` パラメータには、ワイルドカードを使用できます。

数値返信：

```
        RPL_MOTDSTART                   RPL_MOTD
        RPL_ENDOFMOTD                   ERR_NOMOTD
```
