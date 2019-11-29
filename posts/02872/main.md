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
<span class="s1" style="color: #ffffff;">$ catkin_make
$ source ~/.bashrc
</span></pre>
<ul>
 	<li>確認
<ul>
 	<li>ROS_PACKAGE_PATHにcatkin_ws/srcがセットされているはず</li>
</ul>
</li>
</ul>
<pre><span style="color: #ffffff;">$ echo $ROS_PACKAGE_PATH</span>
<span class="s1" style="color: #ffffff;">/home/ubuntu/catkin_ws/src:/opt/ros/kinetic/share</span></pre>
<!--nextpage-->
<h2>パッケージを作る</h2>
<ul>
 	<li>パッケージ: いくつかのノードを含んだ一単位</li>
 	<li>パッケージの生成
<ul>
 	<li>catkin_create_pkg &lt;作るパッケージの名前&gt; [使用するライブラリ...]</li>
 	<li>rospy: Pythonでノードを作るときに使用</li>
 	<li>パッケージを作ったら下にscriptsというディレクトリを作成
<ul>
 	<li>ここにノードとなるプログラムを置く</li>
</ul>
</li>
</ul>
</li>
</ul>
<pre class="p1"><span style="color: #ffffff;"><span class="s1">$ cd ~/catkin_ws/src
</span>$ catkin_create_pkg mypkg rospy</span>
<span style="color: #ffffff;"> Created file mypkg/package.xml</span>
<span style="color: #ffffff;"> Created file mypkg/CMakeLists.txt</span>
<span style="color: #ffffff;"> Created folder mypkg/src</span>
<span style="color: #ffffff;"> Successfully created files in /home/ubuntu/catkin_ws/src/mypkg. Please adjust the values in package.xml.
<span class="s1">$ cd mypkg/
</span><span class="s1">$ mkdir scripts</span></span>
<span class="s1" style="color: #ffffff;">$ cd scripts/</span></pre>
<!--nextpage-->
<h2>パブリッシャを作る</h2>
<ul>
 	<li>次のようなプログラム（count.py）を書いてみましょう</li>
 	<li>ノード名が「count」、パブリッシャが「count_up」</li>
 	<li>rospy.Publisherを作って定期的にデータを投げる
<ul>
 	<li>count_upというトピックに、型はInt32で（バッファとなるキューのサイズは1）</li>
</ul>
</li>
</ul>
<pre class="p1"><span class="s1" style="color: #ffffff;">#!/usr/bin/env python</span>
<span class="s1" style="color: #ffffff;">import rospy</span>
<span class="s1" style="color: #ffffff;">from std_msgs.msg import Int32</span>

<span class="s1" style="color: #ffffff;">if __name__ == '__main__': </span>
<span class="s1" style="color: #ffffff;"><span class="Apple-converted-space">    </span>rospy.init_node('count')</span>
<span class="s1" style="color: #ffffff;"><span class="Apple-converted-space">    </span>pub = rospy.Publisher('count_up', Int32, queue_size=1)</span>
<span class="s1" style="color: #ffffff;"><span class="Apple-converted-space">    </span>rate = rospy.Rate(10)</span>
<span class="s1" style="color: #ffffff;"><span class="Apple-converted-space">    </span>n = 0</span>
<span class="s1" style="color: #ffffff;"><span class="Apple-converted-space">    </span>while not rospy.is_shutdown():</span>
<span class="s1" style="color: #ffffff;"><span class="Apple-converted-space">        </span>n += 1</span>
<span class="s1" style="color: #ffffff;"><span class="Apple-converted-space">        </span>pub.publish(n)</span>
<span class="s1" style="color: #ffffff;"><span class="Apple-converted-space">        </span>rate.sleep()</span></pre>
<!--nextpage-->
<h2>ノードの実行</h2>
<pre class="p1"><span class="s1" style="color: #ffffff;">$ rosrun mypkg count.py</span></pre>
<ul>
 	<li>rosnode listとrostopic listでノードとトピックの確認を</li>
 	<li>次にrostopic echoでcount_upからデータを取り出してみましょう</li>
</ul>
<pre class="p1"><span class="s1" style="color: #ffffff;">$ rostopic echo /count_up </span>
<span class="s1" style="color: #ffffff;">data: 1430</span>
<span class="s1" style="color: #ffffff;">---</span>
<span class="s1" style="color: #ffffff;">data: 1431</span>
<span class="s1" style="color: #ffffff;">---</span>
<span class="s1" style="color: #ffffff;">data: 1432</span>
<span class="s1" style="color: #ffffff;">---</span>
<span class="s1" style="color: #ffffff;">data: 1433
...</span></pre>
<!--nextpage-->
<h2>サブスクライバを作る</h2>
<ul>
 	<li>次のようなtwice.pyを作る</li>
 	<li>rospy.Subscriberを使う
<ul>
 	<li>count_upという名前のトピックを購読する</li>
 	<li>型はInt32</li>
 	<li>データを受け取ったときにcbという関数で処理
<ul>
 	<li>コールバック関数</li>
</ul>
</li>
</ul>
</li>
</ul>
<pre class="p1"><span class="s1" style="color: #ffffff;">#!/usr/bin/env python</span>
<span class="s1" style="color: #ffffff;">import rospy</span>
<span class="s1" style="color: #ffffff;">from std_msgs.msg import Int32</span>

<span class="s1" style="color: #ffffff;">def cb(message):</span>
<span class="s1" style="color: #ffffff;"><span class="Apple-converted-space">    </span>rospy.loginfo(message.data*2)</span>

<span class="s1" style="color: #ffffff;">if __name__ == '__main__': </span>
<span class="s1" style="color: #ffffff;"><span class="Apple-converted-space">    </span>rospy.init_node('twice')</span>
<span class="s1" style="color: #ffffff;"><span class="Apple-converted-space">    </span>sub = rospy.Subscriber('count_up', Int32, cb) </span>
<span class="s1" style="color: #ffffff;"><span class="Apple-converted-space">    </span>rospy.spin()</span></pre>
<!--nextpage-->
<h2>twice.pyの実行</h2>
<ul>
 	<li>roscore、rosrun mypkg count.pyを事前に実行しておく</li>
 	<li>二倍になった数字が端末上に表示される
<ul>
 	<li>非同期なので欠ける可能性があることに注意</li>
 	<li>途中で切ってまた立ち上げても再開</li>
</ul>
</li>
</ul>
<pre><span style="white-space: pre;"><span style="color: #ffffff;"><span class="s1">$ rosrun mypkg twice.py 
</span><span class="s1">[INFO] [1484659840.762425]: 4</span>
<span class="s1">[INFO] [1484659840.862150]: 6</span></span>
<span class="s1" style="color: #ffffff;">[INFO] [1484659840.961791]: 8</span>
<span class="s1" style="color: #ffffff;">[INFO] [1484659841.062162]: 10
...</span>
</span></pre>
<!--nextpage-->
<h2>パブリッシャとサブスクライバの同居</h2>
<ul>
 	<li>一つのノードは複数のパブリッシャ、サブスクライバを持つことが可能</li>
 	<li>twice.pyを次のように加筆</li>
</ul>
<pre class="p1"><span style="color: #ffffff;"><span class="s1">#!/usr/bin/env python
</span><span class="s1">import rospy
</span><span class="s1">from std_msgs.msg import Int32

</span><span class="s1">n = 0

</span><span class="s1">def cb(message):
</span><span class="s1"><span class="Apple-converted-space">    </span>global n
</span><span class="s1"><span class="Apple-converted-space">    </span>n = message.data*2</span></span>

<span style="color: #ffffff;"><span class="s1">if __name__ == '__main__': 
</span><span class="s1"><span class="Apple-converted-space">    </span>rospy.init_node('twice')</span></span>
<span class="s1" style="color: #ffffff;"><span class="Apple-converted-space">    </span>sub = rospy.Subscriber('count_up', Int32, cb) </span>
<span class="s1" style="color: #ffffff;"><span class="Apple-converted-space">    </span>pub = rospy.Publisher('twice', Int32, queue_size=1) </span>
<span class="s1" style="color: #ffffff;"><span class="Apple-converted-space">    </span>rate = rospy.Rate(10)</span>
<span class="s1" style="color: #ffffff;"><span class="Apple-converted-space">    </span>while not rospy.is_shutdown():</span>
<span class="s1" style="color: #ffffff;"><span class="Apple-converted-space">        </span>pub.publish(n)</span>
<span class="s1" style="color: #ffffff;"><span class="Apple-converted-space">        </span>rate.sleep()</span></pre>
