# 3.1.1 Password メッセージ

```
   Command: PASS
Parameters: <password>
```

PASS コマンドは、"接続パスワード" を設定するために使用します。オプションのパスワードは、接続を登録しようとする前に設定することができ、また設定しなければなりません。現在、NICK/USER の組み合わせを送信する前に、PASS コマンドを送信することが必要です。

数値返信：

```
        ERR_NEEDMOREPARAMS              ERR_ALREADYREGISTRED
```

例：

```
PASS secretpasswordhere
```
