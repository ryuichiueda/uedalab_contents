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
 	<li>3要素がバスでつながっている</li>
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
<td style="border: 1px solid #FFF;" width="160">フラッシュメモリ</td>
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
