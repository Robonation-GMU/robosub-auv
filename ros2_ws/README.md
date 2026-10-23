# ROS 2 workspace

Vehicle software lives here as ROS 2 packages inside `src/`. It is empty until we write our first package.

Build (on Ubuntu or the Jetson, with ROS 2 installed):
```
cd ros2_ws
colcon build
source install/setup.bash
```

Likely future packages: `auv_camera` (publish camera images), `auv_vision` (detections), `auv_mavlink_bridge` (talk to ArduSub), `auv_mission` (task logic), `auv_bringup` (launch files).
