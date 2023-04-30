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

The purpose of this software project is to develop an interpreted programming language designed exclusively for agent-based simulations. Moreover, the language should be accessible to people of all scientific fields, especially those with little or no programming experience. Therefore, the language is designed in a way it can be easily converted to and represented by a table of agents and their attributes, making it easy to understand and implement.

The projects features an interpreter for the agent-based modeling programming language, a conversion software which allows for converting source code into table-based structure and finally a web-based application for the agent-based simulation modeling and its real-time visualisation. 

### Technologies
Agent-based simulations do not require fast and efficient processing, the runtime speed is therefore of little to no concern. Moreover, due to the fact that the project also consists of a web-based interface, I decided to unify it on the software architecture level. Therefore, both the interpreter and the web-based interface will be developed in **TypeScript** using the **Node.js** runtime environment. For the web-based application, I opted for the **React.js** framework to handle the user interface.

## Software specification

### Aim of the software project
Since agent-based simulations are useful in many scientific fields, it is necessary to allow people with little to none programming background to be able to model agent-based simulations. Therefore, the main reason behind the idea of this project is the market absence of a simple agent-based modeling language available to everyone including people with non-technical background. Because of that, apart from the programming language itself, the user will be able to use the table-based modeling interface which requires only rudimentary programming knowledge. The source code and the table-based editor will be mutually convertible, meaning that the user will be able to use both simultaneously.

### Main functionality
All parts of the project will be connected together in a web-based application. The application will be divided into two main views - the editor view and the visualisation view. The editor view will contain a source code editor as well as a table-based editor, which will be updated in real-time if either one of them is edited. The visualisation view will handle visual representation of the simulation, as well as a control panel for starting, pausing, stopping and resetting the simulation.

## Software interface
The following sections describe the language in detail including its syntax, keywords, data types, built-in functions and many more.

### Syntax and Keywords

#### Data types
The agent-based modeling language is dynamically typed, meaning it determines the data type of a variable on its own. There are three data types used in this agent-based modeling language.
- **number** - a decimal number
- **boolean** - a true/false value
- **array** - a collection of agents

#### Agent
Agent-based models are based on autonomous entities - agents. Therefore, the `AGENT` datatype is the primary building block of the simulation. It is similar to a class, representing the individual agent attributes (variables) and their behaviour (methods).

The simulation can consist of one or multiple agents, each is given an identifier (name) using which it can be accessed. The following code snippet demonstrates the creation of an agent named 'person' and an agent named 'house'.
```
AGENT person { ... }
AGENT house { ... }
```
We define an agent by declaring the `AGENT` datatype followed by its name. All its attributes and methods are enclosed in the curly brackets `{}`.

#### Variables
An agent can have one or multiple attributes which define its behaviour. There are three main variable types an agent can have.
- `VARIABLE` - this represents an attribute which is changed each step of the simulation. It requires initial value and an expression based on which it is recalculated
- `DYNAMIC` - this variable represents a value which is recalculated each step of the simulation using an expression which can but does not have to be dependent on the `VARIABLE` and `CONST` attributes. It is similar to a function, however, it does not support parameters
- `CONST` - this variable represents a constant value which cannot be changed during the course of the simulation

Below is an example of an agent, which spawns at certain `x` and `y` coordinates, moves in a random direction each step of the simulation and determines whether to fall asleep or not at the given step based on some probability.
```
AGENT tired_person {
    VARIABLE x: RANDOM(0, WIDTH) = x + RANDOM(0, 1) - 0.5;
    VARIABLE y: RANDOM(0, HEIGHT) = y + RANDOM(0, 1) - 0.5;
    
    CONST sleep_probability = 0.3;
    
    DYNAMIC is_asleep = RANDOM(0, 1) < sleep_probability;
}
```
First, we set the initial values to `VARIABLE` attributes `x` and `y` to random coordinates. Then, we change these values in each step of the simulation by the formula `x + RANDOM(0, 1) - 0.5` and `y + RANDOM(0, 1) - 0.5` respectively. Next, we define a `CONST` attribute with the probability of the agent falling asleep, which is set to `0.3`. Finally, we check in each step whether the agent is asleep or not by generating a random value in range 0 and 1 and checking if it is less than the probability using the formula `RANDOM(0, 1) < sleep_probability`.
 
#### Conditional statements
The language supports basic conditional statements. However, it does not support loops such as `for` or `while` known from other programming languages. Instead, it uses aggregations explained in later sections. There are five important keywords which can be used in conditional statements.

- `IF` - the beginning of a conditional statement followed by a condition - a boolean expression based on which further action is taken
- `THEN` - this keyword is followed by an expression executed if the condition is satisfied
- `ELSE` - this keyword is followed by an expression executed if the condition is not satisfied
- `AND` - this keyword is used in boolean expressions and represents conjunction
- `OR` - this keyword is used in boolean expressions and represents disjunction

Suppose we are simulating the progression of an epidemic. We need to know how many days remain until an infected person gets healthy again. We set the infected timespan to a constant number of 14 days and create a `DYNAMIC` attribute indicating whether a person is infected or not (not implemented here). To determine the remaining infected days, we can create a conditional statement. If the person is already infected, decrement its value, since a day passed (day = simulation step) Otherwise, set its value to a `CONST` infected timespan, since the patient is healthy.
```
AGENT person {
    CONST infected_timespan = 14;
    DYNAMIC infected = ...;

    DYNAMIC days_remaining = IF infected THEN days_remaining - 1 ELSE infected_timespan;
}
```

Now, let's determine whether a person is infected or not. If they are infected and the 14 days haven't passed yet, they should stay infected. Otherwise, check if there are any infected people in proximity and if yes, become infected with a certain probability. We can simulate this using the below code.
```
AGENT person {
    CONST infected_probability = 0.1;

    DYNAMIC days_remaining = ...;
    DYNAMIC infected_neighbours = ...;

    DYNAMIC infected = (infected AND days_remaining > 0) OR (COUNT(infected_neighbours) > 0 AND RANDOM(0, 1) < infected_probability);
}
```

#### Built-in Functions
There are several built-in functions that are used primarily for agent aggregations and mathematical calculations.
- `GENERATE` - this method is used to generate a fixed number of agents. The first parameter is an agent identifier and the second parameter is the number of agents to be generated
```
AGENT person { ... }

GENERATE(person, 100);
```
- `AGENTS` - this method returns an array of all agents of some type, based on their identifier
```
AGENT animal { ... }
AGENT person {
    DYNAMIC animals = AGENTS(animal);
}
```
- `FILTER` - this method is used to filter an array of agents based on some condition
```
AGENT person {
    VARIABLE x: RANDOM(0, WIDTH) = x + RANDOM(0, 1) - 0.5;
    VARIABLE y: RANDOM(0, HEIGHT) = y + RANDOM(0, 1) - 0.5; 

    CONST distance = 5;

    DYNAMIC in_proximity = FILTER(AGENTS(person) as p, SQRT(x * p.x + y * p.y) < distance));
}
```
- `COUNT` - this method returns the number of agents in an array
```
AGENT animal { ... }
AGENT person {
    DYNAMIC number_of_animals = COUNT(AGENTS(animal));
}
```
- `RANDOM` - this method returns a random decimal number in a specified range
- `SQRT` - this method returns the square root of a number

## Functionality
The following sections describe detailed functionality of the agent-based modeling language interpreter.

### Lexer
The lexer will take the raw text input (source code) and produce objects called tokens, which are individual symbols or values in the source code (brackets, commas, numbers, keywords, variable names) together with their location (line, character) for later error handling. It returns an array of tokens which will then be propagated further to the parser.

### Parser
The parser will scan the array of tokens generated by the lexer and produce a structured logical representation of the source code. It produces a so called abstract syntax tree, which is a tree structure representing the whole program. It consists of variable declarations, expressions, statements, nested code blocks. The parser is also responsible for throwing exceptions when a syntax error occurs. After the abstract syntax tree is generated, it is propagated further to the interpreter.

### Interpreter
The interpreter goes through the abstract syntax tree and interprets the code by direct execution of the statements and expressions. It allocates objects, variables, methods and executes them when called in real-time. In each step of the simulation, the interpreter outputs the array of agents and their current attribute values. These values will be used by the visualisation to visualise the simulation in real time.

## Other requirements

## Additional notes