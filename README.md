# Pit Lane Limiter

A pit lane speed limiter modelled in MATLAB/Simulink. A PID controller takes over the
motor when the pit button is pressed and holds the car at the target speed.

## Model

The vehicle is represented with two blocks from the Simulink library: one for the body
and one for the two tyres. The motor is a standard ideal torque source. I did not build
the plant myself — the work here is on the control side.

## Controller

A single PID loop. I tuned it with Simulink's auto-tuner and then iterated the gains
manually, judging the step response by overshoot and settling time.

## A problem I ran into

The controller settled cleanly when it engaged close to the target speed, but with a
large initial error the response overshot the target and then took a long time to settle.

I traced this to integral windup: while the actuator is saturated the integral term keeps
accumulating, so the controller has to unwind that accumulated error before it can
respond properly. Enabling anti-windup in the PID block fixed it.
