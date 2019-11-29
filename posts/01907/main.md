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
 	<li><span style="color: #ff0000;">[latex]\\hat{bel}_t(\\boldsymbol{x}) = \\int_\\mathcal{X} p(\\boldsymbol{x} | \\boldsymbol{x}',\\boldsymbol{u}_t )bel_{t-1}(\\boldsymbol{x}') d\\boldsymbol{x}'[/latex]</span>
<ul>
 	<li>式の意味: 状態が動いた後の信念は、その動きの予測の密度関数に、もとの信念の密度関数をかけて積分したもの</li>
</ul>
</li>
</ul>
</li>
 	<li>センサ入力後の更新（sensor update）
<ul>
 	<li><span style="color: #ff0000;">[latex]bel_t(\\boldsymbol{x}) = \\eta \\ell(\\boldsymbol{x}|\\boldsymbol{z}_t)\\hat{bel}_t(\\boldsymbol{x})[/latex]</span>
<ul>
 	<li>式の意味: センサから情報が入った後の信念は、そのセンサ値が分かったときの尤度関数と、もとの信念の密度関数をベイズの定理でかけたもの</li>
</ul>
</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>拡張カルマンフィルタ</h2>
<ul>
 	<li>ベイズフィルタをベイズ分布に限定したもの
<ul>
 	<li>これも前回、前々回の式をまとめると構成できる</li>
</ul>
</li>
 	<li>制御出力後の変更（motion update）
<ul>
 	<li><span style="color: #ff0000;">移動後の[latex]\\hat{bel}_t[/latex]</span>:
<ul>
 	<li><span style="color: #ff0000;">中心: [latex]\\hat{\\boldsymbol{x}}_t = f(\\boldsymbol{\\bar{x}}_{t-1},\\boldsymbol{u}_t)[/latex]</span>
<ul>
 	<li>雑音を考慮しない状態方程式で出力前の推定の中心を移動させたもの</li>
 	<li>[latex]\\bar{x}_{t-1}[/latex]: [latex]bel_{t-1}[/latex]の中心</li>
</ul>
</li>
 	<li><span style="color: #ff0000;">共分散: [latex]\\hat\\Sigma_t = F_t\\bar\\Sigma_{t-1}F_t^T + R_t[/latex]</span>
<ul>
 	<li>[latex]\\bar\\Sigma_{t-1}[/latex]: [latex]bel_{t-1}[/latex]の共分散</li>
 	<li>[latex]F_t[/latex]:[latex]\\bar\\Sigma_{t-1}[/latex]まわりで状態遷移関数[latex]f[/latex]から作ったヤコビ行列</li>
 	<li>[latex]R_t[/latex]: 移動の雑音の共分散行列（事前に計測しておく）</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<ul>
 	<li>センサ入力後の更新（sensor update）
<ul>
 	<li>センサ入力後の[latex]bel_t(\\boldsymbol{x})[/latex]:
<ul>
 	<li><span style="color: #ff0000;">中心: [latex]\\bar{\\boldsymbol{x}}_t = \\boldsymbol{\\hat{x}}_t + K(\\boldsymbol{z}_t - h(\\boldsymbol{\\hat{x}}_t)) [/latex]</span>
<ul>
 	<li> [latex]h(\\boldsymbol{x})[/latex]: [latex][\\boldsymbol{x}[/latex]で得られる観測値</li>
 	<li>[latex]K = \\hat\\Sigma_t H_t (H_t \\Sigma H_t^T + Q_t )^{-1}[/latex]（カルマンゲイン）
<ul>
 	<li>[latex]H_t[/latex]: 観測</li>
</ul>
</li>
</ul>
</li>
 	<li>共分散行列: [latex](I - KH) \\Sigma[/latex]</li>
</ul>
</li>
</ul>
</li>
</ul>
