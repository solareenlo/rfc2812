# 3.3.1 Private メッセージ

```
   Command: PRIVMSG
Parameters: <msgtarget> <text to be sent>
```

PRIVMSG は、ユーザ間のプライベートメッセージの送信や、チャネルへのメッセージの送信に使用されます。`<msgtarget>` は通常メッセージの受信者のニックネームか、チャネル名です。

`<msgtarget>` パラメータには、ホストマスク（`#<mask>`）またはサーバマスク（`$<mask>`）を指定することも可能です。どちらの場合も、サーバはそのマスクに一致するサーバやホストを持つ人にのみ PRIVMSG を送ります。マスクには少なくとも1つの `.` を入れなければならず、最後の `.` の後にはワイルドカードを入れてはいけません。 この条件は、`#*` や `$*` にメッセージを送ると、すべてのユーザにブロードキャストされてしまうことを防ぐために存在します。ワイルドカードとは、`*` および `？` 文字のことです。PRIVMSG コマンドのこの拡張機能は、オペレータのみが使用できます。

数値返信：

```
        ERR_NORECIPIENT                 ERR_NOTEXTTOSEND
        ERR_CANNOTSENDTOCHAN            ERR_NOTOPLEVEL
        ERR_WILDTOPLEVEL                ERR_TOOMANYTARGETS
        ERR_NOSUCHNICK
        RPL_AWAY
```

例：

```
:Angel!wings@irc.org PRIVMSG Wiz :Are you receiving this message ?
    ; Angel から Wiz へのメッセージ

PRIVMSG Angel :yes I'm receiving it !
    ; Angel へメッセージを送信するコマンド。

PRIVMSG jto@tolsun.oulu.fi :Hello !
    ; サーバ tolsun.oulu.fi のユーザ名 "jto" のユーザにメッセージを送信するコマンド。

PRIVMSG kalt%millennium.stealth.net@irc.stealth.net :Are you a frog?
    ; サーバ irc.stealth.net のユーザ名 "kalt" のユーザへのメッセージ。
      で、そのユーザはホスト millennium.stealth.net から接続している。

PRIVMSG kalt%millennium.stealth.net :Do you like cheese?
    ; ローカルサーバのユーザ名 "kalt" のユーザへのメッセージ。
      で、そのユーザはホスト millennium.stealth.net から接続している。

PRIVMSG Wiz!jto@tolsun.oulu.fi :Hello !
    ; ホスト tolsun.oulu.fi から接続している
      ニックネーム Wiz、ユーザ名 "jto" のユーザへのメッセージ。

PRIVMSG $*.fi :Server tolsun.oulu.fi rebooting.
    ; サーバ上の *.fi に一致する名前を持つすべての人へのメッセージ。

PRIVMSG #*.edu :NSFNet is undergoing work, expect interruptions
    ; *.edu に一致する名前を持つホストから来たすべてのユーザへのメッセージ。
```
