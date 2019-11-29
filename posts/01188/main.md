<h1 style="font-size: 250%;">ロボットシステム学</h1>
<h2>第1回</h2>
&nbsp;

上田 隆一

&nbsp;

2016年9月?日\@千葉工業大学

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
</ul>
</li>
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
 	<li>SLAMや位置推定関係（ROSのgmappingやAMCL、他）
<ul>
 	<li>次のページ以降、少し例を見せます</li>
</ul>
</li>
 	<li>マニピュレータ（Move It!）
<ul>
 	<li><a href="http://moveit.ros.org/">公式サイト</a></li>
</ul>
</li>
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
</ul>
<a href="https://lab.ueda.asia/wp-content/uploads/2016/08/2016-03-24-15.22.32-e1472441722374.jpg"><img class="alignnone size-medium wp-image-1179" src="https://lab.ueda.asia/wp-content/uploads/2016/08/2016-03-24-15.22.32-e1472441722374-225x300.jpg" alt="2016-03-24 15.22.32" width="225" height="300" /></a><a href="https://lab.ueda.asia/wp-content/uploads/2016/08/2016-03-26-16.22.17-e1472441304120.jpg"><img class="alignnone size-medium wp-image-1177" src="https://lab.ueda.asia/wp-content/uploads/2016/08/2016-03-26-16.22.17-e1472441304120-300x225.jpg" alt="2016-03-26 16.22.17" width="300" height="225" /></a><a href="https://lab.ueda.asia/wp-content/uploads/2016/08/atohome_抽出.png"><img class="alignnone size-medium wp-image-1176" src="https://lab.ueda.asia/wp-content/uploads/2016/08/atohome_抽出-300x232.png" alt="atohome_抽出" width="300" height="232" /></a>

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
<a href="https://lab.ueda.asia/wp-content/uploads/2016/08/RaspberryPi2.jpeg"><img class="aligncenter size-medium wp-image-1186" src="https://lab.ueda.asia/wp-content/uploads/2016/08/RaspberryPi2-300x225.jpeg" alt="RaspberryPi2" width="300" height="225" /></a>

<!--nextpage-->
<h2>Raspberry Piについて詳しく</h2>
<ul>
 	<li>イギリスで開発された教育用のシングルボードコンピュータ</li>
 	<li><a href="https://www.raspberrypi.org/about/">開発の動機・歴史</a>
<ul>
 	<li>2006-2008年: 構想・試作
<ul>
 	<li>ケンブリッジ大の学生のコンピュータの腕が落ちてきた</li>
 	<li>コンピュータを触ると言ってもWord, Excel, HTMLくらいしか学生がやってない</li>
 	<li>安価でハードから扱えるようなシングルボードPCが作れないか？</li>
</ul>
</li>
 	<li>2009年: Raspberry Pi Foundation設立
<ul>
 	<li>Raspberry Piを販売（2015年初めまでに500万台販売）</li>
</ul>
</li>
</ul>
</li>
</ul>
&nbsp;
