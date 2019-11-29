<h1 style="font-size: 250%;">ロボットシステム学</h1>
<h2>第5回</h2>
上田 隆一

2016年10月26日\@千葉工業大学

<!--nextpage-->
<h2>今日の内容</h2>
<ul>
 	<li>ファイルシステムとデバイス</li>
</ul>
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
 	<li>ストレージ側のファイルシステム
<ul>
 	<li>何百万、何百兆のゼロイチの並びのどこにファイル・ディレクトリ、その他メタデータ等を置くかを規定・実現</li>
</ul>
</li>
 	<li>主なファイルシステム
<ul style="font-size: 80%;">
 	<li>ext4, ext3, (extended file system): Linux</li>
 	<li>UFS2 (UNIX File System2): FreeBSD</li>
 	<li>HFS+ (Hierarchical File System Plus): Mac OS X</li>
 	<li>NTFS (NT File System), FAT16, FAT32, exFAT: Windows</li>
</ul>
</li>
 	<li>特殊なファイルシステム
<ul>
 	<li>procfs, sysfs, tmpfs, スワップファイルシステム</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>ストレージにデータを書く仕組み</h2>
<ul>
 	<li>ストレージがあったら、いくつかのパーティションに分け、それぞれの形式でファイルシステムをフォーマットして使う</li>
 	<li>ストレージの区分け
<ul>
 	<li>パーティション[latex]\\rightarrow[/latex]ローカルファイルシステム[latex]\\rightarrow[/latex]ブロックグループ[latex]\\rightarrow[/latex]ブロック</li>
 	<li>注意: HDD 自体にもセクタ、トラック、シリンダーという階層構造があるが、それは別の話</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>パーティションの確認</h2>
<ul>
 	<li><span style="color: #0000ff;">$ sudo parted -l</span>
<pre><span style="color: #ffffff;">Model: SD SA16G (sd/mmc)</span>
<span style="color: #ffffff;">Disk /dev/mmcblk0: 15.6GB</span>
<span style="color: #ffffff;">Sector size (logical/physical): 512B/512B</span>
<span style="color: #ffffff;">Partition Table: msdos</span>
<span style="color: #ffffff;">Disk Flags:</span>

<span style="color: #ffffff;">Number  Start   End     Size    Type      File system  Flags</span>
<span style="color: #ffffff;">1      4194kB  1089MB  1085MB  primary   fat32        lba</span>
<span style="color: #ffffff;">2      1091MB  15.6GB  14.5GB  extended</span>
<span style="color: #ffffff;">5      1095MB  1158MB  62.9MB  logical   fat16        lba</span>
<span style="color: #ffffff;">6      1162MB  15.6GB  14.5GB  logical   ext4</span>
<span style="color: #ffffff;">3      15.6GB  15.6GB  33.6MB  primary   ext4</span></pre>
</li>
</ul>
<!--nextpage-->
<h2>iノード、ディレクトリ</h2>
<ul>
 	<li>ファイルを管理するためのデータ</li>
 	<li>iノード番号: ファイルやディレクトリ（これもファイル）の固有番号
<ul>
 	<li>
<p class="p1"><span class="s1" style="color: #0000ff;">$ ls -i <span style="color: #333333;">で、iノード番号が表示できる</span></span></p>
</li>
 	<li>
<p class="p1">ディレクトリもファイルなので当然iノード番号を持つ</p>
</li>
</ul>
</li>
 	<li>ディレクトリ
<ul>
 	<li>ディレクトリエントリのリストの管理</li>
 	<li>ディレクトリエントリ
<ul>
 	<li>ファイルのiノードと名前</li>
 	<li>（ファイル名を変えても変わるのはファイル本体ではない）</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2 class="p1">仮想ファイルシステム（<span class="s1">VFS</span>）</h2>
<ul>
 	<li>主な役割
<ul>
 	<li>ローカルファイルシステムの違いを吸収
<ul>
 	<li>write,read 等のシステムコールが呼ばれると各フォーマット用の関数に変換される</li>
 	<li>i ノードという概念がないローカルファイルシステムもi ノードをなんとか再現</li>
</ul>
</li>
</ul>
</li>
 	<li>機能
<ul>
 	<li>メモリ上にi ノード（inode 構造体）やディレクトリエントリ（dentry 構造体）を展開してユーザプログラムとやりとり</li>
 	<li>データブロックの内容をメモリ上に保持（キャッシュ）</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>パーティションの作成</h2>
<ul>
 	<li>partedコマンドを作成
<ul>
 	<li>例/dev/sdcに見えるUSBメモリをext4でフォーマット</li>
</ul>
</li>
</ul>
<pre><span style="color: #ffffff;">$ sudo parted /dev/sdc</span>
<span style="color: #ffffff;">GNU Parted 3.2</span>
<span style="color: #ffffff;">Using /dev/sdc</span>
<span style="color: #ffffff;">Welcome to GNU Parted! Type 'help' to view a list of commands.</span>
<span style="color: #ffffff;">(parted) mklabel gpt                                                      </span>
<span style="color: #ffffff;">(parted) unit GB                                                          </span>
<span style="color: #ffffff;">(parted) print                                                            </span>
<span style="color: #ffffff;">Model: TOSHIBA TransMemory-Mx (scsi)</span>
<span style="color: #ffffff;">Disk /dev/sdc: 62.4GB</span>
<span style="color: #ffffff;">Sector size (logical/physical): 512B/512B</span>
<span style="color: #ffffff;">Partition Table: gpt</span>
<span style="color: #ffffff;">Disk Flags:</span>

<span style="color: #ffffff;">Number  Start  End  Size  File system  Name  Flags</span></pre>
&nbsp;

<!--nextpage-->
<ul>
 	<li>続き
<ul>
 	<li>パーティションを作ったらext4でフォーマット</li>
</ul>
</li>
</ul>
<pre class="p1"><span class="s1" style="color: #ffffff;">(parted) mkpart</span>
<span class="s1" style="color: #ffffff;">Partition name?<span class="Apple-converted-space">  </span>[]? data1 <span class="Apple-converted-space">                                               </span></span>
<span class="s1" style="color: #ffffff;">File system type?<span class="Apple-converted-space">  </span>[ext2]? ext4</span>
<span class="s1" style="color: #ffffff;">Start? 0 <span class="Apple-converted-space">                                                                 </span></span>
<span class="s1" style="color: #ffffff;">End? 62.4<span class="Apple-converted-space">                                                                 </span></span>
<span class="s1" style="color: #ffffff;">(parted)<span class="Apple-converted-space">   q
</span>$</span><span class="s2"><span style="color: #ffffff;"> mkfs.ext4 /dev/sdc1</span> </span></pre>
<!--nextpage-->
<h2>マウント・アンマウント</h2>
<ul>
 	<li>既存のディレクトリにファイルシステムをぶら下げる
<ul>
 	<li>どこにでもぶら下げられる</li>
</ul>
</li>
 	<li>例: ~/tmpにさっきのUSBメモリのパーティションをぶら下げる
<ul>
 	<li>注意: ~/tmpの中でやると話がややこしくなるので~/で作業を</li>
 	<li>
<pre class="p1"><span style="color: #ffffff;"><span class="s1">$</span><span class="s2"> echo aaa &gt; ~/tmp/file1    #元のところにファイルを作っておきましょう
</span><span class="s1">$</span><span class="s3"> ls ~/tmp
 </span><span class="s2">file1
</span><span class="s1">$</span><span class="s2"> sudo mount /dev/sdc1 ./
</span><span class="s1">$</span><span class="s2"> sudo mount /dev/sdc1 ~/tmp   #マウント
</span><span class="s1">$</span><span class="s3"> ls ~/tmp/             #~/tmpが差しているディレクトリが変わる
 </span><span class="s2">lost+found</span></span></pre>
</li>
 	<li></li>
</ul>
</li>
</ul>
<!--nextpage-->
<ul>
 	<li>続き</li>
</ul>
<pre><span style="color: #ffffff;"><span class="s1">$</span><span class="s2"> df</span></span>
<span class="s2" style="color: #ffffff;">ファイルシス <span class="Apple-converted-space">  </span>1K-ブロック<span class="Apple-converted-space">      </span>使用 <span class="Apple-converted-space">    </span>使用可 使用% マウント位置</span>
<span style="color: #ffffff;">（中略）</span>
<span style="color: #ffffff;">/dev/sdc1         59871340     53064   56753856    1% /home/ueda/tmp
$<span class="s2"> sudo umount ~/tmp #アンマウント
</span><span class="s1">$</span><span class="s3"> ls ~/tmp/ #元に戻る</span>
<span class="s2">file1</span></span></pre>
<p class="p1"><!--nextpage--></p>

<h2 class="p1">擬似ファイルシステム</h2>
<ul>
 	<li>仮想ファイルシステムとやりとりして機器の機能や</li>
 	<li>OS 内部の情報を提供</li>
 	<li>主要なもの
<ul>
 	<li>devtmpfs（/dev/）: デバイスファイル置き場</li>
 	<li>procfs（/proc/）: プロセスの情報＋その他OS の情報</li>
 	<li>sysfs（/sys/）: OSの情報（/proc/が混乱したのでこちらに移動）</li>
 	<li>tmpfs（/run/shm/）: DRAM 上にファイルを置く仕組み</li>
</ul>
</li>
</ul>
<p class="p1"><!--nextpage--></p>

<h2>デバイスドライバ・
デバイスファイル</h2>
<ul>
 	<li>デバイスドライバ
<ul>
 	<li>計算機に接続された機器を操作するためのプログラム
<ul>
 	<li>HDD、ディスプレイ、カメラ、マイク、端末、 ...</li>
</ul>
</li>
</ul>
</li>
 	<li>デバイスファイル
<ul>
 	<li>デバイスドライバのインタフェース</li>
 	<li>ファイルとして表現されている
<ul>
 	<li>機械と言えども、結局データをin/outするという点でファイルとして抽象化可能</li>
</ul>
</li>
 	<li>/dev/の下に存在</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>/dev/下のファイル</h2>
<ul>
 	<li><span style="color: #0000ff;"><span class="s1">$</span><span class="s2"> ls -l /dev/</span></span>
<ul style="font-size: 80%;">
 	<li>日付右側の数字（10, 58 等）: デバイスの番号
<ul>
 	<li>メジャー番号（左側）: デバイスドライバ固有の番号</li>
 	<li>マイナー番号（右側）: デバイスドライバの中で与えられる番号</li>
</ul>
</li>
 	<li>ブロックデバイス、キャラクタデバイスの判別
<ul style="font-size: 80%;">
 	<li>パーミッション前の文字（b: ブロック、c: キャラクタ）</li>
 	<li>ブロックデバイス: データをブロック（塊）単位で読み書き</li>
 	<li>キャラクタデバイス: データをシーケンシャルに出し入れ</li>
 	<li>もう一つ、「ネットワークデバイス」（ eth0等のあれ）があるがLinuxでは別扱い</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>デバイスドライバ</h2>
<ul>
 	<li>カーネルの一部として動作
<ul>
 	<li>Cで言えばmainを持たない関数の塊</li>
 	<li>本来はカーネルと同時にコンパイルされるべき</li>
 	<li>ただしそれをやってしまうと時間や手間の無駄</li>
</ul>
</li>
 	<li>Linuxにはカーネルの一部を動的に脱着する仕組みが存在
<ul>
 	<li>カーネルの一部: カーネルモジュール（拡張子 .ko）</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>カーネルモジュールの調査</h2>
<ul>
 	<li>ファイルの検索
<ul>
 	<li>
<pre class="p1"><span style="color: #ffffff;"><span class="s1">$</span><span class="s2"> sudo find / | grep '\\.ko$'</span></span></pre>
</li>
</ul>
</li>
 	<li>今使われているカーネルモジュールはlsmodで調査
<ul>
 	<li>
<pre><span style="color: #ffffff;">$ lsmod</span>
<span style="color: #ffffff;">Module                  Size  Used by</span>
<span style="color: #ffffff;">binfmt_misc             6388  1 </span>
<span style="color: #ffffff;">bnep                   10340  2 </span>
<span style="color: #ffffff;">hci_uart               17943  1 </span>
<span style="color: #ffffff;">btbcm                   5929  1 hci_uart</span>
<span style="color: #ffffff;">bluetooth             326067  22 bnep,btbcm,hci_uart</span>
<span style="color: #ffffff;">（以下略）</span></pre>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>カーネルモジュールの脱着</h2>
<ul>
 	<li>insmod, rmmod
<ul>
 	<li>他にmodplobe</li>
</ul>
</li>
 	<li>例:
<ul>
 	<li>
<pre class="p1"><span style="color: #ffffff;"><span class="s2">$ lsmod
（中略）
</span><span class="s1">i2c_dev <span class="Apple-converted-space">                </span>5859<span class="Apple-converted-space">  </span>0 
（略）
$<span class="s2"> sudo rmmod i2c_dev
$ lsmod | grep i2c
$ 
</span></span><span class="s1">$</span><span class="s2"> sudo insmod /usr/src/linux/drivers/i2c/i2c-dev.ko
$ lsmod
Module                  Size  Used by
i2c_dev                 5859  0 
（以下略）</span></span></pre>
</li>
</ul>
</li>
 	<li>insmodすると/sys/下で情報が見られるようになるので興味のある人は調査を
<ul>
 	<li>あとでカーネルモジュールを書くときにやります</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>デバイスドライバを作る</h2>
<ul>
 	<li>来週から2週にかけて取り組みます</li>
 	<li>デバイスドライバを作る時の制限
<ul>
 	<li>カーネルモジュールはカーネルの一部なので、今動いているカーネルと整合性がないと動かない</li>
 	<li>今動いているカーネルのバージョンにあったLinuxのヘッダファイルが必要</li>
</ul>
</li>
 	<li>Raspberry Piの場合
<ul>
 	<li>基本的に自分でLinuxのソースコードをダウンロードして、一度カーネルを作るのが面倒なようで手っ取り早い
<ul>
 	<li>これで整合性のあるヘッダファイルが得られる</li>
</ul>
</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>カーネルの再構築（宿題）</h2>
<ul>
 	<li>LinuxをGitHubからクローンしてビルドしてカーネルを作ります</li>
 	<li>手順
<ol>
 	<li>
<pre><span style="color: #ffffff;">$ git clone https://github.com/ryuichiueda/raspberry_pi_kernel_build_scripts.git</span>
<span style="color: #ffffff;">$ cd raspberry_pi_kernel_build_scripts</span>
<span style="color: #ffffff;">$ sudo ./kernel_build_and_install_for_pi2_pi3.bash</span>
<span style="color: #ffffff;">$ sudo reboot</span></pre>
</li>
</ol>
</li>
</ul>
<!--nextpage-->
<h2>カーネルの入れ替わりの確認</h2>
<ul>
 	<li>uname -aでビルドされた日時を確認</li>
</ul>
<pre><span style="color: #ffffff;">pi\@raspberrypi:~ $ uname -a
Linux raspberrypi 4.4.22-v7+ #1 SMP Mon Sep 26 13:11:18 JST 2016 armv7l GNU/Linux</span></pre>
