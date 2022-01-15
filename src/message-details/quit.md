# 3.1.7 Quit

```
   Command: QUIT
Parameters: [ <Quit Message> ]
```

クライアントのセッションは、Quit メッセージで終了します。サーバは、ERROR メッセージをクライアントに送信することでこれを確認します。

数値返信：

```
        None.
```

例：

```
QUIT :Gone to have lunch
    ; 望ましいメッセージの形式。

:syrk!kalt@millennium.stealth.net QUIT :Gone to have lunch
    ; ユーザ syrk は昼食のために IRC を終了しました。
```
