# Compiler-project

## Group members
<b> 121891 </b>   Salomon Metre <br>
<b> 131548 </b>  Nathan Ruru <br>
<b> 134977 </b>  Jeff Munyigi <br>
<b> 119314 </b>  Oguta Cassey Moses <br>
<b> 129040 </b>  Wambua James Mutua

## Problem Statement:
The goal of this project is to implement a simple compiler construction project that includes a tokenizer and parser for a specific configuration language used for defining API key configurations. The configuration language allows users to specify services and their corresponding API keys.

## Solution:
The solution involves creating a tokenizer and parser in Python to process a given input code written in the configuration language. The tokenizer breaks down the input code into tokens (lexical analysis), and the parser constructs an Abstract Syntax Tree (AST) based on the identified tokens (syntax analysis).

## Grammar:
The grammar for the configuration language is as follows:

config  ::= service_declaration+
service_declaration ::= SERVICE_NAME '{' api_key_statements '}'
api_key_statements ::= (API_KEY '=' STRING ';')*
SERVICE_NAME     ::= [a-zA-Z_][a-zA-Z0-9_]*
API_KEY          ::= "api_key"
STRING           ::= '"(?:[^"\\]|\\.)*"'

This is grammar tailored to configuring API keys : <br>
<b> program -> service* service -> SERVICE_NAME '{' api_key_statement* '}' api_key_statement -> 'api_key' '=' STRING ';' </b>

An example of API Key configuration : <br>
<b> google_maps { api_key = "YOUR_GOOGLE_MAPS_API_KEY"; } <br>
weather_service { api_key = "YOUR_WEATHER_SERVICE_API_KEY"; } </b>

### Explanation:
### Tokenizer (tokenize function):

* SERVICE_NAME: Matches valid service names, such as alphanumeric strings starting with an alphabet or underscore. <br>
* STRING: Matches strings enclosed in double quotes, allowing for escape characters. <br>
* EQUALS: Matches the equals sign (=). <br>
* SEMICOLON: Matches the semicolon (;). <br>
* OPEN_BRACE and CLOSE_BRACE: Match opening and closing curly braces ({ and }). <br>
* API_KEY: Matches the fixed string "api_key". <br>

## Parser (Parser class):
The Parser class initializes with a list of tokens and implements methods for parsing services and API key statements.
parse_service: Parses a service declaration, including the service name and API key statements.
parse_api_key_statements: Parses API key statements within a service declaration.
match, check, advance, previous: Helper methods for token matching and traversal.
error: Raises an exception in case of a parsing error.

## Project Execution:
config  ::= service_declaration+
service_declaration ::= SERVICE_NAME '{' api_key_statements '}'
api_key_statements ::= (API_KEY '=' STRING ';')*
SERVICE_NAME     ::= [a-zA-Z_][a-zA-Z0-9_]*
API_KEY          ::= "api_key"
STRING           ::= '"(?:[^"\\]|\\.)*"'

The provided input code is tokenized using the tokenize function, generating a list of tokens.
The Parser class is instantiated with the tokens, and the parse method is called to construct the AST.
The AST is then printed to visualize the parsed structure.
