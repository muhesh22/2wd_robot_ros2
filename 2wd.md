***Diff Drive Plugin***



<gazebo>



&#x20; <!-- JOINT STATE PUBLISHER -->

&#x20; <plugin name="joint\_state\_publisher" filename="libgazebo\_ros\_joint\_state\_publisher.so">

&#x20;   <update\_rate>30</update\_rate>

&#x20;   <joint\_name>left\_joint</joint\_name>

&#x20;   <joint\_name>right\_joint</joint\_name>

&#x20; </plugin>



&#x20; <!-- DIFF DRIVE -->

&#x20; <plugin name="diff\_drive" filename="libgazebo\_ros\_diff\_drive.so">



&#x20;   <ros>

&#x20;     <namespace>/</namespace>

&#x20;   </ros>



&#x20;   <left\_joint>left\_joint</left\_joint>

&#x20;   <right\_joint>right\_joint</right\_joint>



&#x20;   <wheel\_separation>0.2</wheel\_separation>

&#x20;   <wheel\_diameter>0.1</wheel\_diameter>



&#x20;   <command\_topic>cmd\_vel</command\_topic>

&#x20;   <odometry\_topic>odom</odometry\_topic>



&#x20;   <publish\_odom>true</publish\_odom>

&#x20;   <publish\_odom\_tf>true</publish\_odom\_tf>



&#x20; </plugin>



</gazebo>







***LiDAR Block***



<gazebo reference="lidar\_1">



&#x20; <sensor type="ray" name="lidar\_sensor">



&#x20;   <update\_rate>10</update\_rate>



&#x20;   <ray>

&#x20;     <scan>

&#x20;       <horizontal>

&#x20;         <samples>640</samples>

&#x20;         <min\_angle>-1.396</min\_angle>

&#x20;         <max\_angle>1.396</max\_angle>

&#x20;       </horizontal>

&#x20;     </scan>



&#x20;     <range>

&#x20;       <min>0.08</min>

&#x20;       <max>10.0</max>

&#x20;       <resolution>0.01</resolution>

&#x20;     </range>

&#x20;   </ray>



&#x20;   <!-- ROS2 LIDAR PLUGIN -->

&#x20;   <plugin name="lidar\_plugin" filename="libgazebo\_ros\_ray\_sensor.so">



&#x20;     <ros>

&#x20;       <namespace>/</namespace>

&#x20;     </ros>



&#x20;     <output\_type>sensor\_msgs/LaserScan</output\_type>

&#x20;     <topicName>/scan</topicName>

&#x20;     <frameName>lidar\_1</frameName>



&#x20;   </plugin>



&#x20; </sensor>



</gazebo>





cd \~/Documents/ros2\_ws

colcon build

source install/setup.bash



ros2 launch 2wd\_description gazebo.launch.py

ros2 topic list





cd \~/Documents/ros2\_ws

source install/setup.bash

ros2 run teleop\_twist\_keyboard teleop\_twist\_keyboard







i → forward

k → stop

j → left

l → right

u/o → diagonal













