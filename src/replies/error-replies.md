# 5.2 エラー返信

400 から 599 の範囲にエラー返信が見られます。

```
401    ERR_NOSUCHNICK
      "<nickname> :No such nick/channel"
```

- コマンドに与えられたニックネームパラメータが現在未使用であることを示すために使用されます。

```
402    ERR_NOSUCHSERVER
      "<server name> :No such server"
```

- 指定されたサーバ名が現在存在しないことを示すために使用されます。

```
403    ERR_NOSUCHCHANNEL
      "<channel name> :No such channel"
```

- 与えられたチャネル名が無効であることを示すために使用されます。

```
404    ERR_CANNOTSENDTOCHAN
      "<channel name> :Cannot send to channel"
```

- (a) `mode +n` が設定されているチャネルにいない、または (b) `mode +m` が設定されているチャネルの chanop（または `mode +v`）でない、またはユーザが禁止されていてそのチャネルに PRIVMSG メッセージを送信しようとしているユーザに対して送信されます。

```
405    ERR_TOOMANYCHANNELS
      "<channel name> :You have joined too many channels"
```

- ユーザが許可された最大数のチャネルに参加し、さらに別のチャネルに参加しようとしたときに送信されます。

```
406    ERR_WASNOSUCHNICK
      "<nickname> :There was no such nickname"
```

- WHOWAS により、そのニックネームの履歴情報がないことを示すために返されます。

```
407    ERR_TOOMANYTARGETS
      "<target> :<error code> recipients. <abort message>"
```

- PRIVMSG/NOTICE を user@host の宛先フォーマットで、user@host が複数存在する場合に送信しようとしたクライアントに返されます。

- PRIVMSG/NOTICE をあまりにも多くの受信者に送信しようとしたクライアントに返されます。

- 安全なチャネルに JOIN しようとするクライアントが、そのようなチャネルが複数存在する場合に返されます。

```
408    ERR_NOSUCHSERVICE
      "<service name> :No such service"
```

- 存在しないサービスに対して SQUERY を送信しようとしたクライアントに返されます。

```
409    ERR_NOORIGIN
      ":No origin specified"
```

- PING または PONG メッセージの発信者パラメータがありません。

```
411    ERR_NORECIPIENT
      ":No recipient given (<command>)"
412    ERR_NOTEXTTOSEND
      ":No text to send"
413    ERR_NOTOPLEVEL
      "<mask> :No toplevel domain specified"
414    ERR_WILDTOPLEVEL
      "<mask> :Wildcard in toplevel domain"
415    ERR_BADMASK
      "<mask> :Bad Server/host mask"
```

- 412 - 415は、何らかの理由でメッセージが届かなかったことを示すために PRIVMSG が返すものです。ERR_NOTOPLEVEL と ERR_WILDTOPLEVEL は `PRIVMSG $<server>` または `PRIVMSG #<host>` を不正に使用しようとしたときに返されるエラーです。

```
421    ERR_UNKNOWNCOMMAND
      "<command> :Unknown command"
```

- 送信されたコマンドがサーバによって不明であることを示すために、登録されたクライアントに返されます。

```
422    ERR_NOMOTD
      ":MOTD File is missing"
```

- サーバーの MOTD ファイルを開くことができませんでした。

```
423    ERR_NOADMININFO
      "<server> :No administrative info available"
```

- ADMIN メッセージの応答として、適切な情報の検索に失敗した場合にサーバから返されます。

```
424    ERR_FILEERROR
      ":File error doing <file op> on <file>"
```

- メッセージの処理中にファイル操作の失敗を報告するために使用される一般的なエラーメッセージです。

```
431    ERR_NONICKNAMEGIVEN
      ":No nickname given"
```

- コマンドに期待したニックネームパラメータが見つからなかった場合に返されます。

```
432    ERR_ERRONEUSNICKNAME
      "<nick> :Erroneous nickname"
```

- 定義された文字セットに該当しない文字を含む NICK メッセージを受信した後に返されます。有効なニックネームの詳細については、[2.3.1 項](../the-irc-client-specification/message-format-in-augumented-bnf.md) を参照してください。

```
433    ERR_NICKNAMEINUSE
      "<nick> :Nickname is already in use"
```

- NICK メッセージが処理された結果、現在存在するニックネームを変更しようとしたときに返されます。

```
436    ERR_NICKCOLLISION
      "<nick> :Nickname collision KILL from <user>@<host>"
```

- ニックネームの衝突（他のサーバによってすでに存在する NICK の登録）を検出したときにサーバからクライアントに返されます。

```
437    ERR_UNAVAILRESOURCE
      "<nick/channel> :Nick/channel is temporarily unavailable"
```

- チャネル遅延メカニズムによって現在ブロックされているチャネルに参加しようとするユーザに対してサーバから返されます。

- ニックネーム遅延メカニズムによって希望するニックネームがブロックされた場合に、ニックネームを変更しようとするユーザにサーバから返されます。

```
441    ERR_USERNOTINCHANNEL
      "<nick> <channel> :They aren't on that channel"
```

- コマンドのターゲットユーザが指定されたチャネルにいないことを示すために、サーバから返されます。

```
442    ERR_NOTONCHANNEL
      "<channel> :You're not on that channel"
```

- クライアントがメンバでないチャネルに影響を与えるコマンドを実行しようとしたときに、サーバから返されます。

```
443    ERR_USERONCHANNEL
      "<user> <channel> :is already on channel"
```

- クライアントが、既に参加しているチャネルにユーザを招待しようとしたときに返されます。

```
444    ERR_NOLOGIN
      "<user> :User not logged in"
```

- あるユーザに対する SUMMON コマンドがログインしていないために実行できなかった場合に、SUMMON から返されます。

```
445    ERR_SUMMONDISABLED
      ":SUMMON has been disabled"
```

- SUMMON コマンドの応答として返されます。これを実装していないサーバは必ず返さなければなりません。

```
446    ERR_USERSDISABLED
      ":USERS has been disabled"
```

- USERS コマンドの応答として返されます。これを実装していないサーバは必ず返さなければなりません。

```
451    ERR_NOTREGISTERED
      ":You have not registered"
```

- サーバが返す値で、サーバが詳細な解析を許可する前にクライアントを登録する必要があることを示します。

```
461    ERR_NEEDMOREPARAMS
      "<command> :Not enough parameters"
```

- サーバが多数のコマンドで返すもので、クライアントに十分なパラメータが供給されていないことを示します。

```
462    ERR_ALREADYREGISTRED
      ":Unauthorized command (already registered)"
```

- 2つ目の USER メッセージからパスワードやユーザ情報などの登録情報の一部を変更しようとするリンクに対して、サーバから返されるメッセージです。

```
463    ERR_NOPERMFORHOST
      ":Your host isn't among the privileged"
```

- 接続しようとしたホストからの接続を許可するように設定されていないサーバに登録しようとしたクライアントに返されます。

```
464    ERR_PASSWDMISMATCH
      ":Password incorrect"
```

- パスワードが要求された接続の登録に失敗したことを示すために返されるもので、パスワードが与えられなかったか、不正確であったためです。

```
465    ERR_YOUREBANNEDCREEP
      ":You are banned from this server"
```

- 接続を明示的に拒否するように設定されたサーバに接続し、自分自身を登録しようとした後に返されます。

```
466    ERR_YOUWILLBEBANNED
```

- サーバからユーザに送信され、間もなくサーバへのアクセスが拒否されることを知らせます。

```
467    ERR_KEYSET
      "<channel> :Channel key already set"
471    ERR_CHANNELISFULL
      "<channel> :Cannot join channel (+l)"
472    ERR_UNKNOWNMODE
      "<char> :is unknown mode char to me for <channel>"
473    ERR_INVITEONLYCHAN
      "<channel> :Cannot join channel (+i)"
474    ERR_BANNEDFROMCHAN
      "<channel> :Cannot join channel (+b)"
475    ERR_BADCHANNELKEY
      "<channel> :Cannot join channel (+k)"
476    ERR_BADCHANMASK
      "<channel> :Bad Channel Mask"
477    ERR_NOCHANMODES
      "<channel> :Channel doesn't support modes"
478    ERR_BANLISTFULL
      "<channel> <char> :Channel list is full"

481    ERR_NOPRIVILEGES
      ":Permission Denied- You're not an IRC operator"
```

- 操作にオペレータ権限が必要なコマンドは、試行に失敗したことを示すためにこのエラーを返さなければなりません。

```
482    ERR_CHANOPRIVSNEEDED
      "<channel> :You're not channel operator"
```

- MODE メッセージのような "chanop" 権限を必要とするコマンドは、試行するクライアントが指定されたチャネルの chanop でない場合、このエラーを返さなければなりません。

```
483    ERR_CANTKILLSERVER
      ":You can't kill a server!"
```

- サーバ上で KILL コマンドを使用しようとすると、拒否され、このエラーが直接クライアントに返されます。

```
484    ERR_RESTRICTED
      ":Your connection is restricted!"
```

- 接続時にサーバからユーザに送信され、接続の制限を示します（ユーザモード `+r`）。

```
485    ERR_UNIQOPPRIVSNEEDED
      ":You're not the original channel operator"
```

- "チャネル作成者" 権限を必要とする MODE は、試行するクライアントが指定されたチャネルのチャノップでない場合、このエラーを返さなければなりません。

```
491    ERR_NOOPERHOST
      ":No O-lines for your host"
```

- クライアントが OPER メッセージを送信し、サーバがクライアントのホストからの接続をオペレータとして許可するように設定されていない場合、このエラーを返さなければなりません。

```
501    ERR_UMODEUNKNOWNFLAG
      ":Unknown MODE flag"
```

- ニックネームパラメータを持つ MODE メッセージが送信され、送信されたモードフラグが認識されなかったことを示すためにサーバによって返されます。

```
502    ERR_USERSDONTMATCH
      ":Cannot change mode for other users"
```

- 自分以外のユーザのユーザーモードを表示または変更しようとしたユーザに送られるエラー。
