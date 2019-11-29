<h1 style="font-size: 250%;">確率ロボティクス</h1>
<h2>第9回</h2>
上田 隆一

2016年11月30日\@千葉工業大学

<!--nextpage-->
<h2>本日の内容</h2>
<ul>
 	<li>強化学習（古典的なもの）</li>
 	<li>参考:<a href="https://www.amazon.co.jp/dp/4627826613" target="_blank"> Sutton and Barto, 三上, 皆川訳: 強化学習, 森北出版, 2000.</a>
<ul>
 	<li><a href="http://webdocs.cs.ualberta.ca/~sutton/book/ebook/the-book.html" target="_blank">ウェブ版 </a></li>
 	<li><a href="https://webdocs.cs.ualberta.ca/~sutton/book/the-book-2nd.html" target="_blank">そろそろ第2版が出るらしい</a></li>
</ul>
</li>
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
 	<li>ある確率分布に従って状態遷移する</li>
 	<li>ある法則に従って報酬が与えられる</li>
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
 	<li>左辺の「[latex]\\max_{a \\in \\mathcal{A} }[/latex]」を満たすものが最適方策[latex]\\pi^*[/latex]</li>
</ul>
</li>
</ul>
</li>
 	<li><span style="color: #ff0000;">エージェントの「経験」</span>
<ul>
 	<li>状態遷移: ある状態[latex]s[/latex]で行動[latex]a[/latex]を選択したら状態[latex]s'[/latex]に遷移して報酬を得た</li>
 	<li>たくさん行動すれば統計的な性質が得られる</li>
 	<li>たくさん行動しなければ統計的な性質が得られない</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>問題の難しさ</h2>
<ul>
 	<li>価値関数に停留点が一つでもあると、エージェントがその場に留まってしまう</li>
 	<li>膨大な試行が必要</li>
</ul>
<!--nextpage-->
<h2>経験からの方策評価</h2>
<ul>
 	<li>とりあえず決定論的な方策[latex]\\pi : \\mathcal{S} \\to \\mathcal{A}[/latex]に対して、
経験から価値関数を求めてみましょう</li>
 	<li> モンテカルロ法を利用
<ul>
 	<li>効率はとりあえず気にしない</li>
</ul>
</li>
 	<li>次のように計算
<ul>
 	<li>次の試行・手続きを十分繰り返す
<ul>
 	<li>エージェントを[latex]\\pi[/latex]で終端状態まで動かす</li>
 	<li>状態遷移・報酬を観測</li>
 	<li>この試行で通ったところの価値を求める</li>
</ul>
</li>
 	<li>各状態、各試行で求めた価値を平均</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>方策を求めるには</h2>
<ul>
 	<li>方策が与えられない場合
<ul>
 	<li>何か適当な初期の方策を与えて価値関数がよくなるように方策を改善していけば良い</li>
 	<li>でもどうやって行動を選ぶのか？</li>
</ul>
</li>
 	<li>価値をもう一種類考えるとやりやすい
<ul>
 	<li>行動価値関数: [latex]Q^{\\pi}(s,a)[/latex]
<ul>
 	<li>方策[latex]\\pi[/latex]の下、状態[latex]s[/latex]で行動[latex]a[/latex]を選択することの価値</li>
 	<li>[latex]V^{\\pi}(s) = \\max_a Q^{\\pi}(s,a)[/latex]</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>手順（方策オン型）</h2>
<ol>
 	<li>[latex]Q(s,a)[/latex]をnullで初期化</li>
 	<li>初期状態を適当に選んでエージェントを動かす</li>
 	<li>[latex]Q(s,a)[/latex]が一番良い行動[latex]a[/latex]（グリーディな行動）を選ぶ
<ul>
 	<li>たまに違うのを選ぶ（[latex]\\epsilon[/latex]-グリーディ方策）</li>
</ul>
</li>
 	<li>その試行における状態行動対の価値を計算</li>
 	<li>各状態の価値を、これまでの全試行の価値の平均値で更新
<ul>
 	<li>問題: [latex]\\epsilon[/latex]-グリーディー方策の価値が求まる</li>
</ul>
</li>
</ol>
<!--nextpage-->
<h2>手順（方策オフ型）</h2>
<ul>
 	<li>各試行の非グリーディな行動が混ざっている部分を価値の更新に使わない
<ul>
 	<li>終端状態から遡ってグリーディな行動だけとっていた部分だけ切り取って、そこの価値だけ更新</li>
</ul>
</li>
 	<li>問題: 無駄が多い</li>
</ul>
<!--nextpage-->
<h2>ブートストラップの導入</h2>
<ul>
 	<li>（強化学習での）ブートストラップ
<ul>
 	<li>以前に計算した遷移後の状態の価値を使って遷移前の状態の価値を求める</li>
</ul>
</li>
 	<li>つまり価値反復で行った手続きの一部</li>
</ul>
<!--nextpage-->
<h2>TD<span style="font-size: 80%;">（temporal difference）</span>学習</h2>
<ul>
 	<li>行動した時に次の式で価値を更新
<ul>
 	<li>[latex]V(s) \\longleftarrow (1-\\alpha)V(s) + \\alpha[r + \\gamma V(s')][/latex]
<ul>
 	<li>[latex]\\alpha[/latex]: ステップサイズパラメータと呼ばれる</li>
 	<li>[latex]\\gamma[/latex]: 割引率
<ul>
 	<li>移動等の問題の場合は1で考えておいて良い</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
 	<li>行動するたびに上の式で価値を更新</li>
 	<li>方策オン型（Sarsa）とオフ型（Q学習）</li>
</ul>
<!--nextpage-->
<h2>Sarsa</h2>
<ul>
 	<li>方策ON型TD学習</li>
 	<li>行動価値を学習
<ul>
 	<li>[latex]Q(s,a) ← (1-\\alpha )Q(s,a) + \\alpha[r + \\gamma Q(s',a')][/latex]</li>
</ul>
</li>
 	<li>手順
<ul>
 	<li>[latex]Q(s,a)[/latex]を初期化</li>
 	<li>[latex]\\epsilon[/latex]-グリーディ方策等から行動[latex]a[/latex]を選択</li>
 	<li>行動[latex]a[/latex]をとり、[latex]s'[/latex]に移った後、次の行動[latex]a'[/latex]を選択</li>
 	<li>上の式で[latex]Q(s,a)[/latex]を更新</li>
</ul>
</li>
</ul>
