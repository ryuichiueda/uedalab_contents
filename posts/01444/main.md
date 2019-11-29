<h1 style="font-size: 250%;">ロボットシステム学</h1>
<h2>第2回</h2>
上田 隆一

2016年9月?日\@千葉工業大学

<!--nextpage-->
<h2>今日の内容</h2>
<ul>
 	<li>ノートPCとラズパイを接続</li>
</ul>
<!--nextpage-->
<h2>やること</h2>
<ul>
 	<li>下の写真のようにノートPCとラズパイを有線LANで直接接続</li>
 	<li>次のような接続を構成
<ul>
 	<li>ラズパイ -&gt; 有線LAN -&gt; ノートPC -&gt; ノートPCのWiFi -&gt; インターネット</li>
 	<li>つまりノートPCをルータにする</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>ノートPCのOS別設定方法</h2>
<ul>
 	<li>Windows: <a href="https://blog.ueda.asia/?p=8694" target="_blank">https://blog.ueda.asia/?p=8694</a>
<ul>
 	<li>拙ブログですみません</li>
</ul>
</li>
 	<li>Mac: <a href="https://blog.ueda.asia/?p=8717" target="_blank">https://blog.ueda.asia/?p=8717</a>
<ul>
 	<li>こちらも拙ブログですみません</li>
 	<li>ラズパイのIPの調べ方
<ul>
 	<li>
<p class="p1"><span class="s1">$ nmap -sP &lt;有線側のセグメント&gt;</span></p>
</li>
</ul>
</li>
</ul>
</li>
 	<li>Linux: DHCPを立てるのが面倒なので割愛</li>
</ul>
<!--nextpage-->
<h2>Linuxの世界</h2>
<ul>
 	<li>ほぼ全てテキストファイルでできている
<ul>
 	<li>設定ファイル等
<ul>
 	<li>/etc下のファイルを見てみましょう</li>
 	<li><span style="color: #ccffff;"><code>$ cat /etc/passwd</code></span></li>
</ul>
</li>
</ul>
</li>
 	<li>どうやって見る？編集する？
<ul>
 	<li><span style="color: #ffff00;">エディタ</span></li>
 	<li><span style="color: #ffff00;">コマンド</span></li>
 	<li>使えないとかなりストレス
<ul>
 	<li>自転車と一緒で使えると自然に使えるようになるので
我慢して慣れられるかどうかで今後が変わる</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>エディタ</h2>
<ul>
 	<li>（CUI）でテキストファイルを読み書きするもの
<ul>
 	<li>EmacsとVimがメジャー</li>
</ul>
</li>
 	<li>特にここでは説明しません
<ul>
 	<li>練習コマンドがあるのでそれで練習を</li>
 	<li>Vimにはvimtutorというコマンドがあり、
最初はこれをやるのが一番良い</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>コマンド</h2>
<ul>
 	<li>CUIからプログラムを起動する場合は字をシェルに打ち込むが、
その字のこと
<ul>
 	<li>プログラム自身のことも指し、このスライドではプログラム自身のこと</li>
</ul>
</li>
 	<li>だいたいこの二種類
<ul>
 	<li>システム操作のためのコマンド
<ul>
 	<li>サービスを立ち上げたり止めたり</li>
 	<li>これはマニュアルを見たら覚えられる</li>
</ul>
</li>
 	<li>フィルタコマンド
<ul>
 	<li>標準入力から文字を受けて標準出力に加工した字を出すもの</li>
 	<li>組み合わせて使う（マニュアルがあまりない）</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>フィルタコマンド</h2>
<ul>
 	<li>多数: grep, find, wc, ...
<ul>
 	<li>/bin/下に存在</li>
</ul>
</li>
 	<li>とりあえず最初に覚えるもの
<ul>
 	<li>cat: 表示</li>
 	<li>sudo: root権限でコマンドを実行
<ol>
 	<li><span style="color: #00ffff;">$ sudo cat /etc/shadow</span></li>
</ol>
</li>
 	<li>grep: 検索
<ol>
 	<li><span style="color: #00ffff;">$ grep ueda /etc/passwd</span></li>
 	<li><span style="color: #ccffff;">ueda:x:1000:1000:Ryuichi UEDA,,,:/home/ueda:/bin/bash</span></li>
</ol>
</li>
 	<li>find: ファイルの列挙
<ul>
 	<li>使い方の例
<ol>
 	<li><span style="color: #00ffff;">$ find /</span></li>
</ol>
</li>
 	<li>出力がザーッと出て使いにくくないか？</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>コマンドの組み合わせ</h2>
<ul>
 	<li>特定のファイルを探すには？
<ul>
 	<li>例: passwdファイルってどこにあったけ？</li>
 	<li>grepと組み合わせる
<ol>
 	<li><span style="color: #00ffff;">sudo find | grep passwd</span></li>
 	<li><span style="color: #ccffff;">[sudo] password for ueda:</span></li>
 	<li><span style="color: #ccffff;">./var/lib/dpkg/info/passwd.postinst</span></li>
 	<li><span style="color: #ccffff;">./var/lib/dpkg/info/base-passwd.postinst</span></li>
 	<li><span style="color: #ccffff;">./var/lib/dpkg/info/passwd.preinst</span></li>
</ol>
</li>
 	<li>さらに絞り込む（grepで正規表現を使う）
<ol>
 	<li><span style="color: #00ffff;">$ sudo find / | grep '/passwd$'</span></li>
 	<li><span style="color: #ccffff;">/var/tmp/etc/init.d/passwd</span></li>
 	<li><span style="color: #ccffff;">/var/tmp/etc/cron.daily/passwd</span></li>
 	<li><span style="color: #ccffff;">...</span></li>
</ol>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>正規表現の例</h2>
<ul>
 	<li>正規表現の例
<ul>
 	<li> /etc/servicesの調査
<ol>
 	<li><span style="color: #00ffff;">$ cat /etc/services | grep 80</span>　　         #80を検索</li>
 	<li><span style="color: #ccffff;">$ cat /etc/services | grep '[^0-9]80/'    </span>#80番ポートのレコードだけ検索</li>
 	<li><span style="color: #ccffff;">$ cat /etc/services | grep ftp                </span>#ftpという語句を検索</li>
 	<li><span style="color: #ccffff;">$ cat /etc/services | grep ^ftp              </span>#最初がftpで始まる行を検索</li>
</ol>
</li>
</ul>
</li>
 	<li>上級者向け
<ul>
 	<li>AWKとgrepで10000番ポート以上のレコードを抽出のこと</li>
</ul>
</li>
</ul>
