# 確率ロボティクス2016第2回
<h1 style="font-size: 250%;">確率ロボティクス</h1>
<h2>第2回</h2>
上田 隆一

2016年9月28日\@千葉工業大学

$\require{\amsmath}$
$\require{\amssymb}$

<!--nextpage-->
<h2>今日の内容</h2>
<ul>
 	<li>定式化の続き</li>
 	<li>制御と状態</li>
</ul>
<!--nextpage-->
<h2>前回</h2>
<ul>
 	<li>状態について考えた
<ul>
 	<li>状態空間\(\\mathcal{X}\)</li>
 	<li>状態\(\\boldsymbol{x} = (x_1,x_2,\\dots,x_n) \\in \\mathcal{X}\)</li>
 	<li>状態変数\(x_1,x_2,\\dots,x_n\)</li>
</ul>
</li>
 	<li>制御の上で区別すべきものを考慮して状態を定義すべき</li>
</ul>
<!--nextpage-->
<h2>今回</h2>
<ul>
 	<li>制御出力</li>
 	<li>確率的な表現
<ul>
 	<li>状態は分からなくなる</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>状態を動かす</h2>
<ul>
 	<li>状態は変化（遷移）する</li>
 	<li>時刻の導入
<ul>
 	<li>ディジタルの計算機を使うときは基本、離散系で考えてよい</li>
 	<li>\(\\boldsymbol{x}_0,\\boldsymbol{x}_1,\\dots,\\boldsymbol{x}_t,\\dots\)（\(t\):時刻）
<ul>
 	<li>（この表記だと\(x\)が太字か細字かで添字の意味が違うので注意）</li>
 	<li>（わかりにくくてごめんなさい）</li>
</ul>
</li>
</ul>
</li>
 	<li>状態が変化する原因
<ul>
 	<li>自分（行動決定する何か）が能動的に動かす</li>
 	<li>自分でないものが動かす</li>
</ul>
</li>
 	<li>とりあえず前者について考えましょう</li>
</ul>
<!--nextpage-->
<h2>制御出力</h2>
<ul>
 	<li>状態を動かすもの
<ul>
 	<li>\(\\boldsymbol{u} = (u_1,u_2,\\dots,u_m)\)</li>
 	<li>\(u_1,u_2,\\dots,u_m\): 制御変数</li>
</ul>
</li>
 	<li>制御出力空間
<ul>
 	<li>\(\\boldsymbol{u} \\in \\mathcal{U}\)</li>
</ul>
</li>
 	<li>制御出力を与えるもの
<ul>
 	<li>厳密に言うとロボットではない。ロボットは状態変数に含まれる</li>
 	<li><span style="color: #ffff00;">とりあえずエージェントと呼びましょう</span></li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>状態遷移</h2>
<ul>
 	<li>ある時刻の状態\(\\boldsymbol{x}_{t-1}\)でエージェントが制御出力\(\\boldsymbol{u}_t\)を
選んだら\(\\boldsymbol{x}_t\)に状態が変化</li>
 	<li>状態遷移の式（状態方程式）
<ul>
 	<li>\(\\boldsymbol{x}_t = f(\\boldsymbol{x}_{t-1},\\boldsymbol{u}_t)\)</li>
</ul>
</li>
 	<li>状態遷移関数
<ul>
 	<li>\(f: \\mathcal{X} \\times \\mathcal{U} \\longrightarrow \\mathcal{X}\)</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>状態方程式を考える</h2>
<ul>
 	<li>どれか一つ選んで定式化してみましょう。15分くらい。
<ul>
 	<li>前回同様、問題の定義ははっきりさせません。定式化の上で何か分からないことがあれば聞いていただければ適当に設定します。</li>
 	<li><a href="/?presenpress=確率ロボティクス2016第1回#/13" target="_blank" rel="noopener">ロボット1</a>
<ul>
 	<li>入力は移動量（何度回転して、何度直進する、等）にしましょう</li>
 	<li>満足いかない人はトルクで</li>
</ul>
</li>
 	<li><a href="/?presenpress=確率ロボティクス2016第1回#/14" target="_blank" rel="noopener">ロボット2</a>
<ul>
 	<li>入力はステップモータの周波数\(\\propto\)角速度</li>
 	<li>ステップモータじゃなくてDCモータならどうなる？</li>
</ul>
</li>
 	<li>上の二つでなかったら前回の資料から好きなものを・・・</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>ロボットは状態方程式通りに・・・</h2>
<ul>
 	<li><span style="color: #ffff00;">動かない</span></li>
 	<li>なぜ
<ul>
 	<li>雑音</li>
 	<li>状態方程式が甘い</li>
 	<li>そもそもエージェントが操作できない変数が存在</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>雑音の考慮</h2>
<ul>
 	<li>いくつかの定式化</li>
 	<li>線形な状態方程式
<ul>
 	<li>\(\\boldsymbol{x}_t = A \\boldsymbol{x}_{t-1} + B\\boldsymbol{u}_t +\\boldsymbol{\\varepsilon}_t \)</li>
</ul>
</li>
 	<li>非線形な方程式
<ul>
 	<li>\(\\boldsymbol{x}_t = f(\\boldsymbol{x}_{t-1},\\boldsymbol{u}_t) +\\boldsymbol{\\varepsilon}_t \)</li>
</ul>
</li>
 	<li><span style="color: #ffff00;">\(\\boldsymbol{x}_t\)が決定論的でなくなる</span>
<ul>
 	<li>上記のような数式では非決定論的なものが表現しづらい</li>
</ul>
</li>
</ul>

<!--nextpage-->
<h2>確率を用いた表現</h2>
<ul>
 	<li>状態遷移の書き方
<ul>
 	<li>\( \\boldsymbol{x}_t \\sim p(\\boldsymbol{x} | \\boldsymbol{x}_{t-1},\\boldsymbol{u}_t) \)
<ul>
 	<li>意味: \(\\boldsymbol{x}_{t-1}\)で\(\\boldsymbol{u}_t\)を選択したときの、遷移後の状態が
従う確率密度関数\(p(\\boldsymbol{x})\)に従って、\(\\boldsymbol{x}_t\)が決まる</li>
</ul>
</li>
</ul>
</li>
 	<li>依然\(\\boldsymbol{x}_t\)が実際には何なのかは分からない
<ul>
 	<li>分かるのは真の状態がどれなのかという<span style="color: #ffff00;">確率密度関数</span></li>
</ul>
</li>
 	<li>確率密度関数（<span style="color: #ffff00;">状態遷移確率</span>）を求める式
<ul>
 	<li>\(bel_t(\\boldsymbol{x}) = \\int_\\mathcal{X} p(\\boldsymbol{x} | \\boldsymbol{x}',\\boldsymbol{u}_t )bel_{t-1}(\\boldsymbol{x}') d\\boldsymbol{x}'\)</li>
 	<li>\(bel\): 状態に関する確率密度関数</li>
</ul>
</li>
</ul>

<!--nextpage-->
<h2>\(bel\)という表記</h2>
<ul>
 	<li>\(bel\): belief、信念
<ul>
 	<li><span style="color: #ffff00;">エージェントが持っている</span>、状態に対する理解</li>
 	<li>何か正解があるわけではなく、
エージェントが自身の知覚と知識で作り上げるもの</li>
</ul>
</li>
 	<li>知覚: 自身の制御出力、センサ入力</li>
 	<li>知識:制御出力、センサ入力と状態の関係
<ul>
 	<li>制御出力の場合は状態方程式</li>
</ul>
</li>
</ul>

<!--nextpage-->
<h2>\(bel\)の計算（ガウス分布）</h2>
<ul>
 	<li>問題
<ul>
 	<li>状態は一次元: \(x \\in \\Re\)</li>
 	<li>制御出力: 状態の変位\(\\Delta_t\)
<ul>
 	<li>\(x\)から\(x + \\Delta_t + \\epsilon\)に移動
<ul>
 	<li>雑音\(\\epsilon\)は標準偏差\(\\delta_t\)でガウス分布に従う</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
 	<li><span style="color: #ffff00;">\(bel_t\)を以下から導出してみましょう（かなり難しい）</span>
<ul>
 	<li>\(bel_{t-1}(x) = \\frac{1}{\\sqrt{2\\pi \\sigma_{t-1}^2}}\\exp \\{-\\frac{(x-\\hat{x}_{t-1})^2}{2\\sigma_{t-1}^2}\\}\)
<ul>
 	<li>\(\\hat{x}_{t-1}: t-1\)における分布の中心（状態の推定値）</li>
 	<li>\(\\sigma_{t-1}: t-1\)における分布の標準偏差</li>
</ul>
</li>
 	<li>\(p(\\boldsymbol{x} | \\boldsymbol{x}_{t-1},\\Delta_t) =\\frac{1}{\\sqrt{2\\pi \\delta_t^2}}\\exp \\{-\\frac{(x-x_{t-1}-\\Delta_t)^2}{2\\delta_t^2}\\}\)</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>\(bel\)の式にガウス分布を代入</h2>
\(bel_t(x) = \\int_{-\\infty}^{\\infty} \\frac{1}{\\sqrt{2\\pi\\delta_t^2}}e^{-\\frac{1}{2\\delta_t^2}(x - x_{t-1} - \\Delta_t)^2}\\frac{1}{\\sqrt{2\\pi\\sigma_{t-1}^2}}e^{-\\frac{1}{2\\sigma_{t-1}^2}(x_{t-1} - \\hat{x_{t-1}})^2}dx_{t-1}\\\\= \\eta\\int_{-\\infty}^{\\infty} e^{\\frac{-1}{2}L}dx_{t-1}\\\\\)
<ul>
 	<li>ここで
<ul>
 	<li>\(\\eta\)は定数項</li>
 	<li>\(L\)は指数部の\(-1/2\)を除く部分</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>\(L\)から\(x_{t-1}\)を分離</h2>
\( L = \\frac{1}{\\delta_t^2}(x - x_{t-1} - \\Delta_t)^2 + \\frac{1}{\\sigma_{t-1}^2}(x_{t-1} - \\hat{x_{t-1}})^2 \\\\
= \\frac{\\sigma_{t-1}^2 + \\delta_t^2}{\\sigma_{t-1}^2\\delta_t^2}\\left\\{ x_{t-1} - \\frac{\\sigma_{t-1}^2(x - \\Delta_t) + \\delta_t^2\\hat{x_{t-1}}}{\\sigma_{t-1}^2 + \\delta_t^2}\\right\\}^2 + \\frac{(x - \\hat{x_{t-1}} - \\Delta_t)^2}{\\sigma_{t-1}^2 + \\delta_t^2}\\\\\)

<span style="color: #00ffff;">左側と右側の項</span><span style="color: #00ffff;">をそれぞれ\(L(x_{t-1},x),L(x)\)とおきましょう</span>

&nbsp;
<h2><!--nextpage--></h2>
<h2>再び\(bel_t\)の式に代入</h2>
\(bel_t(x) = \\eta\\int_{-\\infty}^{\\infty} e^{\\frac{-1}{2}L}dx_{t-1}\\\\
=\\eta\\int_{-\\infty}^{\\infty} e^{- \\frac{1}{2}L(x_{t-1},x) - \\frac{1}{2} L(x)}dx_{t-1}\\\\
=\\eta e^{-\\frac{1}{2} L(x)}\\int_{-\\infty}^{\\infty} e^{- \\frac{1}{2}L(x_{t-1},x)}dx_{t-1}\\\\
=\\eta e^{-\\frac{1}{2}\\frac{(x - \\hat{x_{t-1}} - \\Delta_t)^2}{\\sigma_{t-1}^2 + \\delta_t^2}}\\int_{-\\infty}^{\\infty} e^{- \\frac{1}{2}\\frac{\\sigma_{t-1}^2 + \\delta_t^2}{\\sigma_{t-1}^2\\delta_t^2}\\left\\{ x_{t-1} - \\frac{\\sigma_{t-1}^2(x - \\Delta_t) + \\delta_t^2\\hat{x_{t-1}}}{\\sigma_{t-1}^2 + \\delta_t^2}\\right\\}^2}dx_{t-1} \\\\\)

<span style="color: #ffff00;">積分の部分がガウス分布の積分の形になっており定数となる。\(\\eta\)に入れてしまう</span>
<h2><!--nextpage--></h2>
<h2>結局\(bel_t\)は・・・</h2>
\(bel_t(x) = \\eta \\exp\\left\\{-\\frac{(x - \\hat{x_{t-1}} - \\Delta_t)^2}{2(\\sigma_{t-1}^2 + \\delta_t^2)}\\right\\} = \\mathcal{N}(\\hat{x_{t-1}} + \\Delta_t,\\sigma_{t-1}^2 + \\delta_t^2)\)
<ul>
 	<li>\(bel_t\)は再びガウス分布となる
<ul>
 	<li>分布の中心: 元の移動量に制御出力の値を加えた値</li>
 	<li>分散: 移動の雑音の分散に元の（\(bel_{t-1}\)の）分散を足した値</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>\(bel\)の計算（数値計算）</h2>
<ul>
 	<li>ガウス分布のように計算前後が同じ分布になるものでない場合
<ul>
 	<li>どうすんの？</li>
</ul>
</li>
 	<li>乱数を使った数値計算で近似的に解く
<ul>
 	<li>式を解くよりはこっちの方が簡単なことが多い</li>
 	<li>計算量や近似精度の問題がつきまとう</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>モンテカルロ法を使った\(bel\)の計算</h2>
<ul>
 	<li>手を動かしてみましょう
<ul>
 	<li> 先ほどと同じ問題で
<ul>
 	<li>制御出力: \(\\Delta_t\)</li>
 	<li>誤差: \(\\delta_t\)</li>
</ul>
</li>
</ul>
</li>
 	<li>以下をExcelかプログラミングで何度も繰り返してみる
<ul>
 	<li>\(x = 0\)に点を打つ</li>
 	<li>\(\\Delta = 1,\\delta = 0.1\)として乱数を一つ選んで移動量とし、\(x\)を移動
<ul>
 	<li>簡易的なガウス乱数の作り方: 区間\([0,1]\)から
12個の数字を一様乱数を選んで足し、6を引くと
\(\\mathcal{N}(0,1)\)にほぼ従う乱数が得られる</li>
</ul>
</li>
 	<li>数ステップ\(x\)を動かしてみる（\(t=1,2,3\)と3ステップ程度）</li>
</ul>
</li>
 	<li>1,2,3ステップ後の分布はガウス分布？分散は？</li>
</ul>
<h2><!--nextpage--></h2>
<h2>格子を使った\(bel\)の計算</h2>
<ul>
 	<li>\(bel\)の表現
<ul>
 	<li>状態空間を格子状に区切る
<ul>
 	<li>\(s_1,s_2,s_3,\\dots,s_N \\subset \\mathcal{X}\)
<ul>
 	<li>\(\\bigcap_{i=1}^N s_i = \\phi\)</li>
 	<li>\(\\bigcup_{i=1}^N s_i = \\mathcal{X}\)</li>
</ul>
</li>
</ul>
</li>
 	<li>各格子に確率を割り当て
<ul>
 	<li>P(s_i)
<ul>
 	<li>\(\\sum_{i=1}^N P(s_i) = 1\)</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
 	<li>これも今までと同じ問題で手を動かしてみましょう
<ul>
 	<li>次ページ</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<ul>
 	<li>\(0.1\)刻みで数直線上に区間を作る
<ul>
 	<li>どこかの区間の確率を1に。他を0に。</li>
</ul>
</li>
 	<li> 以下をExcelかプログラミングで何度も繰り返してみる
<ul>
 	<li>\(\\Delta = 1\)だけ分布を動かす
<ul>
 	<li>雑音\(\\delta = 0.1\)の量だけ分布をぼかす
<ul>
 	<li>方法は議論のこと</li>
</ul>
</li>
 	<li>ある区間から移動した確率は二つ以上の区間にまたがる</li>
</ul>
</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>2次元以上な系・かつ非線形な系</h2>
<ul>
 	<li>数式を解く場合
<ul>
 	<li>行列、線形化</li>
</ul>
</li>
 	<li> 数値計算
<ul>
 	<li>自然に拡張可能</li>
 	<li>計算量が増える</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>移動ロボットにおける非線形な系</h2>
<ul>
 	<li>この資料（昨年の講義の第2回資料）の4,5,15ページ
<ul>
 	<li><a href="http://www.slideshare.net/ryuichiueda/ss-53672127" target="_blank" rel="noopener">http://www.slideshare.net/ryuichiueda/ss-53672127</a></li>
 	<li>普通の移動ロボットでも回転がある関係で非線形に</li>
</ul>
</li>
 	<li>線形化は必要？数値計算でいいのでは？
<ul>
 	<li>（残念ながら）graph-based SLAMの実装等で出てくる</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>雑音がガウス分布に従う場合の\(bel\)の導出</h2>
<ul>
 	<li>おさらい
<ul>
 	<li> 線形な状態方程式
<ul>
 	<li>\(\\boldsymbol{x}_t = A \\boldsymbol{x}_{t-1} + B\\boldsymbol{u}_t +\\boldsymbol{\\varepsilon}_t \)</li>
</ul>
</li>
 	<li><span style="color: #ffff00;">非線形な方程式（行列で書けない）</span>
<ul>
 	<li>\(\\boldsymbol{x}_t = f(\\boldsymbol{x}_{t-1},\\boldsymbol{u}_t) +\\boldsymbol{\\varepsilon}_t \)</li>
</ul>
</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>\(f\)を線形化</h2>
<ul>
 	<li>姿勢の推定値\(\\boldsymbol{\\hat{x}}_{t-1}\)まわりでテイラー展開
<ul>
 	<li>\( f(\\boldsymbol{x},\\boldsymbol{u}) = f(\\boldsymbol{\\hat{x}}_{t-1},\\boldsymbol{u}) + \\frac{\\partial f(\\boldsymbol{x},\\boldsymbol{u})}{\\partial\\boldsymbol{x}}\\big|_{\\boldsymbol{\\hat{x}}_{t-1}} (\\boldsymbol{x} - \\boldsymbol{\\hat{x}}_{t-1}) \)</li>
 	<li>この式は\(\\boldsymbol{x}\)の線形式になっている</li>
 	<li>\(\\boldsymbol{x}\): \(n\)次元の状態ベクトル</li>
 	<li>\(\\frac{\\partial f(\\boldsymbol{x},\\boldsymbol{u})}{\\partial\\boldsymbol{x}}\): ヤコビ行列
<ul>
 	<li>\(n\\times n\)行列</li>
</ul>
</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>状態方程式の書き換え</h2>
<ul>
 	<li>\(F_t = \\frac{\\partial f(\\boldsymbol{x},\\boldsymbol{u})}{\\partial\\boldsymbol{x}}\\big|_{\\boldsymbol{\\hat{x}}_{t-1},\\boldsymbol{u}_t}\)とする
<ul>
 	<li>確率ロボティクスだと\(G_t\)になっている</li>
</ul>
</li>
 	<li>\(\\boldsymbol{x}_t = f(\\boldsymbol{x}_{t-1},\\boldsymbol{u}_t) +\\boldsymbol{\\varepsilon}_t \)に前のページで得た\(f\)を代入
<ul>
 	<li>\(\\boldsymbol{x}_t = f(\\boldsymbol{\\hat{x}}_{t-1},\\boldsymbol{u}_t) + F_t(\\boldsymbol{x}_{t-1} - \\boldsymbol{\\hat{x}}_{t-1}) +\\boldsymbol{\\varepsilon}_t\)</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>状態遷移確率</h2>
<ul>
 	<li>\(p(\\boldsymbol{x} | \\boldsymbol{x}_{t-1},  \\boldsymbol{u}_t ) \\approx \\eta e^{ -\\frac{1}{2} \\left[\\boldsymbol{x} -f(\\boldsymbol{\\hat{x}}_{t-1},\\boldsymbol{u}_t) - F_t(\\boldsymbol{x}_{t-1} - \\boldsymbol{\\hat{x}}_{t-1})  \\right]^T  R_t^{-1}\\left[\\boldsymbol{x} - f(\\boldsymbol{\\hat{x}}_{t-1},\\boldsymbol{u}_t) -F_t(\\boldsymbol{x}_{t-1} - \\boldsymbol{\\hat{x}}_{t-1}) \\right]  }\)
<ul>
 	<li>\(\\boldsymbol{x}\): 移動後の状態の候補</li>
 	<li>\(f(\\boldsymbol{\\hat{x}}_{t-1},\\boldsymbol{u}_t)\): 移動前の推定位置から予測される移動後の状態</li>
 	<li>\(\\boldsymbol{x}_{t-1} - \\boldsymbol{\\hat{x}}_{t-1}\): 移動前の姿勢（左辺で指定）と移動前の推定姿勢の差</li>
 	<li>\(R_t\): \(\\boldsymbol{\\varepsilon}_t\)に対応する共分散行列</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>導出される\(bel_t\)</h2>
<ul>
 	<li>移動前の\(bel_{t-1}\)が次のとき
<ul>
 	<li>分布の形状: 多変量ガウス分布</li>
 	<li>中心: \(\\boldsymbol{\\hat{x}}_{t-1}\)</li>
 	<li>共分散: \(\\hat\\Sigma_{t-1}\)</li>
</ul>
</li>
 	<li>移動後の\(bel_t\)は
<ul>
 	<li>中心: \(f(\\boldsymbol{\\hat{x}}_{t-1},\\boldsymbol{u}_t) + F_t(\\boldsymbol{\\hat{x}}_{t-1} - \\boldsymbol{\\hat{x}}_{t-1}) = f(\\boldsymbol{\\hat{x}}_{t-1},\\boldsymbol{u}_t)\)
<ul>
 	<li>移動前の平均値を素直に移動</li>
</ul>
</li>
 	<li>共分散: \(F_t\\hat\\Sigma_{t-1}F_t^T + R_t\)
<ul>
 	<li>共分散行列を回転して雑音を足しているだけ</li>
</ul>
</li>
</ul>
</li>
</ul>
