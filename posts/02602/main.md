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
 	<li>次のような地図m*を求める問題
<ul>
 	<li>[latex]m^* = \\text{argmax}_m P(m | z_{1:t}, x_{0:t})[/latex]
<ul>
 	<li>[latex]z_{1:t}[/latex]: センサ情報のシーケンス[latex]（z_1,z_2,z_3,...,z_t）[/latex]</li>
 	<li>[latex]x_{0:t}[/latex]: 行動のシーケンス[latex]（x_0,x_1,x_2,...,x_t）[/latex]</li>
</ul>
</li>
</ul>
</li>
</ul>
