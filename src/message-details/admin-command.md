# 3.4.9 Admin コマンド

```
   Command: ADMIN
Parameters: [ <target> ]
```

ADMIN コマンドは、指定されたサーバ（`<target>` パラメータが省略された場合は現在のサーバ）の管理者情報を検索するために使用されます。各サーバは、ADMIN メッセージを他のサーバに転送する機能を持つ必要があります。

<target>パラメータには、ワイルドカードを使用できます。

数値返信：

```
        ERR_NOSUCHSERVER
        RPL_ADMINME                   RPL_ADMINLOC1
        RPL_ADMINLOC2                 RPL_ADMINEMAIL
```

例：

```
ADMIN tolsun.oulu.fi
    ; tolsun.oulu.fi から ADMIN の返信を要求します。

ADMIN syrk
    ; ユーザ syrk が接続しているサーバへの ADMIN リクエスト。
```
