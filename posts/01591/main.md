<h1 style="font-size: 250%;">ロボットシステム学</h1>
<h2>第3回</h2>
上田 隆一

2016年9月?日\@千葉工業大学

<!--nextpage-->
<h2>今日の内容</h2>
<ul>
 	<li>マイコンの仕組み
<ul>
 	<li>本講義はOSの存在を前提としているので仕組みだけ簡単に</li>
 	<li>OSの説明のために知識だけ簡潔に</li>
</ul>
</li>
 	<li>OSの役割、仕組み</li>
</ul>
<!--nextpage-->
<h2>マイコン</h2>
<ul>
 	<li>この２つのモノの略語
<ul>
 	<li>マイクロコンピュータ
<ul>
 	<li>今で言うPC</li>
 	<li><a href="https://ja.wikipedia.org/wiki/%E3%82%B3%E3%83%A2%E3%83%89%E3%83%BC%E3%83%AB64" target="_blank">例（コモドール64）</a></li>
</ul>
</li>
 	<li><span style="color: #ffff00;">マイクロコントローラ</span>
<ul>
 	<li>ピンから様々な入出力ができるようになっているIC</li>
 	<li><a href="https://ja.wikipedia.org/wiki/Atmel_AVR" target="_blank">例（Atmel AVR）</a></li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>マイクロコントローラ</h2>
<ul>
 	<li>何のために使うか
<ul>
 	<li>（おそらく私より皆さんの方が詳しいでしょう）</li>
 	<li>デジタル回路に組み込んで使って機器を動かす
<ul>
 	<li>いくつかのピンから電気信号を入力</li>
 	<li>しかるべき電気信号を出力</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>マイコンが無いと・・・</h2>
<ul>
 	<li>回路の部分が増える、回路が増えると・・・
<ul>
 	<li>変更できない、基板の面積をとる、故障したら自分で直さなければならない、電圧・電流の計算面倒くさい、・・・</li>
</ul>
</li>
 	<li>計算の回路は本質的にややこしい
<ul>
 	<li>例: リレー式計算機
<iframe src="https://www.youtube.com/embed/WtzpbZUF2eg" width="560" height="315" frameborder="0" allowfullscreen="allowfullscreen"></iframe></li>
</ul>
</li>
 	<li>ソフトウェアで入出力の関係を実装できるのがマイコンの有り難み</li>
</ul>
<!--nextpage-->
<h2>とても簡単な例</h2>
<ul>
 	<li>簡単なLチカ回路
<ul>
 	<li>同じ回路で・・・
<ul>
 	<li>スイッチのON/OFFとLEDのON/OFFの関係を変更可能</li>
 	<li>LEDの明るさ等を変更可能</li>
</ul>
</li>
</ul>
</li>
</ul>
<a href="https://lab.ueda.asia/wp-content/uploads/2016/09/circuit-photo.jpg"><img class="size-medium wp-image-1487 alignnone" src="https://lab.ueda.asia/wp-content/uploads/2016/09/circuit-photo-295x300.jpg" alt="circuit-photo" width="295" height="300" />　</a><a href="https://lab.ueda.asia/wp-content/uploads/2016/09/circuit.jpg"><img class="size-medium wp-image-1486 alignnone" src="https://lab.ueda.asia/wp-content/uploads/2016/09/circuit-300x201.jpg" alt="circuit" width="300" height="201" /></a>  <a href="https://lab.ueda.asia/wp-content/uploads/2016/09/code.jpg"><img class="alignnone size-medium wp-image-1491" src="https://lab.ueda.asia/wp-content/uploads/2016/09/code-300x204.jpg" alt="code" width="300" height="204" /></a>

<!--nextpage-->
<h2>マイコンの中身</h2>
どうなっているのか？
<ul>
 	<li>大雑把に言って以下の3要素で構成される
<ul>
 	<li>メモリ</li>
 	<li>MPU（micro processing unit）</li>
 	<li>I/O（I/Oポート）</li>
</ul>
</li>
 	<li>3要素がバスでつながっている
<ul>
 	<li>例: <a href="http://www.atmel.com/ja/jp/devices/ATMEGA328P.aspx" target="_blank">ATmega328P</a>（Summaryの8ページ）</li>
 	<li><a href="https://avr.jp/user/Clog.htm#X3-28" target="_blank">日本語のデータシート</a></li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>メモリ</h2>
<ul>
 	<li>データやプログラムを置く</li>
 	<li>以下の3種が適所に配置されている</li>
</ul>
<table style="border: 1px solid #FFF;" width="687">
<tbody>
<tr>
<td style="border: 1px solid #FFF;" width="160"></td>
<td style="border: 1px solid #FFF;" width="193">用途</td>
<td style="border: 1px solid #FFF;" width="147">電源OFF後

のデータ</td>
<td width="200">動作の速さ</td>
</tr>
<tr>
<td style="border: 1px solid #FFF;" width="200">フラッシュメモリ</td>
<td style="border: 1px solid #FFF;" width="193">プログラム</td>
<td style="border: 1px solid #FFF;" width="147">残る</td>
<td style="border: 1px solid #FFF;" width="188">遅い</td>
</tr>
<tr>
<td style="border: 1px solid #FFF;" width="160">EEPROM</td>
<td style="border: 1px solid #FFF;" width="193">保存用データ</td>
<td style="border: 1px solid #FFF;" width="147">残る</td>
<td style="border: 1px solid #FFF;" width="188">遅い</td>
</tr>
<tr>
<td style="border: 1px solid #FFF;" width="160">SRAM</td>
<td style="border: 1px solid #FFF;" width="193">計算中のデータ等</td>
<td style="border: 1px solid #FFF;" width="147">消える</td>
<td style="border: 1px solid #FFF;" width="188">速い</td>
</tr>
</tbody>
</table>
<h2><!--nextpage--></h2>
<h2>メモリのアドレス</h2>
<ul>
 	<li>C言語に出てくるポインタでおなじみ</li>
 	<li>アドレス: 住所</li>
 	<li>アドレス空間: n個のメモリセルごとに住所をつけたもの
<ul>
 	<li>1個のメモリセルは0か1の1ビット情報を保持</li>
 	<li>8ビットなら8個のメモリセルに一つ住所を与える</li>
</ul>
</li>
 	<li>住所のつけ方
<ul>
 	<li>ひたすら無骨に0番からN番まで数字で</li>
 	<li>プログラムで操作するときは16進数になることが多いが、それはあんまり本質的ではない</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>MPUでの処理の流れ</h2>
<ul>
 	<li>これの繰り返し
<ol>
 	<li>命令をメモリから取得
<ul>
 	<li>命令: アセンブリ言語の1行に相当
<ul>
 	<li><span style="color: #00ffff;">「1番と5番のメモリの中身を足して4番に保存」等</span></li>
</ul>
</li>
</ul>
</li>
 	<li>命令に従ってMPUがメモリの中身を操作</li>
</ol>
</li>
 	<li> 参考
<ul>
 	<li>坂井 弘亮 (著): 熱血!アセンブラ入門,秀和システム, 2014.
<ul>
 	<li>実例豊富。様々なCPU</li>
</ul>
</li>
</ul>
</li>
</ul>
&nbsp;

<!--nextpage-->
<h2>I/Oはどう操作する？</h2>
<ul>
 	<li>メモリの中だけいじっていてもピンに信号は出せない</li>
 	<li>MPUとピンの間には<span style="color: #ffff00;">「I/Oポート」</span>が存在
<ul>
 	<li>I/Oポートにバイナリを書き込むとピンの入出力・挙動が変化</li>
 	<li>一番単純（安直）な例
<ul>
 	<li>二進数で8ビットのデータ10101010をポートに書き込むと
ピンがHI LOW HI LOW HI LOW HI LOW と出力</li>
</ul>
</li>
 	<li>他に入出力の切り替え等があるので実際はもっと複雑</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>MPUからI/Oポートへのアクセス</h2>
<ul>
 	<li><span style="color: #ffff00;">メモリマップドI/O</span>
<ul>
 	<li>メモリのアドレス空間にポートのアドレスがマッピングされている</li>
 	<li>メモリの読み書きもポートの読み書きも同じ命令を使う</li>
 	<li>例
<ul>
 	<li>10番のアドレス（メモリに割り当て）に100を書く
-&gt;メモリに100が書き込まれる</li>
 	<li>2番のアドレス（ポートに割り当て）に100を書く
-&gt;ポートに100が渡って解釈され、ピンの状態が変わる</li>
</ul>
</li>
 	<li>抽象度が高い</li>
</ul>
</li>
 	<li>ポートマップドI/O（I/OマップドI/O）
<ul>
 	<li>メモリとI/Oポートのアドレス空間が別</li>
 	<li>抽象度が低い</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>ここまでのまとめ</h2>
<ul>
 	<li>マイコンはMPUとメモリ、I/Oから構成される</li>
 	<li>メモリマップドI/OのMPUはメモリやI/Oを同じアドレス空間で操作
<ul>
 	<li><span style="color: #ffff00;">抽象化</span></li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>補足: 安価なマイコンの構造</h2>
<ul>
 	<li><a href="https://ja.wikipedia.org/wiki/%E3%83%8F%E3%83%BC%E3%83%90%E3%83%BC%E3%83%89%E3%83%BB%E3%82%A2%E3%83%BC%E3%82%AD%E3%83%86%E3%82%AF%E3%83%81%E3%83%A3" target="_blank">ハーバードアーキテクチャ</a>
<ul>
 	<li>命令を保存するメモリとデータ用のメモリが別
<ul>
 	<li>プログラムを途中で書き換えないならこれで良い
<ul>
 	<li>書き換えさせたくないという考えもある</li>
</ul>
</li>
</ul>
</li>
 	<li>プログラムとデータが混在するノイマン型とは違う</li>
</ul>
</li>
</ul>
<img src="https://lab.ueda.asia/wp-content/uploads/2016/09/harvard.jpg" alt="harvard" width="668" height="110" />

<!--nextpage-->
<h2>オペレーティングシステム</h2>
<ul>
 	<li>ハードウェアの複雑さを隠すためのソフトウェア階層
<ul>
 	<li>ハードウェアをいじる人間には邪魔かもしれない</li>
</ul>
</li>
 	<li>仕事
<ul>
 	<li> 抽象化
<ul>
 	<li>機械の世界から情報処理の世界へ</li>
</ul>
</li>
 	<li>資源（リソース）管理
<ul>
 	<li>次々（同時）に来る「計算機（とその周辺機器）を
使いたいという要求」をいかに捌くか</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>マイコン/OSでの抽象化</h2>
<ul>
 	<li>マイコン: メモリアドレスによる抽象化
<ul>
 	<li>様々な機器のデータ読み書き口を同じアドレス空間に配置（メモリマップドI/O）</li>
 	<li>ある番地の01を操作すると、ピンから電圧が出たり、入出力が逆転したり</li>
 	<li>メモリの番地を一つずつ書き換える操作</li>
</ul>
</li>
 	<li>OS: <span style="color: #ffff00;">ファイルによる抽象化</span>
<ul>
 	<li>一連のデータを流し込んだり取り出したりできる（ストリーム）</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2> なんでもファイル</h2>
<ul>
 	<li>機器の操作（例: ラズパイマウスを例に）
<ul>
 	<li>/dev/rtmotor0等、ファイルの読み書きで操作</li>
 	<li>よくよく考えてみると、機器の操作というのはデータを
書いてデータ読むだけで済む
<ul>
 	<li>もちろんマイコンより余計なオーバーヘッドが発生</li>
</ul>
</li>
</ul>
</li>
</ul>
<iframe src="https://www.youtube.com/embed/_SDwb_MJ4SA" width="560" height="315" frameborder="0" allowfullscreen="allowfullscreen"></iframe>

<!--nextpage-->
<h2>こんなファイルも（擬似デバイス）</h2>
<ul>
 	<li>乱数発生器 /dev/random, /dev/urandom</li>
 	<li>ゴミ捨て場 /dev/null</li>
 	<li>ひたすら0x00を吐く /dev/zero</li>
</ul>
<!--nextpage-->
<h2>プロセス</h2>
<ul>
 	<li>基本、OSなしのマイコン制御は一度に一つのプログラムだけ実行</li>
 	<li>OSがあると複数実行可能
<ul>
 	<li>恩恵もあるが複雑になる</li>
 	<li>ここでは簡単な説明に止めて、歴史から仕組みを考えていきましょう</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>OSの歴史</h2>
<ul>
 	<li>昔の話から考えてみましょう
<ul>
 	<li>なぜOSというものがあるのか</li>
 	<li>なぜこんな仕組みなのか？</li>
 	<li>ロボットとの親和性は？</li>
</ul>
</li>
 	<li>話の流れ
<ul>
 	<li>UNIX 以前</li>
 	<li>UNIX</li>
 	<li>UNIX の派生物</li>
 	<li>Linux</li>
</ul>
</li>
</ul>
&nbsp;

<!--nextpage-->
<h2>OSの歴史</h2>
<ul>
 	<li>UNIX以前
<ul>
 	<li>初期の計算機の使われ方（-1965 年）
<ul>
 	<li>主に科学計算や集計</li>
 	<li>使用者が計算機の使用時間を割り当てられて、その時間にプログラムを計算機室に持ち込み、プラグボードやパンチカードを持ち込む</li>
</ul>
</li>
</ul>
</li>
</ul>
<ul>
 	<li>参考
<ul>
 	<li><a href="https://en.wikipedia.org/wiki/File:IBM402plugboard.Shrigley.wireside.jpg" target="_blank">プラグボード</a></li>
 	<li><a href="https://en.wikipedia.org/wiki/File:UNIVAC-120_BRL61-0890.jpg" target="_blank">プラグボードの使用風景</a></li>
 	<li><a href="https://en.wikipedia.org/wiki/File:FortranCardPROJ039.agr.jpg" target="_blank">パンチカード</a></li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>このころのデータの読み書き</h2>
<ul>
 	<li>メディア: パンチカード, 紙テープ, 磁気テープ</li>
 	<li>初期の頃のオペレーション（バッチシステム）
<ol>
 	<li>計算機 A でパンチカードの情報を磁気テープ上の情報に変換</li>
 	<li>磁気テープを計算機 Bにセット</li>
 	<li>計算結果が結果が出力用磁気テープへ</li>
 	<li>磁気テープを取り外し別の計算機 Cでプリントアウト</li>
</ol>
</li>
 	<li>改善すべき点
<ul>
 	<li>1 台の計算機で1つの計算しかしない
<ul>
 	<li>割り込みのない（できない）マイコンのようなもの
<ul>
 	<li>融通が利かない</li>
</ul>
</li>
 	<li>人が列をなして待っていないと止まる</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>マルチプログラミング</h2>
<ul>
 	<li>1964年ごろ実用
<ul>
 	<li><a href="https://en.wikipedia.org/wiki/File:DM_IBM_S360.jpg" target="_blank">このころの計算機（IBM System/360）</a></li>
</ul>
</li>
 	<li>どんなものか
<ul>
 	<li>メモリをパーティション分けして複数のジョブを置き、実行</li>
 	<li>メモリをジョブがお互いに覗かないようにする（ハードで）</li>
</ul>
</li>
 	<li>課題
<ul>
 	<li>メモリの量が動的に変わらない</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>タイムシェアリングへ</h2>
<ul>
 	<li>1960年代</li>
 	<li>マルチプログラミングをさらに発展
<ul>
 	<li>プログラムを持ち込むバッチ処理から端末による対話式へ</li>
</ul>
</li>
 	<li> 主なプロジェクト
<ul>
 	<li>CTSS（compatible time sharing system）</li>
 	<li>MULTICS（multipexed information and computing service）</li>
</ul>
</li>
 	<li><a href="https://en.wikipedia.org/wiki/File:PDP-1.jpg" target="_blank">この頃の計算機（PDP-1）</a></li>
</ul>
<h2><!--nextpage--></h2>
<h2>UNIX（Unix）</h2>
<ul>
 	<li>MULTICS プロジェクトに参加していたAT&amp;Tベル研のKen Thompsonらが
<a href="https://commons.wikimedia.org/wiki/File:Pdp7-oslo-2005.jpeg" target="_blank">PDP-7</a>上で開発（1960 年代末）</li>
 	<li>特許ドキュメント管理・作成用
<ul>
 	<li>（単にゲームを動かしたかっただけという説も）</li>
</ul>
</li>
 	<li>MULTI（多方向）→UNI（単方向）
<ul>
 	<li>MULTICSの失敗: たくさんの研究組織、研究員で右往左往</li>
 	<li>UNIXの開発（注意: 私の独自解釈です）
<ul>
 	<li>ドキュメント管理したい（＋ゲームやりたい）という明確な目標</li>
 	<li>3人+αで早く作りたい→シンプルに作りたい</li>
</ul>
</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>UNIXが具現化・整理した機能</h2>
<ul>
 	<li>階層型ファイルシステム
<ul>
 	<li>ファイル: 一連の文字列</li>
 	<li>ディレクトリ: ファイルを整理するファイル</li>
</ul>
</li>
 	<li>プロセス・タイムシェアリング
<ul>
 	<li>複数の処理を同時に走らせる</li>
 	<li>仮想記憶, プロセススケジューラ</li>
</ul>
</li>
 	<li>デバイスファイル
<ul>
 	<li>機器もファイル</li>
</ul>
</li>
 	<li>シェル
<ul>
 	<li>ファイルとプロセスの連携</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>機能以外に重要なこと</h2>
<ul>
 	<li>オープンソースの走り
<ul>
 	<li>当時AT&amp;T はコンピュータで商売できない（独禁法）</li>
 	<li>そこでコードを配布</li>
 	<li>結果、企業、研究機関、教育機関に広まる</li>
</ul>
</li>
 	<li>1984年AT&amp;T商売解禁
<ul>
 	<li>ライセンス業を始め、クローズ化</li>
 	<li>「UNIX 戦争」が始まる</li>
</ul>
</li>
 	<li>余波: 配布されたUNIX から様々な亜種（UNIX系OS）が誕生
<ul>
 	<li>ソースコードの流用</li>
 	<li>機能の再現</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2><a href="https://en.wikipedia.org/wiki/File:Unix_history-simple.svg" target="_blank">UNIX系OSの系譜</a></h2>
<ul>
 	<li>UNIX直系: 大雑把に言ってSystem V系とBSD系
<ul>
 	<li>ものによって使用感が異なる</li>
 	<li>我々がよく使うもの（ロボットの世界だとBSD系が多い）
FreeBSD, NetBSD, OpenBSD, OS X, iOS…</li>
</ul>
</li>
 	<li>MINIX, Linux
<ul>
 	<li>UNIXのコードを含まないが動作はUNIX</li>
 	<li>MINIX（1987年〜）
<ul>
 	<li>UNIX がクローズ化したためタネンバウムによって教育用に開発</li>
</ul>
</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>Linux</h2>
<ul>
 	<li>リーナス・トーバルズがMINIX 上で開発（1991年）
<ul>
 	<li>当時ヘルシンキ大学の大学生</li>
 	<li>冬季に部屋に引きこもって開発</li>
 	<li>メーリングリストで助言、協力を得ながらゼロから開発
<ul>
 	<li><span style="color: #ffff00;">バザール方式</span></li>
 	<li><a href="http://cruel.org/freeware/cathedral.html#1" target="_blank">「伽藍とバザール」</a></li>
</ul>
</li>
</ul>
</li>
 	<li>広まった理由
<ul>
 	<li>ゼロから開発したことで制約が少ない</li>
 	<li>協力者が多い
<ul>
 	<li>上から押さえつける人（老害）がいないと成功する（私見）</li>
</ul>
</li>
 	<li>タイミング（PCの普及, Microsoftの影響, ライセンスの問題）</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>Linuxとディストリビューション</h2>
<ul>
 	<li>Linuxの構成
<ul>
 	<li>Linuxカーネル（OS本体）</li>
 	<li>付属のソフトウェア（コマンド、パッケージシステム、GUI等）</li>
</ul>
</li>
 	<li>付属のソフトウェアをどういう構成にするかで
多数の「ディストリビューション」が派生
<ul>
 	<li><a href="https://ja.wikipedia.org/wiki/%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB:Linux_Distribution_Timeline.svg" target="_blank">系統図</a></li>
</ul>
</li>
</ul>
