<h1 style="font-size: 250%;">確率ロボティクス</h1>
<h2>第13回</h2>
上田 隆一

2016年1月18日\@千葉工業大学

<!--nextpage-->
<h2>本日の内容</h2>
<ul>
 	<li>graph based SLAM</li>
</ul>
<!--nextpage-->
<h2>graph based SLAM</h2>
<ul>
 	<li>グラフ表現を使ってオフラインSLAMを行う手法の総称</li>
 	<li>確率ロボティクスで「GraphSLAM」と書かれているのはその一つ</li>
 	<li><a href="http://www.slideshare.net/ryuichiueda/13-57036730" target="_blank">昨年の資料</a>はGraphSLAM</li>
 	<li>今日は<a href="http://ieeexplore.ieee.org/document/5681215/" target="_blank">こちらの資料</a>に基づいて説明</li>
</ul>
<!--nextpage-->
<h2>オフラインSLAM</h2>
<ul>
 	<li>Full SLAM（完全SLAM）とも</li>
 	<li>全ての情報が出揃ったところで、全ての情報に対して最も説明がつく地図を求める</li>
 	<li>[latex]\\text{argmax}_m P(m,x_{0:T} | u_{1:T}, z_{1:T})[/latex]</li>
</ul>
<!--nextpage-->
