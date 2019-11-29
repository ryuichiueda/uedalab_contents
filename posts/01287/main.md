<h1 style="font-size: 250%;">確率ロボティクス</h1>
<h2>第1回</h2>
上田 隆一

2016年9月?日\@千葉工業大学

<!--nextpage-->
<h2>今日の内容</h2>
<ul>
 	<li>動機付け（なんでこの講義があるのか）</li>
 	<li>定式化</li>
</ul>
<!--nextpage-->
<h2>講義の内容</h2>
<ul>
 	<li>第1回: 確率ロボティクスとは（今回）
<ul>
 	<li>後半、理論の話をします</li>
</ul>
</li>
 	<li>第2回: デッドレコニング</li>
 	<li>第3回: センサ計測をパーティクルの分布に反映させる方法</li>
 	<li>第4回: センサ情報処理の実装</li>
 	<li>第5回: リサンプリング、リセット</li>
</ul>
<h2><!--nextpage--></h2>
<ul>
 	<li>第6回: マルコフ決定過程</li>
 	<li>第7回: 価値反復</li>
 	<li>第8回: 強化学習</li>
 	<li>第9回: POMDP</li>
 	<li>第10回: POMDPに対する実装の例</li>
</ul>
<h2><!--nextpage--></h2>
<ul>
 	<li>第11回: SLAM</li>
 	<li>第12回: オンラインSLAM</li>
 	<li>第13回: オフラインSLAM</li>
 	<li>第14回: 課題についての議論と解説</li>
 	<li>第15回: まとめ</li>
</ul>
<h2><!--nextpage--></h2>
<h2>進め方</h2>
<ul>
 	<li>式を説明して練習問題を解くような形式で進める予定
<ul>
 	<li>古典的、基礎的なところを重視</li>
 	<li>講師の個人的な事情もあり・・・</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>テスト・レポート等</h2>
<ul>
 	<li>課題は2回
<ul>
 	<li>各20点（＋α）</li>
</ul>
</li>
 	<li>テストは1回
<ul>
 	<li>60点</li>
</ul>
</li>
 	<li>出席
<ul>
 	<li>8回以上で成績をつける対象</li>
 	<li>遅刻、早退は0.5回とカウント</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>参考図書</h2>
<ul>
 	<li>Thrun et al.: Probabilistic ROBOTICS, MIT press, 2005.</li>
 	<li>Bishop: Pattern Recognition and Machine Learning, Springer, 2006.</li>
</ul>
<!--nextpage-->
<h2>さっそく始めましょう</h2>
<ul>
 	<li>まずは「状態」について考えます</li>
</ul>
<!--nextpage-->
<h2>ロボットの問題を一般的に表す</h2>
<ul>
 	<li>ロボットの研究によくある登場人物
<ul>
 	<li>ロボット、環境、障害物（動くもの、動かないもの）、人・・・</li>
 	<li><span style="color: #ffff00;">どうやって数式で表すか？</span></li>
</ul>
</li>
 	<li>ポイント
<ul>
 	<li>物理法則に支配されている</li>
 	<li>ただ、ロボットは自分の判断で状況を変えることができる</li>
 	<li><span style="color: #ffff00;">ロボットの体は</span>環境の一部か否か
<ul>
 	<li>「判断する何か」から見たら<span style="color: #ffff00;">環境の一部</span></li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>世界の表現</h2>
<ul>
 	<li>とりあえず「判断する何か」はおいておき、目の前に存在する世界を表現しましょう
<ul>
 	<li>表現できないとプログラムも書けない</li>
</ul>
</li>
 	<li>ロボットでよく使われる表現
<ul>
 	<li>コンフィグレーション空間
<ul>
 	<li>ロボットアーム等の関節各の組み合わせでロボットの姿勢を表現</li>
</ul>
</li>
 	<li>タイルワールド
<ul>
 	<li>将棋のマス目のように環境を分割</li>
</ul>
</li>
 	<li><span style="color: #ffff00;">状態空間</span>
<ul>
 	<li>制御で使われる</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2> 状態空間と状態</h2>
<ul>
 	<li>状態空間
<ul>
 	<li>制御中の全局面（状態）の集合で構成</li>
 	<li>[latex]\\mathcal{X}[/latex]で表しましょう</li>
</ul>
</li>
 	<li>状態の一般的な表現
<ul>
 	<li>n個の<span style="color: #ffff00;">状態変数</span>で表現</li>
 	<li>状態空間との関係性: [latex]\\boldsymbol{x} \\in \\mathcal{X} [/latex]</li>
 	<li>[latex]\\boldsymbol{x} = (x_1,x_2,x_3,\\dots,x_n)[/latex]</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>状態を定義してみましょう</h2>
<ul>
 	<li>次のページから挙げるロボットの状態を定義してみましょう
<ul>
 	<li> ポイント
<ul>
 	<li><span style="color: #ffff00;">同じ[latex]\\boldsymbol{x}[/latex]が別の状態を指さないようにする</span></li>
 	<li><span style="color: #ffff00;">問題は厳密なものではありません</span>
<ul>
 	<li>こういう場合はこうなる、みたいな議論を</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>移動ロボット1</h2>
<ul>
 	<li>平面上をゆっくり動く</li>
</ul>
<iframe src="https://www.youtube.com/embed/XozlE7fuTso" width="560" height="315" frameborder="0" allowfullscreen="allowfullscreen"></iframe>

<!--nextpage-->
<h2>移動ロボット2</h2>
<ul>
 	<li>速く走る</li>
 	<li>できることは壁沿い走行だけ</li>
</ul>
<iframe src="https://www.youtube.com/embed/nNwKVeCqjus" width="560" height="315" frameborder="0" allowfullscreen="allowfullscreen"></iframe>

<!--nextpage-->
<h2>移動ロボット3</h2>
<ul>
 	<li>平面上を動く</li>
 	<li>全方位移動機構
<ul>
 	<li><span style="color: #ffff00;">[latex]x,y[/latex]はともかく、向きはどうしましょうか？？？</span></li>
 	<li>速度はどうする？</li>
</ul>
</li>
</ul>
<iframe src="https://www.youtube.com/embed/CHbAPKXKB6M" width="560" height="315" frameborder="0" allowfullscreen="allowfullscreen"></iframe>

<!--nextpage-->
<h2>マニピュレータ</h2>
<iframe src="https://www.youtube.com/embed/p8Fi3NZNtnQ" width="560" height="315" frameborder="0" allowfullscreen="allowfullscreen"></iframe>
<ul>
 	<li>麻雀牌はどうする？</li>
</ul>
<!--nextpage-->
<h2>生物</h2>
<iframe src="https://www.youtube.com/embed/W-IsVwURoDA" width="560" height="315" frameborder="0" allowfullscreen="allowfullscreen"></iframe>

<!--nextpage-->
<h2>バリエーション</h2>
<ul>
 	<li>移動ロボットがビルの各フロアを行き来するときはどうする？</li>
 	<li>移動ロボットが螺旋状にフロアがつながっている建物を移動するときはどうする？
<ul>
 	<li>表参道ヒルズのような</li>
</ul>
</li>
</ul>
