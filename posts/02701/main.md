# 確率ロボティクス2016第12回
02701 <h1 style="font-size: 250%;">確率ロボティクス</h1>
<h2>第12回</h2>
上田 隆一

2016年1月11日\@千葉工業大学

<!--nextpage-->
<h2>本日の内容</h2>
<ul>
 	<li>SLAM
<ul>
 	<li>ROSでSLAMを使う</li>
 	<li>ランドマークベースのFastSLAM（去年の資料）</li>
 	<li>GraphSLAM（去年の資料）</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>SLAMのデモ</h2>
<ul>
 	<li>占有格子地図を使ったFastSLAM</li>
 	<li> 使ったもの
<ul>
 	<li>Raspberry Pi Mouse（Raspberry Pi 3）, Ubuntu 16.04 Server, ROS（slam_gmapping, urg_node, pimouse_ros）</li>
</ul>
</li>
</ul>
<iframe src="https://www.youtube.com/embed/b2kYQ11PUSI" width="560" height="315" frameborder="0" allowfullscreen="allowfullscreen"></iframe>

<!--nextpage-->
<h2>コード</h2>
<ul>
 	<li>と言ってもほぼ設定だけ
<ul>
 	<li><a href="https://github.com/ryuichiueda/pimouse_slam" target="_blank">https://github.com/ryuichiueda/pimouse_slam</a></li>
</ul>
</li>
 	<li>コード・設定ファイルでやっていること
<ul>
 	<li>オドメトリの計算</li>
 	<li>誤差の見積もり</li>
 	<li>パーティクルの数等、FastSLAMのパラメータの設定</li>
</ul>
</li>
</ul>
