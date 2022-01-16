# 3. メッセージの詳細

次のページでは、IRC サーバとクライアントが認識する各メッセージについて説明します。この章で説明されているすべてのコマンドは、このプロトコルのすべてのサーバで実装されている必要があります。

ERR_NOSUCHSERVER が返信された場合、メッセージのターゲットが見つからなかったことを意味します。サーバは、このエラー以降、そのコマンドに対して他の応答を送ってはなりません。

クライアントが接続されているサーバは、メッセージ全体を解析し、適切なエラーを返すことが要求されます。

複数のパラメータが提示された場合、それぞれのパラメータの有効性を確認し、適切なレスポンスをクライアントに返さなければなりません。カンマで区切られたパラメータリストを使用した不正なメッセージの場合、各項目に対して応答を送信しなければなりません。