<h2>ロボットシステム学</h2>
<h2>第2回</h2>
上田 隆一

2016年9月27日\@千葉工業大学

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
<blockquote class="twitter-tweet" data-lang="ja">
<p dir="ltr" lang="ja">今度は、ノートPCとラズパイをUSB、LANケーブルで結びます。私のMacだとこのザマですが、普通のノートPCならもうちょいスッキリしているはずです。 <a href="https://twitter.com/hashtag/robosys2017?src=hash">#robosys2017</a> <a href="https://t.co/MZRurPg3ua">pic.twitter.com/MZRurPg3ua</a></p>
— Ryuichi Ueda (\@ryuichiueda) <a href="https://twitter.com/ryuichiueda/status/911498810081165312">2017年9月23日</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

<!--nextpage-->
<h2>ノートPCのOS別設定方法</h2>
<ul>
 	<li>Windows: <a href="https://blog.ueda.tech/?p=8694" target="_blank" rel="noopener">https://blog.ueda.tech/?p=8694</a>
<ul>
 	<li>拙ブログですみません</li>
</ul>
</li>
 	<li>Mac: <a href="https://blog.ueda.tech/?p=8717" target="_blank" rel="noopener">https://blog.ueda.tech/?p=8717</a>
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
 	<li><code>$ cat /etc/passwd</code></li>
</ul>
</li>
</ul>
</li>
 	<li>どうやって見る？編集する？
<ul>
 	<li>エディタ</li>
 	<li>コマンド</li>
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
 	<li>（CLI, command line interface）でテキストファイルを読み書きするもの
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
 	<li>CUIからプログラムを起動する場合は字をシェルに打ち込むが、その字のこと
<ul>
 	<li>プログラム自身のことも指し、このスライドではプログラム自身のこと</li>
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
 	<li>$ sudo cat /etc/shadow</li>
</ol>
</li>
 	<li>grep: 検索
<ol>
 	<li>$ grep ueda /etc/passwd</li>
 	<li>ueda:x:1000:1000:Ryuichi UEDA,,,:/home/ueda:/bin/bash</li>
</ol>
</li>
 	<li>find: ファイルの列挙
<ul>
 	<li>使い方の例
<ol>
 	<li>$ find /</li>
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
<pre><span style="color: #00ff00;">$ sudo find / | grep passwd
 [sudo] password for ueda:
 /var/lib/dpkg/info/passwd.postinst
 /var/lib/dpkg/info/base-passwd.postinst
 /var/lib/dpkg/info/passwd.preinst
...</span></pre>
</li>
 	<li>さらに絞り込む（grepで正規表現を使う）
<pre><span style="color: #00ff00;">$ sudo find / | grep '/passwd$'</span>
<span style="color: #00ff00;">/var/tmp/etc/init.d/passwd</span>
<span style="color: #00ff00;">/var/tmp/etc/cron.daily/passwd</span>
<span style="color: #00ff00;">...</span></pre>
</li>
</ul>
</li>
</ul>
<ul>
 	<li>lessで見る
<pre><span style="color: #00ff00;">$ sudo find / | less</span></pre>
</li>
</ul>
<!--nextpage-->
<h2>正規表現の例</h2>
<ul>
 	<li>正規表現の例
<ul>
 	<li> /etc/servicesの調査
<ol>
 	<li>$ cat /etc/services | grep 80　　         #80を検索</li>
 	<li>$ cat /etc/services | grep '[^0-9]80/'  #80番ポートのレコードだけ検索</li>
 	<li>$ cat /etc/services | grep ftp                #ftpという語句を検索</li>
 	<li>$ cat /etc/services | grep ^ftp       #最初がftpで始まる行を検索</li>
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
 	<li>$ man grep</li>
</ol>
</li>
 	<li>章がある
<ol>
 	<li>$ man 1 printf      #1章（コマンド）のprintf</li>
 	<li>$ man 3 printf      #3章（C言語の関数）のprintf</li>
</ol>
</li>
 	<li>詳しくは $ man man で。</li>
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
 	<li><span class="s1">$</span><span class="s2"> sudo apt-get install nmap   #旧</span></li>
 	<li>$ sudo apt install nmap         #新</li>
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
 	<li>$ ping 8.8.8.8
<ul>
 	<li>GoogleのDNSにパケットが届くか確認</li>
 	<li>インターネットに出られるか確認する時によく使用</li>
</ul>
</li>
 	<li>$ ping www.yahoo.co.jp
<ul>
 	<li>ドメイン名をIPに変換できるか（名前解決）を確認する時に使用</li>
</ul>
</li>
 	<li>$ ping 192.168.1.254
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
 	<li>$ ifconfig</li>
</ol>
</li>
 	<li>ip: 新しい方法
<ol>
 	<li>$ ip addr show    #IPアドレス等の確認</li>
</ol>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>その他通信関係のコマンド</h2>
<ul>
 	<li>nmap: ネットワークのスキャン
<ul>
 	<li>インターネットに向けてやると最悪裁判になるので注意</li>
 	<li>使用例
<ol>
 	<li><span class="s1">$</span><span class="s2"> nmap -sP 192.168.3.0/24   #自分のネットワークのマシンのIPアドレスを調査</span></li>
 	<li>$ nmap 192.168.3.2 #開いているポートの調査</li>
</ol>
</li>
</ul>
</li>
 	<li>traceroute
<ul>
 	<li> パケットの運ばれる経路を調査
<ol>
 	<li>$ traceroute 8.8.8.8</li>
</ol>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>scp, rsync</h2>
<ul>
 	<li>マシン間でファイルをコピー
<ol>
 	<li>$ scp hoge 192.168.3.1~/     #hogeファイルを192..1のホームへ</li>
 	<li>$ scp 192.168.3.1:~/hoge2 ./  #逆向き</li>
 	<li>$ rsync -av hoge/ 192.168.3.1:~/hoge/ #hogeディレクトリを192..1のホームへ</li>
 	<li>$ rsync -av192.168.3.1:~/hoge/ hoge/   #逆向き</li>
</ol>
</li>
 	<li>TeraTermにもscp機能がある</li>
</ul>
&nbsp;

<!--nextpage-->
<h2>停止・再起動</h2>
<ul>
 	<li>停止
<ul>
 	<li>次の2通り
<ul>
 	<li>$ sudo shutdown -h now</li>
 	<li>$ sudo poweroff</li>
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
 	<li>$ sudo reboot</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>プログラムのコンパイル</h2>
<ul>
 	<li>次のようなC言語のファイルhoge.cを作ってみましょう
<ul>
 	<li>端末のエディタがまだ使えない人はこの資料のコピペやscp等を駆使のこと</li>
</ul>
</li>
</ul>
<pre>#include &lt;stdio.h&gt;
int main(int argc, char const* argv[]){
    puts("あばばばば");
    return 0;
}</pre>
<ul>
 	<li>gccを使ってコンパイルし、a.outを実行
<ol>
 	<li>$ gcc hoge.c</li>
 	<li>$ ./a.out</li>
</ol>
</li>
 	<li>もしa.outが実行できなかったら $ chmod +x a.out</li>
</ul>
<!--nextpage-->
<h2>スクリプトの実行</h2>
<ul>
 	<li>次のようなPyhonのファイルhoge.pyを作ってみましょう</li>
</ul>
<pre>#!/usr/bin/python
print "Java"
</pre>
<ul>
 	<li>以下を実行
<ol>
 	<li>
<p class="p1"><span class="s1">$</span><span class="s2"> chmod +x hoge.py</span></p>
</li>
 	<li>
<p class="p1"><span class="s1">$</span><span class="s2"> ./hoge.py</span></p>
</li>
</ol>
</li>
 	<li>#!: シバン（shebang）
<ul>
 	<li>どのプログラムでこのスクリプトを実行するか指定</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>Raspbianのメンテナンス</h2>
<ul>
 	<li>rpi-update: カーネル等のアップデート
<ul>
 	<li>pi\@raspberrypi:~ $ sudo rpi-update</li>
</ul>
</li>
 	<li>apt update: パッケージリストの更新
<ul>
 	<li>pi\@raspberrypi:~ $ sudo apt update</li>
</ul>
</li>
 	<li>apt upgrade: パッケージのアップグレード
<ul>
 	<li>pi\@raspberrypi:~ $ sudo apt upgrade</li>
</ul>
</li>
 	<li>raspi-config: Raspberry Piの機能設定
<ul>
 	<li>pi\@raspberrypi<span class="s2">:</span><span class="s3">~ $</span><span class="s2"> sudo raspi-config</span></li>
 	<li>ロケールの設定</li>
 	<li>言語環境の設定</li>
 	<li>起動時にGUIの抑制</li>
 	<li>SPI等の機能をON/OFF</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>次回までの宿題<del></del></h2>
<ul>
 	<li>エディタが苦手な人はvimtutorをやっておく
<ul>
 	<li>$ vimtutor</li>
</ul>
</li>
 	<li>得意な人はVimやEmacsにプラグインを仕込む
<ul>
 	<li>Vimの場合はdein等
<ul>
 	<li><a href="https://github.com/Shougo/dein.vim" target="_blank" rel="noopener">https://github.com/Shougo/dein.vim</a></li>
</ul>
</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>補足</h2>
<ul>
 	<li>SSH接続でこういうのが出た時</li>
</ul>
<pre>\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@
\@ WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED! \@
\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@\@</pre>
<ul>
 	<li>~/.ssh/known_hosts から接続先のIPアドレスを見つけてレコードを削除</li>
</ul>
