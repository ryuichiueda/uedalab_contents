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
 	<li>センサ入力の定義
<ul>
 	<li>[latex]\\boldsymbol{z} = (z_1,z_2,\\dots,z_m) \\in \\mathcal{Z}[/latex]</li>
</ul>
</li>
 	<li>多くの場合、情報は間接的
<ul>
 	<li>レーザレンジファインダーは移動ロボットの
[latex]\\boldsymbol{x} = (x,y,\\theta)[/latex]を直接は教えてくれない
<ul>
 	<li>変数が違う（[latex]\\mathcal{X} \\neq \\mathcal{Z}[/latex]）</li>
 	<li>雑音もある</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>観測方程式</h2>
<ul>
 	<li>センサ入力と状態を結びつける式
<ul>
 	<li>現代制御に出てくる</li>
</ul>
</li>
 	<li>線形な場合
<ul>
 	<li>[latex]\\boldsymbol{z} = C\\boldsymbol{x} + \\delta[/latex]
<ul>
 	<li>時刻の添字[latex]t[/latex]は省略</li>
 	<li>[latex]\\delta[/latex]: センサ入力の値に混入する雑音</li>
</ul>
</li>
</ul>
</li>
 	<li>非線形な場合
<ul>
 	<li>[latex]\\boldsymbol{z} = h(\\boldsymbol{x}) + \\delta[/latex]</li>
</ul>
</li>
 	<li>前回の制御のときと同様、このような定式化をしてしまうと
観測にまつわる不確かさの表現力に乏しい</li>
</ul>
<!--nextpage-->
<h2>観測にまつわる不確かさの表現</h2>
<ul>
 	<li>[latex]p(\\boldsymbol{z}|\\boldsymbol{x})[/latex]: 状態[latex]\\boldsymbol{x}[/latex]にいた場合に、
[latex]\\boldsymbol{z}[/latex]という観測値を得る確率の密度</li>
 	<li>これをエージェントが知っていると、エージェントが状態を推定できる</li>
 	<li> どうやってこれを知るか？
<ul>
 	<li>事前実験</li>
 	<li>センサの特性や環境の特性の知識</li>
 	<li>正解はない</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>ベイズの定理</h2>
<ul>
 	<li>[latex]bel(\\boldsymbol{x}|\\boldsymbol{o}) = \\frac{P(\\boldsymbol{o}|\\boldsymbol{x})P(\\boldsymbol{x})}{\\sum_{\\boldsymbol{x}'}P(\\boldsymbol{o}|\\boldsymbol{x}')P(\\boldsymbol{x}')} \\\\
= \\eta P(\\boldsymbol{o}|\\boldsymbol{x})P(\\boldsymbol{x}) \\\\
= \\eta L(\\boldsymbol{x}|\\boldsymbol{o})P(\\boldsymbol{x})[/latex]</li>
 	<li></li>
</ul>
