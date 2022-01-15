# 4.6 Users

```
   Command: USERS
Parameters: [ <target> ]
```

USERS コマンドは、UNIX コマンドの who(1), rusers(1), finger(1) と同様のフォーマットで、サーバにログインしているユーザの一覧を返します。無効の場合、それを示す正しい数値が返されなければなりません。

このようなコマンドはセキュリティに影響するため、サーバの実装ではデフォルトで無効化されるべきです。有効にするためには、単にオプションを切り替えてサーバを再起動するのではなく、サーバの再コンパイルや同等の変更が必要になるはずです。このコマンドを有効にする手順には、適切な大きさのコメントを含める必要があります。

数値返信：

```
        ERR_NOSUCHSERVER              ERR_FILEERROR
        RPL_USERSSTART                RPL_USERS
        RPL_NOUSERS                   RPL_ENDOFUSERS
        ERR_USERSDISABLED
```

返信不可：

```
        ERR_USERSDISABLED
```

例：

```
USERS eff.org
    ; request a list of users logged in on server eff.org
    ; サーバ eff.org にログインしているユーザのリストを要求します。
```
