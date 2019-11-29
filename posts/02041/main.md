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
<h2>有限MDPの定式化</h2>
<ul>
 	<li>離散状態の集合<span style="color: #ff0000;">[latex]\\mathcal{S}= \\{s_i | i=1,2,\\dots,N \\}[/latex]</span>を考える
<ul>
 	<li>状態が連続の場合は離散化
<ul>
 	<li>[latex]\\mathcal{X}[/latex]を区切る</li>
</ul>
</li>
</ul>
</li>
 	<li>制御出力
<ul>
 	<li>何種類かから選択<span style="color: #ff0000;">[latex]\\mathcal{A} = \\{ a_j | j = 1,2,\\dots,M \\}[/latex]</span></li>
 	<li>連続系の[latex]\\mathcal{U}[/latex]から何種類か選んで有限個に</li>
</ul>
</li>
 	<li>状態遷移
<ul>
 	<li><span style="color: #ff0000;">[latex]s' \\sim P(s' | s,a)[/latex]</span>
<ul>
 	<li>[latex]s,s'[/latex]はそれぞれ遷移前、遷移後の状態を示す</li>
</ul>
</li>
</ul>
</li>
</ul>
