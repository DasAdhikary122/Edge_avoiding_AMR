# 🤖 Edge_avoiding_AMR – Autonomous Mobile Robot Simulation (ROS 2 Jazzy + Gazebo Harmonic)

This repository contains a ROS 2-based mobile robot simulation with **edge-avoidance behavior**, running in **Gazebo Harmonic**. The robot uses a simulated **LIDAR sensor** to detect drop-offs and navigate safely, demonstrating basic reactive control for indoor AMRs (Autonomous Mobile Robots).

> 🛠️ Originally developed by [Curious-Utkarsh](https://github.com/Curious-Utkarsh) as [`bot_ws`](https://github.com/Curious-Utkarsh/bot_ws), and now updated and maintained by [Suman Das Adhikary](https://github.com/DasAdhikary122) for ROS 2 Jazzy compatibility and future improvements.

---

## 📦 System Requirements

- ✅ **OS:** Ubuntu 24.04 LTS
- ✅ **ROS 2:** Jazzy Jalisco
- ✅ **Simulator:** Gazebo Harmonic
- ✅ **Python:** 3.12+

---

## 🧰 Step-by-Step Installation

### 1️⃣ Install ROS 2 Jazzy

Follow the official guide:  
🔗 https://docs.ros.org/en/jazzy/Installation/Ubuntu-Install-Debs.html

### 2️⃣ Setup Environment

```bash
source /opt/ros/jazzy/setup.bash
echo "source /opt/ros/jazzy/setup.bash" >> ~/.bashrc
export RMW_IMPLEMENTATION=rmw_cyclonedds_cpp
echo "export RMW_IMPLEMENTATION=rmw_cyclonedds_cpp" >> ~/.bashrc
source ~/.bashrc

## 🧠 Workspace Setup

### 5️⃣ Install Git (if not already)

```bash
sudo apt install git
```

### 6️⃣ Clone This Repository

```bash
cd ~
git clone https://github.com/DasAdhikary122/Edge_avoiding_AMR.git
cd Edge_avoiding_AMR

```

---

## ⚙️ Setup ROS Dependencies

### 7️⃣ Install `rosdep` and initialize

```bash
sudo apt update
sudo apt install python3-rosdep
sudo rosdep init
rosdep update

```

### 8️⃣ Install Package Dependencies

```bash
rosdep install --from-paths src -y --ignore-src --skip-keys="ament_python"
```

---

## 🧱 Build the Workspace

```bash
cd ~/Edge_avoiding_AMR
colcon build
```

### 9️⃣ Source the workspace

```bash
source install/setup.bash
echo "source ~/Edge_avoiding_AMR/install/setup.bash" >> ~/.bashrc

```

---

## 🧩 (Optional) Shell Autocompletion

```bash
sudo apt install python3-colcon-argcomplete
source /usr/share/colcon_argcomplete/hook/colcon-argcomplete.bash
echo "source /usr/share/colcon_argcomplete/hook/colcon-argcomplete.bash" >> ~/.bashrc

```

---

## 🚀 Run the Simulation

### 1️⃣ Terminal 1: Launch Gazebo with the robot

```bash
ros2 launch bot_bringup simulated_robot.launch.py
```

### 2️⃣ Terminal 2: Run the Edge Detection Node

```bash
ros2 run bot_script edge_detection
```

You should now see:

* Gazebo with the robot and a world environment
* The robot running an **edge avoidance** algorithm using LIDAR data

---

## 📁 Project Structure Overview

```
Edge_avoiding_AMR/
├── src/
│   ├── bot_description/     # URDF, meshes, Gazebo models
│   ├── bot_controller/      # ROS 2 controllers and parameters
│   ├── bot_bringup/         # Launch files
│   ├── bot_script/          # Edge detection node

```

---

## 🛠 Troubleshooting

* If you see LIDAR not detecting correctly, make sure LIDAR pose and scan angle are valid in `bot_description`.
* Always source the workspace in every terminal:

  ```bash
  source ~/Edge_avoiding_AMR/install/setup.bash
  ```

------

## 📜 License
This project is licensed under the **MIT License**.  
See the [LICENSE](LICENSE) file for details.


---

## 🙌 Credits
💡 Original project by [Curious-Utkarsh](https://github.com/Curious-Utkarsh)  
🔗 Original repository: [bot_ws](https://github.com/Curious-Utkarsh/bot_ws)  

🔄 Modified and maintained by **Suman Das Adhikary** – Inspired by workshop mentor @Curious-Utkarsh  

🧪 Designed for **ROS 2 Jazzy** and **Gazebo Harmonic** (2025+ compatibility)  

---

Let me know if you want to add SLAM or wall-following next!

