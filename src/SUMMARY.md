# Summary

[Home](./index.md)

- [ラベル](./labels/index.md)
  - [サーバ](./labels/servers.md)
  - [クライアント](./labels/clients.md)
    - [ユーザ](./labels/users.md)
      - [オペレータ](./labels/operators.md)
    - [サービス](./labels/services.md)
  - [チャネル](./labels/channels.md)
- [IRC クライアント仕様](./the-irc-client-specification/index.md)
  - [概要](./the-irc-client-specification/overview.md)
  - [文字コード](./the-irc-client-specification/character-codes.md)
  - [メッセージ](./the-irc-client-specification/messages.md)
    - [拡張 BNF によるメッセージフォーマット](./the-irc-client-specification/message-format-in-augumented-bnf.md)
  - [数値返信](./the-irc-client-specification/numeric-replies.md)
  - [ワイルドカード表現](./the-irc-client-specification/wildcard-expressions.md)
- [メッセージの詳細](./message-details/index.md)
  - [コネクション登録](./message-details/connection-registration.md)
    - [Password メッセージ](./message-details/password-message.md)
    - [Nick メッセージ](./message-details/nick-message.md)
    - [User メッセージ](./message-details/user-message.md)
    - [Oper メッセージ](./message-details/oper-message.md)
    - [User モードメッセージ](./message-details/user-mode-message.md)
    - [Service メッセージ](./message-details/service-message.md)
    - [Quit](./message-details/quit.md)
    - [Squit](./message-details/squit.md)
  - [チャネル操作](./message-details/channel-operations.md)
    - [Join メッセージ](./message-details/join-message.md)
    - [Part メッセージ](./message-details/part-message.md)
    - [Channel モードメッセージ](./message-details/channel-mode-message.md)
    - [Topic メッセージ](./message-details/topic-message.md)
    - [Names メッセージ](./message-details/names-message.md)
    - [List メッセージ](./message-details/list-message.md)
    - [Invite メッセージ](./message-details/invite-message.md)
    - [Kick コマンド](./message-details/kick-command.md)
  - [メッセージの送信](./message-details/sending-messages.md)
    - [Private メッセージ](./message-details/private-messages.md)
    - [Notice](./message-details/notice.md)
  - [サーバへのクエリとコマンド](./message-details/server-queries-and-commands.md)
    - [Motd メッセージ](./message-details/motd-message.md)
    - [Lusers メッセージ](./message-details/lusers-message.md)
    - [Version メッセージ](./message-details/version-message.md)
    - [Stats メッセージ](./message-details/stats-message.md)
    - [Links メッセージ](./message-details/links-message.md)
    - [Time メッセージ](./message-details/time-message.md)
    - [Connect メッセージ](./message-details/connect-message.md)
    - [Trace メッセージ](./message-details/trace-message.md)
    - [Admin コマンド](./message-details/admin-command.md)
    - [Info コマンド](./message-details/info-command.md)
  - [サービスへのクエリとコマンド](./message-details/service-query-and-commands.md)
    - [Servlist メッセージ](./message-details/servlist-message.md)
    - [Squery](./message-details/squery.md)
  - [ユーザベースのクエリ](./message-details/user-based-queries.md)
    - [Who クエリ](./message-details/who-query.md)
    - [Whois クエリ](./message-details/whois-query.md)
    - [Whowas](./message-details/whowas.md)
  - [その他のメッセージ](./message-details/miscellaneous-messages.md)
    - [Kill メッセージ](./message-details/kill-message.md)
    - [Ping メッセージ](./message-details/ping-message.md)
    - [Pong メッセージ](./message-details/pong-message.md)
    - [Error](./message-details/error.md)
- [オプション機能](./optional-features/index.md)
  - [Away](./optional-features/away.md)
  - [Rehash メッセージ](./optional-features/rehash-message.md)
  - [Die メッセージ](./optional-features/die-message.md)
  - [Restart メッセージ](./optional-features/restart-message.md)
  - [Summon メッセージ](./optional-features/summon-message.md)
  - [Users](./optional-features/users.md)
  - [Operwall メッセージ](./optional-features/operwall-message.md)
  - [Userhost メッセージ](./optional-features/userhost-message.md)
  - [Ison メッセージ](./optional-features/ison-message.md)
- [返信](./replies/index.md)
  - [コマンド返答](./replies/command-responses.md)
  - [エラー返信](./replies/error-replies.md)
  - [予約済み数値](./replies/reserved-numerics.md)
- [現在の実装](./current-implementations/index.md)
- [現在の問題点](./current-problems/index.md)
  - [ニックネーム](./current-problems/nicknames.md)
  - [ワイルドカードの制限](./current-problems/limitation-of-wildcards.md)
  - [セキュリティへの配慮](./current-problems/security-considerations.md)
- [現在のサポートと可用性](./current-support-and-availability/index.md)
- [謝辞](./acknowledgements/index.md)
- [参考](./references/index.md)
- [Author's Address](./authors-address/index.md)
- [Full Copyright Statement](./full-copyright-statement/index.md)