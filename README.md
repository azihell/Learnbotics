# Learnbotics

Here is the modelling of a Learnbotics differential robot equipped with a camera and a LiDAR on the top.

### Model assembling
The model was first assembled via a .sdl file and loaded on Gazebo.
The meshes were put together using Onshape: the [full robot](https://cad.onshape.com/documents/2d0726446c451e66c4f9f940/w/3d8fa42138515e3156e86638/e/296db76a493188d3a32cdb9a), 
[the wheels centered on the origin](https://cad.onshape.com/documents/0bf61df0cf22714f76a28185/w/bf5cc5c838c9dfeac3991cab/e/135c895e5f6a5d49d514a378) and 
[the sphere used on balancing and differential movement](https://cad.onshape.com/documents/d6a07bd2fb258c46fb40c04f/w/1a545d0ec29e82523e56e3b8/e/ae9074d9b9c88e4b85cc34f1). The LiDAR was conceived on the main robot file, but it had to be "isolated" in a [<i>Part Studio</i>](https://cad.onshape.com/help/Content/sketch.htm) of it's own because it has mobility - the top part should be able to rotate around the vertical axis (usually the z-axis). The same idea applies to the wheels and the sphere or anything that will rotate around an axis, because when describing them in the .xacro file, the axis of rotation will be generated at the origin seen on Onshape.

To make possible interaction with ROS, a .xacro file was derived from the original .sdf file. They are both XML files, and their structure is very similar, although some parameters will be described in with a different syntax or will have different names ("pose" may become "origin", and stuff like that)

The .xacro file describes not only the physical structure of the robot, but it also involves the LiDAR ray parameters, and the Velodyne plugin associated. This plugin is based on Gazebo plugin "gazebo_ros_block_laser".
