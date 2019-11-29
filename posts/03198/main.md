<h1 style="font-size: 250%;">確率ロボティクス</h1>
<h2>第2回</h2>
上田 隆一

2017年9月27日\@千葉工業大学

<!--nextpage-->
<h2>今日の内容</h2>
<ul>
 	<li>定式化の続き</li>
 	<li>制御と状態</li>
</ul>
<!--nextpage-->
<h2>前回</h2>
<ul>
 	<li>状態について考えた
<ul>
 	<li>状態空間[latex]\\mathcal{X}[/latex]</li>
 	<li>状態[latex]\\boldsymbol{x} = (x_1,x_2,\\dots,x_n) \\in \\mathcal{X}[/latex]</li>
 	<li>状態変数[latex]x_1,x_2,\\dots,x_n[/latex]</li>
</ul>
</li>
 	<li>制御の上で区別すべきものを考慮して状態を定義すべき</li>
</ul>
<!--nextpage-->
<h2>今回</h2>
<ul>
 	<li>制御出力</li>
 	<li>確率的な表現
<ul>
 	<li>状態は分からなくなる</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>状態を動かす</h2>
<ul>
 	<li>状態は変化（遷移）する</li>
 	<li>時刻の導入
<ul>
 	<li>ディジタルの計算機を使うときは基本、離散系で考えてよい</li>
 	<li>[latex]\\boldsymbol{x}_0,\\boldsymbol{x}_1,\\dots,\\boldsymbol{x}_t,\\dots[/latex]（[latex]t[/latex]:時刻）
<ul>
 	<li>（この表記だと[latex]x[/latex]が太字か細字かで添字の意味が違うので注意）</li>
 	<li>（わかりにくくてごめんなさい）</li>
</ul>
</li>
</ul>
</li>
 	<li>状態が変化する原因
<ul>
 	<li>自分（行動決定する何か）が能動的に動かす</li>
 	<li>自分でないものが動かす</li>
</ul>
</li>
 	<li>とりあえず前者について考えましょう</li>
</ul>
<!--nextpage-->
<h2>制御出力</h2>
<ul>
 	<li>状態を動かすもの
<ul>
 	<li>[latex]\\boldsymbol{u} = (u_1,u_2,\\dots,u_m)[/latex]</li>
 	<li>[latex]u_1,u_2,\\dots,u_m[/latex]: 制御変数前進</li>
</ul>
</li>
 	<li>制御出力空間
<ul>
 	<li>[latex]\\boldsymbol{u} \\in \\mathcal{U}[/latex]</li>
</ul>
</li>
 	<li>制御出力を与えるもの
<ul>
 	<li>厳密に言うとロボットではない。ロボットは状態変数に含まれる</li>
 	<li><span style="color: #ff9900;">とりあえずエージェントと呼びましょう</span></li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>状態遷移</h2>
<ul>
 	<li>ある時刻の状態[latex]\\boldsymbol{x}_{t-1}[/latex]でエージェントが制御出力[latex]\\boldsymbol{u}_t[/latex]を
選んだら[latex]\\boldsymbol{x}_t[/latex]に状態が変化</li>
 	<li>状態遷移の式（状態方程式）
<ul>
 	<li>[latex]\\boldsymbol{x}_t = f(\\boldsymbol{x}_{t-1},\\boldsymbol{u}_t)[/latex]</li>
</ul>
</li>
 	<li>状態遷移関数
<ul>
 	<li>[latex]f: \\mathcal{X} \\times \\mathcal{U} \\longrightarrow \\mathcal{X}[/latex]</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>状態方程式をプログラミング</h2>
<ul>
 	<li>標準的な移動ロボットを例に
<ul>
 	<li>状態変数: [latex]\\boldsymbol{x} = (x,y,\\theta)[/latex]</li>
 	<li>出力:[latex]\\boldsymbol{u} = (\\ell,\\omega)[/latex]
<ul>
 	<li>最初に[latex]\\ell[/latex]だけ前進してから[latex]\\omega[/latex]だけ回転</li>
</ul>
</li>
</ul>
</li>
 	<li>問題: 状態方程式: [latex]\\boldsymbol{x}_t = f(\\boldsymbol{x}_{t-1},\\boldsymbol{u}_t)[/latex] は？
<ul>
 	<li><a href="https://github.com/ryuichiueda/probrobo_practice/blob/master/state_equations/no_noise.ipynb">コードの例</a></li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>ロボットは状態方程式通りに・・・</h2>
<ul>
 	<li><span style="color: #ff0000;">動かない</span></li>
 	<li>なぜ
<ul>
 	<li>雑音</li>
 	<li>状態方程式が甘い</li>
 	<li>そもそもエージェントが操作できない変数が存在</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>雑音の考慮</h2>
<ul>
 	<li>いくつかの定式化</li>
 	<li>線形な状態方程式
<ul>
 	<li>[latex]\\boldsymbol{x}_t = A \\boldsymbol{x}_{t-1} + B\\boldsymbol{u}_t +\\boldsymbol{\\varepsilon}_t [/latex]</li>
</ul>
</li>
 	<li>非線形な方程式
<ul>
 	<li>[latex]\\boldsymbol{x}_t = f(\\boldsymbol{x}_{t-1},\\boldsymbol{u}_t) +\\boldsymbol{\\varepsilon}_t [/latex]</li>
</ul>
</li>
 	<li><span style="color: #ff0000;">[latex]\\boldsymbol{x}_t[/latex]が決定論的でなくなる</span>
<ul>
 	<li>上記のような数式では非決定論的なものが表現しづらい</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>雑音のシミュレーション</h2>
<ul>
 	<li>先ほどのコードに雑音を足してみましょう。
<ul>
 	<li>指令値を中心に、ガウス分布にしたがって次のようにばらつく</li>
 	<li> 前進するとき
<ul>
 	<li>距離が距離に対して10%の標準偏差でばらつく</li>
</ul>
<ul>
 	<li>向きが標準偏差3[deg]でばらつく</li>
</ul>
</li>
 	<li>向きを変えるとき
<ul>
 	<li>変える向きの角度に対して10%の標準偏差でばらつく</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>確率を用いた表現</h2>
<ul>
 	<li>状態遷移の書き方
<ul>
 	<li>[latex] \\boldsymbol{x}_t \\sim p(\\boldsymbol{x} | \\boldsymbol{x}_{t-1},\\boldsymbol{u}_t) [/latex]
<ul>
 	<li>意味: [latex]\\boldsymbol{x}_{t-1}[/latex]で[latex]\\boldsymbol{u}_t[/latex]を選択したときの、遷移後の状態が
従う確率密度関数[latex]p(\\boldsymbol{x})[/latex]に従って、[latex]\\boldsymbol{x}_t[/latex]が決まる</li>
</ul>
</li>
</ul>
</li>
 	<li>依然[latex]\\boldsymbol{x}_t[/latex]が実際には何なのかは分からない
<ul>
 	<li>分かるのは真の状態がどれなのかという<span style="color: #ff0000;">確率密度関数</span></li>
</ul>
</li>
 	<li>確率密度関数（<span style="color: #ff0000;">状態遷移確率</span>）を求める式
<ul>
 	<li>[latex]bel_t(\\boldsymbol{x}) = \\int_\\mathcal{X} p(\\boldsymbol{x} | \\boldsymbol{x}',\\boldsymbol{u}_t )bel_{t-1}(\\boldsymbol{x}') d\\boldsymbol{x}'[/latex]</li>
 	<li>[latex]bel[/latex]: 状態に関する確率密度関数</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>[latex]bel[/latex]という表記</h2>
<ul>
 	<li>[latex]bel[/latex]: belief、信念
<ul>
 	<li><span style="color: #ff0000;">エージェントが持っている</span>、状態に対する理解</li>
 	<li>何か正解があるわけではなく、
エージェントが自身の知覚と知識で作り上げるもの</li>
</ul>
</li>
 	<li>知覚: 自身の制御出力、センサ入力</li>
 	<li>知識:制御出力、センサ入力と状態の関係
<ul>
 	<li>制御出力の場合は状態方程式</li>
</ul>
</li>
</ul>
