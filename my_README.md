# Update for unpacked ROB_SLAM with pcl view repo

## download:
clone the package into {ros workspace}

## build:

### build libORB_SLAM2.so ( inclouding binary loading tools ):

Build libORB_SLAM2.so according to ORBSLAM2 [origin repo](https://github.com/raulmur/ORB_SLAM2).  

Before the first compilaion, delete the build direciton in the root and thirdparty. And modify the location where save the pcd file in the "pcl::io::savePCDFileBinary" of the "pointcloudmapping.cc". 

The Compile operation is as follows:
```bash
     cd {root_directory}
     chmod +x build.sh
     ./build.sh
```

### build ROS rgbd

```bash
    cd {ros workspace}
    catkin_make
```

## Run:
### run rgbd without ROS
```bash
    cd {root_directory}
    ./bin/rgbd_tum Vocabulary/ORBvoc.bin  Examples/RGB-D/TUM1.yaml /home/zhjd/dataset/rgbd_dataset_freiburg1_desk /home/zhjd/dataset/rgbd_dataset_freiburg1_desk/associate.txt
```
### run rgbd with ROS
```bash
    cd {ros workspace}
    source devel/setup.bash
    roslaunch orbslam2_pointcloud_ros rgbd_kinectdk.launch
```

# TODO:

* 单个物体的测试
