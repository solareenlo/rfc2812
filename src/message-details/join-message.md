# 3.2.1 Join メッセージ

```
   Command: JOIN
Parameters: ( <channel> *( "," <channel> ) [ <key> *( "," <key> ) ] )
            / "0"
```

JOIN コマンドは、ユーザが特定のチャネルのリスニング開始を要求するために使用されます。サーバは、ターゲットのリスト形式で引数をパースできなければなりませんが、クライアントに JOIN メッセージを送るときには、リストを使うべきではありません。

ユーザがチャネルに参加すると、そのチャネルに影響するサーバが受け取るすべてのコマンドに関する情報を受け取ります。これには、JOIN、MODE、KICK、PART、QUIT、そしてもちろん PRIVMSG/NOTICE が含まれます。これにより、チャネルのメンバは、他のチャネルメンバやチャネルモードを把握することができます。

JOIN が成功した場合、ユーザは確認として JOIN メッセージを受け取り、次に RPL_TOPIC を使用してチャネルのトピックを、RPL_NAMREPLY を使用してチャネルに参加しているユーザのリストを送信します（これには参加ユーザを含める必要があります）。

このメッセージは特別な引数（`0`）を受け取ることに注意してください。これは、ユーザが現在所属しているすべてのチャネルから退出するための特別な要求です。サーバはこのメッセージを、あたかもユーザがメンバである各チャネルに対して PART コマンド（[3.2.2 節](./part-message.md) を参照) を送信したかのように処理します。

数値返信：

```
        ERR_NEEDMOREPARAMS              ERR_BANNEDFROMCHAN
        ERR_INVITEONLYCHAN              ERR_BADCHANNELKEY
        ERR_CHANNELISFULL               ERR_BADCHANMASK
        ERR_NOSUCHCHANNEL               ERR_TOOMANYCHANNELS
        ERR_TOOMANYTARGETS              ERR_UNAVAILRESOURCE
        RPL_TOPIC
```

例：

```
JOIN #foobar
    ; チャネル #foobar に参加するコマンド。


JOIN &foo fubar
    ; キー "fubar "を使ってチャネル "&foo" に参加するコマンド。

JOIN #foo,&bar fubar
    ; キー "fubar" を使ってチャネル #foo に、キー無しで &bar に参加するコマンド。

JOIN #foo,#bar fubar,foobar
    ; キー "fubar" を使ってチャネル #foo に、
      キー "foobar" を使ってチャネル #bar に参加するコマンド。

JOIN #foo,#bar
    ; チャネル #foo と #bar に参加するコマンド。

JOIN 0
    ; 現在参加しているすべてのチャネルを去るコマンド。


:WiZ!jto@tolsun.oulu.fi JOIN #Twilight_zone
    ; WiZ からのチャンネル #Twilight_zone への JOIN メッセージ。
```
