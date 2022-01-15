# 3.4.5 Links メッセージ

```
   Command: LINKS
Parameters: [ [ <remote server> ] <server mask> ]
```

LINKS を使用すると、ユーザは、クエリに答えるサーバが知っているすべてのサーバ名をリストアップすることができます。返されるサーバのリストはマスクと一致しなければならず、マスクが与えられない場合は完全なリストが返されます。

`<server mask>` に加えて `<remote server>` が指定された場合、LINKS コマンドはその名前にマッチする最初のサーバに転送され、そのサーバは問い合わせに答えることが要求されます。

数値返信：

```
        ERR_NOSUCHSERVER
        RPL_LINKS                        RPL_ENDOFLINKS
```

例：

```
LINKS *.au
    ; 名前が *.au に一致するサーバをすべてリストアップするコマンド。


LINKS *.edu *.bu.edu
    ; *.bu.edu に一致するサーバを、*.edu に一致する最初のサーバから見てリストアップするコマンド。
```
