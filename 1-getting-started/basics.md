# Chapter 1 - Basics

## Prerequisites

In this section we will go over how the Romi works, and how your codebase will work. Make sure you have a computer with WPILib Visual Studio Code and it's recommended to have a Romi as well, a chromebook can not run WPILib VSC.

## How does the Romi work?

<img align="right" src="https://raw.githubusercontent.com/camden-git/romi-docs/main/assets/pi-4.webp" width="350">

The Romi robot is based on the Raspberry Pi, which is a small [ARM](#ARM) based micro computer. The Pi is a green board located at the top of your Romi, this is what allows you to connect and run code. You’ll notice it's plugged in via a long set of pins called GPIO, this is what allows it to communicate with the Romi and get power. 

Your Raspberry Pi hosts a web control UI, and a service that allows movement commands to be sent. To access this you need to connect to the WiFi network that the Pi hosts. When you connect to the WiFi you can connect to other devices on the WiFI, which includes the Pi. By hosting its own WiFi network more than 1 Romi can be used at one time without hassle. 

<img align="left" src="https://raw.githubusercontent.com/camden-git/romi-docs/main/assets/romi-map.jpg" width="350">

When you run your code, a [websocket](#Websocket) connection is made, which allows it to quickly receive data like position and lets you send movement commands. One thing the Romi does different from a RoboRio is that the code is actually still ran on your pc via the simulator, whereas with the RoboRio code is uploaded and ran on the board. This won't really ever affect you, just good to know. \
\
**Note:** After hitting something the connection is known to drop, it’s unclear what causes this.

## Your codebase

In WPILib your file structure will look something like this.  
```
- commands
- sensors
- subsystems
- Constants.java
- main.java
- Robot.java
- RobotContainer.java
```

When you make your WPILib project these files will be automatically created, and some will be filled in for you. All of these files are pretty important so I'll go over them real quick here.

#### Main.java

This is what starts your robot, you should never need to edit this.

#### Constants.java

This is where people often define common variables so you can change just this file instead of looking through all your files.

#### Robot.java & RobotContainer.java

Both of these files you will need to use quite a bit, here you can register menus in the simulator, add your different schedules, and some other stuff we will go over in later chapters.

#### subsystems/

In this folder you define stuff like your drivetrain and any methods you need to use related to it. You wont really need to use this that often later on, but it is important in the beginning.

#### commands/

This will probably be the folder you use the most. This is where you put the commands that access one of your subsystems and define what data should be sent to them. Think about it like scratch blocks. Here you are making your own blocks, like drive x amount, turn x degrees, and whatever else you would need. This is also where you put the schedules you use when in autonomous mode. These are chains of these blocks and ee go over this more later. There is a lot of cool stuff you can do with this, so feel free to play arround.

#### sensors/

This is another folder you probably wont use, and it is not automatically created. Often this is used to store the file that deals with accessing the gyro data, which is helpful for gyro/PID based movement. 

Most of this stuff we go over again in more detail, but knowing this info is helpful even if you don't use all of it. At this point, you should be ready to go onto actually working on your RomiRobot in the next chapter.  

## Notes

### ARM

ARM is a specification called an “architecture”. This defines how the cpu should be built and handle code, this won't ever be very important. ARM is more common in smaller devices like your phone, and PCs often use x86. 

### Websocket

A websocket is like a chat between 2 programs, both parties can send messages to the other while they both are still there. For example when you visit a normal website you send a request for the site once, and the site responds once. Whereas with a websocket both parties can send or receive indefinitely as long as both parties keep the connection open.

[Back - Intro](https://github.com/camden-git/romi-docs/blob/main/1-getting-started/intro.md) | [Home](https://github.com/camden-git/romi-docs/) | [Chapter Home](https://github.com/camden-git/romi-docs/tree/main/1-getting-started) |  [Next - Start a Project](https://github.com/camden-git/romi-docs/blob/main/1-getting-started/project.md)
