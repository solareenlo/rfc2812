# 2.3.1 拡張 BNF によるメッセージフォーマット

プロトコルメッセージは、オクテットの連続したストリームから抽出されなければなりません。現在の解決策は、CR と LF という2つの文字をメッセージのセパレータとして指定することです。空のメッセージは黙って無視されるので、メッセージ間で CR-LF のシーケンスが余分な問題なく使用できるようになります。

抽出されたメッセージは、`<prefix>`、`<command>`、パラメータのリスト（`<params>`）という構成要素にパースされます。

これに対する拡張 BNF 表現は以下の通りです。

```
    message    =  [ ":" prefix SPACE ] command [ params ] crlf
    prefix     =  servername / ( nickname [ [ "!" user ] "@" host ] )
    command    =  1*letter / 3digit
    params     =  *14( SPACE middle ) [ SPACE ":" trailing ]
               =/ 14( SPACE middle ) [ SPACE [ ":" ] trailing ]

    nospcrlfcl =  %x01-09 / %x0B-0C / %x0E-1F / %x21-39 / %x3B-FF
                    ; any octet except NUL, CR, LF, " " and ":"
    middle     =  nospcrlfcl *( ":" / nospcrlfcl )
    trailing   =  *( ":" / " " / nospcrlfcl )

    SPACE      =  %x20        ; space character
    crlf       =  %x0D %x0A   ; "carriage return" "linefeed"
```

NOTES:
1) パラメータリスト抽出後、`<middle>` と `<trailing>` のどちらでマッチしても、すべてのパラメータは等しくなります。`<trailing>` は、パラメータ内のスペースを許容するための構文上のトリックに過ぎません。

2) `NUL`（`%x00`）文字は、メッセージのフレーム化において特別なものではなく、基本的にパラメーターの中に入ってしまう可能性があります。しかし、通常の C 言語の文字列処理では余計な複雑さを引き起こすことになります。したがって、`NUL` はメッセージ内では使用できません。

ほとんどのプロトコルメッセージは、リスト内の位置によって、抽出されたパラメータ文字列の追加のセマンティクスとシンタックスを指定しています。例えば、多くのサーバコマンドは、コマンドの後の最初のパラメータがターゲットのリストであると仮定し、これを記述することができます。

```
  target     =  nickname / server
  msgtarget  =  msgto *( "," msgto )
  msgto      =  channel / ( user [ "%" host ] "@" servername )
  msgto      =/ ( user "%" host ) / targetmask
  msgto      =/ nickname / ( nickname "!" user "@" host )
  channel    =  ( "#" / "+" / ( "!" channelid ) / "&" ) chanstring
                [ ":" chanstring ]
  servername =  hostname
  host       =  hostname / hostaddr
  hostname   =  shortname *( "." shortname )
  shortname  =  ( letter / digit ) *( letter / digit / "-" )
                *( letter / digit )
                  ; as specified in RFC 1123 [HNAME]
  hostaddr   =  ip4addr / ip6addr
  ip4addr    =  1*3digit "." 1*3digit "." 1*3digit "." 1*3digit
  ip6addr    =  1*hexdigit 7( ":" 1*hexdigit )
  ip6addr    =/ "0:0:0:0:0:" ( "0" / "FFFF" ) ":" ip4addr
  nickname   =  ( letter / special ) *8( letter / digit / special / "-" )
  targetmask =  ( "$" / "#" ) mask
                  ; see details on allowed masks in section 3.3.1
  chanstring =  %x01-07 / %x08-09 / %x0B-0C / %x0E-1F / %x21-2B
  chanstring =/ %x2D-39 / %x3B-FF
                  ; any octet except NUL, BELL, CR, LF, " ", "," and ":"
  channelid  = 5( %x41-5A / digit )   ; 5( A-Z / 0-9 )

  Other parameter syntaxes are:

  user       =  1*( %x01-09 / %x0B-0C / %x0E-1F / %x21-3F / %x41-FF )
                  ; any octet except NUL, CR, LF, " " and "@"
  key        =  1*23( %x01-05 / %x07-08 / %x0C / %x0E-1F / %x21-7F )
                  ; any 7-bit US_ASCII character,
                  ; except NUL, CR, LF, FF, h/v TABs, and " "
  letter     =  %x41-5A / %x61-7A       ; A-Z / a-z
  digit      =  %x30-39                 ; 0-9
  hexdigit   =  digit / "A" / "B" / "C" / "D" / "E" / "F"
  special    =  %x5B-60 / %x7B-7D
                   ; "[", "]", "\", "`", "_", "^", "{", "|", "}"
```

NOTES:
1) `<hostaddr>` 構文は、IP アドレスのために従うべき形式を示すことのみを目的としてここで与えられています。これは、このプロトコルの唯一の実装が、基礎となるネットワークプロトコルとして TCP/IP を使用しているという事実を反映していますが、他のプロトコルを使用することを妨げるものではありません。

2) `<hostname>` の長さは最大63文字です。これは、(特に)インターネット上のホスト名が長くなる可能性があるため、プロトコルの制限事項となっています。IRC のメッセージは512文字に制限されているため、このような制限が必要なのです。63文字より長いホスト名から接続するクライアントは、ホスト名ではなく、ホスト（数字）アドレスを使って登録されます。

3) このドキュメントの以下の章で使用されるいくつかのパラメータは、便宜上使用されている名前以外、特に何もないため、ここでは定義されていません。これらのパラメータは、`<params>` に定義された一般的な構文に従います。
