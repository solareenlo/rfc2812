# 4.8 Userhost メッセージ

```
   Command: USERHOST
Parameters: <nickname> *( SPACE <nickname> )
```

USERHOST コマンドはスペース文字で区切られた最大5つのニックネームのリストを受け取り、見つけたそれぞれのニックネームに関する情報のリストを返します。返されるリストには、それぞれの返答がスペースで区切られています。

数値返信：

```
        RPL_USERHOST                  ERR_NEEDMOREPARAMS
```

例：

```
USERHOST Wiz Michael syrk
    ; USERHOST によるニックネーム "Wiz", "Michael", "syrk" の情報提供の依頼。

:ircd.stealth.net 302 yournick :syrk=+syrk@millennium.stealth.net
    ; ユーザ syrk への返信。
```
