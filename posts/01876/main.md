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
<h2>ベイズフィルタ</h2>
<ul>
 	<li>前々回の制御出力の式と前回のセンサ入力の式を並べて記号を整理
<ul>
 	<li>[latex]bel(\\boldsymbol{x} |\\boldsymbol{u}_{1:t},\\boldsymbol{z}_{1:t-1},bel_0) = \\int_\\mathcal{X} p(\\boldsymbol{x} | \\boldsymbol{x}',\\boldsymbol{u}_t )bel_{t-1}(\\boldsymbol{x}') d\\boldsymbol{x}'[/latex]</li>
 	<li>[latex]bel(\\boldsymbol{x} |\\boldsymbol{u}_{1:t},\\boldsymbol{z}_{1:t},bel_0) = \\eta \\ell(\\boldsymbol{x}|\\boldsymbol{z})bel(\\boldsymbol{x})[/latex]</li>
</ul>
</li>
</ul>
