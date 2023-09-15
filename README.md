# ORB_SLAM2_Deterministic
This repository contains a deterministic variant of ORB_SLAM2 that modifies the components that introduce non-determinism in the algorithm. The deterministic version aims to provide consistent and repeatable results across different runs.

# CMakeLists
COMPILE_WITH_PANGOLIN
  Deactivate this option to run ORB-SLAM2 without compiling Pangolin.
  
COMPILE_SEQUENTIAL
  Activate this option to run a version of ORB-SLAM2 where the tracking and mapping threads run   sequentially and are not affected by real-time effects.
  
COMPILE_DETERMINISTIC
  Activate this option 
