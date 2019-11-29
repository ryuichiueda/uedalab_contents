<h1 style="font-size: 250%;">確率ロボティクス</h1>
<h2>第5/6回</h2>
上田 隆一

2016年10月26日\@千葉工業大学

<!--nextpage-->
<h2>本日の内容</h2>
<ul>
 	<li>有限マルコフ決定過程</li>
</ul>
<!--nextpage-->
<h2>有限マルコフ決定過程</h2>
<ul>
 	<li>finite Markov decision processes (finite MDPs)</li>
 	<li> ロボットの行動を考えるときによく使う
<ul>
 	<li>何が「最適」なのか？</li>
 	<li>最適にするにはロボットがどうすべきか？</li>
</ul>
</li>
 	<li>昔ながらの（今も使われる）経路計画の定式化も有限MDPの部分問題</li>
</ul>
<!--nextpage-->
<h2>有限MDPの考え方</h2>
<ul>
 	<li>ロボット（環境）の状態はエージェントの制御出力により遷移
<ul>
 	<li>これまでの話と同じ</li>
</ul>
</li>
 	<li>「こういう状態になったら終わり」という状態が存在
<ul>
 	<li><span style="color: #ff0000;">「終端状態」 </span></li>
 	<li>例
<ul>
 	<li>移動ロボットが目的地に入った状態</li>
 	<li>ロボットが川に落ちた</li>
</ul>
</li>
</ul>
</li>
 	<li>状態遷移にはコストやペナルティーが伴う
<ul>
 	<li>コスト: 時間、電力消費、燃料消費等</li>
 	<li>ペナルティー: ルール違反、危険な行為に対して</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>定式化（状態と行動）</h2>
<ul>
 	<li><span style="color: #ff0000;">状態</span>
<ul>
 	<li> 離散状態の集合を考える
<ul>
 	<li><span style="color: #ff0000;">[latex]\\mathcal{S}= \\{s_i | i=1,2,\\dots,N \\}[/latex]</span></li>
 	<li>状態が連続の場合は離散化
<ul>
 	<li>[latex]\\mathcal{X}[/latex]を区切る</li>
</ul>
</li>
</ul>
</li>
 	<li>終端状態
<ul>
 	<li><span style="color: #ff0000;">[latex]s_\\text{f} \\in \\mathcal{S}_\\text{f} \\subset \\mathcal{S}[/latex]</span></li>
 	<li>この状態に到達するとそれ以上時間が進まない
<ul>
 	<li>タスクの終わり</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
 	<li><span style="color: #ff0000;">制御出力（行動）</span>
<ul>
 	<li>有限個の行動の集合から選択
<ul>
 	<li><span style="color: #ff0000;">[latex]\\mathcal{A} = \\{ a_j | j = 1,2,\\dots,M \\}[/latex]</span></li>
 	<li>連続系の[latex]\\mathcal{U}[/latex]から何種類か選んで有限個に</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>定式化（状態遷移）</h2>
<ul>
 	<li>状態遷移
<ul>
 	<li><span style="color: #ff0000;">[latex]s' \\sim P(s' | s,a)[/latex]</span>
<ul>
 	<li>[latex]s,s'[/latex]はそれぞれ遷移前、遷移後の状態を示す</li>
</ul>
</li>
 	<li>[latex]P(s' | s,a)[/latex]を<span style="color: #ff0000;">[latex]\\mathcal{P}^a_{ss'}[/latex]<span style="color: #333333;">と表記しましょう</span></span>
<ul>
 	<li>[latex]s \\in \\mathcal{S} - \\mathcal{S}_\\text{f}[/latex]から[latex]a \\in \\mathcal{A}[/latex]を選択した時、[latex]s' \\in \\mathcal{S}[/latex]に遷移する確率</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>定式化（状態遷移の評価）</h2>
<ul>
 	<li>状態遷移の評価
<ul>
 	<li>[latex]R(s,a,s') \\in \\Re[/latex]
<ul>
 	<li>評価は常に実数で行われる</li>
 	<li>評価軸がいくつあっても実数に置き換えて一元化</li>
</ul>
</li>
 	<li>[latex]R(s,a,s')[/latex]を<span style="color: #ff0000;">[latex]\\mathcal{R}^a_{ss'}[/latex]と表記</span></li>
</ul>
</li>
</ul>
