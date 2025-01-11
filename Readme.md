
#  $\color{FF0000}{特别说明}$
现在导航的定位更换为cartograher定位，AMCL还没有完全关闭（删干净），路径规划和cmd_vel,还没有测试，之后请加入多点巡逻功能和landmark视觉辅助定位，多点巡逻用导航nav2的simplecommader API，landmark辅助视觉定位用cartograher中landmark功能，
请把TFtree 修改成map -> Odom -> base_footprint -> base_link -> 其他，这些需要加入urdf和编写坐标转换代码来实现并且需要修改cartograher，nav2，等参数来实现
备注 现在的TFtree ，map -> laser -> 其他 (现在laser即充当导航的Odom又充当代价地图和局策树中base_link)

source install/setup.bash 

# 雷达rviz2可视化

ros2 launch lakibeam1 lakibeam1_scan_view.launch.py

# 雷达启动launch

ros2 launch lakibeam1 lakibeam1_scan.launch.py

# cartographer+rviz2 

ros2 launch cartographer_ros sentry.launch.py

# 查看tf
ros2 run tf2_tools view_frames

# 地图保存

ros2 run nav2_map_server map_saver_cli -f map

ros2 launch nav2_sentry_bringup navigation2.launch.py 

# 导航

ros2 launch lakibeam1 lakibeam1_scan.launch.py

# cartograher定位

ros2 launch cartographer_ros sentry_localtion.launch.py 

# 导航加载

ros2 launch nav2_sentry_bringup navigation2_cartographer.launch.py 


# 项目结构图

```
├── Lakibeam_ROS2_Driver-main
│   ├── assets
│   ├── include
│   ├── launch
│   ├── rviz
│   ├── src
│   └── thirdparty
│       └── rapidjson
│           ├── error
│           ├── internal
│           └── msinttypes
├── nav2_sentry_bringup
│   ├── launch
│   ├── maps
│   ├── params
│   ├── rviz
│   ├── urdf
│   └── worlds
└── sentry_cartographer
    ├── cartographer_ros
    │   ├── configuration_files
    │   ├── include
    │   │   └── cartographer_ros
    │   │       └── metrics
    │   │           └── internal
    │   ├── launch
    │   ├── scripts
    │   │   └── dev
    │   ├── src
    │   │   ├── cartographer_grpc
    │   │   ├── dev
    │   │   └── metrics
    │   │       └── internal
    │   └── urdf
    ├── cartographer_ros_msgs
    │   ├── msg
    │   └── srv
    ├── cartographer_rviz
    │   ├── include
    │   │   └── cartographer_rviz
    │   ├── ogre_media
    │   │   └── materials
    │   │       ├── glsl120
    │   │       └── scripts
    │   └── src
    ├── docs
    │   └── source
    └── scripts
```





