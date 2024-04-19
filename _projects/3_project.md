---
layout: page
title: Stereo VO SLAM framework from scratch
description:
img: assets/img/proj_3_1.png
importance: 2
category: work
---

Creating a modular stereo visual odometry Simultaneous Localization and Mapping (SLAM) system is still a major challenge in Robotics. This is mainly due to the fact that SLAM is often a tightly coupled system and is therefore very hard to debug. In this project, we designed a more modular system that works well for most applications ranging from control of humanoid robots, Unmanned Aerial Vehicles, to guiding endoscopic procedures with precision.

We began our design by using concepts from traditional Computer Vision. Firstly, we used ORB feature detection and mapping to extract the common features from two consecutive frames of the left camera. The cameras used were grayscale, fully calibrated stereo cameras. The depth maps were then built, and the 2D points of the image were converted to 3D points in the world coordinate frame. The reprojection error measures the distance between the reprojection of a model estimation and its corresponding true projection. This distance needs to be minimized to get accurate results. Once these 3D-2D correspondences were found, the reprojection error was minimized, and we obtained the transformation matrix. 

We also performed loop closure detection simultaneously, wherein the frame that is being computed now, is checked for similarity between other frames. This is particularly useful because plain visual odometry accumulates drift over time, and we need to correct it to get an accurate trajectory. We perform two checks to determine the correct loop closure frames to avoid any potential mistakes, as wrong loop closure is really detrimental to the final results. The first check is using the Bag of Visual Words method, and calculating the similarity between two frames. If the similarity score is greater than 0.5, the frames clear this check and are passed back to the feature extractor and matching. If the number of common features between these two frames are greater than 200, then the frames are selected and the backend optimization process is triggered.

We use the GTSAM library to perform backend optimization to get the accurate trajectory. We perform only pose graph optimization in the interest of real-time performance. A nonlinear factor graph is built, and the poses and their corresponding factors are added sequentially. Additional factors were added between the loop closure poses. The Levenberg-Marquardt optimizer was used to solve this nonlinear optimization problem.

We assessed the performance of our SLAM pipeline on the KITTI odometry dataset, which is a benchmark dataset. The sole metric we employed to evaluate our performance is visualization, and there was a substantial improvement in the trajectory of the robot compared to plain stereo visual odometry. In other words, our trajectory was very close to the ground truth trajectory. Multiple sequences were tested out, and our SLAM pipeline gave good results in all the cases.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/proj_3_1.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Black line shows the ground truth path, orange line is the VO path, and pink line is the optimized path
</div>

In conclusion, we implemented a SLAM pipeline from scratch which is more modular, and designing every component of the system gave us a good insight into the engineering intricacies of building such a system. Our next step is to parallelize the three processes mentioned above and further decrease the computation time.
