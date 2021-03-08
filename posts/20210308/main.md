# 黒猫LiDAR実験

## 序論

近年、猫の写真が人気である。例えば、次のような事例があり、2021年3月現在、6万弱のいいねを稼いでいる。

<blockquote class="twitter-tweet" data-partner="tweetdeck"><p lang="ja" dir="ltr">起きて上を見たら猫大橋が掛かっていた。 <a href="https://t.co/1tCBTL06vj">pic.twitter.com/1tCBTL06vj</a></p>&mdash; 上田 隆一 (@ryuichiueda) <a href="https://twitter.com/ryuichiueda/status/1304174807563427841?ref_src=twsrc%5Etfw">September 10, 2020</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>


しかし、猫のdepth画像については未だ事例が少ない。そこで、猫のdepth画像を撮影し、Twitterに掲載することで、いいねを稼ぐことを目的とする。


## 実験環境

次のように、猫をソファーに設置し、1m程度の距離から計測する。

![](env.jpeg)

猫としては黒猫、センサとしてはIntel社製RealSense L515を用いる。


## 実験結果

L515の結果を示す。

<blockquote class="twitter-tweet" data-partner="tweetdeck"><p lang="ja" dir="ltr">悲報：黒猫，LiDARのレーザーを吸収． <a href="https://t.co/eXpjAynrOz">pic.twitter.com/eXpjAynrOz</a></p>&mdash; 上田 隆一 (@ryuichiueda) <a href="https://twitter.com/ryuichiueda/status/1368839305104293890?ref_src=twsrc%5Etfw">March 8, 2021</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>


猫の種類を間違えたため、LiDARから照射される光線が吸収され、猫のdepth画像は得られなかった。


## 議論

上図が示すように、実験は失敗した。しかし、失敗した原因の意外性から、多くのいいねが稼げたので、これはこれでよいのではないだろうか。


## 結論

猫関係のツイートは伸びる。真面目な研究についても、多くの人に興味を持ってもらうことが今後の課題となる。

