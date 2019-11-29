<h1 style="font-size: 250%;">確率ロボティクス</h1>
<h2>第2回</h2>
上田 隆一

2016年9月?日\@千葉工業大学

<!--nextpage-->
<h2>今日の内容</h2>
<ul>
 	<li>定式化の続き</li>
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
 	<li>制御入力</li>
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
 	<li>[latex]\\boldsymbol{x}_0,\\boldsymbol{x}_1,\\dots,\\boldsymbol{x}_t,\\dots[/latex]</li>
 	<li>[latex]\\boldsymbol{x}_t: (t=0,1,2,\\dots)[/latex]</li>
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
<h2>制御入力</h2>
<ul>
 	<li>状態を動かすもの
<ul>
 	<li>[latex]\\boldsymbol{u} = (u_1,u_2,\\dots,u_m)[/latex]</li>
 	<li>[latex]u_1,u_2,\\dots,u_m[/latex]: 制御変数</li>
</ul>
</li>
 	<li>制御入力空間
<ul>
 	<li>[latex]\\boldsymbol{u} \\in \\mathcal{U}[/latex]</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>状態遷移</h2>
