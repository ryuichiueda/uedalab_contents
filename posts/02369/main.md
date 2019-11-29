<h1 style="font-size: 250%;">確率ロボティクス</h1>
<h2>第9回</h2>
上田 隆一

2016年11月30日\@千葉工業大学

<!--nextpage-->
<h2>本日の内容</h2>
<ul>
 	<li>強化学習</li>
</ul>
<!--nextpage-->
<h2>強化学習（reinforcement learning）</h2>
<ul>
 	<li>機械学習の一種
<ul>
 	<li>起源: 動物の心理学研究から<a href="https://www.jstage.jst.go.jp/article/sicejl1962/44/12/44_12_859/_article/-char/ja/" target="_blank">[宮崎2005]</a>
<ul>
 	<li>餌にありつけるような/危険を避けるような行動の学習</li>
</ul>
</li>
 	<li>最近ANN（人工ニューラルネットワーク）との組み合わせで脚光を浴びている</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>基本的な強化学習の問題</h2>
<ul>
 	<li>有限MDPでの行動決定の問題に一つ制限を与える
<ul>
 	<li>状態遷移と報酬が、行動しないと分からない。</li>
</ul>
</li>
 	<li>問題の定義
<ul>
 	<li>時刻: [latex]\\mathcal{T} = \\{t | t = 0,1,2,\\dots,T \\}[/latex]</li>
 	<li>状態: [latex]\\mathcal{S} = \\{s_i | i = 1,2,3,\\dots,N\\}[/latex]
<ul>
 	<li>うち、いくつかは終端状態の集合[latex]\\mathcal{S}_\\text{f}[/latex]に含まれる</li>
</ul>
</li>
 	<li>行動: [latex]\\mathcal{A} = \\{a_j | j = 1,2,3,\\dots,M\\}[/latex]</li>
 	<li>状態遷移や報酬は時不変だが自明でない
<ul>
 	<li>状態遷移（隠れている）: [latex]\\mathcal{P}_{ss'}^a: \\mathcal{S}\\times\\mathcal{S}\\times\\mathcal{A} \\to \\Re[/latex]</li>
 	<li>報酬（隠れている）: [latex]\\mathcal{R}_{ss'}^a: \\mathcal{S}\\times\\mathcal{S}\\times\\mathcal{A} \\to \\Re[/latex]</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>何を求めたいのか</h2>
<ul>
 	<li>（前回あんまり強調してませんでしたね・・・）</li>
 	<li><span style="color: #ff0000;">「最適方策」を求める</span></li>
 	<li>方策（二種類）
<ul>
 	<li>決定論的方策: [latex]\\pi : \\mathcal{S} \\to \\mathcal{A}[/latex]
<ul>
 	<li>状態が決まると行動が決まるもの</li>
</ul>
</li>
 	<li>確率的な方策: [latex]\\pi : \\mathcal{S}\\times \\mathcal{A} \\to \\Re[/latex]
<ul>
 	<li>状態[latex]s[/latex]において行動[latex]a[/latex]を選択する確率</li>
</ul>
</li>
</ul>
</li>
 	<li><span style="color: #ff0000;">最適方策は決定論的になる（理由は次のページに）</span>
<ul>
 	<li><span style="color: #ff0000;">[latex]\\pi^* : \\mathcal{S} \\to \\mathcal{A}[/latex]</span></li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>問題を解く道具</h2>
<ul>
 	<li>ベルマン方程式が成り立つ
<ul>
 	<li>[latex]V^*(s) = \\max_{a \\in \\mathcal{A} } \\sum_{s' \\in \\mathcal{S}}\\mathcal{P}_{ss'}^a [V^*(s') +\\mathcal{R}_{ss'}^a ][/latex]
<ul>
 	<li>[latex]V^*[/latex]: 最適状態価値関数</li>
 	<li>左辺の「[latex]\\max_{a \\in \\mathcal{A} }[/latex]」を満たすものが最適方策[latex]\\pi^*[/latex]となる</li>
</ul>
</li>
</ul>
</li>
 	<li><span style="color: #ff0000;">エージェントの「経験」</span></li>
</ul>
