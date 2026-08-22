# Raspberry-Pi-3-PX4-FC
Hardware and Software Setup for a Cheap PX4 Flight Controller Using a Raspberry Pi 3.

Image: [ROS Realtime Ubuntu 22.04.3](https://github.com/ros-realtime/ros-realtime-rpi4-image/releases/tag/22.04.3_v5.15.98-rt62-raspi_ros2_humble)

git clone https://github.com/PX4/PX4-Autopilot.git --recursive
cd PX4-Autopilot
bash ./Tools/setup/ubuntu.sh --no-sim-tools --no-nuttx
make scumaker_pilotpi_arm64
