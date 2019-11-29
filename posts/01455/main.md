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
 	<li><span style="color: #00ffff;">sudo find / | grep passwd</span></li>
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
 	<li>lessで見る
<ol>
 	<li><span style="color: #00ffff;">sudo find / | less</span></li>
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
 	<li><span style="color: #ccffff;">$ cat /etc/services | grep '[^0-9]80/'  </span>#80番ポートのレコードだけ検索</li>
 	<li><span style="color: #ccffff;">$ cat /etc/services | grep ftp                </span>#ftpという語句を検索</li>
 	<li><span style="color: #ccffff;">$ cat /etc/services | grep ^ftp       </span>#最初がftpで始まる行を検索</li>
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
<!--nextpage-->
<h2>ファイルの操作</h2>
<ul>
 	<li>ls, mv, rm, cp, mkdir, rmdir
<ul>
 	<li>口頭で説明します</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>man</h2>
<ul>
 	<li>マニュアルコマンド
<ol>
 	<li><span style="color: #00ffff;">$ man grep</span></li>
</ol>
</li>
 	<li>章がある
<ol>
 	<li><span style="color: #00ffff;">$ man 1 printf</span>      #1章（コマンド）のprintf</li>
 	<li><span style="color: #00ffff;">$ man 3 printf</span>      #3章（C言語の関数）のprintf</li>
</ol>
</li>
 	<li>詳しくは<span style="color: #00ffff;"> $ man man</span> で。</li>
</ul>
<!--nextpage-->
<h2>apt, apt-get</h2>
<ul>
 	<li>ソフトウェアのインストール
<ul>
 	<li>API (Advanced Packaging Tool): Debian系Linuxの
パッケージシステム</li>
 	<li>使用例
<ul>
 	<li><span class="s1" style="color: #00ffff;">$</span><span class="s2"><span style="color: #00ffff;"> sudo apt-get install nmap</span>   #旧</span></li>
 	<li><span style="color: #00ffff;">$ sudo apt install nmap</span>         #新</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>ping</h2>
<ul>
 	<li>通信先にパケットが届くか確認する時によく使う
<ol>
 	<li><span style="color: #00ffff;">$ ping 8.8.8.8</span>
<ul>
 	<li>GoogleのDNSにパケットが届くか確認</li>
 	<li>インターネットに出られるか確認する時によく使用</li>
</ul>
</li>
 	<li><span style="color: #00ffff;">$ ping www.yahoo.co.jp</span>
<ul>
 	<li>ドメイン名をIPに変換できるか（名前解決）を確認する時に使用</li>
</ul>
</li>
 	<li><span style="color: #00ffff;">$ ping 192.168.1.254</span>
<ul>
 	<li>192.168.1.254に届くか確認
<ul>
 	<li>（192.168.1.254はルーターっぽいIPアドレス）</li>
</ul>
</li>
</ul>
</li>
</ol>
<ul>
 	<li>たまにセキュリティーのために先方がふさがっていることがある</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>ip, ifconfig</h2>
<ul>
 	<li>ネットワークの設定の確認
<ul>
 	<li>ifconfig: 古い確認方法
<ol>
 	<li><span style="color: #00ffff;">$ ifconfig</span></li>
</ol>
</li>
 	<li>ip: 新しい方法
<ol>
 	<li><span style="color: #00ffff;">$ ip addr show</span>    #IPアドレス等の確認</li>
</ol>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>nmap</h2>
<ul>
 	<li>ネットワークのスキャン
<ul>
 	<li><span style="color: #ffff00;">インターネットに向けてやると最悪裁判になるので注意</span></li>
</ul>
</li>
 	<li>使用例
<ol>
 	<li>
<p class="p1"><span class="s1" style="color: #00ffff;">$</span><span class="s2"><span style="color: #00ffff;"> nmap -sP 192.168.3.0/24</span>   #自分のネットワークのマシンのIPアドレスを調査</span></p>
</li>
 	<li><span style="color: #00ffff;">$ nmap 192.168.3.2</span> #開いているポートの調査</li>
</ol>
</li>
</ul>
<!--nextpage-->
<h2>停止・再起動</h2>
<ul>
 	<li>停止
<ul>
 	<li>次の2通り
<ul>
 	<li><span style="color: #00ffff;">$ sudo shutdown -h now</span></li>
 	<li><span style="color: #00ffff;">$ sudo poweroff</span></li>
</ul>
</li>
 	<li>Linuxはデータをストレージに後から書き込むので 、ラズパイの場合は緑のランプが点滅しなくなるまでよく待つ
<ul>
 	<li>ストレージ: HDD, SSD, microSD, ...</li>
</ul>
</li>
 	<li>一方、ラズパイはプログラムやデータ等を別のマシンで管理する
場合が多いのでブチ切りする人が多く、特に問題にならない</li>
</ul>
</li>
 	<li>再起動
<ul>
 	<li><span style="color: #00ffff;">$ sudo reboot</span></li>
</ul>
</li>
</ul>
