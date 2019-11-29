<h2></h2>
<h1 style="font-size: 250%;">ロボットシステム学</h1>
<h2>第12回</h2>
上田 隆一

2017年1月11日\@千葉工業大学

<!--nextpage-->
<h2>課題1補足・雑感</h2>
<ul>
 	<li>元のコードを書いた人（この場合は私）の名前は残しておきましょう。</li>
 	<li>コピペが下手くそな人が
<ul>
 	<li>レイアウトが崩れたり1行飛ばしになっている</li>
 	<li>ちゃんとGitHubのforkやダウンロード機能を使いましょう</li>
</ul>
</li>
 	<li>私にとっては仕事なので「お忙しいところ恐縮で・・・」とメールに書く必要はないっす。</li>
 	<li>これは課題なので、変に動画を凝るくらいならコードの方に工夫が欲しいところ。
<ul>
 	<li>何が求められているかはなかなか相手（私）からは聞き出せないので厄介だなとは思いますが・・・</li>
</ul>
</li>
 	<li>調べ物した人はリファレンスも欲しいところ</li>
</ul>
<!--nextpage-->
<h2>本日の内容</h2>
<ul>
 	<li>通信・暗号（その2）</li>
 	<li>ROS</li>
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
 	<li>社会的には「別のメールでパスワードを送ります」等、
本当にそれで良いのかいまいち謎な方法でごまかしている</li>
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
 	<li>クライアント側（自分のノートPC等）で秘密鍵と公開鍵を作る（<a href="http://webkaru.net/linux/tera-term-ssh-login-public-key/">Windowsの場合はこちら</a>）
<pre><span style="color: #ffffff;">$ mkdir .ssh</span>
<span style="color: #ffffff;">$ chmod 700 .ssh/</span>
<span style="color: #ffffff;">$ cd .ssh/</span>
<span style="color: #ffffff;">$ ssh-keygen</span>
<span style="color: #ffffff;">###いろいろ聞かれるが基本returnで</span><span style="color: #ffffff;"> （一度はちゃんと読みましょう）###</span></pre>
</li>
 	<li>自分の公開鍵をサーバ側（Raspberry Pi等）のauthorized_keysに登録</li>
 	<li>
<pre><span style="color: #ffffff;">###サーバのIPアドレスにscp###</span>
<span style="color: #ffffff;">$ scp ~/.ssh/id_rsa.pub pi\@192.168.?.?:~/</span>
<span style="color: #ffffff;">$ ssh pi\@192.168.?.?</span>
<span style="color: #ffffff;">$ cat id_rsa.pub &gt;&gt; .ssh/authorized_keys</span>
<span style="color: #ffffff;">$ chmod 600 .ssh/authorized_keys</span></pre>
</li>
</ol>
</li>
</ul>
<!--nextpage-->
<h2>ROS: robot operating system</h2>
<ul>
 	<li>ロボットのソフトウェアコンポーネントを作って
動作させるためのフレームワーク/ミドルウェア
<ul>
 	<li>OSでは無い</li>
</ul>
</li>
 	<li>発祥: 2000年代後半、Willow Garage社</li>
 	<li>BSDライセンス</li>
 	<li>Linux（Ubuntu）上での動作がデフォルト</li>
 	<li>サイト
<ul>
 	<li>公式ページ: http://www.ros.org/</li>
 	<li>マニュアル等: http://wiki.ros.org/ja</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>どんなものか</h2>
<ul>
 	<li>本体: プロセス間通信をつかさどる
<ul>
 	<li>プロセス同士をpublish-subscribeモデルやサービスでつなぐ</li>
 	<li>XML-RPC等を利用</li>
 	<li>通信するデータに型</li>
</ul>
</li>
 	<li>周辺
<ul>
 	<li>ビルドシステム、パッケージ管理、テストツール、・・・</li>
 	<li style="color: white;"></li>
</ul>
</li>
</ul>
<span style="color: #ff0000;">と書いてもよくわからんのでこちらで動かしてみます</span>

<!--nextpage-->
<h2>デモ</h2>
<ul>
 	<li>カメラの画像をブラウザから見る</li>
 	<li>手順
<ol>
 	<li>必要なパッケージのダウンロード</li>
 	<li>catkin_make</li>
 	<li>見る</li>
</ol>
</li>
 	<li>非常に手軽（なように多くのロボット界隈の人間がROS周りのオープンソースを開発している）</li>
</ul>
<!--nextpage-->
<h2>さらに便利に使う</h2>
<ul>
 	<li>ROS化されているキラーコンテンツ
<ul>
 	<li>slam_gmapping, ナビゲーションメタパッケージ
<ul>
 	<li>地図生成（次のページにデモ）、位置推定、経路生成</li>
</ul>
</li>
 	<li>MoveIt!
<ul>
 	<li>腕の動作計画 腕先の位置を入力→関節角を計算（逆運動学）</li>
</ul>
</li>
 	<li>その他、様々なハード・ソフトがROS化</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>ROSを使ったSLAMの様子</h2>
<ul>
 	<li>ポイント: SLAMのコードは書いてない
<ul>
 	<li>aptでSLAM（Gmapping）のコードが入る</li>
 	<li>デッドレコニングのコードをちょっと書いただけ</li>
</ul>
</li>
</ul>
<iframe src="https://www.youtube.com/embed/b2kYQ11PUSI" width="560" height="315" frameborder="0" allowfullscreen="allowfullscreen"></iframe>

<!--nextpage-->
<h2>ROSを使ったナビゲーションの様子</h2>
<ul>
 	<li>SLAMをした後のナビゲーション
<ul>
 	<li>自己位置推定</li>
 	<li>障害物回避</li>
 	<li>...</li>
</ul>
</li>
 	<li>足回りもROSのパッケージ化</li>
</ul>
&nbsp;

<iframe width="560" height="315" src="https://www.youtube.com/embed/RpPcmyXOcr4" frameborder="0" allowfullscreen></iframe>

<!--nextpage-->
<h2>イメージファイルからの
OSのセットアップ</h2>
<ul>
 	<li>13,14回はROSを使います
<ul>
 	<li>OSをRaspbianからUbuntuに変えた方が良い</li>
</ul>
</li>
 	<li>OSのイメージ
<ul>
 	<li><a href="https://wiki.ubuntu.com/ARM/RaspberryPi">https://wiki.ubuntu.com/ARM/RaspberryPi</a> の
<a class="http" href="http://www.finnie.org/software/raspberrypi/ubuntu-rpi3/ubuntu-16.04-preinstalled-server-armhf+raspi3.img.xz">ubuntu-16.04-preinstalled-server-armhf+raspi3.img.xz</a>
<ul>
 	<li>これをmicroSDに流し込むと起動</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>方法</h2>
<ul>
 	<li>Linux環境</li>
</ul>
<pre><span style="color: #ffffff;">$ xzcat ubuntu-16.04-preinstalled-server-armhf+raspi3.img.xz</span>
<span style="color: #ffffff;"> | sudo dd bs=1MB of=/dev/（microSDカードのデバイスファイル）</span></pre>
<ul>
 	<li>Mac</li>
</ul>
<pre><span style="color: #ffffff;">$ xzcat ubuntu-16.04-preinstalled-server-armhf+raspi3.img.xz
 | sudo dd bs=1m of=/dev/（microSDカードのデバイスファイル）</span></pre>
<ul>
 	<li>Window
<ul>
 	<li>何かツールを使う（よくわからない）</li>
 	<li>仮想マシンを使う</li>
 	<li>アダプタを使ってラズパイのUSBにmicroSDをさして操作</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>インストール後の作業1</h2>
<ul>
 	<li>カーネルをアップデートすると動かないという
よろしくない状況なので、
カーネルのアップデートを止める
<ul>
 	<li>
<pre class="p1"><span style="color: #ffffff;"><span class="s1">$ echo linux-image-raspi2 hold | sudo dpkg --set-selections</span>
<span class="s1">$ echo linux-headers-raspi2 hold | sudo dpkg --set-selections</span></span></pre>
</li>
</ul>
</li>
 	<li>「hold」になっていることを確認</li>
 	<li>
<pre class="p1"><span style="color: #ffffff;"><span class="s1">$ dpkg --get-selections | grep hold
</span><span class="s1">linux-headers-raspi2<span class="Apple-converted-space">                            </span>hold
</span><span class="s1">linux-image-raspi2<span class="Apple-converted-space">                              </span>hold</span></span></pre>
&nbsp;</li>
</ul>
<!--nextpage-->
<h2>インストール後の作業2</h2>
<ul>
 	<li>これをしておいた方が良さそう</li>
 	<li>
<pre class="p1"><span class="s1" style="color: #ffffff;">sudo apt purge cloud-init</span></pre>
</li>
 	<li>ROSのインストール
<ul>
 	<li>次のリポジトリにインストーラ
<ul>
 	<li><a href="https://github.com/ryuichiueda/ros_setup_scripts_Ubuntu16.04_server" target="_blank">ryuichiueda/ros_setup_scripts_Ubuntu16.04_server</a></li>
 	<li>中にあるシェルスクリプトを
step0.bash, step1.bash, locale.ja.bash
と実行すればOK</li>
</ul>
</li>
</ul>
</li>
</ul>
