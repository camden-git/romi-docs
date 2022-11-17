# Arm Control
## Getting Started

It's assumed you already have built and properly wired the [romi arm](https://www.pololu.com/docs/0J76/1). It is also expected that you have a working [command scheduler system](https://github.com/camden-git/romi-docs/blob/main/command-scheduler.md). Also, make sure you've setup the stuff in the web config UI, however we will go over the web UI config in this doc.

## Creating the subsystem

Like with the drive train, we need to make a subsystem that allows you to control the servos in the arm, if you've been able to drive your romi, you probably have a file structure that looks a bit like this.

```
- commands
- sensors
- subsystems
 - Drivetrain.java
- Constants.java
- main.java
- Robot.java
- RobotContainer.java
```

However we are missing the ability to control the external IO. Our arm is wired to the external IO which is what allows us to send signals and thus control it. However without the subsystem there is no code that defines that they exist or how the signals should be sent. To start, I recommend copying over the drivetrain subsystem and then removing everything but the basic boilerplate.

###### *Todo: define "basic boilerplate" better*

```
- commands
- sensors
- subsystems
 - Drivetrain.java
 + ExternalIO.java
- Constants.java
- main.java
- Robot.java
- RobotContainer.java
```

To save some time, these should be the main imports that you end up needing, along with the boilerplate imports that you already have in your file.

```java
import edu.wpi.first.wpilibj.AnalogInput;
import edu.wpi.first.wpilibj.DigitalInput;
import edu.wpi.first.wpilibj.DigitalOutput;
import edu.wpi.first.wpilibj.DriverStation;
import edu.wpi.first.wpilibj.Servo;
```

Now we need to define what ports to use, this table shows the channel assigned to each EXT channel based on its configuration. This configuration **must be** performed using the web interface to the Romi. In the constructor, you must specify the configuration of each channel. This **MUST** match the configuration created using the web interface. [(View Docs)](https://docs.wpilib.org/en/stable/docs/romi-robot/web-ui.html)

##### ⚠️ I can NOT stress this enough, make sure this is 100% right

|Channel|DIO| PWM |Analog In|
|--|--|--|--|
| EXT0 |8|2|-|
|EXT1|9|3|0|
|EXT2|10|4|1|
|EXT4|11|5|2|
|EXT5|12|6|3|

After this, you have to code the subsystem, not much else to say. Here's bit of our code. You'd have to extend the switch statement and add one for each EXT that you are going to need. What you're trying to do is define what "settings" to use based on what EXT is being called. As you can see, we have a switch statement for each EXT, and then depending on what mode *(DIO,PWM,AIN)* is being requested, it defines what "settings" should be used. There of course is other ways to do this however, this is a pretty good solution and you can of course change it down the road if need be.

```java
switch (ext0) {
  case DIO:
    if (modes[n++] == ChannelMode.INPUT)
      m_input8 = new DigitalInput(8);
    else
      m_output8 = new DigitalOutput(8);
    break;
    case PWM: m_servo2 = new Servo(2); break;
    /* i dont know if this derverstation error works 
     * !!!!!!!!!!!
     * this is only for ext0 because it does support analog in!!! Do not do this anywhere else!!!
     * !!!!!!!!!!!
     */
    case AIN: DriverStation.reportError("Cannot configure EXT0 as Analog Input", true); break;
}
switch (ext1) {
  case DIO:
    if (modes[n++] == ChannelMode.INPUT)
      m_input9 = new DigitalInput(9);
    else
      m_output9 = new DigitalOutput(9);
    break;
    case PWM:   m_servo3 = new Servo(3); break;
    case AIN:   m_analogInput0 = new AnalogInput(0); break;
}
```

## Making the command

A subsystem is useless if it never gets used. Just make a new file in the commands folder and copy the biolerplate from some other command, you'll want to import the subsystem first.

```
- commands
 - SuperSecretCommands.java
 + ArmCommand.java
- sensors
- subsystems
- Constants.java
- main.java
- Robot.java
- RobotContainer.java
```

```java
import frc.robot.subsystems.ExternalIO;
```

And from there you need to make your suppliers. Note: I am use jaws open/closed as a boolean here, for most people it makes sense to make it a double like the rest of them. So make sure to not blindly copy and paste code.

```java
private final ExternalIO m_externalIO;
private final Supplier<Double> m_liftSupplier;
private final Supplier<Double> m_tiltSupplier;
private final Supplier<Boolean> m_jawsSupplier;
```

For the arm command method, just make sure you pass all of the suppliers and requirements for it. In the execute method we actually are using that subsystem we made to control the servo motors, my code ended up something like this.

```java
@Override
public void execute() {
 // this is a boolean because its prob more simple when coding and we never need to have it half open or smth
 m_externalIO.m_servo2.set(m_jawsSupplier.get() ? 1.0 : 0.0);
 m_externalIO.m_servo3.set(m_liftSupplier.get());
 m_externalIO.m_servo4.set(m_tiltSupplier.get());
}
```

For isFinished you can just make it return false, it's weird.

###### *Todo: Explain this better*
