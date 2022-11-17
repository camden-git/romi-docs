**This article is currently in development**

# Command Scheduler
The command scheduler is an integral part of programming the Romi. It is a feature of WPILib, and it does exactly what it suggests--schedules commands.

## Why use the command scheduler?
Scheduling your robot's commands makes programming much more efficient, both for us as the programmers and for the robot itself. It can help juggle multiple parallel operations happening on your robot, and keep running code and writing code organized.
It allows commands to be run only when necessary, instead of writing your own code to check when it is time to run code. (This is massively more efficient and is very beneficial when you accumulate many commands.)

## What does it do?
Commands have three different states:

 1. Initializing
 2. Executing
 3. Ending

Here is a flow chart of how the command scheduler runs.
![Flow chart of command scheduler](https://docs.wpilib.org/en/stable/_images/scheduler-run-sequence.drawio.svg)

The scheduler multitasks between running the `periodic()` method of each subsystem and running any commands that have been scheduled by the program. 
You can see in the flow chart that this is the first thing the command scheduler does.

Next, any commands that have been bound to triggers are run. For example, running a certain command if a button has been pressed, or a sensor triggered. We will cover this later, but you can safely ignore it for now.

Now, ...


...

All of this is run every 20ms on your robot. That's 50 times per second.
