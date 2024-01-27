# AgentLang - Programming Language for Agent-based Modeling
Faculty of Mathematics and Physics \
Charles University in Prague, Czech Republic

**Title:** AgentLang - Programming Language for Agent-based Modeling \
**Author:** Tomáš Boďa \
**Department:** Department of Distributed and Dependable Systems \
**Supervisor:** Tomáš Petříček

## Abstract
In this thesis, we develop a new programming language designed exclusively for modeling agent-based simulations. Agent-based modeling refers to a simulation technique that analyses the dynamics of a simulation using the decisions of autonomous entities called agents and is becoming more and more popular, since these models are easier to understand than more complex mathematical models. The language provides constructs for defining agents and their decision-making logic, while maintaining high level of simplicity, making it simple to learn and use. The simulation operates in an incremental manner, allowing for evalutation and debugging of each step separately. Apart from the language itself, the project provides a web-based sandbox with a spreadsheet interface, through which it is possible to adjust agent parameters and values during runtime of the simulation. Although there are numerous agent-based tools available, this language together with the spreadsheet module aims to provide a new approach for modeling agent-based simulations and makes agent-based modeling more accessible to people of all scientific and non-scientific fields.

Keywords: agent-based modeling, simulation, programming language, interpreter, TypeScript

## Introduction
In the realm of many scientific fields, the importance of simulations and predictions of certain events within an isolated environment cannot be overstated. This is on one hand due to the lack of resources and space for such simulations in the scale of real-world scenarios, on the other hand due to moral reasons, such as in epidemiology or sociology. As our understanding of complex systems deepens, the demand for sophisticated tools to model and analyse the dynamics of the simulation increases. This is where agent-based modeling comes into play, since it offers a new, simpler approach for handling complex simulations.

Agent-based models are built on top of agents, which represent the fundamental units of the given scenario, such as people in an epidemic situation or birds in a flock. To build such models, there is a need for tools or languages that provide constructs for representing agents, their properties and their decision-making logic. Such tools already exist and are widely used to model agent-based simulations, such as NetLogo or AgentScript. These tools are powerful and can handle large amount of agents, however, with their performance also comes the complexity of usage and inaccessiblity to people with little technical knowledge. They are many times difficult to learn, since they are based on modern programming languages, restricting the use case to developers only. And since the demand for agent-based models can be seen in non-technical scientific fields such as epidemiology or sociology, there is a need for simpler tools and languages. That is where AgentLang comes into play, providing a new approach to modeling agent-based simulations.

AgentLang aims to provide a new approach to modeling agent-based simulations. This is one one hand due to the simplicity of the language itself, since it features very simple syntax and only the necessary constructs for modeling almost any simulation. On the other hand, the language is integrated into a specialised web-based sandbox, which offers a code editor, a visualisation module and last but not least, a spreadsheet interface with runtime value editing capabilities, which allows the users to fine-tune the simulation in real time. These above capabilities and features of AgentLang provide all the necessary tools to model agent-based simulations and get a hands-on experience with the language itself.

## 1. Agent-based Modeling
The following sections provide a brief introduction to agent-based modeling, describe the reasons behind its invention and increasing popularity and demonstrate its power and significance on several use cases in real-world scenarios.

### 1.1 Theoretical Background
Agent-based modeling is a simulation technique used in many scientific fields to model and understand complex simulations. In agent-based modeling, a system is modelled using a set of autonomous entities called agents. An agent represents a fundamental meaningful unit of a system, such as a person in an epidemic or a bird in a flock. Each agent individually asseses the current situation, both itself as well as other agents and makes decisions based on a set of defined rules.

It's important to mention that agent-based modeling is more of a mindset than a technology. The main idea behind it is to describe a system from the perspective of its constituent units. If we can assess and understand the behaviour of a fundamental unit of the system, we can model a blueprint or structure of this unit, generate a set of these units with randomised parameters and let their behaviour and interaction among themselves determine the outcome of the simulation. The advantage of such model is its simplicity in terms of implementation and understanding. Even a simple agent-based model can portray complex behavioral patterns and provide insights about the dynamics of the system that it emulates.

### 1.2 Benefits of Agent-based Models
Agent-based modeling offers numerous advantages when compared to other mathematical models and simulation techniques.

First and foremost, the approach of agent-based modelling allows us to uncover novel emergent phenomena within the system, phenomena that were previously unknown or deemed improbable. When we establish and articulate the rules governing the behaviour of agents, the anticipated actions of individual agents seem straightforward, given the simplicity and predictability of these rules. However, upon executing an agent-based model involving numerous interacting agents, the system's behavior often proves surprisingly complex. Even slight alterations to agent rules may have a profound impact on the overall outcome of the system, a phenomenon that can be seen for instance in sociology. Here, the collective behavior of a group can be significantly influenced by subtle changes in the behavior of an individual.

Furthermore, agent-based modeling is particularly well-suited for simulation domains involving individual behavioral entity types and their mutual interactions. This is especially true in scenarios requiring the analysis of human interaction, understanding principles behind bird flocking, or predicting traffic jam occurrences on certain city roads. These situations pose challenges for other mathematical models, which may not explicitly consider the fundamental unit of the system as a whole.

Last but not least, agent-based models are flexible and extensible. We can easily incorporate new agents to the system or increase the quantity of existing agents. Modifying the model's behavior is as simple as fine-tuning the decision-making logic within the agent's blueprint, which may lead to a whole new beahviour of the whole system. This degree of flexibility and extensibility implies the usage of agent-based models in scenarios where the level of complexity of the simulation is either highly unpredictable or not known in advance, making it easy to fine-tune the simulation without the need of making too many adjustments.

### 1.2 Use Cases
Agent-based modeling is used in numerous scientific areas and systems. However, its use cases can be classified into four main categories, where it is natural to opt for agent-based modeling.
1. flows
2. markets
3. organizations
4. diffusion

#### 1.2.1 Flows
To describe the idea behind flows, let's consider evacuation of people. The behaviour of a crowd in a sudden or unexpected dangerous situation often leads to panic and chaos. These situation usually arise during mass events such as concerts, sporting events and demonstrations, where there is high density of people on a certain area. In case of fire or other disasters of such nature, panicking people are obsessed by short-term personal interests uncontrolled by social and cultural constraints. To prevent uncontrolled behaviour and maximize the chances of successful evacuation, we need to design the venues and their escape exits in the best way possible. And this is a typical scenario suitable for agent-based modeling. In agent terms, collective panic behaviour is an emergent phenomenon that results from relatively complex individual behaviour and interactions between individuals, such as mutual excitation of a primordial instinct, chain reaction or social facilitaion.
Based on prior historical observations, statistics and sociological studies, we can fairly accurately define the behaviour of a person in such situation and observe the reaction of masses during evacuation.

#### 1.2.2 Markets

#### 1.2.3 Organizations

#### 1.2.4 Diffusion

## 2. AgentLang Programming Language
The following sections provide an introduction to the AgentLang programming language and detailed description of its syntax and structure, data types, inner workings, standard library and core functionality.

### 2.1 Overview
AgentLang is a programming language designed exclusively for modeling agent-based simulations. It is an interpreted programming language and its interpreter is written in TypeScript. Its syntax is very simple and straightforward, yet it may resemble modern general-purpose programming languages such as Python or JavaScript, establishing a balance between the ease of use for non-technical scientists and familiarity for developers.

The structure of AgentLang is very natural too. The user defines one or multiple agents and their properties. An agent can be viewed as a class in an object-oriented programming language and a property can be understood as a member variable of this class. The output of the interpreter is an array of agents and the current values of their properties. In this way, it is up to the developer to analyse and interpret the output in any way they desire. Moreover, the language supports global variables, which are constant values that can be reused among all agents. User defined functions with parameters are not supported. Each property has an inline value defined by an expression. Since AgentLang is an interpreted language, the program is evaluated in an incremental manner, agent by agent, property by property. Although this would imply that a property cannot be used in the definition of another property unless defined earlier, it is not so, since the interpreter has a built-in topological property sorting mechanism, which determines the order in which properties are evaluated at runtime (more on that later).

Apart from the source code, the AgentLang interpreter takes four additional configuration parameters, which are `steps`, `delay`, `width` and `height`. The `steps` parameter sets the number of steps the simulation should run. A step refers to one evaluation of the entire program. The `delay` parameter determines how often should the interpreter emit the ouput, more specifically, how long should it wait before evaluating the next step of the simulation. The `width` and `height` parameters are important for the interpreter to initialize the built-in `width()` and `height()` functions for the visualisation grid. A configuration with `steps = 100` and `delay = 10` means that the simulation will run for 1 second and will emit 100 uniformly dsitributed outputs.

### 2.2 Syntax Grammar
Below is the complete overview of the AgentLang syntax grammar rules.
```
program:
	declaration
	declaration program

declaration:
    define_declaration
    agent_declaration

define_declaration:
	"define" identifier "=" define_value ";"

define_value:
	numeric_literal
	boolean_literal

agent_declaration:
    "agent" identifier agent_count "{" "}"
	"agent" identifier agent_count "{" agent_body "}"

agent_count:
	numeric_literal
	identifier

agent_body:
	property_declaration
	property_declaration agent_body

property_declaration:
	"property" identifier "=" expression ";"
	"property" identifier ":" expression "=" expression ";"
	"const" identifier "=" expression ";"

expression:
    "(" expression ")"
	identifier
	numeric_literal
	boolean_literal
	function_call
	conditional_expression
	relational_expression
	binary_expression
	unary_expression
	logical_expression

identifier:
    "[a-zA-Z\_]+"

numeric_literal:
    "([0-9]+)|([0-9]+.[0-9]+)"

boolean_literal:
    "true"
    "false"

function_call:
    identifier "(" ")"
	identifier "(" argument_list ")"

argument_list:
	argument
	argument "," argument_list

argument:
	expression

conditional_expression:
	"if" expression "then" expression "else" expression

relational_expression:
	expression relational_operator expression

relational_operator:
	"=="
	">="
	"<="
	">"
	"<"

binary_expression:
	expression binary_operator expression

binary_operator:
	"+"
	"-"
	"*"
	"/"
	"%"

unary_expression:
	unary_operator identifier
	numeric_unary_operator numeric_literal
	boolean_unary_operator boolean_literal

unary_operator:
	boolean_unary_operator
	numeric_unary_operator

boolean_unary_operator:
	"!"

numeric_unary_operator:
	"-"

logical_expression:
	expression logical_operator expression

logical_operator:
	"and"
	"or"
```

### 2.3 Declarations
The following sections describe the three supported kinds of declarations, which are the declaration of an agents, properties and global variables.

#### 2.3.1 Agents
Agent is the main building block of the AgentLang simulation. It represents an agent model and its properties and is used for generating a set of agents for the simulation. Agents are always declared in the top-level program scope and they cannot be nested. Defining multiple agent models and their interaction is also supported.

To declare an agent, use the `agent` keyword followed by its identifier, number of agents to generate and the agent body enclosed in curly braces. Below is an example of an agent declaration.
```
agent car 20 {
    ...
}
```
AgentLang also supports multiple agent model declarations. To define multiple agent models, declare them one after another in the program scope.
```
agent car 20 {
    ...
}

agent pedestrian 60 {
    ...
}
```

#### 2.3.2 Properties
Properties are essential in defining the behaviour of agents. They can be understood as variables with a value defined based on an expression. Agents can have any number of properties, either independent or dependent on each other. AgentLang supports two types of properties, which are `property` and `const`.

They can be understood as named variables with a value defined and calculated based on some expression. Agents can have any number of properties, either independent or dependent on each other.

In AgentLang, there are two types of properties, which are `property` and `const`. While `property` is recalculated in each step of the simulation, `const` is calculated only at the beginning, having a constant value throughout the course of the simulation.

To define a `const`, use the `const` keyword followed by an identifier, an assignment symbol, any expression and a semicolon denoting the end of property declaration.
```
agent car 20 {
    const max_speed = 260;
}
```

To define a `property`, use the `property` keyword followed by an identifier, an assignment symbol, any expression and a semicolon denoting the end of property declaration.
```
agent car 20 {
    property current_speed = 85;
}
```

We can use other property's value in the value expression of another property.
```
agent car 20 {
    const max_speed = 260;
    property current_speed = max_speed / 2;
}
```

#### 2.3.3 Global Variables
AgentLang supports the declaration of global variables which can be used in all agent types as constants.

### 2.4 Data Types

### 2.5 Expressions

#### 2.5.1 Binary Expressions

#### 2.5.2 Unary Expressions

#### 2.5.3 Logical Expressions

#### 2.5.4 Relational Expressions

#### 2.5.5 Conditional Expressions

#### 2.5.6 Otherwise Expressions

### 2.6 Core Library

## 3. Implementation

## 4. Documentation

## 5. Examples

## Conclusion

## Bibliography
[1. Eric Bonabeau - Agent-based modeling: Methods and techniques for simulating human systems](https://www.pnas.org/doi/10.1073/pnas.082080899)
