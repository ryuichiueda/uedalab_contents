---
Keywords: Raspberry pi
Copyright:　(C) 2021 Kotaro Izuno

Yuichiro Hatanaka
---

# 屋内環境でRaspberry Pi 3Bのみでナビゲーションを行った話

## 目的

Raspberry Pi 3B のスペックでナビゲーションを行えるのかを調査します。


## 実験
RT CORPORATION の Raspberry Pi Cat を用いて実験しました。

![](Raspberry-Pi-Cat.png)

Packageは以下のものを使用しました。

・[raspicat_navigation](https://github.com/uhobeike/raspicat_navigation)

実験場所は、千葉工業大学津田沼キャンパスの2号館19階の廊下です。
この区間を一周させることで、ナビゲーションが行えたとします。



地図は、gmapping[http://wiki.ros.org/gmapping] で作成した19階の地図です。

resolutionが0.05の地図ではナビゲーションを行うことができなかったため、resolutionを0.30に設定しました。原因としては、マップサイズが大きいと処理に使うメモリが足りなったことでした。



・resolution 0.05

![19階地図](map_tudanumakai.png)

・resolution 0.30

![19階地図](AnyConv.com__2_19.png)
## 実験結果
Youtubeにて、走行時の動画です。
[![](https://img.youtube.com/vi/tmFjHElCXa8/0.jpg)](https://www.youtube.com/watch?v=tmFjHElCXa8)

目的である廊下の一周が成功しました。

## 考察・今後の活動
本実験で、地図の解像度の変更で走行できるかを調査しました。
今後は、千葉工業大学津田沼キャンパス内の指定された区間を走行することを目標とします。