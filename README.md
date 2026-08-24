# Raspberry-Pi-3-PX4-FC
Hardware and Software Setup for a Cheap PX4 Flight Controller Using a Raspberry Pi 3.

Image: [ROS Realtime Ubuntu 22.04.3](https://github.com/ros-realtime/ros-realtime-rpi4-image/releases/tag/22.04.3_v5.15.98-rt62-raspi_ros2_humble)

Create SWAP
sudo dd if=/dev/zero of=/swapfile bs=1M count=2048 status=progress
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab

Clone and Build
git clone https://github.com/PX4/PX4-Autopilot.git --recursive
cd ~/PX4-Autopilot/boards/scumaker/pilotpi
rm ./arm64.px4board
wget https://raw.githubusercontent.com/AdamPoloha/Raspberry-Pi-3-PX4-FC/refs/heads/main/Software/arm64.px4board
cd ~/PX4-Autopilot
bash ./Tools/setup/ubuntu.sh --no-sim-tools --no-nuttx
make scumaker_pilotpi_arm64 -j3

Run
cd ~/PX4-Autopilot/posix-configs/rpi
wget https://raw.githubusercontent.com/AdamPoloha/Raspberry-Pi-3-PX4-FC/refs/heads/main/Software/rpipx4.config
cd ~/PX4-Autopilot/build/scumaker_pilotpi_arm64/bin
sudo ./px4 -s ~/PX4-Autopilot/posix-configs/rpi/rpipx4.config
