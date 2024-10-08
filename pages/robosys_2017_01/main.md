# ロボットシステム学2017第1回
<h1 style="font-size: 250%;">ロボットシステム学</h1>
<h2>第1回</h2>
&nbsp;

上田 隆一

&nbsp;

2017年9月20日\@千葉工業大学

<!--nextpage-->
<h2>今日の内容</h2>
<ul>
 	<li>動機付け（なんでこの講義があるのか）</li>
</ul>
<!--nextpage-->
<h2>ロボットシステム</h2>
<ul>
 	<li><a href="http://yougo.ascii.jp/caltar/%E3%82%B7%E3%82%B9%E3%83%86%E3%83%A0" target="_blank">システム</a>
<ul>
 	<li style="text-align: justify;">目的を遂行するための体系や組織</li>
</ul>
</li>
 	<li>ロボットシステム
<ul>
 	<li style="text-align: justify;">目的を遂行するために動作</li>
 	<li>動作のための様々な要素
<ul>
 	<li style="text-align: justify;">センサ</li>
 	<li style="text-align: justify;">アクチュエータ</li>
 	<li style="text-align: justify;">電気回路</li>
 	<li style="text-align: justify;">計算機（コンピュータ）</li>
 	<li style="text-align: justify;">外装</li>
 	<li style="text-align: justify;">・・・</li>
</ul>
</li>
 	<li style="text-align: justify;">例: <a href="http://www.nikkei.com/article/DGXMZO80396140S4A201C1000000/" target="_blank">ルンバ</a>、<a href="https://www.toshiba.co.jp/sis/railwaysystem/jp/products/highspeed/index.htm" target="_blank">新幹線</a></li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>ロボットシステム開発の変化</h2>
<ul>
 	<li>一人で黙々と作る時代の終焉
<ul>
 	<li>個人的な終焉: 大学生から社会人へ</li>
 	<li>時代としての終焉: インターネット上への知識の集積</li>
 	<li>注意: 一人で一通り作れることは相変わらず貴重
<ul>
 	<li>ただ、それだけだと広がりがない</li>
</ul>
</li>
</ul>
</li>
 	<li>開発のスピードの急激な変化
<ul>
 	<li>CAD、3Dプリンタ、ROS、各種サービスの無い時代と
有る時代のスピードの違い</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>外のリソースを使う</h2>
<ul>
 	<li>分かりやすい例: オープンソース
<ul>
 	<li>SLAMや位置推定関係（ROSのgmappingやAMCL、他、次ページ）</li>
 	<li>マニピュレータ（Move It!）
<ul>
 	<li><a href="http://moveit.ros.org/">公式サイト</a></li>
</ul>
</li>
 	<li>Gitのホスティングサービス、CIサービス</li>
 	<li>個人的な見解では、人の作ったソフトを使いこなせた後に理屈をしっかり学ぶべき</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>ROSでSLAM</h2>
<ul>
 	<li>RoboCup JapanOpen 2016にて。</li>
 	<li>ROS（robot operating system）+gmapping
<ul>
 	<li>ROSは講義後半で扱う</li>
</ul>
</li>
 	<li><a href="https://www.youtube.com/watch?v=XozlE7fuTso" target="_blank">ついでにRoboCup2016のビデオ</a></li>
</ul>
<a href="https://lab.ueda.tech/wp-content/uploads/2016/08/2016-03-24-15.22.32-e1472441722374.jpg"><img class="alignnone size-medium wp-image-1179" src="https://lab.ueda.tech/wp-content/uploads/2016/08/2016-03-24-15.22.32-e1472441722374-225x300.jpg" alt="2016-03-24 15.22.32" width="225" height="300" /></a><a href="https://lab.ueda.tech/wp-content/uploads/2016/08/2016-03-26-16.22.17-e1472441304120.jpg"><img class="alignnone size-medium wp-image-1177" src="https://lab.ueda.tech/wp-content/uploads/2016/08/2016-03-26-16.22.17-e1472441304120-300x225.jpg" alt="2016-03-26 16.22.17" width="300" height="225" /></a><a href="https://lab.ueda.tech/wp-content/uploads/2016/08/atohome_抽出.png"><img class="alignnone size-medium wp-image-1176" src="https://lab.ueda.tech/wp-content/uploads/2016/08/atohome_抽出-300x232.png" alt="atohome_抽出" width="300" height="232" /></a>

<!--nextpage-->
<h2>変化の中心にあるもの</h2>
<ul>
 	<li>プラットフォームの存在
<ul>
 	<li>知識やソフト等を流通させるには、それらが適用できるモノが必要</li>
 	<li>ロボットは計算機だけの場合より多様だが存在</li>
</ul>
</li>
 	<li>プラットフォームの例
<ul>
 	<li>ハード: PC、Raspberry Pi、Arduinoとその互換品、各種規格品</li>
 	<li>ソフト: UNIX、Linux</li>
 	<li>サービス: GitHub</li>
 	<li>ロボット: TurtleBot、iCart-mini、HSR、・・・</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>Raspberry Pi</h2>
<ul>
 	<li>シングルボードコンピュータ</li>
 	<li>本講義で扱う
<ul>
 	<li>特に講師が信者ということではない</li>
 	<li>性能はともかく、プラットフォームとして非常に優秀
<ul>
 	<li><span style="color: #ffff00;">使ったことがあっても、
ここで性能のことにしか目に行かない人は非常にまずい</span></li>
</ul>
</li>
</ul>
</li>
</ul>
<a href="https://lab.ueda.tech/wp-content/uploads/2016/08/RaspberryPi2.jpeg"><img class="aligncenter size-medium wp-image-1186" src="https://lab.ueda.tech/wp-content/uploads/2016/08/RaspberryPi2-300x225.jpeg" alt="RaspberryPi2" width="300" height="225" /></a>

<!--nextpage-->
<h2>Raspberry Piについて詳しく</h2>
<ul>
 	<li>イギリスで開発された教育用のシングルボードコンピュータ</li>
 	<li><a href="https://www.raspberrypi.org/about/" target="_blank">開発の動機・歴史</a>
<ul>
 	<li>2006-2008年: 構想・試作
<ul>
 	<li>ケンブリッジ大の学生のコンピュータの腕が落ちてきた
<ul>
 	<li>経験者と言ってもWord, Excel, HTMLくらい</li>
 	<li>（未ロボだと逆の人も多い）</li>
</ul>
</li>
 	<li>安価でハードの制御ができるようなシングルボードPCが作れないか？</li>
</ul>
</li>
 	<li>2009年: Raspberry Pi Foundation設立
<ul>
 	<li><a href="https://www.raspberrypi.org/blog/ten-millionth-raspberry-pi-new-kit/" target="_blank">Raspberry Piを販売（2016年に1000万台販売）</a></li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>講義の目的</h2>
<ul>
 	<li>一つのシングルボードコンピュータで低レイヤーから
高レイヤーまで一通り経験する
<ul>
 	<li>低レイヤー: デバイスドライバ</li>
 	<li>高レイヤー: インターネットとのやりとり
<ul>
 	<li>さらには著作権やライセンスまで</li>
</ul>
</li>
 	<li>全部実現できるラズパイで</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>講義の内容</h2>
全15回。シラバスから一部変更あり
<ul>
 	<li>第1週: イントロダクション（本講義）</li>
 	<li>第2週: ラズパイの操作
<ul>
 	<li>通信等</li>
</ul>
</li>
 	<li>第3週: マイコンの仕組み（3,4週は入れ替えで）
<ul>
 	<li>低レイヤーを学習</li>
</ul>
</li>
 	<li>第4週: オペレーティングシステム
<ul>
 	<li>プロセス、ファイルシステム</li>
</ul>
</li>
</ul>
<!--nextpage-->
<ul>
 	<li>第5週: 電子回路とプログラミングI
<ul>
 	<li>GPIOをソフトウェアで操作</li>
 	<li>12週のデバドラを先にやるかもしれません</li>
</ul>
</li>
 	<li>第6週: 電子回路とプログラミングII
<ul>
 	<li>実習</li>
</ul>
</li>
 	<li>第7週: ペリフェラル
<ul>
 	<li>様々なデバイスの操作</li>
</ul>
</li>
 	<li>第8週: ネットワーク</li>
 	<li>第9週: システム管理とデータ処理</li>
</ul>
<!--nextpage-->
<ul>
 	<li>第10週: オープンソースとライセンス</li>
 	<li>第11週: GitとGitHub</li>
 	<li>第12週: デバイスドライバ
<ul>
 	<li>Travis CIになるかも</li>
</ul>
</li>
 	<li>第13週: ROSの役割と構造</li>
 	<li>第14週: ROSの利用</li>
 	<li>第15週: まとめ</li>
</ul>
<!--nextpage-->
<h2>講義で使う道具</h2>
<ul>
 	<li>ノートPC</li>
 	<li>Raspberry Pi</li>
 	<li>Raspberry Piのアクセサリ（次のページ）</li>
 	<li>仮想マシン上のUbuntu
<ul>
 	<li>Raspberry Piと繋がらないときのつなぎ</li>
 	<li>Ubuntu Server16.04 LTS
<ul>
 	<li>Desktop版でも良いけど重い</li>
</ul>
</li>
 	<li>仮想マシンは特にこだわりがなければVirtualBoxで</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>ラズパイのアクセサリ</h2>
<ul>
 	<li>USBケーブル（Type A-Micro B）
<ul>
 	<li>ノートPCからRaspberry Piに電源供給</li>
</ul>
</li>
 	<li>microSDカード
<ul>
 	<li> 16GBのものがおすすめ</li>
 	<li>複数あるとよい</li>
</ul>
</li>
 	<li>LANケーブル
<ul>
 	<li>ノートPCとRaspberry Piを接続</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>ウェブサイト等</h2>
<ul>
 	<li><a href="https://lab.ueda.tech/?page_id=3112">講義のサイト</a></li>
 	<li>連絡: 人にバレてもいい内容はTwitterで <a href="https://twitter.com/ryuichiueda" target="_blank">\@ryuichiueda</a></li>
 	<li>授業支援システムは勉強中（）
<ul>
 	<li>去年、一昨年はメールでレポートを提出してもらいました</li>
 	<li>追って連絡</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>テスト・レポート等</h2>
<ul>
 	<li>課題は2回
<ul>
 	<li>各20点（＋α）</li>
</ul>
</li>
 	<li>テストは1回
<ul>
 	<li>60点</li>
</ul>
</li>
 	<li>出席
<ul>
 	<li>遅刻、早退は0.5回とカウント</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>参考図書</h2>
<ul>
 	<li>初心者の人はこれを購入のこと
<ul>
 	<li><a href="https://www.amazon.co.jp/dp/480071172X" target="_blank">福田: これ１冊でできる！ラズベリー・パイ　超入門 改訂第3版、ソーテック社, 2017.</a></li>
</ul>
</li>
 	<li>Linuxの操作
<ul>
 	<li>初心者向け
<ul>
 	<li><a href="https://www.amazon.co.jp/dp/4822224961" target="_blank">Piro（結城洋志）: シス管系女子, 日経BP, 2015.</a></li>
</ul>
</li>
 	<li>中級者〜
<ul>
 	<li><a href="https://www.amazon.co.jp/dp/4774173444" target="_blank">上田: シェルプログラミング実用テクニック, 技術評論社, 2015.</a></li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>参考図書（続き）</h2>
<ul>
 	<li> デバドラ関係
<ul>
 	<li><a href="https://www.amazon.co.jp/dp/4873112532" target="_blank">Corbet 他(著), 山崎 他(翻訳): Linuxデバイスドライバ 第3版, オライリージャパン, 2005.</a>
<ul>
 	<li>デバイスドライバのリファレンス</li>
 	<li>ちょっと古い</li>
 	<li><a href="http://www.makelinux.net/ldd3/" target="_blank">英語ならネット上に</a></li>
</ul>
</li>
</ul>
</li>
 	<li>OS
<ul>
 	<li><a href="https://www.amazon.co.jp/dp/4894717697" target="_blank">Tanenbaum: オペレーティングシステム 第3版, ピアソンエデュケーション, 2007.</a>
<ul>
 	<li>中古が出回っている</li>
</ul>
</li>
 	<li><a href="https://www.amazon.co.jp/dp/487311313X" target="_blank">Bovet: 詳解 Linuxカーネル 第3版, オライリー・ジャパン, 2007.</a></li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>宿題: Raspberry Piの
セットアップ</h2>
<ul>
 	<li>Raspberry Piを入手してRaspbianをインストールのこと
<ul>
 	<li>初心者向けの指示: <a href="https://www.raspberrypi.org/downloads/noobs/" target="_blank">NOOBS</a>を使って<a href="https://www.raspberrypi.org/downloads/raspbian/" target="_blank">Raspbian</a>をインストールのこと</li>
 	<li>本当は最短手順を私が示せばよいのですが、割愛で
<ul>
 	<li>ネット上に山のように情報</li>
 	<li>「これ1冊で・・・」に詳しい解説
<ul>
 	<li>Windows、Mac対応。pp.32-40</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
 	<li>諸注意
<ul>
 	<li>デスクトップ環境は使いません</li>
 	<li>ギブアップしても来週時間をとります</li>
</ul>
</li>
 	<li>慣れている人はUbuntuでもよい</li>
</ul>
<!--nextpage-->
<h2>Raspberry Piの入出力</h2>
[caption id="attachment_1189" align="alignright" width="225"]<a href="https://lab.ueda.tech/wp-content/uploads/2016/08/raspberrypi.png"><img class="wp-image-1189 size-medium" src="https://lab.ueda.tech/wp-content/uploads/2016/08/raspberrypi-225x300.png" alt="raspberrypi" width="225" height="300" /></a> <span style="color: #ffffff;">Raspberry Pi 2 Model B</span>[/caption]
<ul>
 	<li>電源入力: MicroUSB</li>
 	<li>ディスプレイへ出力: HDMI</li>
 	<li>ストレージ: microSDカード</li>
 	<li>有線LANポート</li>
 	<li>USBポート</li>
 	<li><span style="color: #ffff00;">40ピンのブロック</span>
<ul>
 	<li>「GPIOピン」と呼ばれる</li>
</ul>
</li>
 	<li>他: 専用カメラの取り付け端子等</li>
</ul>
&nbsp;

<!--nextpage-->
<h2>GPIOピンの構成</h2>
<ul>
 	<li>配置（Model Bのもの）: <a href="http://pinout.xyz" target="_blank">http://pinout.xyz</a>
<ul>
 	<li>電源: 3.3V、5V</li>
 	<li>GND</li>
 	<li>GPIOピン: 27
<ul>
 	<li>うち何本かがI2C、SPI、UARTも使える</li>
</ul>
</li>
 	<li>I2C ID EEPROM用ピン</li>
</ul>
</li>
 	<li>A/D変換機能は付いていない</li>
</ul>
<!--nextpage-->
<h2>CPU・メモリ・ストレージ</h2>
<ul>
 	<li>Raspberry Pi 3
<ul>
 	<li>CPU: 1.2GHz Cortex-A53 ARMv8 64bit（4コア）</li>
 	<li>DRAM: 1GB DDR2 450MHz</li>
 	<li>ストレージ: microSD
<ul>
 	<li>細かい規格の制限や相性等に注意
<ul>
 	<li>16GBまではトラブルが少ない</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>Raspberry Piのソフトウェア</h2>
<ul>
 	<li>Linuxが標準
<ul>
 	<li>Raspbian</li>
 	<li>Ubuntu</li>
</ul>
</li>
 	<li>ロボットのコントローラとしてのLinux
<ul>
 	<li>欠点: マイコンのように単純なリアルタイム制御ができない</li>
 	<li>長所: 開発時、運用時にインターネットとシームレスに接続
<ul>
 	<li>これから講義でいろいろやります</li>
</ul>
</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>次回</h2>
<ul>
 	<li>教室でRaspberry Piを使います
<ul>
 	<li>ノートPCにLANケーブルで接続してSSHから操作</li>
</ul>
</li>
</ul>

