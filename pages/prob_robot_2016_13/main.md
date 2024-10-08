# 確率ロボティクス2016第13回
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
 	<li>[latex]F_{ij} =  e_{ij}^T \\Omega_{ij} e_{ij}[/latex]としておきます</li>
 	<li>対数尤度として扱われる</li>
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
 	<li>今の経路の推定値[latex]\\boldsymbol{x}[/latex]（チュートリアルでは[latex]\\breve{\\boldsymbol{x}}[/latex]）周りで、どっちに推定値を動かせば前ページの値が最も減るかを求める</li>
 	<li>導出手順
<ul>
 	<li>[latex]F(\\boldsymbol{x})[/latex]を[latex]\\Delta{\\boldsymbol{x}}[/latex]だけ動かして値が動かないところを探す
<ul>
 	<li>線形化のときに出てきた方法</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>手順</h2>
<ul>
 	<li> 推定値を動かした時の誤差の増分を線形化しておく
<ul>
 	<li>[latex]e_{ij}(x_i + \\Delta x_i , x_j + \\Delta x_j) = e_{ij} (\\boldsymbol{x} + \\Delta \\boldsymbol{x}) \\approx e_{ij} + J_{ij}\\Delta \\boldsymbol{x} [/latex]</li>
</ul>
</li>
 	<li>[latex]F(\\boldsymbol{x})[/latex]の変化量を求める
<ul>
 	<li>[latex]F(\\boldsymbol{x} + \\Delta\\boldsymbol{x}) = \\sum_{&lt;i,j&gt; \\in C} F_{ij}( \\boldsymbol{x} + \\Delta\\boldsymbol{x} ) \\\\
= \\sum_{&lt;i,j&gt; \\in C} \\{ (e_{ij} + J_{ij} \\Delta\\boldsymbol{x})^T \\Omega_{ij}(e_{ij} + J_{ij} \\Delta\\boldsymbol{x}) \\}\\\\
\\approx \\sum_{&lt;i,j&gt; \\in C} \\{ \\text{定数} + 2e_{ij}^T \\Omega_{ij} J_{ij}\\Delta{\\boldsymbol{x}} +\\Delta{\\boldsymbol{x}}^T J_{ij}^T \\Omega_{ij} J_{ij}\\Delta{\\boldsymbol{x}}  \\} [/latex]</li>
</ul>
</li>
 	<li>記号の整理
<ul>
 	<li>[latex]e_{ij}^T \\Omega_{ij} J_{ij}[/latex]を[latex]\\boldsymbol{b}_{ij}[/latex]に</li>
 	<li>[latex]J_{ij}^T \\Omega_{ij} J_{ij}[/latex]を[latex]H_{ij}[/latex]に</li>
 	<li>[latex]F(\\boldsymbol{x} + \\Delta\\boldsymbol{x}) \\approx \\sum_{&lt;i,j&gt; \\in C} \\{ \\text{定数} + 2\\boldsymbol{b}_{ij}\\Delta{\\boldsymbol{x}} +\\Delta{\\boldsymbol{x}}^T H_{ij}\\Delta{\\boldsymbol{x}}  \\}[/latex]</li>
</ul>
</li>
</ul>
<!--nextpage-->
<ul>
 	<li>和の部分を巨大なベクトル、行列に
<ul>
 	<li>[latex]F(\\boldsymbol{x} + \\Delta\\boldsymbol{x}) \\approx  \\text{定数} + 2\\boldsymbol{b}^T \\Delta{\\boldsymbol{x}} +\\Delta{\\boldsymbol{x}}^T H \\Delta{\\boldsymbol{x}}  [/latex]</li>
 	<li>[latex]H[/latex]: 経路に関する情報行列</li>
 	<li>[latex]\\boldsymbol{b}[/latex]: 係数ベクトルと呼ぶ</li>
</ul>
</li>
 	<li>変化量がゼロになる[latex]\\Delta\\boldsymbol{x}[/latex]を求める
<ul>
 	<li>上の式の右辺を[latex]\\Delta{\\boldsymbol{x}}[/latex]で微分した量がゼロになる[latex]\\Delta\\boldsymbol{x}[/latex]</li>
 	<li><span style="color: #ff0000;">[latex]H \\Delta\\boldsymbol{x} = - \\boldsymbol{b}[/latex]</span></li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>情報行列[latex]H[/latex]の性質</h2>
<ul>
 	<li>[latex]H[/latex]: 関係性が得られている姿勢に関係する要素だけが非ゼロのスパース行列</li>
 	<li>このような形の行列[latex]H_{ij}[/latex]が足し合わさった形になる
<ul>
 	<li>[latex]H_{ij} = \\begin{bmatrix}
\\ddots  \\\\
&amp;A_{ij}^T\\Omega_{ij}A_{ij} &amp; \\dots &amp; A_{ij}^T\\Omega_{ij}B_{ij} \\\\
&amp; \\vdots &amp; \\ddots &amp; \\vdots  \\\\
&amp;B_{ij}^T\\Omega_{ij}A_{ij} &amp; \\dots &amp; B_{ij}^T\\Omega_{ij}B_{ij} \\\\
&amp; &amp; &amp; &amp; \\ddots
\\end{bmatrix}
[/latex]</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>ベクトル[latex]b[/latex]の性質</h2>
<ul>
 	<li>なんの値かはよくわからない（ごめんなさい）が次のような形のベクトル[latex]\\boldsymbol{b}_{ij}[/latex]が足し合わさった形になる
<ul>
 	<li>[latex]\\boldsymbol{b}_{ij} = \\begin{bmatrix}
\\vdots  \\\\
A_{ij}^T\\Omega_{ij} e_{ij} \\\\
\\vdots  \\\\
B_{ij}^T\\Omega_{ij} e_{ij} \\\\
\\vdots  \\\\
\\end{bmatrix}
[/latex]</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>アルゴリズム</h2>
<ul>
 	<li>以下を収束するまで繰り返し
<ol>
 	<li>オドメトリ等のデータから初期の[latex]x_{0:T}[/latex]を初期化</li>
 	<li>センサデータから得られる各相対姿勢に関して
<ol>
 	<li>[latex]H_{ij}[/latex]を[latex]H[/latex]に足す</li>
 	<li>[latex]\\boldsymbol{b}_{ij}[/latex]を[latex]\\boldsymbol{b}[/latex]に足す</li>
</ol>
</li>
 	<li>[latex]H[/latex]の[latex]H_{01}[/latex]の部分の左上
（姿勢[latex]x_0[/latex]の部分）に単位行列を足す
<ul>
 	<li>姿勢[latex]x_0[/latex]は絶対的に正しいので値をかさ上げ</li>
</ul>
</li>
 	<li>[latex]H\\Delta \\boldsymbol{x} = - \\boldsymbol{b}[/latex]から[latex]\\Delta \\boldsymbol{x}[/latex]を導出</li>
 	<li>[latex]x_{0:T}[/latex]を[latex]\\Delta \\boldsymbol{x}[/latex]で更新</li>
</ol>
</li>
</ul>
<!--nextpage-->
<h2>数式上の問題</h2>
<ul>
 	<li>特異点が出る（らしい）</li>
 	<li>クォータニオン等、適切な表現を用いる</li>
</ul>
<!--nextpage-->
<h2>課題</h2>
<ul>
 	<li>講義で扱った手法について簡単な例題を作り、コードを書いて解く
<ul>
 	<li>コードと問題の定義から解答までまとめたドキュメントを提出</li>
</ul>
</li>
 	<li>提出方法
<ul>
 	<li>コードをGitHubか何かにアップしてREADMEに説明と動いた時の様子を書く</li>
 	<li>GitHubがわからん人はコードとドキュメントをメールで添付してください</li>
 	<li>Travis CIとかで実行してるときの様子がわかるようにしてくださると大変ありがたく（点数おまけします）</li>
</ul>
</li>
 	<li>30点満点にします（30点を超えることもあり）</li>
 	<li>締め切り: 2/8</li>
</ul>
