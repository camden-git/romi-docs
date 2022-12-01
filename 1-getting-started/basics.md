# Chapter 1 - Basics

## Prerequisites

In this section we will go over how the Romi works, and how your codebase will work. Make sure you have a computer with WPILib Visual Studio Code and it's recommended to have a Romi as well, a chromebook can not run WPILib VSC.

## How does the Romi work?

<img align="right" src="https://raw.githubusercontent.com/camden-git/romi-docs/main/assets/pi-4.webp" width="350">

The Romi robot is based on the Raspberry Pi, which is a small [ARM](#ARM) based micro computer. The Pi is a green board located at the top of your Romi, this is what allows you to connect and run code. You’ll notice it's plugged in via a long set of pins called GPIO, this is what allows it to communicate with the Romi and get power. 

Your Raspberry Pi hosts a web control UI, and a service that allows movement commands to be sent. To access this you need to connect to the WiFi network that the Pi hosts. When you connect to the WiFi you can connect to other devices on the WiFI, which includes the Pi. By hosting its own WiFi network more than 1 Romi can be used at one time without hassle. 

<img align="left" src="https://raw.githubusercontent.com/camden-git/romi-docs/main/assets/romi-map.jpg" width="450">

When you run your code, a [websocket](#Websocket) connection is made, which allows it to quickly receive data like position and send movement commands. \
Note: After hitting something the connection is known to drop, it’s unclear what causes this.

## Notes

### ARM

ARM is a specification called an “architecture”. This defines how the cpu should be built and handle code, this won't ever be very important. ARM is more common in smaller devices like your phone, and pc's often use AMD64/X_86. 

### Websocket

A websocket is like a chat between 2 programs, both parties can send messages to the other while they both are still there. For example when you visit a normal website you send a request for the site once, and the site responds once. Whereas with a websocket both parties can send or receive indefinitely as long as both parties keep the connection open. 

[Back - Get Started](https://github.com/camden-git/romi-docs/blob/main/1-getting-started/intro.md) -
[Next - Start a codebase](https://github.com/camden-git/romi-docs/blob/main/1-getting-started/basics.md)
