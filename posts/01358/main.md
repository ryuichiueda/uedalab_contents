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
 	<li>制御入力を与えるもの
<ul>
 	<li>厳密に言うとロボットではない。ロボットは状態変数に含まれる</li>
 	<li><span style="color: #ffff00;">とりあえずエージェントと呼びましょう</span></li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>状態遷移</h2>
<ul>
 	<li>ある時刻の状態[latex]\\boldsymbol{x}_{t-1}[/latex]でエージェントが制御入力[latex]\\boldsymbol{u}_t[/latex]を
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
<h2>状態方程式を考える</h2>
<ul>
 	<li>どれか一つ選んで定式化してみましょう。15分くらい。
<ul>
 	<li>前回同様、問題の定義ははっきりさせません。定式化の上で何か分からないことがあれば聞いていただければ適当に設定します。</li>
 	<li><a href="/?presenpress=確率ロボティクス2016第1回#/13" target="_blank">ロボット1</a>
<ul>
 	<li>入力は移動量（何度回転して、何度直進する、等）にしましょう</li>
 	<li>満足いかない人はトルクで</li>
</ul>
</li>
 	<li><a href="/?presenpress=確率ロボティクス2016第1回#/14" target="_blank">ロボット2</a>
<ul>
 	<li>入力はステップモータの周波数[latex]\\propto[/latex]角速度</li>
 	<li>ステップモータじゃなくてDCモータならどうなる？</li>
</ul>
</li>
 	<li>上の二つでなかったら前回の資料から好きなものを・・・</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>ロボットは状態方程式通りに・・・</h2>
<ul>
 	<li><span style="color: #ffff00;">動かない</span></li>
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
 	<li><span style="color: #ffff00;">[latex]\\boldsymbol{x}_t[/latex]が決定論的でなくなる</span>
<ul>
 	<li>上記のような数式では非決定論的なものが表現しづらい</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
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
 	<li>分かるのは真の状態がどれなのかという<span style="color: #ffff00;">確率密度関数</span></li>
</ul>
</li>
 	<li>確率密度関数を求める式
<ul>
 	<li>[latex]bel(\\boldsymbol{x}_t) = \\int_\\mathcal{X} p(\\boldsymbol{x}_t | \\boldsymbol{x}_{t-1},\\boldsymbol{u}_t )bel(\\boldsymbol{x}_{t-1}) d\\boldsymbol{x}[/latex]</li>
 	<li>[latex]bel[/latex]という表記は謎ですが、
確率密度関数だと考えておきましょう</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>[latex]bel[/latex]の計算（ガウス分布）</h2>
<ul>
 	<li>問題
<ul>
 	<li>状態は一次元: [latex]x \\in \\Re[/latex]</li>
 	<li>制御出力は[latex]\\Delta x[/latex]</li>
</ul>
</li>
 	<li>線形、かつ移動誤差が正規分布に従う場合</li>
 	<li>[latex]bel[/latex]はずっとガウス分布として計算できる
<ul>
 	<li>ガウス分布: [latex]\\mathcal{N}(\\mu,\\sigma) = \\frac{1}{\\sqrt{2\\pi \\sigma^2}}\\exp \\{-\\frac{(x-\\mu)^2}{2\\sigma^2}\\} [/latex]</li>
 	<li>[latex]bel_{t-1}(\\boldsymbol{x}) = \\frac{1}{\\sqrt{2\\pi \\sigma^2}}\\exp \\{-\\frac{(x-\\mu)^2}{2\\sigma^2}\\}[/latex]</li>
</ul>
</li>
</ul>
