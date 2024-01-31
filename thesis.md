# AgentLang - Programming Language for Agent-based Modeling
Faculty of Mathematics and Physics \
Charles University in Prague, Czech Republic

**Title**: AgentLang - Programming Language for Agent-based Modeling \
**Author**: Tomáš Boďa \
**Department**: Department of Distributed and Dependable Systems \
**Supervisor**: Tomáš Petříček

## Abstract
In this thesis, we develop a new programming language (AgentLang) designed exclusively for modeling agent-based simulations. Agent-based modeling refers to a simulation technique that analyses the dynamics of a simulation using the decisions of autonomous entities called agents and is becoming more and more popular, since these models are easier to understand than more complex mathematical models. The language provides constructs for defining agents and their decision-making logic, while maintaining high level of simplicity, making it simple to learn and use. The simulation operates in an incremental manner, allowing for evalutation and debugging of each step separately. Apart from the language itself, the project provides a web-based sandbox with a spreadsheet interface, through which it is possible to adjust agent parameters and values during runtime of the simulation. Although there are numerous agent-based tools available, this language together with the spreadsheet module aims to provide a new approach for modeling agent-based simulations and makes agent-based modeling more accessible to people of all scientific and non-scientific fields.

Keywords: agent-based modeling, simulation, programming language, interpreter, TypeScript

## Introduction
In the realm of many scientific fields, the importance of simulations and predictions of certain events within an isolated environment cannot be overstated. This is on one hand due to the lack of resources and space for such simulations in the scale of real-world scenarios, on the other hand due to moral reasons, such as in epidemiology or sociology. As our understanding of complex systems deepens, the demand for sophisticated tools to model and analyse the dynamics of the simulation increases. This is where agent-based modeling comes into play, since it offers a new, simpler approach for handling complex simulations.

Agent-based models are built on top of agents, which represent the fundamental units of the given scenario, such as people in an epidemic situation or birds in a flock. To build such models, there is a need for tools or languages that provide constructs for representing agents, their properties and their decision-making logic. Such tools already exist and are widely used to model agent-based simulations, such as NetLogo or AgentScript. These tools are powerful and can handle large amount of agents, however, with their performance also comes the complexity of usage and inaccessiblity to people with little technical knowledge. They are many times difficult to learn, since they are based on modern programming languages, restricting the use case to developers only. And since the demand for agent-based models can be seen in non-technical scientific fields such as epidemiology or sociology, there is a need for simpler tools and languages. That is where AgentLang comes into play, providing a new approach to modeling agent-based simulations.

AgentLang aims to provide a new approach to modeling agent-based simulations. This is one one hand due to the simplicity of the language itself, since it features very simple syntax and only the necessary constructs for modeling almost any simulation. On the other hand, the language is integrated into a specialised web-based sandbox, which offers a code editor, a visualisation module and last but not least, a spreadsheet interface with runtime value editing capabilities, which allows the users to fine-tune the simulation in real-time. These above capabilities and features of AgentLang provide all the necessary tools to model agent-based simulations and get a hands-on experience with the language itself.

## 1. Agent-based Modeling
The following sections provide a brief introduction to agent-based modeling, describe the reasons behind its invention and increasing popularity and demonstrate its power and significance on several use cases in real-world scenarios.

### 1.1 Theoretical Background
Agent-based modeling is a simulation technique used in many scientific fields to model and understand complex simulations. In agent-based modeling, a system is modelled using a set of autonomous entities called agents. An agent represents a fundamental meaningful unit of a system, such as a person in an epidemic or a bird in a flock. Each agent individually asseses the current situation, both itself as well as other agents and makes decisions based on a set of defined rules.

It's important to mention that agent-based modeling is more of a mindset than a technology. The main idea behind it is to describe a system from the perspective of its constituent units. If we can assess and understand the behaviour of a fundamental unit of the system, we can model a blueprint or structure of this unit, generate a set of these units with randomised parameters and let their behaviour and interaction among themselves determine the outcome of the simulation. The advantage of such model is its simplicity in terms of implementation and understanding. Even a simple agent-based model can portray complex behavioral patterns and provide insights about the dynamics of the system that it emulates.

### 1.2 Benefits of Agent-based Models
Agent-based modeling offers numerous advantages when compared to other mathematical models and simulation techniques.

First and foremost, the approach of agent-based modelling allows us to uncover novel emergent phenomena within the system, phenomena that were previously unknown or deemed improbable. When we establish and articulate the rules governing the behaviour of agents, the anticipated actions of individual agents seem straightforward, given the simplicity and predictability of these rules. However, upon executing an agent-based model involving numerous interacting agents, the system's behavior often proves to be surprisingly complex. Even slight alterations to agent rules may have a profound impact on the overall outcome of the system, a phenomenon that can be seen for instance in sociology. Here, the collective behavior of a group can be significantly influenced by subtle changes in the behavior of an individual.

Furthermore, agent-based modeling is particularly well-suited for simulation domains involving individual behavioral entity types and their mutual interactions. This is especially true in scenarios requiring the analysis of human interaction, understanding principles behind bird flocking, or predicting traffic jam occurrences on certain city roads. These situations pose challenges for other mathematical models, which may not explicitly consider the fundamental unit of the system as a whole.

Last but not least, agent-based models are flexible and extensible. We can easily incorporate new agents to the system or increase the quantity of existing agents. Modifying the model's behavior is as simple as fine-tuning the decision-making logic within the agent's blueprint, which may lead to a whole new beahviour of the whole system. This degree of flexibility and extensibility implies the usage of agent-based models in scenarios where the level of complexity of the simulation is either highly unpredictable or not known in advance, making it easy to fine-tune the simulation without the need of making too many adjustments.

### 1.2 Use Cases
Agent-based modeling is used in numerous scientific areas and systems. However, its use cases can be classified into four main categories, where it is natural to opt for agent-based modeling.
1. flows
2. markets
3. organizations
4. diffusion

#### 1.2.1 Flows
To describe the idea behind flows, let's consider evacuation of people. The behaviour of a crowd in a sudden or unexpected dangerous situation often leads to panic and chaos. These situation usually arise during mass events such as concerts, sporting events and demonstrations, where there is high density of people on a certain area. In case of fire or other disasters of such nature, panicking people are obsessed by short-term personal interests uncontrolled by social and cultural constraints. To prevent uncontrolled behaviour and maximize the chances of successful evacuation, we need to design venues and their escape exits in the best way possible. And this is a typical scenario suitable for agent-based modeling. In agent terms, collective panic behaviour is an emergent phenomenon that results from relatively complex individual behaviour and interactions between individuals, such as mutual excitation of a primordial instinct, chain reaction or social facilitaion. Based on prior historical observations, statistics and sociological studies, we can fairly accurately define the behaviour of a person in such situations and observe the reaction of masses during evacuation.

#### 1.2.2 Markets

#### 1.2.3 Organizations

#### 1.2.4 Diffusion

## 2. AgentLang Programming Language
The following sections provide an introduction to the AgentLang programming language and detailed description of its syntax and structure, data types, inner workings, standard library and core functionality.

### 2.1 Overview
AgentLang is a programming language designed exclusively for modeling agent-based simulations. It is an interpreted programming language and its interpreter is written in TypeScript. Its syntax is very simple and straightforward, yet it may resemble modern general-purpose programming languages such as Python or JavaScript, establishing a balance between the ease of use for non-technical scientists and familiarity for developers.

The structure of AgentLang is very natural too. The user defines one or multiple agents and their properties. An agent can be viewed as a class in an object-oriented programming language and a property can be understood as a member variable of this class. The output of the interpreter is an array of agents and the current values of their properties. This gives the developer the flexibility to analyse and interpret the output in any way they need. Moreover, the language supports global variables, which are constant values that can be reused among all agents. User defined functions with parameters are not supported. Each property has an inline value defined by an expression. Since AgentLang is an interpreted language, the program is evaluated in an incremental manner, agent by agent, property by property. Although this would imply that a property cannot be used in the definition of another property unless defined earlier, it is not so, since the interpreter has a built-in topological property sorting mechanism, which determines the order in which properties are evaluated at runtime (more on that later).

Apart from the source code, the AgentLang interpreter takes four additional configuration parameters, which are `steps`, `delay`, `width` and `height`. The `steps` parameter sets the number of steps the simulation should run. A step refers to one evaluation of the program. The `delay` parameter determines how often should the interpreter emit the ouput, more specifically, how long should it wait before evaluating the next step of the simulation. The `width` and `height` parameters are important for the interpreter to initialize the built-in `width()` and `height()` functions used in visualisation. To give an example, a configuration with `steps = 100` and `delay = 10` means that the simulation will run for 1 second and will emit 100 uniformly dsitributed outputs.

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
    lambda_expression
    otherwise_expression

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

lambda_expression:
    expression "=>" identifier "=>" expression

otherwise_expression:
    expression "otherwise" expression
```

### 2.3 Declarations
The following sections describe the three supported kinds of declarations, which are the declaration of an agents, properties and global variables.

#### 2.3.1 Agents
Agent is the main building block of the AgentLang simulation. It represents an agent model and its properties and is used for generating a set of agents for the simulation. Agents are always declared in the top-level program scope and they cannot be nested. Defining multiple agent models is also supported.

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
Note that the number of agents parameter does not have to be an explicit number. We can define a global variable with a numeric value and use this variable as the number of agents parameter.
```
define car_count = 20;

agent car car_count {
...
}
```
More about global variables will be explained later in this section.

After defining agents and their behaviour, AgentLang will generate the corresponding number of agents for each agent model and evaluate their properties during runtime.

#### 2.3.2 Properties
Properties are essential in defining the behaviour of an agent model. They can be understood as variables with a value defined based on an expression. Agents can have any number of properties, either independent or dependent on each other.

AgentLang supports two types of properties, which are `property` and `const`. While `property` is recalculated in each step of the simulation based on actual values, `const` is calculated only at the beginning of the simulation, holding a constant value throughout the entire course of the simulation.

##### 2.3.2.1 Const
Property of type `const` is a special kind of property, which holds a constant value during the entire simulation. It is calculated only once as the agent is generated.

To define a `const`, use the `const` keyword followed by an identifier, the assignment symbol `=`, any expression and a semicolon `;` denoting the end of property declaration.
```
agent car 20 {
    const max_speed = 260;
}
```
Properties of type `const` are used for instance when generating random initial coordinates of agents, since they are calculated only once.
```
agent person 10 {
    const x_spawn = random(100, 200);
    const y_spawn = random(100, 200);
}
```

##### 2.3.2.2 Property
Property of type `property` is the most common kind of property. It is recalculated in each step of the simulation for every agent.

To define a `property`, use the `property` keyword followed by an identifier, the assignment symbol `=`, any expression and a semicolon `;` denoting the end of property declaration.
```
agent car 20 {
    property current_speed = random(5, 10);
}
```
However, what if we want to set the property to some kind of initial value and use this property inside of itself to update its value? That is why AgentLang supports default property values.

###### 2.3.2.2.1 Default Property Value
Sometimes we need to initialize a property to some default value before being used and recalculated in the following steps, such as `x` and `y` spawn coordinates or car speed initialisation. Therefore, AgentLang supports default value initialisation.

To define a `property` with a default value, we use the same syntax as basic property initialisation, however, we put a colon `:` after its identifier followed by an expression defining its initial value. This initial value is used only in the first step to initialise the property.
```
agent point {
    property x: 15 = x + 1;
    property y: 5 = y * 2;
}
```
A better example would be the one earlier with the car's current speed. We want the car to accelarate, so we increment its speed by one.
```
agent car {
    property speed = speed + 1;
}
```
However, how can the speed be incremented, when its value is not initialised anywhere?
```
agent car {
    property speed: 0 = speed + 1;
}
```
In this way, the speed is set to 0 in the first step and is incremented by 1 in each following step.

However, this is not the only use case of default property values. Suppose an exaggerated example, where we have two properties, where each depends on the other.
```
agent entity 1 {
    property a = b + 1;
    property b = a + 2;
}
```

#### 2.3.3 Global Variables
Apart from local agent property declarations, AgentLang supports the declaration of global variables which can be reused among all agent types as constant values. Global variables are always declared in the top-level program scope and the best practice is to declare them before all agent declarations.

To declare a global variable, use the `define` keyword followed by its identifier, the assignment symbol `=` followed by an expression defining its initial value and finally the semicolon `;` denoting the end of declaration.
```
define person_count = 120;
define default_speed = 5;

agent person person_count {
    const speed = default_speed / 2;
}

agent car 10 {
    const speed = default_speed * 3;
}
```

### 2.4 Data Types
The following sections describe data types that AgentLang supports.

#### 2.4.1 Number
Number is one of the two primitive data types in AgentLang. A number represents either an integer or a decimal number. Decimal numbers can have any number of decimal points, however, they are always rounded to two decimal places in the output of the simulation.

Numbers can be used in many ways, either as standalone values, or in any numeric expression, such as binary or unary or as parameters to function calls.
```
agent data_instance 10 {
    const decimal_value = 12.8;
    const integer_value = 3;
    const binary_expression = 6.5 * 2 / integer_value;
}
```

#### 2.4.2 Boolean
Boolean is the second of the two primitive data types in AgentLang. It represents a binary value, which can either be `true` or `false`.

Booleans can be expressed either explicitely, using the `true` or `false` keywords, or they can result from other types of expression, such as the relational expression (more on relational expression later).
```
agent data_instance 10 {
    const is_active = false;
    const is_first = index() == 0;
}
```

#### 2.4.3 Agent List
Agent List is a special type of array that contains agent objects. Moreover, it is the only type of array AgentLang supports. This array cannot be defined explicitely, but results from various built-in functions.

The easiest way to get an array of agents is to use the `agents()` method.
```
agent prey 10 {

}

agent predator 5 {
    property targets = agents(prey);
}
```
The `targets` property holds an array of agents of type `prey` with their most recent values (since it is a `property`).

Agent List, however, cannot be indexed. It can only be used as input to other build-in methods, which will be explained later. Also, there are more built-in functions returning an array of agents, however, they will be discussed in later sections.

#### 2.4.4 Agent Object
Agent Object represents one specific agent of the simulation and its properties. It can be used to retrieve the agent's property values and use them in the current agent's body.

Agent Object can be retrieved only using specific built-in functions, such as `min()`.
```
agent person 10 {
    property x = ...;
    property y = ...;

    property closest_person = min(agents(person) => p => dist(p.x, p.y, x, y));
}
```
The above example uses a lambda expression to retrieve an agent of type `person` which is closest to the current person. The structure of lambda expression and other complex expressions and techniques will be explained in later sections.

#### 2.4.5 Null
Null is a special type of value that represents an undefined or missing value. It is tightly bound to the Agent Object data type. Note the following example.
```
define visual_range = 65;

agent person 10 {
    property x = ...;
    property y = ...;

    property close_people = filter(agents(person) => p => dist(p.x, p.y, x, y) < visual_range);
    property close_person = min(close_people => c => dist(c.x, c.y, x, y));
}
```
The `close_person` property attempts to find an agent that is the closest to the current agent, but is also in the visual range of 65. If there are no agents in this visual range, the `close_person` searches an empty array and cannot retrieve a specific agent. Therefore, it holds a Null value.

A problem with null values, however, is that we cannot use it in other properties. More specifically, we cannot retrieve the agent's properties, since it does not hold an agent, but a Null value. That is why the `otherwise` expression exists in AgentLang, which tackles Null values, but will be explained later.

### 2.5 Expressions
The following sections introduce all supported expression in AgentLang, from basic ones such as binary or relational expressions to more complex and domain-specific expression such as the `otherwise` expression.

#### 2.5.1 Binary Expressions
Binary expression is the most basic expression in AgentLang. It consists of two numeric operands and one operator. The operator can be of type addition, subtraction, multiplication, division or modulo. These expressions can be arbitrarily nested and parenthesised.
```
agent data_instance 1 {
    const add_expr = 2 + 3;
    const sub_expr = 6 - 2;
    const mul_expr = 12 * 4;
    const div_expr = 8 / 3;
    const mod_expr = 16 % 6;

    const complex_expr = 2 + 3 * 4 - 8 / 14;
    const parenth_expr = (2 + 3) * 4 - (12 + 2);
}
```

#### 2.5.2 Unary Expressions
There are two types of unary expressions, which are numeric and boolean unary expressions.

##### 2.5.2.1 Numeric Unary Expression
Numeric unary expression is used to convert a positive number to a negative number using the minus `-` operator. The operand can be either a plain number or an identifier holding a numeric value.
```
agent data_instance 1 {
    const value = 12.6;
    const neg_basic = -12.6;
    const neg_ident = -value;
}
```

##### 2.5.2.2 Boolean Unary Expression
Boolean unary expression is used to negate a boolean value using the emphasis `!` operator. The operand can be either a plain boolean (`true` or `false`) or an identifier holding a boolean value.
```
agent data_instance 1 {
    const value = false;
    const neg_basic = !false;
    const neg_ident = !value;
}
```

#### 2.5.3 Logical Expressions
Logical expressions are exressions operating on booleans and always return a boolean value as the result. They are special types of binary expressions which use operators `and` and `or` with boolean operands on both sides.
```
agent data_instace 1 {
    const value_one = true and false;
    const value_two = true or false;
}
```
The first property `value_one` returns `false`, since not all operands are `true` and the second property `value_two` returns `true`, since at least one operand is `true`.

#### 2.5.4 Relational Expressions
Relational expressions are special types of binary expressions that operate on numeric or boolean operands but return boolean results. They use relational operands, such as `==`, `!=`, `>`, `>=`, `<` and `<=`. These operators are used to compare two numbers or booleans.

The `==` and `!=` operators can be used with either numbers and booleans and they check for equality. If the two values are equal or not-equal, the result is `true`, otherwise `false`.
```
agent data_instance 1 {
    const bool_1 = true;
    const bool_2 = false;

    const bool_expr_1 = bool_1 == bool_2;
    const bool_expr_2 = bool_1 != bool_2;

    const num_1 = 1.5;
    const num_2 = 8.4;

    const num_expr_1 = num_1 == num_2;
    const num_expr_2 = num_1 != num_2;
    const num_expr_3 = num_1 > num_2;
    const num_expr_4 = num_1 >= num_2;
    const num_expr_5 = num_1 < num_2;
    const num_expr_6 = num_1 <= num_2;
}
```

#### 2.5.5 Conditional Expressions
Conditional expressions are used to control branch and control the calculation of property values. They decide between two options based on some condition. The condition is always a boolean expression and the results can be of any type.

To use a conditional expression, we use the `if`, `then` and `else` keywords. The `if` keyword marks the start of a conditional expression. It is followed by a boolean expression denoting the condition upon which the structure decides. Then comes the `then` keyword followed by an expression representing the value to be used if the condition is met (is `true`). Finally comes the `else` keyword followed by an expression representing the value to be used if the condition is not met (is `false`).
```
define max_speed = 10;

agent person 5 {
    property speed: 5 = if speed >= max_speed then speed else speed + random(-1, 1);
}
```
The above example controls the maximum value of `speed` using the `max_speed` global variable. If it overflows, it keeps the `max_speed` value, otherwise it is randomly incremented or decremented.

#### 2.5.6 Otherwise Expressions
Otherwise expression are very specific types of expression used to handle Null values. It is a binary expression with the operand `otherwise`. The left-hand side of the `otherwise` expression consists of any expression containing a value of type Agent Object. The right-hand side consists of any expression that does not contain a value of type AgentObject. When the `otherwise` expression is being evaluated, AgentLang checks whether the value of type Agent Object on the left-hand side is Null. If not, it evaluates the left-hand side expression and uses its value. On the other hand, if the value is Null, it instantly switches to the right-hand side of the expression and evaluates and uses it. Otherwise expressions serve as guards for null values, since sometimes we cannot tell if a value of type Agent Object is Null during runtime.
```
define visual_range = 60;

agent person 120 {
    property x = x + x_move;
    property y = y + y_move;

    property people = agents(person);

    property in_proximity = filter(people => p => dist(p.x, p.y, x, y) <= distance);
    property closest = min(in_proximity => p => dist(p.x, p.y, x, y));

    property x_move = (closest.x - x) / 10 otherwise 0;
    property y_move = (closest.y - y) / 10 otherwise 0;
}
```

The above example finds all people in some visual proximity of the current person and select the closest person from the list. It then calculates the direction in which the current person should move to approach the closest person. However, we cannot be certain that we will find some people in proximity. If not, the Agent List array will be empty and the `closest` property will be therefore Null. That is why we used the `otherwise` keyword to ensure that if no such person is found, we will use values `0` for the movement properties.

#### 2.5.7 Lambda Expressions
Lambda expressions are specific types of expressions that cannot be used on their own. Their only use case is as parameters to lambda-specific built-in functions. They are rather a syntactial structure than an expression. They are used for traversing a list of agents and manipulating it. Use cases include filtering of agents, summing certain agent properties or finding a specific agent based on some condition.

There are several built-in functions that take lambda expression as their parameter, some of which are `filter()`, `sum()`, `min()` and `max()`.

To use a lambda expression, we start with an expression holding a value of type AgentList, followed by a lambda arrow `=>`. Then, we declare the lambda parameter name, which is any identifier we choose, such as `item` followed again by a lambda arrow `=>`. The final part of the lambda expression is an expression representing for instance a condition based on which to manipulate the agents.

```
define visual_range = 60;

agent person 120 {
    property x = x + random(-1, 1);
    property y = y + random(-1, 1);

    property people = agents(person);
    property in_proximity = filter(people => p => dist(p.x, p.y, x, y) <= distance);
}
```
The `filter()` function takes a lambda expression as a parameter. We use the `p` parameter to access each individual agent and their properties. Finally, the right-hand side of the lambda expression is used for filtering the agents based on their proximity to the current agent. The result of `in_proximity` property is a filtered array of agents of type `person`.

### 2.6 Core Library

## 3. Implementation

## 4. Documentation

## 5. Examples

## Conclusion

## Bibliography
[1. Eric Bonabeau - Agent-based modeling: Methods and techniques for simulating human systems](https://www.pnas.org/doi/10.1073/pnas.082080899)
