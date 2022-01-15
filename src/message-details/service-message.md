# 3.1.6 Service メッセージ

```
   Command: SERVICE
Parameters: <nickname> <reserved> <distribution> <type>
            <reserved> <info>
```

新しいサービスを登録するための SERVICE コマンドです。コマンドのパラメータは、新しいサービスのニックネーム、ディストリビューション、タイプ、情報を指定します。

`<distribution>` パラメータは，サービスの可視性を指定するために使用します．サービスは，ディストリビューションに一致する名前を持つサーバにのみ知られる可能性があります。名前が一致するサーバがサービスを知るためには，そのサーバとサービスが接続されているサーバとの間のネットワークパスが，すべてマスクに一致するサーバで構成されている必要があります。

`<type>` パラメータは現在、将来の使用のために予約されています。

数値返信：

```
        ERR_ALREADYREGISTRED            ERR_NEEDMOREPARAMS
        ERR_ERRONEUSNICKNAME
        RPL_YOURESERVICE                RPL_YOURHOST
        RPL_MYINFO
```

例：

```
SERVICE dict * *.fr 0 0 :French Dictionary
    ; "dict" という名前で自分自身を登録するサービス。
      このサービスは、名前が "*.fr" にマッチするサーバでのみ利用可能です。
```
