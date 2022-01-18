# 3.3.2 Notice

```
   Command: NOTICE
Parameters: <msgtarget> <text>
```

NOTICE コマンドは、PRIVMSG と同様に使用されます。NOTICE と PRIVMSG の違いは、NOTICE メッセージに応答して自動返信が決して送られてはならないことです。この規則はサーバにも適用されます。サーバは、NOTICE を受信したときに、クライアントにエラー応答を返してはいけません。このルールの目的は、クライアントが受信した何かに応答して自動的に何かを送るというループを避けることです。

このコマンドは、ユーザだけでなく、サービスでも使用できます。

これは通常、サービスやオートマトン（AI や他の対話型プログラムが行動を制御するクライアント）で使用されます。

返信の詳細および例については、PRIVMSG を参照してください。