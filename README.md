# Spot_sensor
Sensors integration

# Custom Messages
To add the custom message to your microros_ws:
1. Download the sensor_pkg zip file and unzip.
2. Copy the 'custom_message' folder and place it in following location: microros_ws/firmware/mcu_ws
3. In the terminal run following commands
```
cd microros_ws/
ros2 run micro_ros_setup build_firmware.sh
```
this should give error free output
# Sensor data publisher
To use the sample code to use above created custom message
1. copy the 'sensor' folder from above unzipped folder and place it following location: microros_ws/firmware/freertos_apps/apps
2. In the terminal run following set of commands:
```
cd microros_ws
colcon build
ros2 run micro_ros_setup configure_firmware.sh sensor -t udp -i [LOCAL MACHINE IP ADDRESS] -p 8888
ros2 run micro_ros_setup build_firmware.sh
ros2 run micro_ros_setup flash_firmware.sh
ros2 run micro_ros_setup build_agent.sh
source install/local_setup.bash
ros2 run micro_ros_agent micro_ros_agent udp4 --port 8888
ros2 topic list 
```
(here you should be able to see the topic /sensor_publisher)
