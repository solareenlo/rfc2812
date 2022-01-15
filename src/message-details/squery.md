# 3.5.2 Squery

```
   Command: SQUERY
Parameters: <servicename> <text>
```

SQUERY コマンドは、PRIVMSG と同様の使い方をします。唯一の違いは、受信者がサービスでなければならないことです。これは、テキストメッセージをサービスに配信する唯一の方法です。

返信の詳細および例については、PRIVMSG を参照してください。

例：

```
SQUERY irchelp :HELP privmsg
    ; irchelp というニックネームのサービスに対するメッセージ。

SQUERY dict@irc.fr :fr2en blaireau
    ; Message to the service with name dict@irc.fr.
    ; 名前 dict@irc.fr のサービスに対するメッセージ。

```
