# 2.5 ワイルドカード表現

文字列の中にワイルドカードが許される場合を "マスク" と呼びます。

文字列のマッチングのために、プロトコルは二つの特殊文字を使うことができます。`?`（`%x3F`）は一文字だけにマッチし、`*`（`%x2A`）は任意の数の任意の文字にマッチすます。これらの2つの文字は、`second`（`%x5C`）という文字を使ってエスケープすることができます。

これを表す拡張 BNF 構文は以下の通りです。

```
    mask       =  *( nowild / noesc wildone / noesc wildmany )
    wildone    =  %x3F
    wildmany   =  %x2A
    nowild     =  %x01-29 / %x2B-3E / %x40-FF
                    ; NUL, "*", "?" 以外の任意のオクテット。
    noesc      =  %x01-5B / %x5D-FF
                    ; NUL と "\" 以外の任意のオクテット。
    matchone   =  %x01-FF
                    ; matches wildone
    matchmany  =  *matchone
                    ; matches wildmany

   Examples:

   a?c         ; "a" で始まり "c" で終わる3文字以内の文字列に一致する。

   a*c         ; "a" で始まり "c" で終わる2文字以上の文字列と一致する。
```
