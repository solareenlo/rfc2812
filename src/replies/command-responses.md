# 5.1 コマンド返答

001から099の範囲の数値は、クライアントとサーバの接続にのみ使用され、サーバ間を移動することはありません。コマンドに対する応答として生成されるリプライは、200から399の範囲にあります。

```
001    RPL_WELCOME
       "Welcome to the Internet Relay Network
        <nick>!<user>@<host>"
002    RPL_YOURHOST
       "Your host is <servername>, running version <ver>"
003    RPL_CREATED
       "This server was created <date>"
004    RPL_MYINFO
       "<servername> <version> <available user modes>
        <available channel modes>"
```

- サーバは、登録に成功したユーザに対して、返信001～004を送信します。

```
005    RPL_BOUNCE
       "Try server <server name>, port <port number>"
```

- 代替サーバを提案するために、サーバからユーザに送信されます。これは、サーバがすでに満杯で接続を拒否された場合によく使われます。

```
302    RPL_USERHOST
       ":*1<reply> *( " " <reply> )"
```

- USERHOST がクエリリストの返信を一覧表示するために使用する返信フォーマット。返信文字列は以下のように構成されます。

  `reply = nickname [ "*" ] "=" ( "+" / "-" ) hostname`

  `*` は、クライアントがオペレータとして登録されているかどうかを示します。`-`, `+` は，それぞれクライアントが AWAY メッセージを設定しているか否かを示します。

```
303    RPL_ISON
       ":*1<nick> *( " " <nick> )"
```

- ISON がクエリリストに対する返信を一覧表示するために使用する返信フォーマット。

```
301    RPL_AWAY
       "<nick> :<away message>"
305    RPL_UNAWAY
       ":You are no longer marked as being away"
306    RPL_NOWAWAY
       ":You have been marked as being away"
```

- これらの応答は、AWAY コマンドと一緒に使用されます（許可されている場合）。RPL_AWAY は、離席中のクライアントに PRIVMSG を送信するすべてのクライアントに送信されます。RPL_AWAY は、クライアントが接続されているサーバによってのみ送信されます。応答 RPL_UNAWAY と RPL_NOWAWAY は、クライアントが AWAY メッセージを削除して設定するときに送信されます。

```
311    RPL_WHOISUSER
       "<nick> <user> <host> * :<real name>"
312    RPL_WHOISSERVER
       "<nick> <server> :<server info>"
313    RPL_WHOISOPERATOR
       "<nick> :is an IRC operator"

317    RPL_WHOISIDLE
       "<nick> <integer> :seconds idle"
318    RPL_ENDOFWHOIS
       "<nick> :End of WHOIS list"
319    RPL_WHOISCHANNELS
       "<nick> :*( ( "@" / "+" ) <channel> " " )"
```

- 返信 311 - 313, 317 - 319 は、すべて WHOIS メッセージに応答して生成される返信です。十分な数のパラメータが存在する場合、応答サーバは上記の数値から応答を作成するか（クエリニックが見つかった場合）、エラー応答を返す必要があります。RPL_WHOISUSER の `*` はワイルドカードとしてではなく、リテラル文字として存在します。各返事セットについて、RPL_WHOISCHANNELS だけが複数回現れるかもしれません（チャネル名の長いリストの場合）。チャネル名の横にある `@` と `+` の文字は、クライアントがチャネルオペレータであるか、モデレートされたチャネルで発言する許可を得ているかどうかを示します。RPL_ENDOFWHOIS 応答は、WHOIS メッセージの処理の終了をマークするために使用されます。

```
314    RPL_WHOWASUSER
       "<nick> <user> <host> * :<real name>"
369    RPL_ENDOFWHOWAS
       "<nick> :End of WHOWAS"
```

- WHOWAS メッセージに返信するとき、サーバは提示されたリストの各ニックネームに対して RPL_WHOWASUSER、RPL_WHOISSERVER または ERR_WASNOSUCHNICK の返信を使用しなければなりません。すべての応答バッチの終わりには、たとえ1つの応答しかなく、それがエラーであったとしても、RPL_ENDOFWHOWAS がなければなりません。

```
321    RPL_LISTSTART
       Obsolete. Not used.

322    RPL_LIST
       "<channel> <# visible> :<topic>"
323    RPL_LISTEND
       ":End of LIST"
```

- 返信 RPL_LIST、RPL_LISTENDは、LIST コマンドに対するサーバの応答のデータと終了を伴う実際の返信をマークします。返送可能なチャネルがない場合は、終了応答のみを送信する必要があります。

```
325    RPL_UNIQOPIS
       "<channel> <nickname>"

324    RPL_CHANNELMODEIS
       "<channel> <mode> <mode params>"

331    RPL_NOTOPIC
       "<channel> :No topic is set"
332    RPL_TOPIC
       "<channel> :<topic>"
```

- チャネルのトピックを決定する TOPIC メッセージを送信する場合、2つの返信のうち 1つを送信します。トピックが設定されていれば、RPL_TOPIC が返送され、そうでなければ RPL_NOTOPIC が返送されます。

```
341    RPL_INVITING
       "<channel> <nick>"
```

- 試行された INVITE メッセージが成功し、エンドクライアントに渡されることを示すためにサーバから返されます。

```
342    RPL_SUMMONING
       "<user> :Summoning user to IRC"
```

- SUMMON メッセージに応答したサーバが、そのユーザを呼び出していることを示すために返されます。

```
346    RPL_INVITELIST
       "<channel> <invitemask>"
347    RPL_ENDOFINVITELIST
       "<channel> :End of channel invite list"
```

- 与えられたチャネルの "招待マスク" をリストするとき、サーバは RPL_INVITELIST と RPL_ENDOFINVITELIST メッセージを使用してリストを送り返すことが要求されます。別々の RPL_INVITELIST が各アクティブマスクに対して送信されます。マスクがリストされた後、または1つも存在しない場合、RPL_ENDOFINVITELIST を送信する必要があります。

```
348    RPL_EXCEPTLIST
       "<channel> <exceptionmask>"
349    RPL_ENDOFEXCEPTLIST
       "<channel> :End of channel exception list"
```

- 与えられたチャネルの "例外マスク" をリストするとき、サーバは RPL_EXCEPTLIST および RPL_ENDOFEXCEPTLIST メッセージを使用してリストを送り返すことが要求されます。アクティブなマスクごとに個別の RPL_EXCEPTLIST が送信されます。マスクがリストアップされた後、または1つも存在しない場合は、RPL_ENDOFEXCEPTLIST を送信する必要があります。

```
351    RPL_VERSION
       "<version>.<debuglevel> <server> :<comments>"
```

- サーバがそのバージョンの詳細を示す返信。`<version>` はパッチレベルのリビジョンを含む使用中のソフトウェアのバージョンで、`<debuglevel>` はサーバが "デバッグモード" で動作しているかどうかを示すために使用されます。

  "comments" 欄には、バージョンに関するコメントや、さらなるバージョンに関する詳細情報を入力することができます。

```
352    RPL_WHOREPLY
       "<channel> <user> <host> <server> <nick>
       ( "H" / "G" > ["*"] [ ( "@" / "+" ) ]
       :<hopcount> <real name>"

315    RPL_ENDOFWHO
       "<name> :End of WHO list"
```

- RPL_WHOREPLY と RPL_ENDOFWHO のペアは、WHO メッセージに答えるために使用されます。RPL_WHOREPLY は、WHO クエリに適切なマッチがある場合にのみ送信されます。WHO メッセージで供給されるパラメータのリストがある場合、`<name>` を項目とする各リスト項目を処理した後に RPL_ENDOFWHO を送信する必要があります。

```
353    RPL_NAMREPLY
       "( "=" / "*" / "@" ) <channel>
        :[ "@" / "+" ] <nick> *( " " [ "@" / "+" ] <nick> )
  - "@" is used for secret channels, "*" for private
    channels, and "=" for others (public channels).

366    RPL_ENDOFNAMES
       "<channel> :End of NAMES list"
```

- NAMES メッセージに返信するために、RPL_NAMREPLY と RPL_ENDOFNAMES からなる返信ペアがサーバからクライアントに返送されます。クエリのように見つかったチャネルがない場合、RPL_ENDOFNAMES だけが返されます。この例外は、NAMES メッセージがパラメータなしで送信され、すべての可視チャネルとコンテンツが一連の RPL_NAMEREPLY メッセージで送り返され、RPL_ENDOFNAMES で終了をマークする場合です。

```
364    RPL_LINKS
       "<mask> <server> :<hopcount> <server info>"
365    RPL_ENDOFLINKS
       "<mask> :End of LINKS list"
```

- LINKS メッセージに返信する際、サーバは RPL_LINKS 数値を使用して返信を送り、RPL_ENDOFLINKS 返信を使用してリストの終わりをマークしなければなりません。

```
367    RPL_BANLIST
       "<channel> <banmask>"
368    RPL_ENDOFBANLIST
       "<channel> :End of channel ban list"
```

- 特定のチャネルのアクティブな "禁止" をリストアップする場合、サーバは RPL_BANLIST と RPL_ENDOFBANLIST メッセージを使用してリストを送り返すことが要求されます。アクティブな禁止マスクごとに別々の RPL_BANLIST が送信されます。禁止マスクがリストアップされた後、または1つも存在しない場合は、RPL_ENDOFBANLIST を送信する必要があります。

```
371    RPL_INFO
       ":<string>"
374    RPL_ENDOFINFO
       ":End of INFO list"
```

- INFO メッセージに応答するサーバは、そのすべての "info" を一連の RPL_INFO メッセージで送信し、返信の終わりを示すために RPL_ENDOFINFO 返信をすることが要求されます。

```
375    RPL_MOTDSTART
       ":- <server> Message of the day - "
372    RPL_MOTD
       ":- <text>"
376    RPL_ENDOFMOTD
       ":End of MOTD command"
```

- MOTD メッセージに応答し、MOTD ファイルが見つかった場合、RPL_MOTD 形式の返信で、1行80文字以内で1行ずつ表示されます。これらは、RPL_MOTD の前に RPL_MOTDSTART、後に RPL_ENDOFMOTD で囲む必要があります。

```
381    RPL_YOUREOPER
       ":You are now an IRC operator"
```

- RPL_YOUREOPER は、OPER メッセージを正常に発行し、オペレータ・ステータスを得たばかりのクライアントに返送されます。

```
382    RPL_REHASHING
       "<config file> :Rehashing"
```

- REHASH オプションが使用され、オペレータが REHASH メッセージを送信する場合、RPL_REHASHING がオペレータに返送されます。

```
383    RPL_YOURESERVICE
       "You are service <servicename>"
```

- 登録に成功したときにサーバからサービスに送信されます。

```
391    RPL_TIME
       "<server> :<string showing server's local time>"
```

- TIME メッセージに返信する場合、サーバは上記の RPL_TIME 形式を使用して返信を送信する必要があります。時刻を示す文字列は、そこに正しい曜日と時刻を含むだけでよいです。時刻を示す文字列には、それ以上の要件はありません。

```
392    RPL_USERSSTART
       ":UserID   Terminal  Host"
393    RPL_USERS
       ":<username> <ttyline> <hostname>"
394    RPL_ENDOFUSERS
       ":End of users"
395    RPL_NOUSERS
       ":Nobody logged in"
```

- USERS メッセージがサーバによって処理される場合、応答 RPL_USERSTART、RPL_USERS、RPL_ENDOFUSERS、RPL_NOUSERS が使用されます。RPL_USERSSTART を最初に送信し、その後に一連の RPL_USERS または単一の RPL_NOUSER のいずれかを送信する必要があります。これに続くのは RPL_ENDOFUSERS です。

```
200    RPL_TRACELINK
       "Link <version & debug level> <destination>
        <next server> V<protocol version>
        <link uptime in seconds> <backstream sendq>
        <upstream sendq>"
201    RPL_TRACECONNECTING
       "Try. <class> <server>"
202    RPL_TRACEHANDSHAKE
       "H.S. <class> <server>"
203    RPL_TRACEUNKNOWN
       "???? <class> [<client IP address in dot form>]"
204    RPL_TRACEOPERATOR
       "Oper <class> <nick>"
205    RPL_TRACEUSER
       "User <class> <nick>"
206    RPL_TRACESERVER
       "Serv <class> <int>S <int>C <server>
        <nick!user|*!*>@<host|server> V<protocol version>"
207    RPL_TRACESERVICE
       "Service <class> <name> <type> <active type>"
208    RPL_TRACENEWTYPE
       "<newtype> 0 <client name>"
209    RPL_TRACECLASS
       "Class <class> <count>"
210    RPL_TRACERECONNECT
       Unused.
261    RPL_TRACELOG
       "File <logfile> <debug level>"
262    RPL_TRACEEND
       "<server name> <version & debug level> :End of TRACE"
```

- `RPL_TRACE*` はすべて TRACE メッセージに応答してサーバから返されます。いくつ返されるかは、TRACE メッセージとそれがオペレータによって送信されたかどうかに依存します。どれが最初に起こるか、あらかじめ定義された順序はありません。リプライ RPL_TRACEUNKNOWN、RPL_TRACECONNECTING、RPL_TRACEHANDSHAKE はすべて、完全に確立されていない接続、不明、まだ接続しようとしている、または "サーバハンドシェイク" の完了プロセスのいずれかに使用されています。RPL_TRACELINK は、TRACE メッセージを処理し、それを別のサーバに渡す必要があるすべてのサーバによって送信されます。IRC ネットワーク を横断する TRACE コマンドに応答して送信される RPL_TRACELINK のリストは、その経路に沿ったサーバ自身の実際の接続性を反映する必要があります。RPL_TRACENEWTYPE は、他のカテゴリに当てはまらないが、とにかく表示される接続に使用されます。RPL_TRACEEND は、リストの終わりを示すために送信されます。

```
211    RPL_STATSLINKINFO
       "<linkname> <sendq> <sent messages>
        <sent Kbytes> <received messages>
        <received Kbytes> <time open>"
```

- 接続に関する統計情報を報告します。`<linkname>` は特定の接続を識別し、`<sendq>` はキューに入れられ送信待ちのデータ量、`<sent messages>` は送信したメッセージ数、`<sent Kbytes>` は送信データ量（Kbytes 単位）を表わします。`<received messages>` と `<received Kbytes>` は、それぞれ受信データの `<sent messages>` と `<sent Kbytes>` に相当します。`<time open>` は、接続が開かれてから何日経ったかを秒単位で示します。

```
212    RPL_STATSCOMMANDS
       "<command> <count> <byte count> <remote count>"
```

- コマンドの使用に関する統計情報を報告します。

```
219    RPL_ENDOFSTATS
       "<stats letter> :End of STATS report"

242    RPL_STATSUPTIME
       ":Server Up %d days %d:%02d:%02d"
```

- サーバーの稼働時間を報告します。

```
243    RPL_STATSOLINE
       "O <hostmask> * <name>"
```

- ユーザが IRC オペレータになることを許可するホストを報告します。

```
221    RPL_UMODEIS
       "<user mode string>"
```

- クライアント自身のモードに関するクエリに答えるために、RPL_UMODEIS が返送されます。

```
234    RPL_SERVLIST
       "<name> <server> <mask> <type> <hopcount> <info>"

235    RPL_SERVLISTEND
       "<mask> <type> :End of service listing"
```

- SERVLIST メッセージに応答してサービスをリストアップするとき、サーバは RPL_SERVLIST と RPL_SERVLISTEND メッセージを使用してリストを送り返すことが要求されます。各サービスに対して別々の RPL_SERVLIST が送信されます。サービスがリストアップされた後、または何も存在しない場合は、RPL_SERVLISTEND を送信する必要があります。

```
251    RPL_LUSERCLIENT
       ":There are <integer> users and <integer>
        services on <integer> servers"
252    RPL_LUSEROP
       "<integer> :operator(s) online"
253    RPL_LUSERUNKNOWN
       "<integer> :unknown connection(s)"
254    RPL_LUSERCHANNELS
       "<integer> :channels formed"
255    RPL_LUSERME
       ":I have <integer> clients and <integer>
         servers"
```

- LUSERS メッセージの処理では、サーバは RPL_LUSERCLIENT、RPL_LUSEROP、RPL_USERUNKNOWN、RPL_LUSERCHANNELS および RPL_LUSERME から一式の応答を送信します。返信するとき、サーバは RPL_LUSERCLIENT と RPL_LUSERME を送り返さなければなりません。他の返信は、それらにゼロでないカウントが見つかった場合にのみ送り返されます。

```
256    RPL_ADMINME
       "<server> :Administrative info"
257    RPL_ADMINLOC1
       ":<admin info>"
258    RPL_ADMINLOC2
       ":<admin info>"
259    RPL_ADMINEMAIL
       ":<admin info>"
```

- ADMIN メッセージに返信する場合、サーバは RPL_ADMINME から RPL_ADMINEMAIL までの返信を使用し、それぞれにテキストメッセージを提供することが期待されています。RPL_ADMINLOC1 には、サーバがある都市、州、国の説明が期待され、次に機関の詳細 RPL_ADMINLOC2、最後にサーバの管理連絡先 RPL_ADMINEMAIL にはメールアドレスが必要です。

```
263    RPL_TRYAGAIN
       "<command> :Please wait a while and try again."
```

- サーバがコマンドを処理せずにドロップした場合、応答 RPL_TRYAGAIN を使用して発信元クライアントに通知する必要があります。
