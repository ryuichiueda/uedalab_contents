# 確率ロボティクス2016第5回
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
 	<li>ロボット（環境）の状態は制御出力により遷移
<ul>
 	<li>これまでの話と同じ</li>
 	<li>雑音が伴う</li>
</ul>
</li>
 	<li>状態をエージェントは観察できる
<ul>
 	<li>これまでとは違う</li>
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
</ul>
<!--nextpage-->
<ul>
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
 	<li><span style="color: #ff0000;">[latex]\\mathcal{S}= \\{s^{(i)} | i=1,2,\\dots,N \\}[/latex]</span></li>
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
</ul>
<!--nextpage-->
<ul>
 	<li><span style="color: #ff0000;">制御出力（行動）</span>
<ul>
 	<li>有限個の行動の集合から選択
<ul>
 	<li><span style="color: #ff0000;">[latex]\\mathcal{A} = \\{ a^{(j)} | j = 1,2,\\dots,M \\}[/latex]</span></li>
 	<li>連続系の[latex]\\mathcal{U}[/latex]から何種類か選んで有限個に</li>
</ul>
</li>
</ul>
</li>
 	<li>この資料では[latex]s_i,a_j[/latex]と書くときは時刻を表すことにします</li>
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
 	<li><span style="color: #ff0000;">時刻に依存しないと仮定しましょう</span></li>
</ul>
</li>
</ul>
</li>
 	<li>評価軸がいくつあっても実数に置き換えて一元化
<ul>
 	<li>例: 移動ロボットが水たまりを踏んだら1回につき3分のペナルティー、等</li>
</ul>
</li>
 	<li>[latex]R(s,a,s')[/latex]を<span style="color: #ff0000;">[latex]\\mathcal{R}^a_{ss'}[/latex]と表記</span></li>
</ul>
<!--nextpage-->
<h2>定式化（終端状態の評価）</h2>
<ul>
 	<li>どの終端状態に行くかも評価の対象</li>
 	<li><span style="color: #ff0000;">終端状態の価値</span>
<ul>
 	<li>[latex]V(s)\\in \\Re[/latex] where [latex]\\forall s \\in \\mathcal{S}_\\text{f}[/latex]</li>
 	<li>この値も[latex]\\mathcal{R}^a_{ss'}[/latex]と同じ評価軸の上にある</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>行動の評価</h2>
<ul>
 	<li>ある状態からスタートして、ある終端状態に入った時の評価の和</li>
 	<li>状態遷移と行動が[latex]s_0,a_1,s_1,a_2,\\dots,s_T[/latex]だったときの評価:
<ul>
 	<li><span style="color: #ff0000;">[latex]J(s_{0:T},a_{1:T})[/latex]</span> [latex] = \\mathcal{R}^{a_1}_{s_0s_1} +\\mathcal{R}^{a_2}_{s_1s_2} +\\mathcal{R}^{a_3}_{s_2s_3} + \\dots +\\mathcal{R}^{a_T}_{s_{T-1}s_T} + V(s_T)[/latex]
<span style="color: #ff0000;">[latex] = \\sum_{t=1}^T \\mathcal{R}^{a_t}_{s_{t-1}s_t} + V(s_T)  [/latex]</span></li>
 	<li>[latex]J(s_{0:T},a_{1:T})[/latex]は毎回違う
<ul>
 	<li>[latex]\\mathcal{P}^a_{ss'}[/latex]で、事後の状態[latex]s'[/latex]がばらつく</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>有限MDPでの最適な行動</h2>
<ul>
 	<li>[latex]J(s_{0:T},a_{1:T})[/latex]の期待値が最大になる行動決定則
<ul>
 	<li>毎回、事後状態がばらつくのにどうやって求めるの？</li>
 	<li>結構難しい
<ul>
 	<li>識別の問題なら判断は<span style="color: #ff0000;">1回</span></li>
 	<li>行動決定の場合は終端状態に至るまで<span style="color: #ff0000;">何度も</span>判断</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>状態のマルコフ性と最適性の原理</h2>
<ul>
 	<li>これまでなんとなく仮定してきた</li>
 	<li><span style="color: #ff0000;">[latex]\\mathcal{P}^a_{ss'}[/latex]が過去に依存しないこと</span>
<ul>
 	<li>違う時刻に同じ状態に来たら、同じ行動をとれば同じ確率分布で次の状態に遷移する</li>
</ul>
</li>
 	<li>これが成り立つと・・・
<ul>
 	<li>ある試行の状態遷移[latex]s_0,s_1,s_2,\\dots,s_N[/latex]のうち、どこを初期状態にしても、[latex]J(s_{0:T},a_{1:T})[/latex]の期待値を最大にする問題は、同じ問題になる。</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>状態の価値</h2>
<ul>
 	<li>[latex]J(s_{0:T},a_{1:T})[/latex]の期待値の最大値を考えてみる</li>
 	<li>先ほどの議論から、[latex]J(s_{0:T},a_{1:T})[/latex]の期待値の最大値が存在すると仮定すると、初期状態だろうがなかろうが、ある状態[latex]s[/latex]から先の行動決定を考えると、この期待値の最大値が存在するし、それは、その状態[latex]s[/latex]の関数となる</li>
 	<li>これをその状態の（エージェントが最適な行動を取った時の）「価値」と言う</li>
 	<li><span style="color: #ff0000;">終端状態の価値[latex]V(s) ( s \\in \\mathcal{S}_\\text{f})[/latex]を拡張して、状態空間全体の関数: [latex]V^*: \\mathcal{S} \\to \\Re[/latex]とする</span>
<ul>
 	<li>[latex]V^*[/latex]: 最適状態価値関数</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>価値の性質
（<span style="color: #ff0000;">ベルマン方程式</span>）</h2>
<ul>
 	<li><span style="color: #ff0000;">[latex]V^* (s) = \\max_{a\\in\\mathcal{A}} \\sum_{s' \\in \\mathcal{S}} \\mathcal{P}_{ss'}^a \\left[ V^*(s') + \\mathcal{R}_{ss'}^a \\right] [/latex]</span>
<ul>
 	<li>もし最適状態価値関数が存在するなら、ある状態[latex]\\forall s \\in \\mathcal{S}-\\mathcal{S}_\\text{f}[/latex]の値[latex]V^*(s)[/latex]は、以下の値を最大にする行動[latex]a \\in \\mathcal{A}[/latex]を選んだ時の値になる
<ul>
 	<li>[latex]s[/latex]から遷移した先の値[latex]V^*(s')[/latex]と、その状態遷移に対する評価[latex]\\mathcal{R}_{ss'}^a[/latex]を足した値を考える。遷移先は確率的にばらつくので、この値について[latex]\\mathcal{P}_{ss'}^a[/latex]で重み付き平均を求めたもの。</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>例</h2>
<ul>
 	<li>・・・黒板で</li>
</ul>
<!--nextpage-->
<h2>価値の計算（価値反復）</h2>
<ul>
 	<li>ある状態[latex]s[/latex]の[latex]V^*(s)[/latex]だけ分からない。あとの状態の[latex]V^*[/latex]の値は分かるという、都合の良い状況を考えてみましょう。
<ul>
 	<li>価値の計算式はベルマン方程式そのものとなる
<ul>
 	<li>[latex]V^* (s) =\\max_{a\\in\\mathcal{A}} \\sum_{s' \\in \\mathcal{S}} \\mathcal{P}_{ss'}^a \\left[ V^*(s') + \\mathcal{R}_{ss'}^a \\right] [/latex]</li>
</ul>
</li>
</ul>
</li>
 	<li><span style="color: #ff0000;">価値反復アルゴリズム</span>
<ul>
 	<li>この計算を[latex]\\forall s \\in \\mathcal{S} - \\mathcal{S}_\\text{f}[/latex]に対して何度も計算していく
<ul>
 	<li>（状態を適切に設定すると）<span style="color: #ff0000;">終端状態に（遷移数という意味で）近い状態から[latex]V^* (s)[/latex]の値が収束していく</span></li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>最適方策</h2>
<ul>
 	<li>最適状態価値関数が分かっていると、ベルマン方程式を成立させるための行動が求まる</li>
 	<li>最適な行動: [latex]\\text{argmax}_a \\sum_{s' \\in \\mathcal{S}} \\mathcal{P}_{ss'}^a \\left[ V^*(s') + \\mathcal{R}_{ss'}^a \\right] [/latex]</li>
 	<li><span style="color: #ff0000;">「最適方策」という関数:
[latex]\\qquad\\qquad\\pi^*: \\mathcal{S}-\\mathcal{S}_\\text{f} \\to \\mathcal{A}[/latex]
</span>を考える</li>
 	<li>最適方策は状態と行動を対にしたリストとなる
<ul>
 	<li>時刻は全く関係ない</li>
 	<li>[latex]\\pi^*[/latex]を知っているロボットは、置き直されたりタスクを妨害されたりしても、その後に自身の状態を知覚できれば、最適な行動をとることが可能</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>古典的な定式化との比較</h2>
<ul>
 	<li>経路計画問題を有限MDPで記述すると、確率的な遷移や途中の行動でのペナルティーや報酬を扱える</li>
 	<li>解析的な軌道生成の問題を有限MDPで記述すると、数値計算を行うことができる</li>
 	<li>ただし、いろいろ面倒なこともある
<ul>
 	<li>どうやって状態を離散化するか</li>
 	<li>数値計算の計算量を現実的なレベルに抑えるにはどうするべきか</li>
</ul>
</li>
</ul>
