<h1 style="font-size: 250%;">ロボットシステム学</h1>
<h2>第4回</h2>
上田 隆一

2016年10月19日\@千葉工業大学

<!--nextpage-->
<h2>今日の内容</h2>
<ul>
 	<li>プロセス等、Linuxの仕組みについて</li>
</ul>
<!--nextpage-->
<h2>プロセス</h2>
<ul>
 	<li>プログラム実行の一単位
<ul>
 	<li>実行中のプログラム＋OSが準備した付帯情報</li>
</ul>
</li>
 	<li>プロセスID、ユーザ、親プロセス
<ul>
 	<li>普段はps(1)やtop(1)で調査</li>
 	<li>CPUやメモリ使用量、ゴミプロセスがないか調査、等</li>
</ul>
</li>
 	<li>一つのプロセスについて調査したければ/proc/&lt;プロセス番号&gt;を見る
<ul>
 	<li>プロセス情報もファイルで提供される。なんでもファイル</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>カーネルから見たプロセス</h2>
<ul>
 	<li>リソースを割り当てる一単位
<ul>
 	<li>メモリの割り当て</li>
 	<li>プログラムが自身のプロセス外のメモリを参照しないよう保護</li>
 	<li>仮想アドレス空間</li>
 	<li>CPU の利用時間（タイムシェアリング）</li>
 	<li>優先度の高低を考慮
<ul>
 	<li>端末とのやり取りが多いものほど高頻度
<span style="color: #ff0000;">↑ロボットを動かす時に問題となる</span></li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>プロセスツリー</h2>
<ul>
 	<li>プロセスはプロセスから生まれる
<ul>
 	<li>fork-execと呼ばれる仕組み</li>
 	<li>家系図（プロセスツリー）ができる
<ul>
 	<li>pstree(1)で調査を</li>
 	<li>initというプロセスからぶら下がる</li>
</ul>
</li>
</ul>
</li>
 	<li>プロセスツリーの役割
<ul>
 	<li>親子間で環境や開いているファイルを引き継ぐ</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>プロセスの観察</h2>
<ul>
 	<li>psというコマンドを打ってみましょう
<ul>
 	<li><span style="color: #0000ff;">$ ps aux</span></li>
 	<li>項目の意味
<ul>
 	<li>USER: ユーザ, PID: プロセスID, %CPU: CPU 使用率,
%MEM: メモリ使用率, VSZ: 仮想メモリのサイズ,
RSS: 使用している物理メモリ量, TTY: 端末,
STAT: プロセスの状態, START: 起動した時間,
TIME: 使ったCPU 時間,
COMMAND: コマンド名、カーネルスレッド名</li>
</ul>
</li>
 	<li>STATの意味
<ul>
 	<li>
<p class="p1">R: Run, S: Sleep, D: Disk Sleep, T: Stopped,
Z: Zombie, +: forground, &lt;: high priority,
s: session leader</p>
</li>
</ul>
</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<ul>
 	<li>top
<ul>
 	<li><span style="color: #0000ff;">$ top -c</span></li>
 	<li>項目の意味
<ul>
 	<li>
<p class="p1">PID: プロセスID, USER: ユーザ, PR: 優先度,
NI: nice 値, VIRT: 仮想メモリ使用量,
RES: 物理メモリ使用量, SHR: 共有メモリ使用量,
S: プロセスの状態,%CPU: CPU 使用率,
%MEM: 物理メモリ使用率,
TIME+:CPU 使用時間, COMMAND: コマンド</p>
</li>
</ul>
</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>プロセス番号等</h2>
<ul>
 	<li><span style="color: #0000ff;">$ ps -eo command,pid,ppid,pgid,sid</span>
<ul>
 	<li>pid: プロセス番号
<ul>
 	<li>そのプロセス固有の番号</li>
</ul>
</li>
 	<li>ppid: 親のプロセス番号
<ul>
 	<li> 今の親のプロセス番号</li>
 	<li>親がいなくなると1（init）にぶら下がる</li>
</ul>
</li>
 	<li>pgid: プロセスグループID
<ul>
 	<li>同じジョブ（後述）の下にいるプロセスが共有するID</li>
</ul>
</li>
 	<li>sid: セッションID
<ul>
 	<li>一つの端末にぶら下がっているプロセスが共有するID</li>
</ul>
</li>
</ul>
</li>
 	<li>参考: <a href="https://linuxjm.osdn.jp/html/procps/man1/ps.1.html" target="_blank">https://linuxjm.osdn.jp/html/procps/man1/ps.1.html</a></li>
</ul>
<h2><!--nextpage--></h2>
<h2>プロセスの一生</h2>
<ol>
 	<li>あるプロセスからforkして生まれる
<ul>
 	<li><a href="https://gist.github.com/ryuichiueda/9593919" target="_blank">forkを実行するコード</a></li>
</ul>
</li>
 	<li>新しいプロセスIDをもらう</li>
 	<li>親の情報をすべて自分のメモリ空間にコピー（コピーしない場合もある）</li>
 	<li>（execされた場合）プログラムの部分が入れ替わる
<ul>
 	<li>例: <a href="https://gist.github.com/ryuichiueda/063765e1e0d8b1e8a501" target="_blank">execを行うシェルスクリプト</a></li>
</ul>
</li>
 	<li>プログラム実行</li>
 	<li>終了。終了ステータスを返す
<ul>
 	<li>0が正常終了、1が何らかの異常</li>
</ul>
</li>
</ol>
<h2><!--nextpage--></h2>
<h2>ジョブ</h2>
<ul>
 	<li>シェルがプロセスを管理する塊</li>
 	<li>ちゃんと説明すると大変なので操作だけ
<ol>
 	<li><span style="color: #3366ff;">$ seq 1 10000000000 | awk '$1%2'</span></li>
 	<li><span style="color: #3366ff;">Ctrl+Zしてみましょう</span>
<ul>
 	<li>
<p class="p1"><span class="s1">[1]+<span class="Apple-converted-space">  </span>停止<span class="Apple-converted-space">                  </span>seq 1 10000000000 | awk '$1%2'</span></p>
</li>
</ul>
</li>
 	<li>
<p class="p1"><span class="s1" style="color: #3366ff;">$ find / | grep aho</span></p>
</li>
 	<li><span style="color: #3366ff;">またCtrl+Z</span>
<ul>
 	<li>
<p class="p1"><span class="s1">[2]+<span class="Apple-converted-space">  </span>停止<span class="Apple-converted-space">                  </span>find / | grep --color=auto aho</span></p>
</li>
</ul>
</li>
 	<li>
<p class="p1"><span class="s1" style="color: #3366ff;">$ jobs</span></p>
</li>
 	<li>
<p class="p1"><span class="s1">[1]-<span class="Apple-converted-space">  </span>停止<span class="Apple-converted-space">                  </span>seq 1 10000000000 | awk '$1%2'</span></p>
<p class="p1"><span class="s1">[2]+<span class="Apple-converted-space">  </span>停止<span class="Apple-converted-space">                  </span>find / | grep --color=auto aho</span></p>
</li>
</ol>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>プロセスとメモリ</h2>
<ul>
 	<li>プロセスは、基本的に他のプロセスが使っているメモリの中身を見ることができない
<ul>
 	<li><span style="color: #ff0000;">見ることができたら事故</span></li>
</ul>
</li>
 	<li>プロセス間でメモリが見えないようにする仕組み: 仮想記憶
<ul>
 	<li>問題: 右のような1列のメモリを
どのように複数のプロセスに割り当てる？<a href="https://lab.ueda.asia/wp-content/uploads/2016/09/mem_sequence.png"><img class="alignright size-full wp-image-1598" src="https://lab.ueda.asia/wp-content/uploads/2016/09/mem_sequence.png" alt="mem_sequence" width="222" height="233" /></a></li>
</ul>
</li>
</ul>
&nbsp;
<h2><!--nextpage--></h2>
<h2>仮想記憶
（ページング方式）</h2>
<ul>
 	<li>アドレス空間を二種類用意
<ul>
 	<li>物理アドレス空間（DRAMやその他を直接指す）</li>
 	<li>仮想アドレス空間（プロセスごとに準備）</li>
</ul>
</li>
 	<li>アドレス空間を「ページ」に分割</li>
 	<li>仮想のページと物理ページを対応付け<a href="https://lab.ueda.asia/wp-content/uploads/2016/09/page.jpg"><img class="alignright wp-image-1601" src="https://lab.ueda.asia/wp-content/uploads/2016/09/page.jpg" alt="page" width="545" height="215" /></a></li>
</ul>
&nbsp;

&nbsp;
<h2><!--nextpage--></h2>
<h2>仮想記憶の導入で可能となること</h2>
<ul>
 	<li>別のプロセスのメモリ番地が見えない</li>
 	<li> lazyな物理メモリ割り当て
<ul>
 	<li>プログラムが割り当てのないページの番地にアクセスした時に、物理メモリのページを割り当て</li>
 	<li>割り当てのないページの番地にアクセスすることを「ページフォルト」と言い、これが起こると割り当てが起こる</li>
</ul>
</li>
 	<li>スワップ
<ul>
 	<li>メモリが不足時にページ上のデータをストレージ上のページに追い出せる（スワップアウト）</li>
 	<li>仮想アドレスの先が物理メモリである必要がなくなる</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<ul>
 	<li>キャッシュの管理が簡単に
<ul>
 	<li>プロセスが使用していない物理メモリのページに
読み書きしたファイルのデータを記憶</li>
 	<li>キャッシュが有効だとHDDの読み書き回数を減らすことができる</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>来週</h2>
<ul>
 	<li>電子回路とプログラミングとなっていましたが・・</li>
 	<li>ファイルシステムとデバイスの話をします</li>
</ul>
