# Project specification

This document serves as a detailed project specification for the Agent-based Modeling Language.

<table>
    <tr><td><b>Author</b></td><td>Tomáš Boďa</td></tr>
    <tr><td><b>Version</b></td><td>1.0.0</td></tr>
    <tr><td><b>Date</b></td><td>30 April, 2023</td></tr>
</table>

## About
The Agent-based Modeling Language is a programming language designed exclusively for modeling agent-based simulations. Its syntax and structure allows for simple understanding and usage, but more importantly for easy conversion to table-based, almost no-code representation of simulations and their agents.

## Basic information

### Software description and main focus
Agent-based model is a computational model and a simulation technique that uses autonomous entities (agents) in order to understand the behaviour and outcome of a system over time. It is used in variety of scientific fields, most common of which are social science, epidemiology, biology or economy. Agent-based models are most commonly implemented as computer simulations. Therefore, a programming language for defining agents and their behaviour is necessary to be able to simulate an agent-based model.

The purpose of this software project is to design and develop an interpreted programming language designed exclusively for agent-based simulations. Moreover, the language should be accessible to people of all scientific fields, especially those with little or no programming experience. Therefore, the language is designed in a way it can be easily converted to and represented by a table of agents and their attributes, making it easy to understand and implement.

The projects features an interpreter for the agent-based modeling programming language, a conversion software which allows for converting source code into table-based structure and finally a web-based application for the agent-based simulation modeling and its real-time visualisation. 

### Technologies
Agent-based simulations do not require fast and efficient processing, the runtime speed is therefore of little to no concern. Moreover, due to the fact that the project also consists of a web-based interface, I decided to unify it on the software architecture level. Therefore, both the interpreter and the web-based interface will be developed in **TypeScript** using the **Node.js** runtime environment. For the web-based application, I opted for the **React.js** framework to handle the user interface.

## Software specification

### Aim of the software project
Since agent-based simulations are useful in many scientific fields, it is necessary to allow people with little to none programming background to be able to model agent-based simulations. Therefore, the main reason behind the idea of this project is the market absence of a simple agent-based modeling language available to everyone including people with non-technical background. Because of that, apart from the programming language itself, the user will be able to use the table-based modeling interface which requires only rudimentary programming knowledge. The source code and the table-based editor will be mutually convertible, meaning that the user will be able to use both simultaneously.

### Main functionality
All parts of the project will be connected together in a web-based application. The application will be divided into two main views - the editor view and the visualisation view. The editor view will contain a source code editor as well as a table-based editor, which will be updated in real-time if either one of them is edited. The visualisation view will handle visual representation of the simulation, as well as a control panel for starting, pausing, stopping and resetting the simulation.

## Software interface

## Functionality

## Other requirements

## Additional notes