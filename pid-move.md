# PID Movement Commands

## Initial Info
PID is something you can use to control multiple different moving aspects of your robot, such as wheels or arms.
Without using PID, you may find that parts of your robot can overshoot their intended positions or oscilate. To solve this, you can employ a continious PID loop, which essentially looks at your intended output as well as your current output (from various sensors), and uses math to bridge the gap between the two and apply corrections.

## What is PID?
PID stands for *proportional*, *integral*, and *derivative*. These terms can be denoted by *P*, *I*, and *D* respectively. All three of these values are constants, meaning that you configure them once for your particular robot, and then you won't have to touch them again.

Let's take a look at what PID actually looks like, and see it in action on the Romi.

## Links to incorporate *(do)*

https://docs.wpilib.org/en/stable/docs/software/advanced-controls/introduction/pid-video.html
https://frc-pdr.readthedocs.io/en/latest/control/pid_control.html
This 2-part video series was super helpful to me: [part 1](https://www.youtube.com/watch?v=jIKBWO7ps0w) covers why to use pid, what it does, and goes over kP; [part 2](https://www.youtube.com/watch?v=Z24fSBVJeGs) goes over kI and kD
