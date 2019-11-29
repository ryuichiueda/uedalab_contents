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
