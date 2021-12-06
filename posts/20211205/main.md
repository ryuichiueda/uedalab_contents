---
Keywords: つくばチャレンジ
Copyright: (C) 2021 Tatsuhiro Ikebe
---

# つくばチャレンジ2021に参加した話

執筆: B4池邉

## はじめに
今年から初めて[つくばチャレンジ](https://tsukubachallenge.jp/2021/)に参加しました。
つくばチャレンジの会場には様々な自律移動ロボットをたくさん見たり、
参加者の方と自律移動についての技術トークができたり、とても刺激を受けました。


今回、初参加ということで色々なことを試してみました。結果的に信号あり横断歩道まで走行することができました！
<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">本走行は、スタートから信号あり横断歩道まで走行しました。<a href="https://t.co/fZF7aQIi54">https://t.co/fZF7aQIi54</a></p>&mdash; BEIKE (@BEIKE_RE) <a href="https://twitter.com/BEIKE_RE/status/1462623996461998083?ref_src=twsrc%5Etfw">November 22, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 

ということで、つくばチャレンジで試したことなどについて話していきます。

## つくばチャレンジ2021に参加した目的

つくばチャレンジでは、センサをたくさん載せたりしてツヨツヨに強化した機体がよく見られます。
例えば、GNSSやIMUや3D LiDARや色々なカメラや2D LiDAR複数搭載などです。
また、機体のサイズも大きいものが多いような気がします。確かに、ホイールのサイズが大きいと走破性があって安定します。

しかし、あえて私たちのチームは最小構成(2D LiDARのみ)で小型である移動ロボットを使用しています。
その理由は、上記のロボットを使用して出てくる問題に対して、ソフトウェアで実装して対応できるものであれば対応しようというモットーのもとやっているからです。
なので、最小構成で小型である移動ロボットでどこまで走行できるかチャレンジしてみることを目的としました。

## 使用した機体について

つくばチャレンジ2021に参加するために[Raspberry Pi Cat](https://rt-net.jp/products/raspberry-pi-cat/)という機体を使用しました。
つくばチャレンジ2021に参加している機体の中でも小型です。
つくばチャレンジに参加するためには[機体の仕様条件として高さが0.6mである](https://tsukubachallenge.jp/2021/regulations/specs#:~:text=%E5%85%A8%E9%AB%98%3A0.6%20m%20%E4%BB%A5%E4%B8%8A%E3%80%811.8%20m%20%E4%BB%A5%E4%B8%8B)のと
[非常停止スイッチがどこからでも押せる](https://tsukubachallenge.jp/2021/regulations/specs#:~:text=%E4%BB%95%E6%A7%98-,%E3%81%A9%E3%81%AE%E6%96%B9%E5%90%91%E3%81%8B%E3%82%89,%E3%81%A4%E3%81%A7%E3%82%82%E8%89%AF%E3%81%84,-%E9%9D%9E%E5%B8%B8%E5%81%9C%E6%AD%A2%E3%82%B9%E3%82%A4%E3%83%83%E3%83%81)必要があります。
なのでアルミフレームを追加して高さ増しをして非常停止スイッチの位置も変更しました。

![](raspicat.png)

注：写真ではRealSenseが搭載されてますが、本走行では使用していません。

## つくばチャレンジ2021で試したこと

つくばチャレンジ2021に参加して色々なことを試しました。
その中でも試してよかったことについて4つほど話します。

### 2D LiDARの位置調整

「ソフトウェアで何でも解決させると言っておきながら調整してるんかい！」と思う方がいるかもしれませんが、流石に許してください。
安定した自己位置推定を行うためにランドマークを獲得することは重要です。
なので、どの高さの位置に2D LiDARを設置するべきなのか現地で計測して最適な値を導きました。(多分)

花壇やベンチの高さを計測した所、地面から45cmぐらいの高さに2D LiDARを設置すると、
花壇やベンチをマップに含ませることができます。マップに含まれるということは走行中に観測ができるということです。

[![Image from Gyazo](https://i.gyazo.com/ad2c5bf6b34a1fcb4c9ecf015a2a2c2e.png)](https://gyazo.com/ad2c5bf6b34a1fcb4c9ecf015a2a2c2e)

[![Image from Gyazo](https://i.gyazo.com/2cd2d5f2c0b0d3b1aa5a4355cf886dc7.png)](https://gyazo.com/2cd2d5f2c0b0d3b1aa5a4355cf886dc7)


### マッピング・自己位置推定テスト用のシステム作成

マッピングや自己位置推定のテストをチームメンバーが簡単にできれば良いなと思ったので、システムを作りました。これのおかげでマッピングや自己位置推定のテストを他のメンバーに任せることができました。

DockerとROSがインストールされていれば、実行することができます。
rosbagは[google driveで管理されていて](https://drive.google.com/drive/u/2/folders/10M9LNWEwlFVunHTv-vx0vhNK5xqopGc_)実行したいrosbagを選択すれば使用することができます。

[![raspicat_rosbag](https://i.gyazo.com/16b79a35eb0fcdb3aaf48630f091238a.png)](https://github.com/uhobeike/raspicat_rosbag)

### 合成したマップの使用

本走行2日前に確認走行エリアを完走しました。
その時、確認走行エリアの分のマップ作成は終わっていましたが確認走行エリア以降から信号あり横断歩道までのマップは未完成でした。
rosbagを取る時間やいちから地図生成を行う時間の無駄を考え、確認走行エリアの分のマップは実際に完走できたマップであることから再利用した方が良いと考えました。

そこでGIMPを使用してマップの合成を行いました。
確認走行エリアのマップと確認走行エリア以降から信号あり横断歩道までのマップを合成しました。

[![Image from Gyazo](https://i.gyazo.com/e25677773b28d90ca6ebdb861d664fba.png)](https://gyazo.com/e25677773b28d90ca6ebdb861d664fba)

[![Image from Gyazo](https://i.gyazo.com/1bc66ee5e67560cf4b59c0fdf5acf690.png)](https://gyazo.com/1bc66ee5e67560cf4b59c0fdf5acf690)

[![Image from Gyazo](https://i.gyazo.com/1bc2ce46f6774d5539f759d626a33f8f.png)](https://gyazo.com/1bc2ce46f6774d5539f759d626a33f8f)


### 自己位置推定用と経路計画用にマップを分ける

期待通りの経路計画を行ってくれるようにマップの編集を行いました。

当然、過度に編集したマップは自己位置推定に使用すると支障を来すので[別々にする必要](https://github.com/uhobeike/raspicat_navigation/blob/832165b142f9460742062f679fcc6eaf3a092244/launch/raspicat_navigation.launch#L18-L24)があります。

何が期待通りかというと、以下の写真のように線で囲まれた範囲内でしか経路計画が行われないということです。線の範囲外に行くとロボットがスタックする可能性があるので線の範囲内で走行するようにマップを以下の写真のように編集しました。

[![Image from Gyazo](https://i.gyazo.com/ba83a3216c5dce219c0864107455e57f.png)](https://gyazo.com/ba83a3216c5dce219c0864107455e57f)

スタックしそうな場所の例を２つほど紹介させて頂きます。

#### ①芝生エリア

車輪径が小さいこともあり、一度芝生エリアに入ると芝生エリアから戻る際にスタックしそうなので避けた方が良さそうです。

[![Image from Gyazo](https://i.gyazo.com/fe7eb23f5784be413b4765e3c6fa39ff.png)](https://gyazo.com/fe7eb23f5784be413b4765e3c6fa39ff)

#### ②横断歩道の段差

これは実際にスタックした例ですが、やはり車輪径が小さいため横断歩道の段差を乗り越えるのが厳しく、結果的に自己位置推定にも影響が出てしまいました。

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">小型ロボットは辛い2 <a href="https://twitter.com/hashtag/%E3%81%A4%E3%81%8F%E3%83%81%E3%83%A3%E3%83%AC?src=hash&amp;ref_src=twsrc%5Etfw">#つくチャレ</a> <a href="https://t.co/Vq0mxatPHi">pic.twitter.com/Vq0mxatPHi</a></p>&mdash; 千葉工大未ロボ上田研 (@uedalaboratory) <a href="https://twitter.com/uedalaboratory/status/1461934150328504320?ref_src=twsrc%5Etfw">November 20, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 

動画を見ると右側が段差になっていて左側がスロープになっていることがわかります。右側の段差を避けて通るような経路計画をすれば問題なく走行する事ができます。

[![Image from Gyazo](https://i.gyazo.com/27a238946abe05f7438c141192a30624.png)](https://gyazo.com/27a238946abe05f7438c141192a30624)

マップを編集する時にふと思ったのですが、通りたくないと設定した領域を上手く利用して、ロボットの存在確率をその領域だけ高くするのもありなのではと考えました。パーティクルが誘拐され全く別の場所にワープしてしまうことがあるので、その対策として効果的であるか気になります。

### つくばチャレンジ用に作成したシミュレータ環境の活用

地図や自己位置推定をテストするのは、rosbagを使用することで可能です。rosbagのようにナビゲーションもつくばチャレンジの現地に近いデータでテストできたら良いなと考え、下の記事のように2次元のマップからGazeboのモデルを作成しました。

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">10LGTM！ | 2次元地図からGazeboのmodelを作ってナビゲーションしてみた by <a href="https://twitter.com/BEIKE_RE?ref_src=twsrc%5Etfw">@BEIKE_RE</a> <a href="https://t.co/Z5TnKlt7YG">https://t.co/Z5TnKlt7YG</a></p>&mdash; Qiitaマイルストーン (@qiita_milestone) <a href="https://twitter.com/qiita_milestone/status/1466917672373960704?ref_src=twsrc%5Etfw">December 3, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 


これは、本走行前日の夜に作成したワールドです。
色々あってwaypointを一から置き直す必要がありました。
本走行は1度きりなので、以下のワールドを使用することで事前にテスト(確認)を行うことができました。

確認したことは、waypointの置きミスやマッピングの際にできた余計な障害物やパスプランです。

[![Image from Gyazo](https://i.gyazo.com/54f325ad8f2c6604520f60d98bed4c99.png)](https://gyazo.com/54f325ad8f2c6604520f60d98bed4c99)


### 実際にナビゲーションのテストをしている様子

<iframe width="560" height="315" src="https://www.youtube.com/embed/tRTD174K4bE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## 今後について

現在、経路計画においてはmove_baseを使用しており、元々あるリソースを上手く使用している状況です。中身のアルゴリズムやシステムに関してはブラックボックスとして扱ってきてしまってます。

何か対応するべき時に中身を理解してないと、いざという時に対応できない問題があったりするので、経路計画や障害物回避などを自分たちで実装するなどをしてチーム全体でレベルアップを図っていきたいと考えています。


## チームメンバー

* B3
  * 出野 廣太郎
  * 畑中 優一郎
* B4
  * 池邉龍宏
  * 内田璃空
* M1
  * 曹越
* M2
  * クルス・アントニオ
* スタッフ
  * 上田隆一

[![Image from Gyazo](https://i.gyazo.com/34acdad58aa175c9a8121ab953bf12c0.jpg)](https://gyazo.com/34acdad58aa175c9a8121ab953bf12c0)
