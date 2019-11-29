<h1 style="font-size: 250%;">確率ロボティクス</h1>
<h2>第4回</h2>
上田 隆一

2016年10月10日\@千葉工業大学

<!--nextpage-->
<h2>前回・前々回のおさらいと今回</h2>
<ul>
 	<li>前々回
<ul>
 	<li>制御出力（移動）に伴う雑音の扱い</li>
 	<li>信念に反映させる方法</li>
</ul>
</li>
 	<li> 前回
<ul>
 	<li>センサ入力に乗る雑音の扱い</li>
 	<li>信念に反映させる方法</li>
</ul>
</li>
 	<li>今回
<ul>
 	<li> 制御とセンサ計測を繰り返していくと信念もその都度更新されなければならない
<ul>
 	<li><span style="color: #ff0000;">ベイズフィルタ</span></li>
</ul>
</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>ベイズフィルタ（の前に）</h2>
<ul>
 	<li>前々回の制御出力の式と前回のセンサ入力の式を並べて記号を整理
<ul>
 	<li>以下のように定義しましょう
<ul>
 	<li>制御出力[latex]\\boldsymbol{u}_t [/latex]後の信念:
<ul>
 	<li>[latex]\\hat{bel}_t(\\boldsymbol{x}) = bel(\\boldsymbol{x} |\\boldsymbol{u}_{1:t},\\boldsymbol{z}_{1:t-1},bel_0)[/latex]</li>
</ul>
</li>
 	<li>センサ入力[latex]\\boldsymbol{z}_t[/latex]後の信念:
<ul>
 	<li>[latex]bel_t(\\boldsymbol{x}) = bel(\\boldsymbol{x} |\\boldsymbol{u}_{1:t},\\boldsymbol{z}_{1:t},bel_0)[/latex]</li>
</ul>
</li>
 	<li>ここで
<ul>
 	<li>[latex]bel_0[/latex]: 最初にエージェントが持つ信念</li>
 	<li>[latex]\\boldsymbol{u}_{1:t}[/latex]: 時刻[latex]1[/latex]から[latex]t[/latex]までの制御出力のシーケンス</li>
 	<li>[latex]\\boldsymbol{z}_{1:t}[/latex]: 時刻[latex]1[/latex]から[latex]t[/latex]までのセンサ入力のシーケンス</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>ベイズフィルタ</h2>
<ul>
 	<li>制御出力後の変更（motion update）
<ul>
 	<li>[latex]\\hat{bel}_t(\\boldsymbol{x}) = \\int_\\mathcal{X} p(\\boldsymbol{x} | \\boldsymbol{x}',\\boldsymbol{u}_t )bel_{t-1}(\\boldsymbol{x}') d\\boldsymbol{x}'[/latex]</li>
 	<li>状態が動いた後の信念は、その動きの予測の密度関数に、もとの信念の密度関数をかけて積分したもの</li>
</ul>
</li>
 	<li>センサ入力後の更新（sensor update）
<ul>
 	<li>[latex]bel_t(\\boldsymbol{x}) = \\eta \\ell(\\boldsymbol{x}|\\boldsymbol{z}_t)\\hat{bel}_t(\\boldsymbol{x})[/latex]</li>
 	<li>センサから情報が入った後の信念は、そのセンサ値が分かったときの各状態の尤度と、もとの信念の密度関数をベイズの定理でかけたもの</li>
</ul>
</li>
</ul>
