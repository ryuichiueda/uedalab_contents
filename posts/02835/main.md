<h2></h2>
<h1 style="font-size: 250%;">ロボットシステム学</h1>
<h2>第13回</h2>
上田 隆一

2017年1月18日\@千葉工業大学

<!--nextpage-->
<h2>本日の内容</h2>
<ul>
 	<li>ROS
<ul>
 	<li>ROSのインストールが終わった状態からスタート</li>
 	<li>ノード間の通信</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>ROSの大雑把な説明</h2>
<!--nextpage-->
<h2>動作確認</h2>
<ul>
 	<li>$ roscore
<ul>
 	<li>色々情報が出てプログラムが立ち上がる（Ctrl+cで出る）</li>
</ul>
</li>
</ul>
<pre><span style="color: #ffffff;">$ roscore</span>
<span style="color: #ffffff;">（略）</span>
<span style="color: #ffffff;">started roslaunch server http://localhost:39310/</span>
<span style="color: #ffffff;">ros_comm version 1.12.6</span>

<span style="color: #ffffff;">SUMMARY</span>
<span style="color: #ffffff;">========</span>

<span style="color: #ffffff;">PARAMETERS</span>
<span style="color: #ffffff;">* /rosdistro: kinetic</span>
<span style="color: #ffffff;">* /rosversion: 1.12.6</span>

<span style="color: #ffffff;">NODES</span>

<span style="color: #ffffff;">auto-starting new master</span>
<span style="color: #ffffff;">process[master]: started with pid [1439]</span>
<span style="color: #ffffff;">ROS_MASTER_URI=http://localhost:11311/</span>

<span style="color: #ffffff;">setting /run_id to b749a100-d0dc-11e5-a506-b827eb17cb96</span>
<span style="color: #ffffff;">process[rosout-1]: started with pid [1452]</span>
<span style="color: #ffffff;">started core service [/rosout]</span></pre>
