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
<h2></h2>
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
 	<li>cv_cameraとmjpeg_serverを立ち上げる（roscoreは立ち上げておく）</li>
 	<li>
<pre class="p1"><span class="s1"><span style="color: #ffffff;">$ rosrun cv_camera cv_camera_node</span> 
</span><span class="s1"><span style="color: #ffffff;">$ rosrun mjpeg_server mjpeg_server</span> </span></pre>
</li>
 	<li>ノードの確認
<pre><span style="color: #ffffff;">$ rosnode list
<span class="s1">/cv_camera
</span><span class="s1">/mjpeg_server
</span><span class="s1">/rosout</span></span></pre>
</li>
 	<li>ディレクトリのように管理されている</li>
</ul>
</li>
</ul>
<!--nextpage-->
<h2>トピック・メッセージ</h2>
<ul>
 	<li>今度はrostopic listと打ってみる</li>
 	<li>データをやり取りする口（トピック）が表示される</li>
 	<li>
<pre class="p1"><span class="s1" style="color: #ffffff;">$ rostopic list</span>
<span class="s1" style="color: #ffffff;">/cv_camera/camera_info</span>
<span class="s1" style="color: #ffffff;">/cv_camera/image_raw</span>
<span class="s1" style="color: #ffffff;">/rosout</span>
<span class="s1" style="color: #ffffff;">/rosout_agg</span></pre>
</li>
 	<li>トピックからデータを取り出す（先週もやりました）</li>
 	<li>
<pre class="p1"><span class="s1" style="color: #ffffff;">$ rostopic echo /cv_camera/image_raw</span></pre>
<ul>
 	<li>このデータは「メッセージ」と呼ばれる</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>パブリッシャ・
サブスクライバ</h2>
<ul>
 	<li>各ノードがトピックを通じてメッセージを融通することで全体として仕事を行う</li>
 	<li>mjpeg_serverは/cv_camera/image_rawからカメラ画像を取得して、ブラウザに画像を配信</li>
 	<li>データを出す側が<span style="color: #ff0000;">パブリッシャ</span></li>
 	<li>データを受け取る側が<span style="color: #ff0000;">サブスクライバ</span></li>
 	<li>この構造でサブスクライバ側の柔軟な組み換えが可能に
<ul>
 	<li>ブラウザに配信するノード、顔検出をするノード、mp4に変換するノード・・・</li>
</ul>
</li>
</ul>
<h2><!--nextpage--></h2>
<h2>ROSプログラミングの準備</h2>
<ul>
 	<li>パブリッシャ、サブスクライバを作ってみましょう</li>
 	<li>その前に・・・</li>
 	<li>「ワークスペース」（作業場）を作る</li>
 	<li>
<pre class="p1"><span style="color: #ffffff;"><span class="s1">$ cd
$ mkdir -p catkin_ws/src
</span><span class="s1">$ cd ~/catkin_ws/src
</span><span class="s1">$ catkin_init_workspace 
</span><span class="s1">Creating symlink "/home/ubuntu/catkin_ws/src/CMakeLists.txt" pointing to "/opt/ros/kinetic/share/catkin/cmake/toplevel.cmake"
</span><span class="s1">$ ls
</span><span class="s1">CMakeLists.txt</span></span></pre>
</li>
</ul>
<h2><!--nextpage--></h2>
<ul>
 	<li>.bashrcの末尾に以下を記述</li>
</ul>
<pre class="p1"><span style="color: #ffffff;"><span class="s1">source</span><span class="s2"> /opt/ros/kinetic/setup.bash #これは元からある
</span><span class="s1">source</span><span class="s2"> ~/catkin_ws/devel/setup.bash #ここから3行追加</span></span>
<span style="color: #ffffff;"><span class="s1">export</span><span class="s3"> ROS_MASTER_URI=</span><span class="s2">http://localhost:</span><span class="s4">11311</span></span>
<span style="color: #ffffff;"><span class="s1">export</span><span class="s2"> ROS_HOSTNAME=</span><span class="s5">localhost
</span></span></pre>
<ul>
 	<li>環境のビルド</li>
</ul>

<pre><span style="color: #ffffff;">$ cd ~/catkin_ws</span>
<span class="s1" style="color: #ffffff;">$ catkin_make</span></pre>

<!--nextpage-->
<h2>パブリッシャを作る</h2>
<p class="p1"></p>

<h2><!--nextpage--></h2>
<h2>通信の大雑把な説明</h2>
