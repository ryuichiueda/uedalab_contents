<h1 style="font-size: 250%;">確率ロボティクス</h1>
<h2>第11回</h2>
上田 隆一

2016年12月21日\@千葉工業大学

<!--nextpage-->
<h2>本日の内容</h2>
<ul>
 	<li>SLAM</li>
</ul>
<!--nextpage-->
<h2>SLAM</h2>
<ul>
 	<li>SLAM（simultaneous localization and mapping）
<ul>
 	<li>自己位置推定と地図生成を同時に行う方法</li>
</ul>
</li>
 	<li>移動の誤差を考慮しなくても良い場合のアルゴリズム</li>
</ul>
&nbsp;

<!--nextpage-->
<h2>SLAM問題</h2>
<ul>
 	<li>次のような地図[latex]m^*[/latex]を求める問題
<ul>
 	<li>[latex]m^* = \\text{argmax}_m P(m |x_{0:t}, u_{1:t}, z_{1:t})[/latex]
<ul>
 	<li>[latex]x_{0:t}[/latex]: 行動のシーケンス[latex]（x_0,x_1,x_2,...,x_t）[/latex]</li>
 	<li>[latex]u_{1:t}[/latex]: センサ情報のシーケンス[latex]（u_1,u_2,u_3,...,u_t）[/latex]</li>
 	<li>[latex]z_{1:t}[/latex]: センサ情報のシーケンス[latex]（z_1,z_2,z_3,...,z_t）[/latex]</li>
 	<li>（面倒なのでベクトルも細字で書いてます）</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>SLAMの基本手続き</h2>
<ul>
 	<li>これで地図ができる （2次元の例, 距離センサを想定）
<ul>
 	<li>最初のロボットの位置[latex]x_0[/latex]（絶対座標）を[latex] (x,y,θ) = (0,0,0)[/latex]とする</li>
 	<li>以下の繰り返し
<ol>
 	<li>センサで障害物の位置を計測</li>
 	<li>障害物の位置を絶対座標に変換して記録</li>
 	<li>ロボットを動かしてロボットの座標を更新</li>
</ol>
</li>
</ul>
</li>
 	<li>問題
<ul>
 	<li>移動誤差、センサの雑音</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>実際の例</h2>
<ul>
 	<li>日経Linux 2015年11月号の上田の記事より</li>
</ul>
<table>
<tbody>
<tr>
<td><a href="https://lab.ueda.asia/wp-content/uploads/2016/12/env.png"><img class="size-medium wp-image-2607 alignnone" src="https://lab.ueda.asia/wp-content/uploads/2016/12/env-300x223.png" /></a></td>
<td><img class=" wp-image-2608 alignnone" src="https://lab.ueda.asia/wp-content/uploads/2016/12/map-300x300.png" /></td>
</tr>
</tbody>
</table>
<!--nextpage-->
<h2>誤差への対応</h2>
<ul>
 	<li>とりあえず、まずセンサの誤差を考える</li>
 	<li>占有格子地図（occupancy grid map）による確率表現
<ul>
 	<li>地図を区切って各区画に障害物が存在する確率（の対数オッズ）を入れる</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>占有格子地図の作成方法</h2>
<ul>
 	<li>空間を格子状に区切る
<ul>
 	<li><a href="https://lab.ueda.asia/wp-content/uploads/2016/12/occ.png"><img class="alignright size-medium wp-image-2613" src="https://lab.ueda.asia/wp-content/uploads/2016/12/occ-300x179.png" alt="" width="300" height="179" /></a>価値反復の際と同様に</li>
 	<li>ただし向きの次元はない</li>
</ul>
</li>
 	<li>格子に持たせる値
<ul>
 	<li>確率、対数オッズ等</li>
</ul>
</li>
</ul>
