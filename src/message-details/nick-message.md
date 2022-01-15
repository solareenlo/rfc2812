# 3.1.2 Nick メッセージ

```
   Command: NICK
Parameters: <nickname>
```

NICK コマンドは、ユーザにニックネームを与えたり、既存のニックネームを変更するために使用されます。

数値返信：

```
        ERR_NONICKNAMEGIVEN             ERR_ERRONEUSNICKNAME
        ERR_NICKNAMEINUSE               ERR_NICKCOLLISION
        ERR_UNAVAILRESOURCE             ERR_RESTRICTED
```

例：

```
NICK Wiz
    ; セッションが未登録の場合、新しいニックネーム "Wiz" を導入、
      またはユーザがニックネームを "Wiz" に変更した場合。


:WiZ!jto@tolsun.oulu.fi NICK Kilroy
    ; WiZ が Kilroy にニックネームを変更したことを伝えるサーバ。
```
