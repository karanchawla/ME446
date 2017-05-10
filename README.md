<div style="text-align:center" markdown="1">
[![Final Demonstration Video](https://i.ytimg.com/vi/SaDDB5C_TfM/hqdefault.jpg?custom=true&w=336&h=188&stc=true&jpg444=true&jpgq=90&sp=68&sat=0.3&sigh=WNhMJET3OzVWjJ3hIvl0t2yuy4I)](https://www.youtube.com/watch?v=SaDDB5C_TfM&w=560&h=315)

**Task space trajectory tracking using Impedance Control**
</div>
 <iframe width="420" height="315"
src="https://www.youtube.com/watch?v=SaDDB5C_TfM&w=560&h=315autoplay=1">
</iframe> 

## Position Control
___
<p align="justify"> 
The goal of position control is moving the end effector of the robot to a precise position. To finish this task, we use Task Space PD Controller. This controller contains PD control with countering the friction components to minimize the error.
</p> 
<p align="justify"> 
For the friction is related to the angular velocity of the joint, we find a group of coefficients as the proportional of torque to the angular velocity. Therefore, once the angular velocity of one joint is obtained, the friction on this joint is known. Adding the friction part to the final torque output can counter the friction on the joint, which can minimize the error without the Integral controller. For a position in the world frame, the inverse kinematic equation will transfer the position in the DH frame, as a group of angles at each joint. These joints form the Jacobian of the robot which transfers the position information to torque at each joint. 
</p>
<p align="justify"> 
The final torque contains two parts, the active part contains PD control so that the robot can move to the desired position precisely and quickly. The friction part is only related to the angular velocity of each joint and it can minimize the error. In this final project, moving the end effector to any points is conducted by this controller.
</p>

## Impedance Control
___
<p align="justify"> 
The impedance control allows the end effector of the robot to move slightly in one direction. To realize it, decreasing the `K_p` and `K_d` gain of one direction in the Task Space PD controller. For an arbitary direction, we first transfer this direction to one axis by the rotational matrix and then applying the matrix to the original `K_p` and `K_d` gain. Decreasing the value of the `K_p` and `K_d` of that direction and using the transpose of the previous rotational matrix to obtain the final `K_p` and `K_d` gain we need. In this final project, the Peg in a hole and Zigzag Groove task need this technique to smooth the whole process. In the Zigzag Groove task, the path direction is fixed and the direction perpendicular to the aim direction can be moved slightly so that this end-effector can pass the corner smoothly.
</p>
![alt text](https://raw.githubusercontent.com/karanchawla/TheDumbRobotArm/master/control.PNG)

## Path Planning
___
<p align="justify"> 
For the whole task is a group of action and we need to avoid the obstacle in the second task, an effective path can finish this whole task successfully. In our group, a group of key points is obtained for designing the path. The key points of the first task are the point above the hole. From the point above the hole to the starting point of the zigzag groove, two more points are designed to avoid the obstacle. In the zigzag, each starting points and end points of the lines are key points and two more points on the curve are also the key points. Finally, the point above the egg is the last key point. Connecting these keypoints by line to form the whole path of the task.
</p>
![alt text](https://raw.githubusercontent.com/karanchawla/TheDumbRobotArm/master/line.PNG)
![alt text](https://raw.githubusercontent.com/karanchawla/TheDumbRobotArm/master/traj.PNG)

### Project Source
The project code can be downloaded [here.](https://github.com/karanchawla/theDumbRobotArm/blob/master/finalCode.c) 


## About Team
<div style="text-align:center" markdown="1">
![alt text](https://raw.githubusercontent.com/karanchawla/TheDumbRobotArm/master/IMG_20170509_200526_984.jpg "Group Photo")
**The Team Photo with Prof. Daniel Block**
</div>

| **Group Members** |               |
| ------------- | ------------- |
| Karan Chawla  |  Zhaoer Li    |
| Zhicaho Zhang |               |


