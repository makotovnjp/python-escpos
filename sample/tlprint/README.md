# タイムラインプリンター

新規性はありません。
いろいろ処理が雑です。以下、雑な点の解説をします。

## ポーリング
* Streaming APIを使おうと思った
* `filter`に日本語(など分かち書きしない言語)を指定するとダメらしい
  * そんなに形態素解析のコストが嫌なのだろうか
  * 含まれているかどうか、だけでも良いのだけれど
  * テレビで見かける「Twitter リアルタイム」みたいなのって、最終的にはNTTデータみたいなFirehoseにアクセス可能な業者と契約して、いろいろやっているのだろうか
* 私は`filter`に日本語を指定するけど、TwitterやNTTデータと契約できるわけない…うーん、どうすれば…
* ポーリング
* 60秒に1回、検索APIを叩く
* まだ印刷していないツイートがあれば、印刷

## リツイートの処理
* `retweeted_status`内のツイートで、印刷したか否かを判定すれば良いのでは？
* ダメでした
* 理由は不明
* `text`が`RT`で始まっていれば、印刷しないことにした
* 取りこぼす可能性もあるが、仕方ない

## アイコン画像
* 取ってくるようにした
* 印刷したら、とても小さくなった
* 別にいいや

## 添付画像
* 複数添付に対応した
* つもりだったが、1枚しか取ってこない
* というか、レスポンスに含まれていない
* 何かパラメータで指定しないとダメなのか
* それとも、サードパーティクライアントの制約なのか
* 別にいいや
