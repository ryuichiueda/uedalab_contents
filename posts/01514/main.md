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
 	<li>I/O</li>
</ul>
</li>
 	<li>3要素がバスでつながっている
<ul>
 	<li>例: <a href="http://www.atmel.com/ja/jp/devices/ATMEGA328P.aspx" target="_blank">ATmega328P</a>（Summaryの8ページ）</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>処理の流れ</h2>
<ul>
 	<li>これの繰り返し
<ol>
 	<li>命令を<span style="color: #ffff00;">メモリ</span>から取得
<ul>
 	<li>命令: アセンブリ言語の1行に相当
<ul>
 	<li><span style="color: #00ffff;">「1番と5番のメモリの中身を足して4番に保存」等</span></li>
</ul>
</li>
</ul>
</li>
 	<li>命令に従ってMPUが<span style="color: #ffff00;">メモリ</span>の中身を操作</li>
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
<!--nextpage-->
<h2>安価なマイコンの構造</h2>
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
<h2>MPUとI/Oポート</h2>
<ul>
 	<li>MPUからのアクセスの方方法
<ul>
 	<li><span style="color: #ffff00;">メモリマップドI/O</span>
<ul>
 	<li>メモリのアドレス空間にポートのアドレスがマッピングされている</li>
 	<li>メモリの読み書きもポートの読み書きも同じ命令を使う</li>
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
</li>
</ul>
<h2></h2>
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
&nbsp;
