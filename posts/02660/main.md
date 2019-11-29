# SLAM with a tiny robot
Yesterday we successfully created a room map by using a tiny micromouse type robot that has a Hokuyo URG-LX04. The robot, <a href="http://products.rt-net.jp/micromouse/raspberry-pi-mouse">Raspberry Pi Mouse</a>, is provided by RT-Corporation. 

In the following movie, the gmapping node on ROS works on the laptop pc and the robot sends the scan data and its odometry to the laptop pc through ROS. We have also verified that the gmapping node can work on Raspberry Pi 3 with a standalone fashion. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/b2kYQ11PUSI" frameborder="0" allowfullscreen></iframe>

<a href="https://lab.ueda.asia/wp-content/uploads/2016/12/map_cut_around.png"><img src="https://lab.ueda.asia/wp-content/uploads/2016/12/map_cut_around.png" alt="" width="167" height="107" class="alignright size-full wp-image-2675" /></a>

The detail will be published as a part of a book, which is unfortunately written in Japanese, in the next spring. Actually, the Gmapping works robustly with the skiddy mouse even if we don't tune parameters well. 


