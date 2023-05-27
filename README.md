## 1\. Git Clone from ros-planning navigation2

```
cd ${your ros2 workspace}/src
git clone -b foxy-devel https://github.com/ros-planning/navigation2.git
```

## 2\. 필요 library & package 설치 및 compile

### 2-1. ZeroMQ (requires in nav2\_common)

```
sudo apt-get install libzmq3-dev
```

### 2-2. test\_interface\_files (requires in rcl\_interface)

```
cd ${your ros2 workspace}/src
git clone -b foxy https://github.com/ros2/test_interface_files.git
cd test_interface_files
colcon build --symlink-install
source install/setup.bash
cd ../../
colcon build --packages-select test_interface_files
source install/setup.bash
```

### 2-3. rcl\_interfaces (requires in nav2\_common)

```
cd ${your ros2 workspace}/src
git clone -b foxy https://github.com/ros2/rcl_interfaces.git
cd rcl_interfaces
colcon build --symlink-install
source install/setup.bash
cd ../../
colcon build --packages-select rcl_interfaces
source install/setup.bash
```

### 2-4. BehaviorTree.CPP (requires in nav2\_behavior\_tree)

```
sudo apt-get install ros-foxy-behavior-cpp-v3
cd ${your ros2 workspace}/src
git clone https://github.com/BehaviorTree/BehaviorTree.CPP.git
cd BehaviorTreeCPP
colcon build --symlink-install
source install/setup.bash
cd ../../
colcon build --packages-select behaviortree_cpp
source install/setup.bash
```

### 2-5. GRAPHICSMAGICKPP (requires in nav2\_map\_server)

```
sudo apt-get install graphicsmagick*
cd ${your ros2 workspace}
colcon build --packages-select nav2_map_server
source install/setup.bash
```

### 2-6. Ceres (requires in smac\_planner)

### 2-6-1. gflags (requires in glog)

```
sudo apt-get install libgflags-dev
```

### 2-6-2. glog (requires in Ceres)

```
cd ${your ros2 workspace}/src
git clone https://github.com/google/glog.git
cd glog
colcon build --symlink-install
source install/setup.bash
cd ../../
colcon build --packages-select glog
source install/setup.bash
```

### 2-6-3. atlas (requires in Ceres)

```
sudo apt-get install libatlas-base-dev
```

### 2-6-4. eigen3 (requires in Ceres)

```
sudo apt-get install libeigen3-dev
```

### 2-6-5. suitesparse (requires in Ceres)

```
sudo apt-get install libsuitesparse-dev
```

### 2-6-6. ceres-solver (requires in smac\_planner)

```
cd ${your ros2 workspace}/src
git clone https://ceres-solver.googlesource.com/ceres-solver
mkdir ceres-bin && cd ceres-bin
cmake ../ceres-solver
make -j3
make test
sudo make install
```

### 2-6-7. ompl (requires in smac\_planner)

```
cd ${your ros2 workspace}/src
git clone https://github.com/ompl/ompl.git
cd ompl
mkdir -p build/Release
cmake ../..
make -j4
sudo make install
```

### 2-7. gazebo\_ros\_pkgs (requires in nav2\_planner)

```
sudo apt-get install ros-foxy-gazebo-ros-pkgs
```
