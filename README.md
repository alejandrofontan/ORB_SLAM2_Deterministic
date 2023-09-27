# ORB_SLAM2_Deterministic
This repository contains a deterministic variant of ORB_SLAM2 that modifies the components that introduce non-determinism in the algorithm. The deterministic version aims to provide consistent and 
repeatable results across different runs. Additionally, we've made extra modifications, including the ability to compile ORB-SLAM2 without Pangolin, save the trajectory as a collection of frame poses in monocular mode, and updating dependencies to their latest versions."

# Updated Libraries
C++17, OpenCV 4.7.0, Eigen 3.4.0 and Pangolin 0.8

# Modifications for Determinism
1) **Sorted Functions**: We've modified sort functions to ensure deterministic behavior when two or more elements are equal.
2) **Deterministic Random Integer Generator**: Implemented a deterministic random integer generator that produces a predefined list of random integers at the start of execution, preventing conflicts with other processes using `rand()`.
3) **C++ Standard Library Map**: Introduced an Observation Class to avoid non-deterministic effects arising from memory allocation of std::map using pointers as key.
4) **Sequential ORB-SLAM2**: We've modified the tracking, mapping, and loop closure threads to operate sequentially, eliminating non-deterministic effects associated with real-time performance.
   
# CMakeLists
COMPILE_SEQUENTIAL
  Activate this option to run a version of ORB-SLAM2 where the tracking and mapping threads run sequentially and are not affected by real-time effects.
  
COMPILE_DETERMINISTIC
  Activate this option 
  
COMPILE_WITH_PANGOLIN
  Deactivate this option to run ORB-SLAM2 without compiling Pangolin.

# Extra-modifications
1) `#include <unistd.h>` in System.h
2) **Fixed the code in LoopClosing.h**:
```
typedef map<KeyFrame*,g2o::Sim3,std::less<KeyFrame*>,
            Eigen::aligned_allocator<std::pair<KeyFrame* const, g2o::Sim3> > > KeyFrameAndPose;
```
3) **Compiled without Pangolin**
4) **Graph SLAM**: Introduced a Graph SLAM Class to manage keyframes, enabling the saving of frame poses in monocular mode.
   
# Known Issues
The deterministic version of ORB-SLAM2 in this fork has only been tested in monocular mode.

# References
Link to the original ORB-SLAM2 repository
<a href="https://github.com/raulmur/ORB_SLAM2" target="_blank">https://github.com/raulmur/ORB_SLAM2 
  
