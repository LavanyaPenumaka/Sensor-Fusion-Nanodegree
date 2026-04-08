# Lesson 1 - LiDAR Fundamentals

Started this on my local Ubuntu laptop instead of Udacity workspace. First thing that happened - build failed because of PCL version mismatch. CMakeLists.txt was asking for 1.11 but
my system had 1.10. Fixed it by changing one line in CMakeLists.txt. Small thing but took me a while to figure out what cmake was even doing.

## What I understood about LiDAR

Before this I knew LiDAR fires lasers and detects objects. Now I actually understand how.
It fires a laser pulse, that pulse hits something and bounces back, and the sensor measures how long that took. Since we know the speed of light, we can calculate exact distance. 
It does this millions of times per second in all directions, that's how you get a 3D picture of everything around the car.

The output is called a point cloud, basically millions of dots in 3D space. Every dot has X (how far forward), Y (how far left or right), Z (how high), and Intensity (how strongly the
surface reflected the laser). The sensor itself is always at 0,0,0. Everything is measured relative to it.

What surprised me is how much data this generates. A 64-beam LiDAR produces around 13 MB every second. A full self-driving car with all its sensors combined generates 1 to 4 TB per hour 
of driving. That's why cars don't store raw data instead they process it on the spot and throw away what they don't need

## PCL and the build system

PCL (Point Cloud Library) is a C++ library that gives you ready-made tools for processing point clouds - filtering, segmenting, clustering etc.
Think of it like OpenCV but for 3D point clouds instead of images.

The build process confused me at first:
- cmake reads CMakeLists.txt and figures out where all the libraries are
- make actually compiles everything
- then you run ./environment to launch the viewer

So cmake plans, make builds, you run.

## Where this fits in a real car

The LiDAR sits on the car (BMW 7 Series has Innoviz at the front, Waymo has 5+ units covering 360 degrees). The raw point cloud goes into a compute platform like NVIDIA DRIVE, which runs
AI models to detect objects. That output goes to the ADAS ECU which decides what to do - brake, steer, alert.


## What I'd test if this was production

- Are the point counts per frame within expected range or is the sensor dropping data
- Any NaN values in coordinates - means sensor glitch
- Is frame rate stable at 10-20Hz or dropping
- Are intensity values valid or corrupted

## What broke and how I fixed it

cmake failed with:
"Could not find PCL compatible with version 1.11"

My system had 1.10. Changed CMakeLists.txt from find_package(PCL 1.11 REQUIRED) to 1.10. Built fine after that.

Lesson: 
Udacity assumes their workspace versions.
On your own machine always check what's actually installed before assuming the code will just work.
