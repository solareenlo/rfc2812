# 3.6.2 Whois クエリ

```
   Command: WHOIS
Parameters: [ <target> ] <mask> *( "," <mask> )
```

このコマンドは、特定のユーザに関する情報を照会するために使用されます。サーバはこのコマンドに対して、マスクにマッチする各ユーザのさまざまなステータスを示すいくつかの数値メッセージを返します（あなたがそれらを見る権利がある場合）。`<mask>` にワイルドカードが含まれていない場合、そのニックネームに関する、閲覧が許可されているすべての情報が表示されます。

`<target>` パラメータを指定した場合、特定のサーバーに問い合わせを行います。これは、該当するユーザがどれくらいの時間アイドル状態であったかを知りたい場合に有効で、その情報はローカルサーバ（ユーザが直接接続しているサーバ）のみが知っており、その他の情報はグローバルに知られています。

`<target>` パラメータには、ワイルドカードを使用できます。

数値返信：

```
        ERR_NOSUCHSERVER              ERR_NONICKNAMEGIVEN
        RPL_WHOISUSER                 RPL_WHOISCHANNELS
        RPL_WHOISCHANNELS             RPL_WHOISSERVER
        RPL_AWAY                      RPL_WHOISOPERATOR
        RPL_WHOISIDLE                 ERR_NOSUCHNICK
        RPL_ENDOFWHOIS
```

例：

```
WHOIS wiz
    ; ニックネーム WiZ に関する利用可能なユーザ情報を返します。

WHOIS eff.org trillian
    ; trillian に関するユーザ情報をサーバ eff.org に問い合わせます。
```
