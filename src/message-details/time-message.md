# 3.4.6 Time メッセージ

```
   Command: TIME
Parameters: [ <target> ]
```

TIME コマンドは、指定されたサーバからローカルタイムを問い合わせるために使用されます。`<target>` パラメータを指定しない場合、コマンドを受信したサーバは問い合わせに応答する必要があります。

`<target>` パラメータには、ワイルドカードを使用できます。

数値返信：

```
        ERR_NOSUCHSERVER              RPL_TIME
```

例：

```
TIME tolsun.oulu.fi
    ; サーバ "tolson.oulu.fi" の時刻を確認する。
```
