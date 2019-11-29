# 確率ロボティクス2017第1回
<h1 style="font-size: 250%;">確率ロボティクス</h1>
<h2>第1回</h2>
上田 隆一

2017年9月20日\@千葉工業大学

<!--nextpage-->
<h2>今日の内容</h2>
<ul>
 	<li>動機付け（なんでこの講義があるのか）</li>
 	<li>定式化</li>
</ul>
<!--nextpage-->
<h2>移動ロボットの
ナビゲーション</h2>
<div style="float: left; width: 50%;">
<ul>
 	<li>ナビゲーション: 航海術</li>
 	<li>その昔、課題となったこと
<ul style="font-size: 85%;">
 	<li>どこにいるか知りたい</li>
 	<li>正確な地図を知りたい</li>
 	<li>安全で短い経路が知りたい</li>
</ul>
</li>
</ul>
</div>
<div style="float: left; width: 50%;">

<a href="https://commons.wikimedia.org/wiki/File:Chasing_the_light.jpg#/media/File:Chasing_the_light.jpg"><img src="https://upload.wikimedia.org/wikipedia/commons/6/68/Chasing_the_light.jpg" alt="Chasing the light.jpg" /></a>
<p style="font-size: 75%;">遭難したらおしまい</p>
<p style="font-size: 50%;">By <a class="extiw" title="en:George Grie" href="//en.wikipedia.org/wiki/George_Grie">George Grie</a> - <span class="int-own-work" lang="ja">投稿者自身による作品</span>, <a class="external autonumber" href="http://www.neosurrealismart.com" rel="nofollow">[1]</a>, <a title="Creative Commons Attribution-Share Alike 3.0" href="http://creativecommons.org/licenses/by-sa/3.0/">CC 表示-継承 3.0</a>, https://commons.wikimedia.org/w/index.php?curid=3298445</p>

</div>
<!--nextpage-->
<h2>ナビゲーション技術</h2>
<ul>
 	<li>自己位置推定</li>
 	<li>SLAM（simultaneous localization and mapping）</li>
 	<li>目的地までの経路探索</li>
</ul>
<iframe src="https://www.youtube.com/embed/A3FqZraWqX4" width="420" height="315" frameborder="0" allowfullscreen="allowfullscreen"></iframe>

<!--nextpage-->
<h2>最近（ここ20年）の考え方</h2>
<ul>
 	<li>確率論（ベイズ推論）の導入
<ul>
 	<li>自身の分かっていること/分かっていないことを
確率分布で表現<img style="border-style: none;" src="https://blog.ueda.asia/wp-content/uploads/2016/05/prob_representation.png" /></li>
 	<li>センサが良くなるまでのつなぎ扱いになることも</li>
</ul>
</li>
</ul>
<!--nextpage-->

<img src="https://blog.ueda.asia/wp-content/uploads/2016/05/prob_representation2.png" />

<!--nextpage-->
<h2>確率分布の記述</h2>
<ul>
 	<li>ガウス分布
<ul>
 	<li>カルマンフィルタ（1960年〜）</li>
</ul>
</li>
 	<li>格子地図
<ul>
 	<li>状態空間を切って格子一つ一つに確率を記述</li>
</ul>
</li>
 	<li>パーティクルフィルタ
<ul>
 	<li>確率分布から標本抽出した標本の分布で記述</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>よく使われるアルゴリズム</h2>
<ul>
 	<li>こちらが詳しいです
<ul>
 	<li><a href="http://myenigma.hatenablog.com" target="_blank" rel="noopener">MyEnigma | </a><a href="https://twitter.com/atsushi_twi" target="_blank" rel="noopener">\@Atsushi_twi</a></li>
</ul>
</li>
 	<li><a href="http://myenigma.hatenablog.com/entry/20140628/1403956852" target="_blank" rel="noopener">Monte Carlo Locaization</a>（MCL）</li>
 	<li>FastSLAM
<ul>
 	<li>MCLのパーティクルに地図を持たせたもの</li>
 	<li><iframe src="https://www.youtube.com/embed/EeW9OL1J9sM" width="560" height="315" frameborder="0" allowfullscreen="allowfullscreen"></iframe></li>
</ul>
</li>
</ul>
<!--nextpage-->
<ul>
 	<li>graph-based SLAM
<ul>
 	<li>精度行列（情報行列）に移動履歴やセンサでの
観測履歴を登録し、後で最も精度行列を操作して
ロボットの経路と地図を得る</li>
 	<li><iframe src="https://www.youtube.com/embed/nLEbJZFm5-E" width="560" height="315" frameborder="0" allowfullscreen="allowfullscreen"></iframe></li>
</ul>
</li>
</ul>
<!--nextpage-->
<ul>
 	<li>visual SLAM
<ul>
 	<li>画像の重ね合わせ</li>
 	<li>画像どうしの相対姿勢からカメラの経路を推定
（visual odometry）</li>
 	<li><iframe src="https://www.youtube.com/embed/XySrhZpODYs" width="560" height="315" frameborder="0" allowfullscreen="allowfullscreen"></iframe></li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>講義の内容</h2>
<ul>
 	<li>基本、シラバス通りですが、ちょっと手を動かす実習を増やしますので削るかもしれません。</li>
</ul>
<h2><!--nextpage--></h2>
<h2>進め方</h2>
<ul>
 	<li>式を説明してコードを書く</li>
 	<li>Jupyter Notebook</li>
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
 	<li>Jupyter Notebookのセットアップ
<ul>
 	<li>特にこだわりがなければanacondaをインストールすると使える
<ul>
 	<li><a href="https://www.anaconda.com/download/">https://www.anaconda.com/download/</a></li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>ロボットの問題を一般的に表す</h2>
<ul>
 	<li>ロボットの研究によくある登場人物
<ul>
 	<li>ロボット、環境、障害物（動くもの、動かないもの）、人・・・</li>
 	<li><span style="color: #ff0000;">どうやって数式で表すか？</span></li>
</ul>
</li>
 	<li>ポイント
<ul>
 	<li>物理法則に支配されている</li>
 	<li>ただ、ロボットは自分の判断で状況を変えることができる</li>
 	<li><span style="color: #ff0000;">ロボットの体は</span>環境の一部か否か
<ul>
 	<li>「判断する何か」から見たら<span style="color: #ff0000;">環境の一部</span></li>
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
 	<li><span style="color: #ff0000;">状態空間</span>
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
 	<li>n個の<span style="color: #ff0000;">状態変数</span>で表現</li>
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
 	<li><span style="color: #ff0000;">同じ[latex]\\boldsymbol{x}[/latex]が別の状態を指さないようにする</span>
<ul>
 	<li>これはロボットの知覚の問題</li>
 	<li>ロボットが「同じだ！」と思ってしまったら別の行動ができない</li>
 	<li>例: 雨が状態に考慮されていないと、ロボットは雨が降っても絶対に傘はささない</li>
</ul>
</li>
 	<li><span style="color: #ff0000;">問題は厳密なものではありません</span>
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
 	<li><span style="color: #ff0000;">[latex]x,y[/latex]はともかく、向きはどうしましょうか？？？</span></li>
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
 	<li>表参道ヒルズのような話</li>
</ul>
</li>
 	<li>人がロボットの周囲にたくさんいる</li>
</ul>
<!--nextpage-->
<h2>まとめ</h2>
<ul>
 	<li>何をしたいか、何をしても問題ないかで状態の定義は変わる
<ul>
 	<li>速度を状態変数に入れる/入れない
<ul>
 	<li>動的/準静的</li>
</ul>
</li>
 	<li>建物の階数を入れる/入れない
<ul>
 	<li>別のフロアで別の行動が潜在的に可能/不可能</li>
</ul>
</li>
 	<li>フレーム問題とも関係する話</li>
</ul>
</li>
 	<li>自分の体/他人の体に関する状態変数
<ul>
 	<li>制御できるかどうかを別にすると同じもの</li>
</ul>
</li>
 	<li>やわらかいものは難しい</li>
 	<li>・・・</li>
</ul>
<!--nextpage-->
<h2>次回</h2>
<ul>
 	<li>「状態の不確かさ」について考えます。</li>
</ul>
