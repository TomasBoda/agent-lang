# AgentLang - Programming Language for Agent-based Modeling
Faculty of Mathematics and Physics \
Charles University in Prague, Czech Republic

**Title:** AgentLang - Programming Language for Agent-based Modeling \
**Author:** Tomáš Boďa \
**Department:** Department of Distributed and Dependable Systems \
**Supervisor:** Tomáš Petříček

## Abstract
In this thesis, we develop a new programming language designed exclusively for modeling agent-based simulations. Agent-based modeling refers to a simulation technique that analyses the dynamics of a simulation using the behaviour and decisions of autonomous entities called agents. These models are increasing in popularity, since they are easier to understand and analyse that more complex mathematical models. The language provides constructs for defining agents and their decision-making logic, while maintaining high level of simplicity, making it simple to learn and use. The simulation operates in an incremental manner, making it possible to evaluate and debug each step separately. Although there are numerous agent-based tools available, this language aims to provide a new approach for modeling agent-based simulations and makes agent-based modeling more accessible to people of all scientific, as well as non-scientific fields.

Keywords: agent-based modeling, simulation, programming language, interpreter, TypeScript

## Introduction
In the realm of many scientific and non-scientific fields, the importance of simulations and predictions of certain events within an isolated environment cannot be overstated. This is on one hand due to the lack of resources and space for such simulations in the scale of real-world scenarios, on the other hand due to moral reasons, such as in epidemiology or sociology. As our understanding of complex systems deepens, the demand for sophisticated tools to model and analyse the dynamics of the simulation increases. This is where agent-based modeling comes into play, since it offers a new, simpler approach for handling complex simulations.

Agent-based models are built on top of agents, which represent the fundamental units of the given scenario, such as people in an epidemic situation or birds in a flock. To build such models, there is a need for tools or languages that provide constructs for representing agents, their properties and their decision-making logic. Such tools already exist and are widely used to model agent-based simulations, such as NetLogo. These tools are powerful and can handle large amount of agents, however, with their performance also comes the complexity of usage and inaccessiblity to people with little technical knowledge. And since the demand for agent-based models can be seen in non-technical scientific fields such as epidemiology or sociology, there is a need for simpler tools and languages. That is where AgentLang comes into play, providing a new approach to modeling agent-based simulations.

## 1. Agent-based Modeling
The following sections provide a brief introduction to agent-based modeling, describe the reasons behind its invention and increasing popularity and demonstrate its power and significance on several use cases in real-world scenarios.

### 1.1 Theoretical Background
Agent-based modeling is a simulation technique used in many scientific fields to model and understand complex simulations. In agent-based modeling, a system is modelled using a set of autonomous entities called agents. An agent represents a fundamental meaningful unit of a system, such as a person in an epidemic or a bird in a flock. Each agent individually asseses the current situation, both itself as well as other agents and makes decisions based on a set of defined rules.

It's important to mention that agent-based modeling is more of a mindset than a technology. The main idea behind it is to describe a system from the perspective of its constituent units. If we can assess and understand the behaviour of a fundamental unit of the system, we can model a blueprint or structure of this unit, generate a set of these units with randomised parameters and let their behaviour and interaction among themselves determine the outcome of the simulation. The advantage of such model is its simplicity in terms of implementation and understanding. Even a simple agent-based model can portray complex behavioral patterns and provide insights about the dynamics of the system that it emulates.

### 1.2 Benefits of Agent-based Models
There are multiple benefits that agent-based modeling offers in comparison to other mathematical models.

First and foremost, through agent-based modeling, we can observe new emergent phenomena of the system that we did not know existed or could occur. When we describe and define rules based on which agents should behave, we can often easily state how we expect an agent to behave, since these rules are often very simple and predictable. However, after running an agent-based model with hundreds of agents that interact with each other, the outcome and behaviour of the system is usually very surprising and we can see that even a slight change of rules can result can have a drastic impact on the outcome of the whole system. This phenomenon can be seen in sociology, where the group's collective behaviour is defined by very slight and negligible changes to the person's behaviour and is a perfect example of an emergent phenomenon.

Moreover, the domain and nature of the simulation is often very suitable for agent-based modeling, if the simulation is composed of individual behavioral entities and their connections. This is truthful especially in situations where we need to analyze human interaction, the principles behind bird flocking or predicting the occurences of traffic jams on certain city roads. Such scenarios are difficult to model using other mathematical models, where the fundamental unit of the system as a whole is not taken into consideration.

Last but not least, agent-based models are flexible and extensible. We can easily add new agents to the system or increase the count of current agents. To change the behaviour of the model, we can just tune the decision-making logic of the agent's blueprint and the whole simulation starts to behave differently. This degree of flexibility implies the usage of agent-based models in situations where the level of complexity of the simulation is not known in advance, making it easy to fine-tune the simulation on the run.

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
This chapter introduces the AgentLang programming language and describes its syntax, structure, data types, standard library and core functionality provided in the language.

### 2.1 Overview
AgentLang's syntax is very simple and straightforward, yet it may resemble many modern general-purpose programming languages, establishing balance between the ease of use for non-technical newcomers and familiarity for developers. The structure of AgentLang's programs is very natural too. The user defines one or multiple agents and for each agent their properties. An agent can be viewed as a class in a multi-purpose programming language, such as Java and a property can be understood as a class variable. However, functions are not supported. Each property has a value, there are no voids or code blocks executing statememts. In each step of the simulation, the values of each agent are calculated based on their previous values and returned by the interpreter. In this way, the results can be processed and interpreted by the user based on their needs and usage of AgentLang.

### 2.2 Declarations
AgentLang supports three main kinds of declarations, which are the declaration of an agent, a property or a global variable.

#### 2.2.1 Agents
Agents are always declared in the top-level program context, so they cannot be nested. To declare an agent, use the `agent` keyword followed by the agent's identifier, a number or identifier representing the agent count and finally an open and closed brace `{}` encapsulating the agent's body (explained later). 

Below is an example of an agent declaration.
```
agent car 20 {}
```
We defined an agent with identifier `car` and want to generate 20 agents of this type.

AgentLang supports multiple agent declarations and their interactions (explained later). To define multiple agents, declare them one after another in the program scope.
```
agent car 20 {}

agent obstacle 10 {}
```

#### 2.2.2 Properties
Properties are the essential building block of the behaviour of agents. They can be understood as named variables with a value defined and calculated based on some expression. Agents can have any number of properties, either independent or dependent on each other.

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

#### 2.2.3 Global Variables
AgentLang supports the declaration of global variables which can be used in all agent types as constants.

### 2.3 Data Types

### 2.4 Expressions

#### 2.4.1 Binary Expressions

#### 2.4.2 Unary Expressions

#### 2.4.3 Logical Expressions

#### 2.4.4 Relational Expressions

#### 2.4.5 Conditional Expressions

#### 2.4.6 Otherwise Expressions

### 2.5 Core Library

## 3. Implementation

## 4. Documentation

## 5. Examples

## Conclusion

## Bibliography
[1. Eric Bonabeau - Agent-based modeling: Methods and techniques for simulating human systems](https://www.pnas.org/doi/10.1073/pnas.082080899)