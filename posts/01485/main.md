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
&nbsp;
