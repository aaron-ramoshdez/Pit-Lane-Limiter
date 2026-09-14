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

## Known limitation

The controller performs well when it engages close to the target speed, but degrades
when the initial error is large: the response either oscillates or takes too long to
settle. I read this as the expected behaviour of a linear controller operating away from
its design point.

In practice the useful range is narrow anyway, since the driver is already near the pit
lane limit when the limiter engages, so I accepted this for the first version.

## Next step

Add a switching scheme: while the speed is far from the target, act directly on the
motor; hand over to the PID once the gap is small enough for it to work properly. The
open problem is making that handover smooth, so the control signal does not jump when
the PID takes over.
