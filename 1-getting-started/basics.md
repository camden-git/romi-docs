# Chapter 1 - Basics

## Prerequisites

In this section, we will go over how the Romi works and how your codebase will be structured. Before you begin, make sure you have a computer with WPILib Visual Studio Code installed. It's also recommended to have a Romi robot, **a Chromebook cannot run WPILib VSC**.

## How does the Romi work?

<img align="right" src="https://raw.githubusercontent.com/camden-git/romi-docs/main/assets/pi-4.webp" width="350">

The Romi robot is based on the Raspberry Pi, a small ARM-based microcomputer. The Pi, located at the top of your Romi, enables you to connect and run code. It is connected to the Romi via a set of pins called GPIO, which allows communication and power transfer.

The Raspberry Pi hosts a web control UI and a service that allows movement commands to be sent. To access this, you need to connect to the WiFi network that the Pi hosts. Once connected, you can communicate with the Pi and other devices on the WiFi network. This setup enables multiple Romi robots to be used simultaneously without any hassle.

When you run your code, a websocket connection is established, allowing you to quickly receive data like position and send movement commands. Unlike a RoboRio, where the code is uploaded and run on the board itself, the Romi's code is still executed on your PC through the simulator. However, this distinction is not something that will directly affect you.

**Note:** After hitting something, the connection is known to drop, and the cause is unclear.

## Your codebase

In WPILib, your file structure will look something like this:

```
- commands
- sensors
- subsystems
- Constants.java
- main.java
- Robot.java
- RobotContainer.java
```

When you create your WPILib project, these files will be automatically generated, and some of them will be pre-filled for you. Each of these files serves an important purpose, and let's quickly go over them:

### Main.java

This file is responsible for starting your robot, and you should never need to edit it.

### Constants.java

In this file, people often define common variables, allowing you to change values in a single place instead of searching through all your files.

### Robot.java & RobotContainer.java

Both of these files will be frequently used. In these files, you can register menus in the simulator, add different schedules, and perform other tasks that we will cover in later chapters.

### subsystems/

This folder is where you define components like your drivetrain and any methods related to them. While you may not need to use this folder extensively later on, it is important in the beginning.

### commands/

This will likely be the folder you work with the most. Here, you place commands that interact with your subsystems and define the data to be sent to them. Think of it as creating your own custom blocks, such as driving a certain distance or turning a specific angle. This is also where you define the schedules used in autonomous mode, which are chains of these commands. There's a lot of cool stuff you can do with this, so feel free to experiment.

### sensors/

This folder is not automatically created and may not be used frequently. It is often used to store files related to accessing gyro data, which is helpful for gyro/PID-based movement.

We will cover most of these topics in more detail later, but having this information is helpful even if you don't use all of it. At this point, you should be ready to move on to working on your RomiRobot in the next chapter.

## Notes

### ARM

ARM is a specification known as an "architecture." It defines how the CPU should be built and handle code. While this information may not be crucial, it is worth noting that ARM is more common in smaller devices like phones, while PCs often use x86.

### Websocket

A websocket is like a chat between two programs, where both parties can send messages as long as the connection remains open. In contrast to a regular website request, where data is sent and received once, a websocket enables continuous bidirectional communication.

[Back - Intro](https://github.com/camden-git/romi-docs/blob/main/1-getting-started/intro.md) | [Home](https://github.com/camden-git/romi-docs/) | [Chapter Home](https://github.com/camden-git/romi-docs/tree/main/1-getting-started) | [Next - Setup the Romi](https://github.com/camden-git/romi-docs/blob/main/1-getting-started/setup.md)
