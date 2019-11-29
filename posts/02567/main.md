<h2></h2>
<h1 style="font-size: 250%;">ロボットシステム学</h1>
<h2>第11回</h2>
上田 隆一

2016年12月21日\@千葉工業大学

<!--nextpage-->
<h2>ロボットと通信</h2>
<ul>
 	<li>自律分散系には必須ですね
<ul>
 	<li>そうですよね？</li>
</ul>
</li>
 	<li>使いますよね
<ul>
 	<li>リモート監視・操作等</li>
 	<li>環境に埋め込んだセンサやアクチュエータの操作</li>
 	<li>ソフトウェアのインストール</li>
</ul>
</li>
 	<li><span style="color: #ff0000;">必須 </span></li>
</ul>
<!--nextpage-->
<h2>本日の内容</h2>
<ul>
 	<li>ネットワーク関係の設定方法を一通りおさえる</li>
 	<li>イーサネット・TCP/IP IP
<ul>
 	<li>アドレス・ポート</li>
 	<li>ソケット通信については前期やったそうなので割愛</li>
</ul>
</li>
 	<li>ssh</li>
</ul>
<!--nextpage-->
<h2>IPアドレスの体系</h2>
<ul>
 	<li>計算機の住所（ただし複数持つことができる）</li>
 	<li>IPアドレス: 0-255の数字を4つドットでつないで表記
<ul>
 	<li>例: 192.168.0.1</li>
 	<li>ローカルのものとグローバルのものが存在
<ul>
 	<li>グローバル: 世界中でその計算機しか持っていない</li>
 	<li>ローカル（プライベートIPアドレス）: 閉じた環境で使うアドレス</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>ネットワーク部・ホスト部</h2>
<ul>
 	<li>IPアドレスを2進数で書いた時、左側の何桁かは「ネットワーク部」を表し、残りは「ホスト部」を表す</li>
 	<li>ネットワーク部
<ul>
 	<li>インターネットの中の一つのグループ</li>
</ul>
</li>
 	<li>ホスト部
<ul>
 	<li>各PC固有の番号（住所で言うと番地）</li>
</ul>
</li>
 	<li>サブネットマスク
<ul>
 	<li>どの部分がネットワーク部を表すかを示す数字</li>
 	<li>例: 255.255.255.0
<ul>
 	<li>2進数にすると11111111.11111111.11111111.00000000</li>
 	<li>ということで、上24ビットがネットワーク部となる</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>IPアドレスの設定</h2>
<ul>
 	<li>有線（Raspberry Piの場合）
<ul>
 	<li>最初からDHCPに設定されている</li>
 	<li>通常はこのままDHCPで良い
<ul>
 	<li>固定すると別の環境でログインできなくなる等、難しくなる</li>
</ul>
</li>
</ul>
</li>
 	<li>IPアドレスはルータのウェブページ、nmap等で確認可能
<ul>
 	<li>
<pre><span style="color: #ffffff;">$ nmap -sP 192.168.2.0/24</span></pre>
</li>
</ul>
</li>
 	<li>DHCPでもルータ等で固定できる</li>
</ul>
<!--nextpage-->
<h2>固定IPの設定</h2>
<ul>
 	<li>/etc/network/interfacesに設定を書く
<ul>
 	<li>下図: デフォルトの設定例（バージョンによって異なる）</li>
</ul>
</li>
</ul>
<pre><span style="color: #ffffff;">pi\@raspberrypi ~ $ cat /etc/network/interfaces</span>
<span style="color: #ffffff;">auto lo</span>
<span style="color: #ffffff;">iface lo inet loopback</span>

<span style="color: #ffffff;">iface eth0 inet dhcp </span></pre>
<!--nextpage-->
<ul>
 	<li>固定にする例</li>
 	<li>
<pre><span style="color: #ffffff;">pi\@raspberrypi ~ $ cat /etc/network/interfaces</span>
<span style="color: #ffffff;">auto lo</span>

<span style="color: #ffffff;">iface lo inet loopback</span>
<span style="color: #ffffff;">#iface eth0 inet dhcp</span>
<span style="color: #ffffff;">auto eth0</span>
<span style="color: #ffffff;">iface eth0 inet static</span>
<span style="color: #ffffff;">address 192.168.1.200</span>
<span style="color: #ffffff;">netmask 255.255.255.0</span>
<span style="color: #ffffff;">gateway 192.168.1.1</span></pre>
<ul>
 	<li>dhcpの設定は#でコメントアウトを</li>
 	<li>設定後はrebootするのが素直</li>
 	<li>したくない時は</li>
 	<li>
<pre><span style="color: #ffffff;">$ sudo service networking restart</span></pre>
</li>
</ul>
</li>
</ul>
