# 3.6.3 Whowas

```
   Command: WHOWAS
Parameters: <nickname> *( "," <nickname> ) [ <count> [ <target> ] ]
```

WHOWAS は、もう存在しないニックネームに関する情報を要求します。これはニックネームの変更か、ユーザが IRC を去ったかのどちらかでしょう。この問い合わせに対して、サーバはニックネームの履歴を検索し、字句的に同じニックネームを探します（ここではワイルドカードによるマッチングは 行なわれません）。履歴は後方から検索され、最新のエントリが最初に返されます。複数のエントリがある場合は、`<count>` 個までの返答が返されます（`<count>` パラメータが与えられていない場合は、それらすべてが返されます）。`<count>` として正でない数字が渡された場合、完全な検索が行われます。

`<target>` パラメータには、ワイルドカードを使用できます。

数値返信：

```
        ERR_NONICKNAMEGIVEN           ERR_WASNOSUCHNICK
        RPL_WHOWASUSER                RPL_WHOISSERVER
        RPL_ENDOFWHOWAS
```

例：

```
WHOWAS Wiz
    ; ニックネーム "WiZ" に関するニックネーム履歴の全ての情報を返します。


WHOWAS Mermaid 9
    ; "Mermaid" のニックネーム履歴のうち、最大で最新の9件を返します。

WHOWAS Trillian 1 *.edu
    ; "Trillian" の最新の履歴を、"*.edu" にマッチする最初に見つかったサーバから返します。
```
