# 4.2 Rehash メッセージ

```
   Command: REHASH
Parameters: None
```

REHASH コマンドは管理用コマンドで、オペレータがサーバに設定ファイルの再読み込みと処理を強制するために使用することができます。

数値返信：

```
        RPL_REHASHING                 ERR_NOPRIVILEGES
```


例：

```
REHASH
    ; オペレータステータスを持つユーザからサーバに設定ファイルの再読込を依頼するメッセージ。
```
