<h1 style="font-size: 250%;">ロボットシステム学</h1>
<h2>第5回</h2>
上田 隆一

2016年10月?日\@千葉工業大学

<!--nextpage-->
<h2>今日の内容</h2>
<ul>
 	<li>ファイルシステムとデバイス</li>
</ul>
<!--nextpage-->
<h2>カーネルの再構築（宿題）</h2>
<ul>
 	<li>LinuxをGitHubからクローンしてビルドしてカーネルを作ります</li>
 	<li>手順
<ol>
 	<li><span style="color: #00ffff;">$ git clone https://github.com/ryuichiueda/raspberry_pi_kernel_build_scripts.git</span></li>
 	<li><span style="color: #00ffff;">$ cd raspberry_pi_kernel_build_scripts</span></li>
 	<li><span style="color: #00ffff;">$ sudo ./kernel_build_and_install_for_pi2_pi3.bash</span></li>
 	<li><span style="color: #00ffff;">$ sudo reboot</span></li>
</ol>
</li>
 	<li>スクリプトの中は一度読んでおいてください</li>
</ul>
<!--nextpage-->
<h2>カーネルの入れ替わりの確認</h2>
<ul>
 	<li>uname -aでビルドされた日時を確認</li>
</ul>
<pre><span style="color: #ffffff;">pi\@raspberrypi:~ $ uname -a
Linux raspberrypi 4.4.22-v7+ #1 SMP Mon Sep 26 13:11:18 JST 2016 armv7l GNU/Linux</span></pre>
<!--nextpage-->
<h2>ファイルシステム</h2>
<ul>
 	<li>OS の最重要機能の一つ</li>
 	<li>機能
<ul>
 	<li>誰にでも分かりやすいもの</li>
 	<li>HDDを使えるようにする</li>
 	<li>USBメモリを使えるようにする</li>
</ul>
</li>
 	<li>人によっては意外なもの
<ul>
 	<li>外部の機器（センサ等）を使えるようにする</li>
 	<li>OS と通信する</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>ローカルファイルシステム</h2>
<ul>
 	<li>何百万、何百兆のゼロイチの並びのどこにファイル・ディレクトリ、その他メタデータ等を置くかを規定・実現</li>
 	<li>主なファイルシステム
<ul style="font-size: 80%;">
 	<li>ext4, ext3, (extended file system): Linux</li>
 	<li>UFS2 (UNIX File System2): FreeBSD, HFS+ (Hierarchical File System Plus): Mac OS X</li>
 	<li>NTFS (NT File System): Windows, FAT16, FAT32, exFAT: Windows（USB メモリ等）</li>
 	<li>他にZFS, XFS</li>
</ul>
</li>
 	<li>特殊なファイルシステム
<ul>
 	<li>procfs, sysfs, tmpfs, スワップファイルシステム</li>
</ul>
</li>
 	<li>ストレージがあったら、いくつかのパーティションに分け、それぞれの形式でファイルシステムをフォーマットして使う</li>
</ul>
<!--nextpage-->
<h2>デバイスドライバ</h2>
<ul>
 	<li>機器の機能をユーザが使えるようにするプログラム</li>
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
