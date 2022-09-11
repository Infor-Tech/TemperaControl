# TemperaControl - Concept

## Table of Contents

1. [**General Description**](#general-description)
2. [**Proposed approaches to an architecture of a system**](#proposed-approaches-to-an-architecture-of-a-system)
   1. [Proposal 1](#proposal-1)
   2. [Proposal 2](#proposal-2)
   3. [Proposal 3](#proposal-3)
3. [**Establishing connection between a sensor and a hub**](#establishing-connection-between-a-sensor-and-a-hub)

# General Description

The main role of this system is to log temperatures in intervals from connected sensors. To make that happen devices and services must be made.

It is sure, that a temperature sensor must be build. For that a microcontroller from esp8266 familly is going to be used. WiFi is going to be a way for communication.

Logged data is going to be sent to a service on a server which is going to save in on a database.

Some way of data representation is needed. I want this part of a system to be as customizable, as it can be, thus providing just a rest api would be reasonable. With that this system could be implemented to already existing projects.

# Proposed approaches to an architecture of a system

I have came up with a few ideas for an architecture of a system and the main difference between them is in a way of communication between temperature sensors and a inbound data managment service on a remote server.

## Proposal 1

In this proposal, between sensors and a server there is a hub. It's role is to manage connected to it sensors and send temperature data to a server. This solution requires sensors and a hub to be in the same network. What makes this approach compelling is that it gives a lot of control over the sensors connected, though it makes setting up a fleet of sensors harder.

![diagram 1](./assets/architecture-diagram-1.png)

## Proposal 2

Simpler solution is to directly connect all sensors with a server. It makes setting up a fleet of sensors easier as there is no need to group them and it doesn't matter whether they are in the same network. This proposal makes managment of them harder.

![diagram 2](./assets/architecture-diagram-2.png)

## Proposal 3

It is possible to implement both of proposals. It allows customization for everyone needs. It makes inbound data managment service more complex.

![diagram 3](./assets/architecture-diagram-3.png)

# Establishing connection between a sensor and a hub

Both of these devices must find each other within a network. For that a thermometer is going to send a requests in a loop until it receves 200 HTTP response code. The hub will process such request, so that it can request temperatures later.

**Finding a hub's ip by a thermometer device**

![diagram-1](./assets/Establishing-Connection-1.png)

**Request handling by a hub**

![diagram-1](./assets/Establishing-Connection-2.png)
