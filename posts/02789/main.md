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
 	<li>問題: [latex]\\text{argmax}_{m,x_{1:T}} P(m,x_{1:T} | u_{1:T}, z_{1:T},x_0)[/latex]
<ul>
 	<li>[latex]x_{0:T}[/latex]: ロボットの姿勢のシーケンス（経路）</li>
</ul>
</li>
 	<li>一般的なアルゴリズム
<ul>
 	<li>経路を求めてから地図を求めるという手順</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>ロボットの経路の算出</h2>
<ul>
 	<li>例えばオドメトリの情報だけで[latex]x_{0:T}[/latex]を初期化
<ul>
 	<li>これだけだと実際とかなりずれる</li>
 	<li>センサの値で少しずつ補正をかけていく</li>
 	<li>評価関数を定義してニュートン法等で</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>最適化問題への落とし込み</h2>
<ul>
 	<li> 二つの姿勢[latex]x_i,x_j[/latex]について、以下の差を考える</li>
 	<li>[latex]\\hat{z}_{ij}(x_i,x_j)[/latex]: ある時点での推定値で作るベクトル</li>
 	<li>[latex]z_{ij}[/latex]: [latex]x_i,x_j[/latex]それぞれの地点で得たセンサデータから計算される相対姿勢</li>
 	<li>この両者の差が全体的に少ない経路を探す・・・のだけど</li>
</ul>
<!--nextpage-->
<h2>情報の多寡の考慮</h2>
<ul>
 	<li>差を小さくするときに重みをつける
<ul>
 	<li>センサで正確に相対姿勢が分かっているところを重視</li>
</ul>
</li>
 	<li>情報行列[latex]\\Omega_{ij}[/latex]を基準に
<ul>
 	<li>誤差の少なそうな [latex]\\approx[/latex] 情報が多い</li>
 	<li>共分散行列の逆行列</li>
 	<li>計測ごとに足し算していける（前回の講義）</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>尤度の計算</h2>
<ul>
 	<li> 1対の姿勢間の推定値[latex]\\hat{z}_{ij}(x_i,x_j)[/latex]とセンサデータの示す推定姿勢[latex]\\hat{z}_{ij}(x_i,x_j)[/latex]の差:
<ul>
 	<li>[latex]\\ell_{ij} \\propto \\{ z_{ij} - \\hat{z}_{ij}(x_i,x_j) \\}^T \\Omega_{ij}  \\{ z_{ij} - \\hat{z}_{ij}(x_i,x_j) \\}[/latex]</li>
 	<li>[latex]e_{ij} = z_{ij} - \\hat{z}_{ij}(x_i,x_j)[/latex]とすると[latex]\\ell_{ij} \\propto e_{ij}^T \\Omega_{ij} e_{ij}[/latex]</li>
 	<li>[latex]F_{ij} = \\ell_{ij} \\propto e_{ij}^T \\Omega_{ij} e_{ij}[/latex]としておきます</li>
 	<li>尤度として扱われる</li>
 	<li>マハラノビス距離の2乗でもある</li>
</ul>
</li>
 	<li>この値の和[latex]F(\\boldsymbol{x})[/latex]を最小にする
<ul>
 	<li>[latex]F(\\boldsymbol{x}) = \\sum_{&lt;i,j&gt; \\in C} F_{ij}[/latex]</li>
 	<li>[latex]\\boldsymbol{x}[/latex]: 姿勢の変数を並べたベクトル</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>和を減少させる差分の導出</h2>
<ul>
 	<li>今の経路の推定値周りで、どっちに推定値を動かせば前ページの値が最も減るかを求める</li>
</ul>
<!--nextpage-->
<h2>最終的な式</h2>
<!--nextpage-->
<h2>アルゴリズム</h2>
<!--nextpage-->
<h2>数式上の問題</h2>
<ul>
 	<li>特異点が出る（らしい）</li>
 	<li>クォータニオン等、適切な表現を用いる</li>
</ul>
