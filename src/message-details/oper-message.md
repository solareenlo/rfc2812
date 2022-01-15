# 3.1.4 Oper メッセージ

```
   Command: OPER
Parameters: <name> <password>
```

一般ユーザは、OPER コマンドを使用してオペレータ権限を取得します。オペレータ権限を得るには，`<name>` と `<password>` の組み合わせが必要です。成功すると、新しいユーザモードを示す MODE メッセージ（[3.1.5 節](./user-mode-message.md) を参照）がユーザに送信されます。

数値返信：

```
        ERR_NEEDMOREPARAMS              RPL_YOUREOPER
        ERR_NOOPERHOST                  ERR_PASSWDMISMATCH
```

例：

```
OPER foo bar
    ; ユーザ名に "foo"、パスワードに "bar" を用いてオペレータ登録を試みる。
```
