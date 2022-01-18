# 3.4.8 Trace メッセージ

```
   Command: TRACE
Parameters: [ <target> ]
```

TRACE コマンドは、特定のサーバへの経路とそのピアの情報を見つけるために使用されます。このコマンドを処理した各サーバは、送信者にそのことを報告しなければなりません。パススルー・リンクからの応答は連鎖を形成し、目的地までの経路を示します。この応答を返した後、与えられた `<target>` サーバに到達するまで、次のサーバに問い合わせを送信する必要があります。

TRACE コマンドは、特定のサーバへの経路を検索するために使用されます。このメッセージを処理する各サーバは、パススルーリンクであることを示す応答を送信して送信者に伝え、応答の連鎖を形成する必要があります。この応答を返した後、指定されたサーバに到達するまで、次のサーバに TRACE メッセージを送信しなければなりません。`<target>` パラメータが省略された場合、TRACE コマンドはローカルサーバがどのサーバに直接接続しているかを示すメッセージを送信者に送信することを推奨します。

`<target>` で指定された宛先が実際のサーバの場合、宛先サーバは接続されている全てのサーバ、サービス、オペレータを報告する必要があります。オペレータによってコマンドが発行された場合、サーバは接続されている全てのユーザを報告してもかまいません。`<target>` で指定された宛先がニックネームの場合、そのニックネームに対する応答のみが返されます。`<target>` パラメータが省略された場合、TRACE コマンドは処理中のサーバをターゲットとして解析されることが推奨されます。

`<target>` パラメータには、ワイルドカードを使用できます。

数値返信：

```
        ERR_NOSUCHSERVER
```

TRACE メッセージが他のサーバに向けられた場合、すべての中間サーバは RPL_TRACELINK 応答を返して、TRACE がそれを通過したことと次の行き先を示さなければなりません。

```
        RPL_TRACELINK
```

   TRACE 応答は、以下の数値応答からいくつでも構成することができます。

```
        RPL_TRACECONNECTING           RPL_TRACEHANDSHAKE
        RPL_TRACEUNKNOWN              RPL_TRACEOPERATOR
        RPL_TRACEUSER                 RPL_TRACESERVER
        RPL_TRACESERVICE              RPL_TRACENEWTYPE
        RPL_TRACECLASS                RPL_TRACELOG
        RPL_TRACEEND
```

例：

```
TRACE *.oulu.fi
    ; *.oulu.fi に一致するサーバーへの TRACE
```