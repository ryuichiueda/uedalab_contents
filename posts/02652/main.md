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
<h2>占有格子地図の作成方法<a href="https://lab.ueda.asia/wp-content/uploads/2016/12/occ.png"><img class="wp-image-2613 alignright" src="https://lab.ueda.asia/wp-content/uploads/2016/12/occ-300x179.png" alt="" width="337" height="207" /></a></h2>
<ul>
 	<li>空間を格子状に区切る
<ul>
 	<li>価値反復の際と同様に</li>
 	<li>ただし向きの次元はない</li>
</ul>
</li>
 	<li style="color: white;"></li>
 	<li>格子に持たせる値
<ul>
 	<li>確率、対数オッズ等</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>占有格子地図を使った地図作成方法</h2>
<ul>
 	<li>本日は二つ紹介
<ul>
 	<li>オンライン手法
<ul>
 	<li>ロボットが動いている最中に逐次的に地図を作る</li>
</ul>
</li>
 	<li>オフライン手法
<ul>
 	<li>ロボットが動いた後に地図を作る</li>
 	<li>ロボットは動いている時はひたすらデッドレコニング情報とセンサ計測値を蓄積</li>
 	<li>ロボットの計算機で地図を作る必要もない</li>
</ul>
</li>
 	<li>占有格子地図を使わないSLAMもオフライン/オンライン手法に大別される</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>オンライン手法</h2>
<ul>
 	<li>手順（2次元、距離センサを想定）
<ol>
 	<li>最初のロボットの位置（絶対座標）を[latex](x,y,θ) = (0,0,0)[/latex]とする
<ul>
 	<li>格子の中に壁のある確率を[latex]0.5[/latex]に初期化</li>
</ul>
</li>
 	<li>以下の繰り返し
<ul>
 	<li>A: センサ計測</li>
 	<li>B: センサの計測対象となったセルを抽出</li>
 	<li>C: 各セルの対数オッズを更新</li>
</ul>
</li>
</ol>
</li>
</ul>
<!--nextpage-->
<h2>対数オッズ（ロジット）</h2>
<ul>
 	<li>確率（0から1の値）を[latex]-\\infty[/latex]から[latex]+\\infty[/latex]に拡張
<ul>
 	<li>[latex]\\ell = \\log \\frac{P(x)}{1-P(x)}[/latex]
<ul>
 	<li>確率が1の時に[latex]+\\infty[/latex]</li>
 	<li>確率が0の時に[latex]-\\infty[/latex]</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>セルの更新に必要な式</h2>
<ul>
 	<li>[latex]P(m_i | x,z)[/latex]
<ul>
 	<li>姿勢[latex]x[/latex]でセンサ値が[latex]z[/latex]のとき、[latex]m_i[/latex]である確率
<ul>
 	<li>[latex]m_i[/latex]: 占有格子地図の中の一つのセルに障害物があるかどうかのバイナリ（ある: 1, ない: 0）</li>
</ul>
</li>
 	<li>「逆計測モデル」と言われる
<ul>
 	<li>因果が逆: 障害物があってセンサの値が決まる</li>
</ul>
</li>
</ul>
</li>
 	<li>逆計測モデルの求め方
<ul>
 	<li>統計を取る/学習/適当に</li>
</ul>
</li>
</ul>
<a href="https://lab.ueda.asia/wp-content/uploads/2016/12/inv_model.png"><img class="wp-image-2629 alignnone" src="https://lab.ueda.asia/wp-content/uploads/2016/12/inv_model-300x117.png" alt="" width="410" height="167" /></a>

<!--nextpage-->
<h2>セルの対数オッズの更新</h2>
&nbsp;
<ul>
 	<li style="font-size: 150%;">[latex]\\ell_i \\longleftarrow \\ell_i  + \\log \\frac{P(m_i | x,z)}{1-P(m_i | x,z)}[/latex]</li>
</ul>
<!--nextpage-->
<h2>占有格子地図の例</h2>
<ul>
 	<li>注意: ちゃんと地図を作るには来週、再来週の手法が必要
<ul>
 	<li><a href="http://www.sciencedirect.com/science/article/pii/S0952197614003029" target="_blank">http://www.sciencedirect.com/science/article/pii/S0952197614003029</a></li>
 	<li><a href="https://www.openslam.org/gmapping.html" target="_blank">https://www.openslam.org/gmapping.html </a></li>
</ul>
</li>
</ul>
<iframe src="https://www.youtube.com/embed/RpPcmyXOcr4" width="560" height="315" frameborder="0" allowfullscreen="allowfullscreen"></iframe>

<!--nextpage-->
<h2>オフライン手法</h2>
<ul>
 	<li>最大事後確率（maximum a posterior）推定を利用
<ul>
 	<li>これまでのセンサ入力や制御出力を最もよく説明できる地図を作成</li>
</ul>
</li>
 	<li>逆計測モデルは用いなくて良い
<ul>
 	<li>地図を先に用意して、それに対してセンサ値が得られるかどうかを評価して、地図を書き換えていく</li>
</ul>
</li>
 	<li>ソナーのように壁の位置がピンポイントで決まらないセンサで特に有効
<ul>
 	<li>理由: 逆計測モデルを利用すると、廊下の交差点等が実際より狭い地図ができる</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>手順</h2>
<ol>
 	<li>初期化
<ul>
 	<li>各セルを0（=壁がない）に（0が「壁がない」、1が「壁がある」）</li>
</ul>
</li>
 	<li>センサ値と地図の比較
<ul>
 	<li>あるセルの0か1に入れ替えた地図[latex]m'[/latex]二つに対して対数オッズに[latex]\\log P(z_t|m', x_t)[/latex]を足した値を比較
<ul>
 	<li>[latex]\\log P(z_t|m', x_t)[/latex]: これまでのセンサ値、ロボットの位置に対する対数尤度</li>
 	<li>値の大きい方を選ぶ</li>
</ul>
</li>
</ul>
</li>
</ol>
