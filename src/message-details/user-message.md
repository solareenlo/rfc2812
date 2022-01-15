# 3.1.3 User メッセージ

```
   Command: USER
Parameters: <user> <mode> <unused> <realname>
```

USER コマンドは、接続の最初に使用し、新規ユーザのユーザ名、ホスト名、リアルネームを指定します。

`<mode>` パラメータには数値を指定し、サーバに登録する際にユーザモードを自動的に設定することができます。このパラメータはビットマスクで、2ビットだけが意味を持ちます。ビット2が設定されるとユーザモード `w` が設定され、ビット3が設定されるとユーザモード `i` が設定されます。（[3.1.5 節 "ユーザモード"](./user-mode-message.md) を参照）。

`<realname>` には空白文字が含まれることがあります。

数値返信：

```
        ERR_NEEDMOREPARAMS              ERR_ALREADYREGISTRED
```

例：

```
USER guest 0 * :Ronnie Reagan
    ; ユーザ名 "guest"、本名 "Ronnie Reagan" で登録したユーザ。

USER guest 8 * :Ronnie Reagan
    ; ユーザ名 "guest"、本名 "Ronnie Reagan" で登録し、非表示にすることを依頼するユーザ。
```
