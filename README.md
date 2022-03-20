# ToyRobot
Robot Movement simulation in xy plane - IRESS

I basically developed this exam code in an online IDE like https://www.onlinegdb.com/
All you have to do is copy and paste the entire code from toy_Robot.cpp into the online IDE and click "Run".

You will be prompted to enter your instructions after seeing below text lines:

 ################################
 Enter instructions for Toy Robot
 ################################
 
 
 Commands:
 
 1. PLACE - this places the robot at a starting point in an X-Y plane, 5x5 units in dimension.
 If PLACE command is not invoked, it is assumed that initial position is 0,0,NORTH
 
 USAGE: PLACE <x-coordinate>,<y-coordinate>,<DIRECTION>
 EXAMPLE: PLACE 1,2,EAST - this places the robot at coordinates (1,2), facing EAST.
  
 2. MOVE - this command moves the robot 1 unit to its current direction.
 
 USAGE: MOVE
 EXAMPLE: If a robot is at coordinates 1,1,NORTH, a MOVE command will place the robot at 1,2,NORTH
 NOTE: If the move command will cause the robot to be positioned outside the bounderies of 5x5 plane, then move command will have no effect.
  
 3. LEFT - this command will change the DIRECTION of the robot's facing, 90 degress to the left. 
  
  USAGE: LEFT
  EXAMPLE: if the robot is currently facing NORTH, a LEFT command will change its direction to WEST. Another LEFT command will change the robot's direction to SOUTH.
  
 4. RIGHT - this command will change the DIRECTION of the robot's facing, 90 degress to the right. 
  
  USAGE: RIGHT
  EXAMPLE: if the robot is currently facing NORTH, a RIGHT command will change its direction to EAST. Another RIGHT command will change the robot's direction to SOUTH.
  
 5. REPORT - this command displays the current coordinates and direction of the robot.
  
  USAGE: REPORT
  SAMPLE OUTPUT: 1,1, SOUTH
  
  
  Program can be terminated by pressing "CTRL + C"
  
  
  
