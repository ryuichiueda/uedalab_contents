# 確率ロボティクス2016第8回
02242 <h1 style="font-size: 250%;">確率ロボティクス</h1>
<h2>第8回</h2>
上田 隆一

2016年11月16日\@千葉工業大学

<!--nextpage-->
<h2>本日の内容</h2>
<ul>
 	<li>有限MDPの問題を解きます</li>
</ul>
<!--nextpage-->
<h2>問題1</h2>
<ul>
 	<li>エージェントが図のようなグラフの環境を移動</li>
 	<li>エージェントは辺で結ばれたノードに1秒で移動可能</li>
 	<li>Gと書いてあるノードはゴール</li>
 	<li>各ノードに対して<span style="color: #ff0000;">価値反復で</span>価値を求めてみましょう。
<ul>
 	<li>価値はゴールまでの秒数</li>
</ul>
</li>
</ul>
<img class="alignright size-full wp-image-2247" src="https://lab.ueda.asia/wp-content/uploads/2016/11/questions1.png" alt="questions1" width="292" height="292" />

<!--nextpage-->
<h2>問題2</h2>
<ul>
 	<li>今度は、灰色のノードに水たまりがあるとします。</li>
 	<li>水たまりに入るペナルティーを[latex]R[/latex]とします。</li>
 	<li>以下の場合の各状態の価値を求めましょう。
<ul>
 	<li>[latex]R = 1[s][/latex]</li>
 	<li>[latex]R = 10[s][/latex]</li>
</ul>
</li>
</ul>
<a href="https://lab.ueda.asia/wp-content/uploads/2016/11/questions2.png"><img class="size-full wp-image-2251 alignright" src="https://lab.ueda.asia/wp-content/uploads/2016/11/questions2.png" alt="questions2" width="292" height="292" /></a>

<!--nextpage-->
<h2>問題3</h2>
<ul>
 	<li>今度は、移動するエッジを選んでノードを移る時に、他のエッジに間違って入ることがある場合を考えましょう。</li>
 	<li>間違える確率: 移動するエッジ以外のエッジがある場合、それらのエッジにそれぞれ10%の確率で入る
<ul>
 	<li>例: 4つエッジがあるノードの場合、正しく移動できる確率は70%、あとは10%ずつ間違えたエッジに入る</li>
</ul>
</li>
</ul>
<img class="alignright size-full wp-image-2247" src="https://lab.ueda.asia/wp-content/uploads/2016/11/questions1.png" alt="questions1" width="292" height="292" /><!--nextpage-->
<h2>問題4</h2>
<ul>
 	<li>今度は水たまりがある時について、問題3の遷移条件で解いてみましょう</li>
 	<li>水たまりのペナルティー
<ul>
 	<li>[latex]R = 1[s][/latex]</li>
 	<li>[latex]R = 10[s][/latex]</li>
 	<li>[latex]R = 100[s][/latex]</li>
</ul>
</li>
</ul>
<a href="https://lab.ueda.asia/wp-content/uploads/2016/11/questions2.png"><img class="size-full wp-image-2251 alignright" src="https://lab.ueda.asia/wp-content/uploads/2016/11/questions2.png" alt="questions2" width="292" height="292" /></a>

<!--nextpage-->
<h2>問題5<del></del></h2>
<ul>
 	<li>問題4の設定で、グラフにゴールを一つ加えます。</li>
 	<li>上下二つのゴールのうち、下のゴールの価値や水たまりのペナルティーの値を変えて価値関数を解いてみましょう。</li>
</ul>
<a href="https://lab.ueda.asia/wp-content/uploads/2016/11/questions3.png"><img class="size-medium wp-image-2263 alignright" src="https://lab.ueda.asia/wp-content/uploads/2016/11/questions3-215x300.png" alt="questions3" width="215" height="300" /></a>
