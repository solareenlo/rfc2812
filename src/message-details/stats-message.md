# 3.4.4 Stats メッセージ

```
   Command: STATS
Parameters: [ <query> [ <target> ] ]
```

STATS コマンドは、特定のサーバの統計情報を問い合わせるために使用します。`<query>` パラメータを省略した場合は，統計情報の末尾のみを返送します。

クエリは、任意の1文字について指定することができ、宛先サーバでのみチェックされ、それ以外の中間サーバで無視され、変更されずに渡されます。

`<target>` パラメータには、ワイルドカードを使用できます。

以下のものを除き、有効なクエリのリストは実装に依存します。以下の標準的なクエリは、サーバ側でサポートされている必要があります。

```
    l - サーバの接続のリストを返します。
        各接続の確立時間、その接続上のトラフィックを Kbyte および各方向のメッセージで表示します。
    m - サーバがサポートする各コマンドの使用回数を返します。
        使用回数が 0 のコマンドは省略できます。
    o - 構成された特権ユーザ、オペレータのリストを返します。
    u - サーバが稼働している時間を示す文字列を返します。
```

また、クライアントやサーバのアクセス設定もこの方法で公開することが推奨されます。

数値返信：

```
        ERR_NOSUCHSERVER
        RPL_STATSLINKINFO                RPL_STATSUPTIME
        RPL_STATSCOMMANDS                RPL_STATSOLINE
        RPL_ENDOFSTATS
```

例：

```
STATS m
    ; 接続中のサーバのコマンド使用状況を確認するためのコマンド
```
