<h1 style="font-size: 250%;">確率ロボティクス</h1>
<h2>第3回</h2>
上田 隆一

2016年10月5日\@千葉工業大学

<!--nextpage-->
<h2>今日の内容</h2>
<ul>
 	<li>センサ値と状態、信念</li>
</ul>
<!--nextpage-->
<h2>前回</h2>
<ul>
 	<li>制御出力[latex]\\boldsymbol{u}_t[/latex]で状態[latex]\\boldsymbol{x}_{t-1}[/latex]から[latex]\\boldsymbol{x}_t[/latex]に変化</li>
 	<li>自律ロボット（エージェント）にとって、状態[latex]\\boldsymbol{x}_t[/latex]は、未知</li>
 	<li>エージェントは状態[latex]\\boldsymbol{x}_t[/latex]に対する認識である信念[latex]bel_t[/latex]を持つ</li>
 	<li>[latex]bel_t[/latex]には、制御出力に対する実際の動きの雑音が蓄積していく
<ul>
 	<li>ガウス分布に従う場合は共分散行列に雑音が足されていく</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>状態を（間接的に）観測する</h2>
<ul>
 	<li>センサの値には状態に対するヒント（情報）が隠れている</li>
 	<li>多くの場合、情報は間接的
<ul>
 	<li>レーザレンジファインダーは移動ロボットの
[latex]\\boldsymbol{x} = (x,y,\\theta)[/latex]を直接は教えてくれない
<ul>
 	<li>変数が違う</li>
 	<li>雑音もある</li>
</ul>
</li>
</ul>
</li>
 	<li>情報を[latex]bel_t[/latex]に反映するにはどういう式を使ったら良いか？</li>
</ul>
<!--nextpage-->
<h2>ベイズの定理</h2>
<ul>
 	<li>[latex]bel(\\boldsymbol{x}|\\boldsymbol{o}) = \\frac{P(\\boldsymbol{o}|\\boldsymbol{x})P(\\boldsymbol{x})}{\\sum_{\\boldsymbol{x}'}P(\\boldsymbol{o}|\\boldsymbol{x}')P(\\boldsymbol{x}')} \\\\
= \\eta P(\\boldsymbol{o}|\\boldsymbol{x})P(\\boldsymbol{x}) \\\\
= \\eta L(\\boldsymbol{x}|\\boldsymbol{o})P(\\boldsymbol{x})[/latex]</li>
 	<li></li>
</ul>
