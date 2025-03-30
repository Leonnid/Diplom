# TurtleBot3 SLAM в ROS2 (Humble) с Gazebo

## Пошаговая инструкция

### 1. Подготовка (выполнить один раз)

```bash
# Установка ROS2 Humble (если ещё не стоит)
sudo apt update && sudo apt upgrade -y
sudo apt install curl gnupg2 lsb-release
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
sudo apt update
sudo apt install ros-humble-desktop

# Установка TurtleBot3 и симулятора
sudo apt install ros-humble-turtlebot3* ros-humble-turtlebot3-gazebo ros-humble-slam-toolbox
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc
```
```bash
export TURTLEBOT3_MODEL=waffle_pi && ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py	Запуск Gazebo с роботом
```
```bash
export TURTLEBOT3_MODEL=waffle_pi && ros2 launch slam_toolbox online_async_launch.py use_sim_time:=true	Запуск SLAM
```
```bash
export TURTLEBOT3_MODEL=waffle_pi && ros2 launch turtlebot3_navigation2 navigation2.launch.py use_sim_time:=true	Запуск навигации в RVIZ2
```
```bash
export TURTLEBOT3_MODEL=waffle_pi && ros2 run turtlebot3_teleop teleop_keyboard
```
