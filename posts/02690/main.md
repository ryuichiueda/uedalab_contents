<h2></h2>
<h1 style="font-size: 250%;">ロボットシステム学</h1>
<h2>第12回</h2>
上田 隆一

2017年1月11日\@千葉工業大学

<!--nextpage-->
<h2>本日の内容</h2>
<ul>
 	<li>通信・暗号（その2）</li>
 	<li>Raspbian -&gt; Ubuntu</li>
</ul>
<!--nextpage-->
<h2>暗号</h2>
<ul>
 	<li>通信において重要な役割
<ul>
 	<li>暗号化していないパケットの内容は簡単に覗ける</li>
 	<li>インターネットのパケットはどこを通るか分からない</li>
 	<li>通販サイトで暗号化していないとどうなるか？</li>
 	<li>ネットワークカメラで暗号化していないとどうなるか？</li>
</ul>
</li>
 	<li>暗号化の方式
<ul>
 	<li>ざっくり分類: 共通鍵暗号方式、公開鍵暗号方式</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>共通鍵暗号方式</h2>
<ul>
 	<li>基本的にはパスワードの延長線上にあるもの</li>
 	<li>データを鍵で暗号化し、同じ鍵で復号</li>
 	<li>送信者と受信者が同じ鍵を持つ</li>
 	<li><span style="color: #ff0000;">通信の時の問題: どうやって鍵を交換するか？</span>
<ul>
 	<li>「別のメールでパスワードを送ります」等、アホな習慣でごまかしている状況</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>公開鍵暗号方式</h2>
<ul>
 	<li>二つの鍵を使う
<ul>
 	<li><span style="color: #ff0000;">「公開鍵」と「秘密鍵」</span></li>
</ul>
</li>
 	<li>公開鍵
<ul>
 	<li>暗号化に用いる。人に見せても良い</li>
</ul>
</li>
 	<li>秘密鍵
<ul>
 	<li>複号に用いる。人に見せてはいけない</li>
</ul>
</li>
 	<li><span style="color: #ff0000;">誰でもデータを暗号化できるが、復号できるのは秘密鍵の所有者のみ</span></li>
</ul>
<!--nextpage-->
<h2>セキュアシェル（SSH）</h2>
<ul>
 	<li>セキュアシェル（SSH）
<ul>
 	<li>遠隔の計算機と暗号通信をするためのプロトコル</li>
 	<li>コマンドのssh(1) はセキュアシェルを使って遠隔の計算機と通信するためのもの</li>
</ul>
</li>
 	<li>特に暗号化が必要のないところでも使うことになっている
<ul>
 	<li>かつてはrshというものがあったが使わないことになっている</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>サーバへのssh接続</h2>
<ul>
 	<li>パスワードを使う場合
<ol>
 	<li>パスワードを送る前にサーバからクライアントへ公開鍵というものが送られる</li>
 	<li>クライアントは以下をサーバに送信
<ul>
 	<li>もらった公開鍵で通信用の共通鍵を暗号化したもの</li>
 	<li>パスワードを共通鍵で暗号化したもの</li>
</ul>
</li>
 	<li>サーバは自身の秘密鍵でもらった共通鍵とパスワードを復元共通鍵で通信開始</li>
</ol>
</li>
</ul>
<!--nextpage-->
<h2>SSHの鍵認証</h2>
<ul>
 	<li>パスワードの代わりに公開鍵を使う</li>
 	<li>方法
<ol>
 	<li>クライアント側（自分のノートPC等）で秘密鍵と公開鍵を作る
<pre><span style="color: #ffffff;">$ mkdir .ssh</span>
<span style="color: #ffffff;">$ chmod 700 .ssh/</span>
<span style="color: #ffffff;">$ cd .ssh/</span>
<span style="color: #ffffff;">$ ssh-keygen</span>
<span style="color: #ffffff;">###いろいろ聞かれるが基本returnで</span>
<span style="color: #ffffff;"> （一度はちゃんと読みましょう）###</span></pre>
</li>
 	<li>自分の公開鍵をサーバ側（Raspberry Pi等）のauthorized_keysに登録</li>
</ol>
</li>
</ul>
