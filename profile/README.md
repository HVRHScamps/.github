# 2022 Robotics Camp
This is the repository for the Housatonic Valley Regional High School Science and Technology Center's summer robotics program. This program was designed as a one week course for rising 7-10th grade students. Created by [Jacob Elington](https://github.com/cannotilever/).

## Purpose
This github orgainzation represents the final project for students to work toward while learning Python and is *not* a standalone tool. It should be supplimented with two to three days of classroom instruction and smaller scale projects to introduce basic syntax and the like before this system is introduced.


## Technical Details
This program was designed for use on a modified FIRST Robotics Competition robot, specifically Team 716's Infinite Recharge robot. The test cases were diesigned with this robot's specific hardware in mind, however the test cases and RoboRio code should be relativley easy to modify for any FRC robot.

This control system consists of three parts, two of which are required.
* [RoboRio](https://github.com/HVRHScamps/Rio22) - Required. This direclty controls all of the actuators and sensors and hosts the NetworkTables instance.
* [Raspberry Pi 1](https://github.com/HVRHScamps/camp22) - Required. This runs the interactive python program and all student code. It gets sensor data and sends actuator commands over NetworkTables to the RoboRio.
* [Raspberry Pi 2](https://github.com/HVRHScamps/sensePi) - Optional. This Raspberry Pi has a Sense HAT which displays a smiley face that shows the overall completion rate of student objectives. The Sense HAT can also be used as a source for gycroscope and acceleration data if the RoboRio does not have its own IMU board installed. 

The reason for this odd configuration was that, since the interactive program on the Raspberry Pi runs unverified code from beginner programmers, it may be susceptable to crashing or locking up which would present a major saftey issue if the motors were active at the time. To solve this, the Raspberry Pi tests all student code before executing it with real motor control, and also updates a "deadman" value in NetworkTables. If this value is not updated, the RoboRio automatically stops all actuators. This also allows the instructor to use the robot Drive Station as a separate emergency stop.

## Student Code
Each task for students to complete is separated into its own repository within this organization to allow students to easily collaborate on each task. When students want to run their code, they select their task with the Xbox controller's d-pad and A button which automatically pulls the latest version from github, imports it, and runs test cases against it. If these tests pass, students may then press Y to execute the code. 
