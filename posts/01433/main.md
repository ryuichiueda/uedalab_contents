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
 	<li><code>$ cat /etc/passwd</code></li>
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
 	<li>Vimにはvimtutorというコマンドがあり、<span style="font-size: 15px; font-weight: 300; line-height: 1.62em;">最初はこれをやるのが一番良い</span></li>
</ul>
</li>
</ul>
