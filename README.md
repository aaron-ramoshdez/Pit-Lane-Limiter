# Pit-Lane-Limiter
This is a personal project I did during the past year. 
It is a PID controller that keeps the speed at the targeted one. 

I used 2 different blocks to simulate the vehicle, one for the body and the other for the two tires.
For the motor I used a standard ideal torque source. 

The control part is a simple PID loop that takes control over the motor when the pit button is pressed.
Now I plan to add a system to make the response smoother, one option is to make that the PID only engage when its close to the target speed. While it isn't close, the control would be taken in a more direct approach than a PID.
