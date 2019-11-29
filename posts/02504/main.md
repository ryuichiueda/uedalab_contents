&nbsp;
<h1 style="font-size: 250%;">確率ロボティクス</h1>
<h2>第10回</h2>
上田 隆一

2016年12月7日\@千葉工業大学

<!--nextpage-->
<h2>本日の内容</h2>
<ul>
 	<li>POMDP</li>
</ul>
<!--nextpage-->
<h2>POMDP</h2>
<ul>
 	<li>部分観測マルコフ決定過程</li>
 	<li>状態が自明でない場合のマルコフ決定過程
<ul>
 	<li>センサ情報から得られるが、部分的</li>
</ul>
</li>
 	<li>ほぼ、自律型ロボットの問題と等価
<ul>
 	<li>状態が分かっているものをロボットと言うかどうか</li>
</ul>
</li>
 	<li>他者がいるとさらに問題が難しくなるが、
POMDPでは考えない/扱えない</li>
</ul>
<!--nextpage-->
<h2>定式化</h2>
<ul>
 	<li>状態が直接観測できず、観測から間接的に分かる
<ul>
 	<li>要は自己位置推定の問題に行動決定をくっつけたもの</li>
</ul>
</li>
 	<li>各シンボルの定義
<ul>
 	<li>時刻: [latex]\\mathcal{T} = \\{t | t=0,1,2,\\dots,T\\}[/latex]</li>
 	<li>状態: [latex]\\mathcal{S} = \\{s_i | i=1,2,3,\\dots,N\\}[/latex]
<ul>
 	<li>どんな状態があるかはknown、どの状態にいるかはunknown</li>
</ul>
</li>
 	<li>行動: [latex]\\mathcal{A} = \\{a_j | j=1,2,3,\\dots,M\\}[/latex]</li>
 	<li>状態遷移: [latex]\\mathcal{P}_{ss'}^a[/latex]</li>
 	<li>報酬: [latex]\\mathcal{R}_{ss'}^a[/latex]</li>
 	<li>観測: [latex]\\mathcal{O}[/latex]</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>問題の例</h2>
<ul>
 	<li>スイカ割り
<ul>
 	<li>自分とスイカの相対姿勢がはっきり分からない</li>
 	<li>他者からの情報で</li>
</ul>
</li>
 	<li>真っ暗なビルから脱出
<ul>
 	<li>壁に手をついて自己位置推定</li>
</ul>
</li>
 	<li>実はスイカ割りで目隠しを取っても、ビルに照明がついていても、我々は正確な位置計測ができている訳ではない
<ul>
 	<li>結局POMDP</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>自己位置推定の曖昧さ</h2>
<ul>
 	<li>例えばパーティクルフィルタでもカルマンフィルタでも<a href="https://lab.ueda.asia/wp-content/uploads/2016/12/particle_mean.png"><img class="alignright size-medium wp-image-2471" src="https://lab.ueda.asia/wp-content/uploads/2016/12/particle_mean-300x151.png" alt="particle_mean" width="300" height="151" /></a>
分布は常に広がりを持つ</li>
</ul>
<ul>
 	<li>広がっているときに平均値（と決定論的方策[latex]\\pi[/latex]）を信じて動くとどうなるか？</li>
 	<li>そもそも平均値が意味を持たないこともある</li>
 	<li style="color: white;"></li>
 	<li>平均値でなくてもっといい行動の選び方はないだろうか？</li>
</ul>
<!--nextpage-->
<h2>入力が信念の方策</h2>
<ul>
 	<li>エージェントが[latex]bel[/latex]から行動決定</li>
 	<li>状態空間の上で定義された方策ではなく、[latex]bel[/latex]が属する空間の上で定義された方策となる
<ul>
 	<li>「信念に対する方策」「信念方策」</li>
 	<li style="color: white;"></li>
</ul>
</li>
 	<li>どうやって求めるか？</li>
 	<li>そもそも求められるのか？</li>
</ul>
<!--nextpage-->
<h2>問題の大きさ</h2>
<ul>
 	<li>状態が100個、行動が2種類の場合</li>
 	<li>有限MDP
<ul>
 	<li>方策のパターンは[latex]2^{100}[/latex]通り</li>
 	<li>価値反復を使うと
<ul>
 	<li>[latex]O[/latex](状態数・行動数・タスクの長さ)で方策を計算可能</li>
</ul>
</li>
</ul>
</li>
 	<li>POMDP
<ul>
 	<li>[latex]bel[/latex]は100個の状態上で定義される関数
<ul>
 	<li>無限に存在</li>
</ul>
</li>
 	<li>無限にあるものに対する方策のパターンは無限</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>POMDPと
ハンドコーディング</h2>
<ul>
 	<li>例えば、パーティクルの分布から移動ロボットの行動を決めるコードを書いてみましょう
<ul>
 	<li>例えば脱輪したり縁石に乗り上げたりしないで、できるだけ早く角を曲がる場合を考えてみましょう</li>
 	<li>（たいていの場合）ほぼ無限に場合分けできる
<ul>
 	<li><span style="color: #ff0000;">疲れる</span></li>
 	<li>そもそも無理？</li>
 	<li style="color: white;"></li>
</ul>
</li>
</ul>
</li>
 	<li>豊富な研究テーマ<img class="alignright wp-image-2487" src="https://lab.ueda.asia/wp-content/uploads/2016/12/corner-300x110.png" alt="corner" width="403" height="157" /></li>
</ul>
<!--nextpage-->
<h2>対策</h2>
<ul>
 	<li>センサを強化</li>
 	<li style="color: white;"></li>
 	<li>観測戦略
<ul>
 	<li>位置の情報が得られそうな行動を能動的にとる</li>
</ul>
</li>
 	<li style="color: white;"></li>
 	<li>センサやアクチュエータの配置、ロボットの形状の工夫<span style="color: #ff0000;">（身体性）</span>
<ul>
 	<li>ぶつかっても壊れない</li>
 	<li>情報を得やすい位置にセンサをつける</li>
 	<li>情報を得やすい/情報がなくても動けるようにアクチュエータを選定して取り付け</li>
 	<li style="color: white;"></li>
</ul>
</li>
 	<li>計算でなんとか良い行動を見つける</li>
</ul>
<!--nextpage-->
<h2>計算でなんとか</h2>
<ul>
 	<li>だいたい以下のような方針になる</li>
 	<li>方法1:
<ul>
 	<li>[latex]bel[/latex]の形状一個一個を状態と皆して有限MDPのように問題を解く</li>
</ul>
</li>
 	<li>方法2:
<ul>
 	<li>事前に状態が既知の有限MDPの問題を解いて[latex]bel[/latex]からなんとか行動を得る</li>
 	<li>分布の平均値やその他代表値を1つ選んで行動決定するのもこの方法の単純な実装</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>方法1
<span style="font-size: 80%;">（AMDPと呼ばれる手法群）</span></h2>
<ul>
 	<li>信念の数を有限個に近似</li>
 	<li>例[Roy 99]
<ul>
 	<li>距離センサを持つ移動ロボットのナビゲーション問題</li>
 	<li>4次元の状態空間を作る
<ul>
 	<li>[latex]xy\\theta[/latex]を離散化</li>
 	<li>[latex]bel[/latex]がどれだけ曖昧か数値化して離散化</li>
 	<li>状態遷移はなんとか計算</li>
</ul>
</li>
 	<li>あとは価値反復等で計算</li>
 	<li style="color: white;"></li>
 	<li>得られる行動
<ul>
 	<li><span style="color: #ff0000;">自己位置が分からなくならないように壁沿いを走る</span></li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>方法2（[latex]Q_\\text{MDP}[/latex], 他）</h2>
<ul>
 	<li>有限MDPの計算結果を利用する
<ul>
 	<li>状態遷移の法則性が分かっているが、ロボットが自分の状態を完全に分からない場合に使える</li>
 	<li style="color: white;"></li>
</ul>
</li>
 	<li>例[Littman95]
<ul>
 	<li>確率密度関数[latex]bel[/latex]と価値関数[latex]V[/latex]から価値の期待値を計算</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>[latex]Q_\\text{MDP}[/latex]の例</h2>
<ul>
 	<li>碁盤の目の環境を考える
<ul>
 	<li><a href="https://lab.ueda.asia/wp-content/uploads/2016/12/qmdp.png"><img class="alignright wp-image-2501" src="https://lab.ueda.asia/wp-content/uploads/2016/12/qmdp-300x278.png" alt="qmdp" width="246" height="229" /></a>1マスが1状態</li>
 	<li>行動は上下左右</li>
 	<li>同じ重みを持ったパーティクル10個が分布</li>
 	<li>タスクはゴール（G）に最短歩数で到達すること</li>
 	<li>数字はコスト</li>
 	<li>灰色のところに入ろうとすると戻される</li>
</ul>
</li>
 	<li>問題: 一番「価値の高い」行動は？</li>
</ul>
<!--nextpage-->
<ul>
 	<li>この環境だとどうなる？<a href="https://lab.ueda.asia/wp-content/uploads/2016/12/qmpd2.png"><img class="alignright size-medium wp-image-2503" src="https://lab.ueda.asia/wp-content/uploads/2016/12/qmpd2-300x277.png" alt="qmpd2" width="300" height="277" /></a></li>
</ul>
&nbsp;
