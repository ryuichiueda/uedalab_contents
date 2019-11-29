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
<h2><!--nextpage--></h2>
<h2>通信の大雑把な説明</h2>
<ul>
 	<li>ノードは「トピック」や「サービス」を持つ</li>
 	<li>トピックやサービスはディレクトリのように管理
<ul>
 	<li>UNIX系OSのプロセスにあたるのがノード、ファイルシステムに当たるのがトピックやサービス</li>
</ul>
</li>
 	<li>トピック
<ul>
 	<li>情報がダラダラと流れるデバイスファイルのようなもの</li>
</ul>
</li>
 	<li>サービス
<ul>
 	<li>呼び出すと何か仕事をして結果を返すデバイスファイルのようなもの</li>
 	<li>呼び出し側を待たせる</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>動作確認</h2>
<ul>
 	<li>$ roscore
<ul>
 	<li>ROSのバックにいるプログラムが立ち上がる</li>
 	<li>Ctrl+cで出る</li>
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
<!--nextpage-->
<h2>ROSのノード</h2>
<ul>
 	<li>プログラムのプロセス一つ一つが「ノード」と呼ばれる</li>
 	<li>ノードの例
<ul>
 	<li>cv_cameraを立ち上げる（roscoreは立ち上げておく）</li>
 	<li>
<pre class="p1"><span class="s1"><span style="color: #ffffff;">$ rosrun cv_camera cv_camera_node</span> </span></pre>
</li>
 	<li>ノードを確認（cv_cameraがノード）
<pre><span style="color: #ffffff;">$ rosnode list</span>
<span style="color: #ffffff;">/cv_camera</span>
<span style="color: #ffffff;">/rosout</span></pre>
</li>
</ul>
</li>
</ul>

<!--nextpage-->

<ul>
 	<li>カメラの画像を出力するノード、ブラウザにデータを飛ばすノード、モータを動かすノード、行動を決めるノード</li>
</ul>
<ul>
 	<li>ノード間の通信を「ROSマスタ」が仕切る</li>
 	<li>ノードがネットワーク越しに通信し合って連携</li>
</ul>
&nbsp;
