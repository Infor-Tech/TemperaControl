# TemperaControl - Concept

## Table of Contents

1. [**General Description**](#general-description)

# General Description

The main role of this system is to log temperatures in intervals from connected sensors. To make that happen devices and services must be made.

It is sure, that a temperature sensor must be build. For that a microcontroller from esp8266 familly is going to be used. WiFi is going to be a way for communication.

Logged data is going to be sent to a service on a server which is going to save in on a database.

Some way of data representation is needed. I want this part of a system to be as customizable, as it can be, thus providing just a rest api would be reasonable. With that this system could be implemented to already existing projects.
