# Goのエラーハンドリング



### エラーは基本的にmainまで返そう

- mainに返す場合を考えてみる
  - エラーによって処理を分けられる
    - コンテンツが存在しないなら 404 Not Found など
- mainに返さない場合を考えてみる
  - サーバー内で処理が終わってしまう
    - なにも返されず強制的に502 Internal Server Error が返っちゃったりする



### 実際のエラー処理

https://zenn.dev/nekoshita/articles/097e00c6d3d1c9



スタックトレースが必要かどうかによって変わってくる

- 必要あれば、標準の`errors`パッケージにスタックトレースの機能はないため`pkg/errors`などのライブラリを用いる必要がある
  - また、これには2つの実装パターンがある

- 必要ないのであれば、`fmt.Errorf`を使って単純にエラーメッセージをつなげていくだけで良い



#### pkg/errorsを使った2通りの方法

1. `pkg/errors.WithStack`を使うパターン

2. `pkg/errors.Wrap`を使うパターン



1つ目の方法は`errors.WithStack`を付け忘れがち

2つ目の方法は脳死で書ける



詳細は記事を見てくれ～～

