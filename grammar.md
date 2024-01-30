# AgentLang Syntax Grammar
Below is the syntax grammar to the AgentLang programming language.
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
