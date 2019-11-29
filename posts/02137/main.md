<h1 style="font-size: 250%;">ロボットシステム学</h1>
<h2>第6回</h2>
上田 隆一

2016年11月2日\@千葉工業大学

<!--nextpage-->
<h2>今日の内容</h2>
<ul>
 	<li>デバイスドライバを作る</li>
 	<li>次回はGPIOの操作に挑戦しますが、今回はPCの中で完結する話
<ul>
 	<li>仮想マシンでもOK</li>
 	<li>RaspbianとUbuntuでは少しやり方が違う</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>回路の例<a href="https://lab.ueda.asia/wp-content/uploads/2016/09/gpio25.jpg"><img class="alignright size-medium wp-image-1706" src="https://lab.ueda.asia/wp-content/uploads/2016/09/gpio25-300x225.jpg" alt="gpio25" width="300" height="225" /></a></h2>
<ul>
 	<li>GPIO25とGNDの間にLEDを接続
<ul>
 	<li>GPIO25: 22番ピン</li>
 	<li>GND: 39番ピン</li>
 	<li>LEDのアノード（足の長い方）をGPIO25に</li>
</ul>
</li>
 	<li>抵抗はなくても特に問題ない
<ul>
 	<li>抵抗をつなぐとLEDに優しい</li>
 	<li>抵抗をつなぐ場合は200-300Ω程度（適当）</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>最初のコード</h2>
<ul>
 	<li>適当なディレクトリを作ってその中に</li>
 	<li>ファイル名は「myled.c」にしましょう</li>
 	<li>コードの中身
<ul>
 	<li>カーネルモジュールの初期化と後始末の関数を書く</li>
 	<li>マクロに関数名を与える</li>
</ul>
</li>
</ul>
<pre><span style="color: #ffffff;">#include &lt;linux/module.h&gt;

static int __init init_mod(void)
{
 return 0;
}

static void __exit cleanup_mod(void)
{
}

module_init(init_mod);
module_exit(cleanup_mod);
</span></pre>
<!--nextpage-->
<h2>Makefileを書く</h2>
<ul>
 	<li>Makefileという名前のファイルを作って次のように書く</li>
 	<li><span style="color: #ff0000;">インデントはタブで</span></li>
 	<li>Makefileのごくごく簡単な説明
<ul style="font-size: 80%;">
 	<li>&lt;作りたいファイル or 行いたい処理&gt;: &lt;必要なファイル&gt;と書いてその下に実行するコマンドを書く</li>
 	<li>コロンの左側をターゲットと言う</li>
 	<li>makeと打つと最初に書いてあるターゲットの作成が試みられる</li>
 	<li>必要なファイルがないと、ないファイルのターゲットの処理が試みられる</li>
</ul>
</li>
</ul>
<pre class="p1"><span class="s1" style="color: #ffffff;">obj-m:= myled.o #オブジェクトファイルの名前を指定（拡張子はo）</span>

<span class="s1" style="color: #ffffff;">myled.ko: myled.c </span>
<span class="s1" style="color: #ffffff;"> make -C /usr/src/linux M=`pwd` V=1 modules #makeと打つと実行される</span>
<span class="s1" style="color: #ffffff;">clean:</span>
<span class="s1" style="color: #ffffff;"> make -C /usr/src/linux M=`pwd` V=1 clean #make cleanで実行</span></pre>
<!--nextpage-->
<ul>
 	<li>このディレクトリで次のようにmake</li>
</ul>
<pre><span style="color: #ffffff;">$ make</span></pre>
<!--nextpage-->
<h2>コンパイルと実行</h2>
<pre><span style="color: #ffffff;">$ make #Makefileとmyled.cが正しければこれでOK</span>
<span style="color: #ffffff;">$ ls #確認</span>
<span class="s1"><span style="color: #ffffff;">Makefile<span class="Apple-converted-space">  </span>Module.symvers<span class="Apple-converted-space">  </span>modules.order<span class="Apple-converted-space">  </span>myled.c<span class="Apple-converted-space">  </span>myled.ko<span class="Apple-converted-space">  </span>myled.mod.c</span><span class="Apple-converted-space">  </span>myled.mod.o<span class="Apple-converted-space">  </span>myled.o</span></pre>
