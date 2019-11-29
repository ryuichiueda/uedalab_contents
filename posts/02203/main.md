<h1 style="font-size: 250%;">ロボットシステム学</h1>
<h2>第6/7回</h2>
上田 隆一

2016年11月2日\@千葉工業大学

<!--nextpage-->
<h2>今日の内容</h2>
<ul>
 	<li>デバイスドライバを作る</li>
 	<li>次回はGPIOの操作に挑戦します
<ul>
 	<li> 第6回はPCの中で完結する話
<ul>
 	<li>ただしRaspbianとUbuntuでは少しやり方が違う</li>
</ul>
</li>
 	<li>第7回はRaspberry Pi必須</li>
</ul>
</li>
 	<li>リポジトリ
<ul>
 	<li><a href="https://github.com/ryuichiueda/robosys_device_drivers" target="_blank">https://github.com/ryuichiueda/robosys_device_drivers</a></li>
</ul>
</li>
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
<h2>最初のコード</h2>
<ul>
 	<li>適当なディレクトリを作ってその中に</li>
 	<li>ファイル名は「myled.c」にしましょう</li>
 	<li>コードの中身
<ul>
 	<li>カーネルモジュールの初期化と後始末の関数を書く</li>
 	<li>マクロに関数名を与える</li>
</ul>
</li>
</ul>
<pre><span style="color: #ffffff;">#include &lt;linux/module.h&gt;

static int __init init_mod(void)
{
 return 0;
}

static void __exit cleanup_mod(void)
{
}

module_init(init_mod);
module_exit(cleanup_mod);
</span></pre>
<!--nextpage-->
<h2>Makefileを書く</h2>
<ul>
 	<li>Makefileという名前のファイルを作って次のように書く</li>
 	<li><span style="color: #ff0000;">インデントはタブで</span></li>
 	<li>Makefileのごくごく簡単な説明
<ul style="font-size: 80%;">
 	<li>&lt;作りたいファイル or 行いたい処理&gt;: &lt;必要なファイル&gt;と書いてその下に実行するコマンドを書く</li>
 	<li>コロンの左側をターゲットと言う</li>
 	<li>makeと打つと最初に書いてあるターゲットの作成が試みられる</li>
 	<li>必要なファイルがないと、ないファイルのターゲットの処理が試みられる</li>
</ul>
</li>
</ul>
<pre class="p1"><span class="s1" style="color: #ffffff;">obj-m:= myled.o #オブジェクトファイルの名前を指定（拡張子はo）</span>

<span class="s1" style="color: #ffffff;">myled.ko: myled.c </span>
<span class="s1" style="color: #ffffff;"> make -C /usr/src/linux M=`pwd` V=1 modules #makeと打つと実行される</span>
<span class="s1" style="color: #ffffff;">clean:</span>
<span class="s1" style="color: #ffffff;"> make -C /usr/src/linux M=`pwd` V=1 clean #make cleanで実行</span></pre>
&nbsp;

<!--nextpage-->
<h2>コンパイルと実行
インストール</h2>
<ul>
 	<li>insmodでインストールできる</li>
 	<li>/dev/等にはまだ何も出てこない</li>
</ul>
<pre><span style="color: #ffffff;">$ make #Makefileとmyled.cが正しければこれでOK</span>
<span style="color: #ffffff;">$ ls #確認</span>
<span class="s1"><span style="color: #ffffff;">Makefile<span class="Apple-converted-space">  </span>Module.symvers<span class="Apple-converted-space">  </span>modules.order<span class="Apple-converted-space">  </span>myled.c<span class="Apple-converted-space">  </span>myled.ko<span class="Apple-converted-space">  </span>myled.mod.c<span class="Apple-converted-space">  </span>myled.mod.o<span class="Apple-converted-space">  </span>myled.o
$ sudo insmod myled.ko
</span></span><span style="color: #ffffff;"><span class="s1">$</span><span class="s2"> lsmod
</span><span class="s2">Module<span class="Apple-converted-space">                  </span>Size<span class="Apple-converted-space">  </span>Used by
</span><span class="s2">myled<span class="Apple-converted-space">                    </span>735<span class="Apple-converted-space">  </span>0 
...
</span><span class="s1">$</span><span class="s2"> sudo rmmod myled</span></span></pre>
<!--nextpage-->
<h2>ログを吐くようにする</h2>
<ul>
 	<li>init_modとcleanup_modに「printk」という関数を追加</li>
 	<li>KERN_INFO: ログのレベルを示すマクロ</li>
 	<li>__FILE__: ソースコードのファイル名</li>
</ul>
<pre><span style="color: #ffffff;">static int __init init_mod(void)
{
 printk(KERN_INFO "%s is loaded.\\n",__FILE__);
 return 0;
}

static void __exit cleanup_mod(void)
{
 printk(KERN_INFO "%s is unloaded.\\n",__FILE__);
}
</span></pre>
<!--nextpage-->
<h2>動作確認</h2>
<ul>
 	<li>/var/log/messagesにカーネルモジュールの脱着が記録される</li>
</ul>
<pre><span style="color: #ffffff;">$ make
$ sudo insmod myled.ko
pi\@raspberrypi:~/myled_lecture $ tail /var/log/messages
...
Oct 23 11:42:48 raspberrypi kernel: [ 5639.631142] /home/pi/myled_lecture/myled.c is loaded.
$ sudo rmmod myled 
pi\@raspberrypi:~/myled_lecture $ tail /var/log/messages
...
Oct 23 11:44:23 raspberrypi kernel: [ 5734.994105] /home/pi/myled_lecture/myled.c is unloaded.
</span></pre>
<!--nextpage-->
<h2>ヘッダにモジュールの情報を記述</h2>
<ul>
 	<li>作者、何のモジュール化、ライセンスは何か、バージョン</li>
 	<li>ライセンス
<ul>
 	<li>基本的にはGPL（後日説明）</li>
</ul>
</li>
</ul>
<pre><span style="color: #ffffff;">#include &lt;linux/module.h&gt;
MODULE_AUTHOR("Ryuichi Ueda");
MODULE_DESCRIPTION("driver for LED control");
MODULE_LICENSE("GPL");
MODULE_VERSION("0.1");

static int __init init_mod(void)
（以下略）
</span></pre>
<!--nextpage-->
<h2>情報の確認</h2>
<ul>
<ul>
 	<li>modinfoというコマンドを利用</li>
</ul>
</ul>
<pre><span style="color: #ffffff;">$ modinfo myled.ko
filename: /home/pi/myled_lecture/myled.ko
version: 0.1
license: GPL
description: driver for LED control
author: Ryuichi Ueda
srcversion: 1278C67A0C932CB5D86D367
depends: 
vermagic: 4.4.27-v7+ SMP mod_unload modversions ARMv7</span> 
</pre>
<!--nextpage-->
<h2>デバイス番号の取得</h2>
<ul>
 	<li>解説は次ページ</li>
</ul>
<pre><span style="color: #ffffff;">#include &lt;linux/module.h&gt;
<span style="color: #ffff00;">#include &lt;linux/fs.h&gt;</span>
（中略）（MODULE_AUTHOR〜MODULE_VERSION）
<span style="color: #ffff00;">static dev_t dev;</span>

static int __init init_mod(void)
{
<span style="color: #ffff00;">	int retval;
	retval = alloc_chrdev_region(&amp;dev, 0, 1, "myled");
	if(retval &lt; 0){
		printk(KERN_ERR "alloc_chrdev_region failed.\\n");
		return retval;
	}
	printk(KERN_INFO "%s is loaded. major:%d\\n",__FILE__,MAJOR(dev));
</span>	return 0;
}

static void __exit cleanup_mod(void)
{
<span style="color: #ffff00;">	unregister_chrdev_region(dev, 1);
	printk(KERN_INFO "%s is unloaded. major:%d\\n",__FILE__,MAJOR(dev));</span>
}
</span><span style="color: #ffffff;">（略）
</span></pre>
<!--nextpage-->
<ul>
 	<li>alloc_chrdev_region: デバイス番号の取得
<ul>
 	<li>引数: dev（番号の入れ物）のアドレス、0番から1個マイナー番号が欲しい、デバイスの名前はmyled</li>
</ul>
</li>
 	<li>unregister_chrdev_region: デバイス番号の解放
<ul>
 	<li>引数: dev、マイナー番号を1個返す</li>
 	<li>これを怠るとinsmodのたびに番号が増えていくので実験すると面白い</li>
</ul>
</li>
 	<li>MAJOR: devからメジャー番号を取り出すマクロ</li>
</ul>
<!--nextpage-->
<h2>メジャー番号の確認</h2>
&nbsp;
<pre><span style="color: #ffffff;">$ make
$ sudo insmod myled.ko
$ tail /var/log/messages
（略）
Oct 23 12:26:56 raspberrypi kernel: [ 492.932021] /home/pi/myled_lecture/myled.c 
</span><span style="color: #ffffff;">is loaded. <span style="color: #ffff00;">major:243
<span style="color: #ffffff;">$ cat /proc/devices | grep myled
<span style="color: #ffff00;">243 myled</span>
$sudo rmmod myled</span></span></span></pre>
<!--nextpage-->
<h2>キャラクタ型デバイスを作る</h2>
<ul>
 	<li>コードに以下を追加
<ul>
 	<li>ヘッダファイル: linux/cdev.hのinclude</li>
 	<li>キャラクタデバイスの挙動</li>
 	<li>キャラクタデバイスの登録</li>
</ul>
</li>
</ul>
<!--nextpage-->
<ul>
 	<li>static struct cdev cdv: キャラクタデバイスの情報を格納する構造体</li>
 	<li>led_write: デバイスファイルに書き込みがあった時の挙動</li>
 	<li>static struct file_operations led_fops: 挙動を書いた関数のポインタを格納する構造体</li>
</ul>
<pre><span style="color: #ffffff;">#include &lt;linux/module.h&gt;
#include &lt;linux/fs.h&gt;
<span style="color: #ffff00;">#include &lt;linux/cdev.h&gt;
</span>（中略）（MODULE_AUTHOR〜MODULE_VERSION）
static dev_t dev;
<span style="color: #ffff00;">static struct cdev cdv;
</span>
<span style="color: #ffff00;">static ssize_t led_write(struct file* filp, const char* buf, size_t count, loff_t* pos)
{
 printk(KERN_INFO "led_write is called\\n");
 return 1; //読み込んだ文字数を返す（この場合はダミーの1）
}

static struct file_operations led_fops = {
 .owner = THIS_MODULE,
 .write = led_write
};</span>
（次ページへ）
</span></pre>
<!--nextpage-->
<ul>
 	<li>cdev_init, cdev_del:キャラクタデバイスの初期化と破棄
<ul>
 	<li>file_operationsをcdev_initに渡している</li>
</ul>
</li>
 	<li>cdev_add: キャラクタデバイスをカーネルに登録</li>
</ul>
<pre><span style="color: #ffffff;">static int __init init_mod(void)
{
 （略。デバイス番号を取得する部分）
 printk(KERN_INFO "%s is loaded. major:%d\\n",__FILE__,MAJOR(dev));
<span style="color: #ffff00;">
 cdev_init(&amp;cdv, &amp;led_fops);
 retval = cdev_add(&amp;cdv, dev, 1);
 if(retval &lt; 0){
 printk(KERN_ERR "cdev_add failed. major:%d, minor:%d",MAJOR(dev),MINOR(dev));
 return retval;
 }</span>

 return 0;
}

static void __exit cleanup_mod(void)
{<span style="color: #ffff00;">
 cdev_del(&amp;cdv);</span>
 unregister_chrdev_region(dev, 1);
 printk(KERN_INFO "%s is unloaded. major:%d\\n",__FILE__,MAJOR(dev));
}
（略）
</span></pre>
<!--nextpage-->
<h2>動作確認</h2>
<ul>
 	<li>mknodでデバイスファイルを手動作成
<ul>
 	<li>c: キャラクタデバイス、243: メジャー番号（場合により変わる）、0: マイナー番号</li>
</ul>
</li>
</ul>
<pre><span style="color: #ffffff;">$ sudo insmod myled.ko
$ tail /var/log/messages
（略）
Oct 23 12:59:08 raspberrypi kernel: [ 2424.243775] /home/pi/myled_lecture/myled.c
 is loaded. major:243
$ sudo mknod /dev/myled0 c 243 0
$ sudo chmod 666 /dev/myled0 
$ ls -l /dev/myled0 
crw-rw-rw- 1 root root 243, 0 10月 23 13:00 /dev/myled0
</span></pre>
<!--nextpage-->
<ul>
 	<li>デバイスファイルに4文字（abcと改行記号）書き込む
<ul>
 	<li>ログに4回、led_writeに仕掛けたprintkの出力が残る</li>
</ul>
</li>
</ul>
<pre><span style="color: #ffffff;">$ echo abc &gt; /dev/myled0 
$ tail /var/log/messages
（略）
Oct 23 12:59:08 raspberrypi kernel: [ 2424.243775] /home/pi/myled_lecture/myled.c is loaded. major:243
Oct 23 13:03:08 raspberrypi kernel: [ 2664.510510] led_write is called
Oct 23 13:03:08 raspberrypi kernel: [ 2664.510533] led_write is called
Oct 23 13:03:08 raspberrypi kernel: [ 2664.510543] led_write is called
Oct 23 13:03:08 raspberrypi kernel: [ 2664.510551] led_write is called
$ sudo rm /dev/myled0 #後始末
$ sudo rmmod myled
</span></pre>
<!--nextpage-->
<h2>クラスの作成と削除</h2>
<ul>
 	<li>/sys/class下にこのデバイスの情報を置く</li>
 	<li>class_createで作成、class_destroyで削除
<ul>
 	<li style="font-size: 80%;">THIS_MODULE: このモジュールを管理する構造体のポインタ</li>
</ul>
</li>
</ul>
<pre><span style="color: #ffffff;">（略。ヘッダファイル）
<span style="color: #ffff00;">#include &lt;linux/device.h&gt; //追加</span>
（中略）（MODULE_*とグローバル変数）
<span style="color: #ffff00;">static struct class *cls = NULL; //追加</span>
（中略）
static int __init init_mod(void)
{ （中略）
<span style="color: #ffff00;"> cls = class_create(THIS_MODULE,"myled"); //ここから追加
 if(IS_ERR(cls)){
 printk(KERN_ERR "class_create failed.");
 return PTR_ERR(cls);
 }</span>
 return 0;
}

static void __exit cleanup_mod(void)
{
 cdev_del(&amp;cdv);
<span style="color: #ffff00;"> class_destroy(cls); //追加</span>
（以下略）
</span></pre>
<!--nextpage-->
<h2>/sys下の確認</h2>
<ul>
 	<li>/sys/class下にmyledというディレクトリができる</li>
 	<li>まだ中身は空</li>
</ul>
<pre><span style="color: #ffffff;">$ sudo insmod myled.ko
$ ls -l /sys/class/myled/ #ディレクトリができている
合計 0
</span></pre>
<!--nextpage-->
<h2>クラスへの情報書き込み</h2>
<ul>
 	<li>device_create, device_destroy: デバイス情報の作成、削除
<ul>
 	<li style="font-size: 80%;">引数（NULLのところ以外）: クラス、デバイス、デバイスの名前、 デバイスのマイナー番号</li>
</ul>
</li>
</ul>
<pre><span style="color: #ffffff;">static int __init init_mod(void)
{ （中略）
 cls = class_create(THIS_MODULE,"myled");
 if(IS_ERR(cls)){
 printk(KERN_ERR "class_create failed.");
 return PTR_ERR(cls);
 }
<span style="color: #ffff00;"> device_create(cls, NULL, dev, NULL, "myled%d",MINOR(dev));</span>
 return 0;
}

static void __exit cleanup_mod(void)
{
 cdev_del(&amp;cdv);
 <span style="color: #ffff00;"> device_destroy(cls, dev);</span>
 class_destroy(cls);
（以下略）
</span></pre>
<!--nextpage-->
<h2>/sys下の確認</h2>
<pre><span style="color: #ffffff;">$ ls -l /sys/class/myled/
合計 0
lrwxrwxrwx 1 root root 0 10月 23 13:40 myled0 -&gt; ../../devices/virtual/myled/myled0
$ ls -l /sys/class/myled/myled0/
合計 0
-r--r--r-- 1 root root 4096 10月 23 13:40 dev
drwxr-xr-x 2 root root 0 10月 23 13:40 power
lrwxrwxrwx 1 root root 0 10月 23 13:40 subsystem -&gt; ../../../../class/myled
-rw-r--r-- 1 root root 4096 10月 23 13:39 uevent
$ cd /sys/class/myled/myled0/
$ cat dev
243:0 #これがメジャー番号とマイナー番号
</span></pre>
<!--nextpage-->
<h2>/dev下の確認</h2>
<ul>
 	<li>udevというサービスが/sys/class/myled/myled0/devを見て
デバイスファイルを作成</li>
</ul>
<pre><span style="color: #ffffff;">$ ls -l /dev/myled0 
crw------- 1 root root 243, 0 10月 23 13:39 /dev/myled0
$ sudo rmmod myled
$ ls -l /dev/myled0 #rmmodで自動的にデバイスファイルが消える
ls: /dev/myled0 にアクセスできません: そのようなファイルやディレクトリはありません
</span></pre>
<!--nextpage-->
<h2>デバイスファイルからの字の読み込み</h2>
<ul>
 	<li>ユーザランドからの字の書き込みをカーネルに読み込む
<ul>
 	<li>アドレス空間が違う</li>
 	<li>copy_from_userという関数を使用</li>
</ul>
</li>
</ul>
<pre><span style="color: #ffffff;">#include &lt;asm/uaccess.h&gt; //ヘッダに追加</span>

<span style="color: #ffffff;">//led_writeを次のように書き換え</span>
<span style="color: #ffffff;">static ssize_t led_write(struct file* filp, const char* buf, size_t count, loff_t* pos)</span>
<span style="color: #ffffff;">{</span>
<span style="color: #ffffff;"> char c; //読み込んだ字を入れる変数</span>
<span style="color: #ffffff;"> if(copy_from_user(&amp;c,buf,sizeof(char)))</span>
<span style="color: #ffffff;"> return -EFAULT;</span>

<span style="color: #ffffff;"> printk(KERN_INFO "receive %c\\n",c);</span>
<span style="color: #ffffff;"> return 1;</span>
<span style="color: #ffffff;">}</span></pre>
<!--nextpage-->
<h2>動作確認</h2>
<ul>
 	<li>（細かい手順はもう書きません）</li>
</ul>
<pre><span style="color: #ffffff;">$ echo abc &gt; /dev/myled0 </span>
<span style="color: #ffffff;">$ tail /var/log/messages</span>
<span style="color: #ffffff;">（中略）</span>
<span style="color: #ffffff;">Oct 23 14:10:45 raspberrypi kernel: [ 1437.805316] /home/pi/robosys_device_drivers/myled.c is loaded. major:243</span>
<span style="color: #ffffff;">Oct 23 14:11:10 raspberrypi kernel: [ 1462.960887] receive a</span>
<span style="color: #ffffff;">Oct 23 14:11:10 raspberrypi kernel: [ 1462.960911] receive b</span>
<span style="color: #ffffff;">Oct 23 14:11:10 raspberrypi kernel: [ 1462.960920] receive c</span>
<span style="color: #ffffff;">Oct 23 14:11:10 raspberrypi kernel: [ 1462.960929] receive</span></pre>
<!--nextpage-->
<h2>デバイスファイルからの出力</h2>
<ul>
 	<li><span style="color: #ff0000;">catすると寿司を表示する無駄機能</span>の実装
<ul>
 	<li>copy_to_userでカーネルからユーザランドへ文字を送ります</li>
</ul>
</li>
</ul>
<pre><span style="color: #ffffff;">static ssize_t sushi_read(struct file* filp, char* buf, size_t count, loff_t* pos)</span>
<span style="color: #ffffff;">{</span>
<span style="color: #ffffff;">    int size = 0;</span>
<span style="color: #ffffff;">     char sushi[] = {0xF0,0x9F,0x8D,0xA3,0x0A}; //寿司の絵文字のバイナリ</span>
<span style="color: #ffffff;">     if(copy_to_user(buf+size,(const char *)sushi, sizeof(sushi))){</span>
<span style="color: #ffffff;">        printk( KERN_INFO "sushi : copy_to_user failed\\n" );</span>
<span style="color: #ffffff;">     return -EFAULT;</span>
<span style="color: #ffffff;">     }</span>
<span style="color: #ffffff;">     size += sizeof(sushi);</span>
<span style="color: #ffffff;">    return size;</span>
<span style="color: #ffffff;">}</span>

<span style="color: #ffffff;">static struct file_operations led_fops = {</span>
<span style="color: #ffffff;">     .owner = THIS_MODULE,</span>
<span style="color: #ffffff;">     .write = led_write,</span>
<span style="color: #ffffff;">     .read = sushi_read</span>
<span style="color: #ffffff;">};</span></pre>
<!--nextpage-->
<h2>GPIOの操作</h2>
<ul>
 	<li>ピンの操作は特定のメモリアドレスへゼロイチを書き込むことで行う
<ul>
 	<li>メモリマップドI/O</li>
 	<li>番地をどう調べるか（なかなか難しい問題）</li>
</ul>
</li>
 	<li>Raspberry Piの場合
<ul>
 	<li><a href="https://www.raspberrypi.org/documentation/hardware/raspberrypi/bcm2835/README.md" target="_blank">Raspberry Piのページのbcm2835に関するページ</a>で調査
<ul>
 	<li>「<a href="https://www.raspberrypi.org/documentation/hardware/raspberrypi/bcm2835/BCM2835-ARM-Peripherals.pdf">Peripheral specification</a>」をクリック</li>
</ul>
</li>
 	<li>Raspberry Pi 3のbcm2837とはレジスタのアドレスの開始位置が違うので読み替え</li>
</ul>
</li>
</ul>
<!--nextpage-->

&nbsp;
