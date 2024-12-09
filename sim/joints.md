# Joints.py Explainer

## Node

- indev

### children()

- indev

### joints()

- indev

### joints_motors()

- indev

### all_joints()

- Creating tree of joints

### __str__()

- Report out class as string

### class BodyPart

Various classes must be defined that associate the names of the revolute joints in the robot urdf file to the internal naming scheme of `sim`. More of these body part groups can be added or subtracted, but it will have implications on existing training processes.

Currently:

- LeftHand(Node): // RightHand(Node)
    - wrist_roll
    - gripper


- LeftArm(Node) // RightArm(Node)
    - shoulder_yaw
    - shoulder_pitch
    - shoulder_roll
    - bicep_roll
    - elbow_pitch
    - _hand = LeftHand_ // _hand = RightHand_

- LeftLeg(Node) // RightLeg(Node)
    - hip_roll
    - hip_yaw
    - hip_pitch
    - thigh_roll
    - knee_pitch
    - ankle_pitch
    - ankle_roll

*__Check the above__*

### class Robot(node)

`height`: The height of the robot. Appears to influence way the training algorithm runs, though not necessarily how it instantiates the robot in the simulation environment.

`rotation`: How the robot is oriented while instantiating. **Important** for getting these values correct so that it CAN walk when put into simulation; unfortunately, it isn't entirely obvious which of these corresponds to which body axis.

- A workflow: running train.py _non-headless_, checking the isaacgym starting position. Adjust rotation axis until you start approaching a good orientation; note that it takes pretty fine adjustment (a few tenths of a Radian have major effect).

`collision_links` : The URDF bodies (not joints! 3D body names) that are to interact with the physics environment. Generally, feet at minimum.

#### default_standing(cls)

All of the default values for specific joint orientations. Edit to align them better with the ground *after* fixing `rotation` from above.


