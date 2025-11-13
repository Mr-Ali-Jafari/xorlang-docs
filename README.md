# XorLang Programming Language Reference

## Language Overview
XorLang is a compiled programming language with Persian syntax that generates optimized C code.

## Compilation Pipeline
```
Source Code (.xor) → Lexer → Parser → AST → Codegen → C Code → Executable
```

## Data Types

### Basic Types
- **Integer**: `bucket x = 42;`
- **Float**: `bucket pi = 3.14;`
- **String**: `bucket name = 'Ali';`
- **Boolean**: `bucket flag = yes;` / `bucket flag = no;`
- **Array**: `bucket arr[] = [1, 2, 3];`

## Keywords & Operators

### Keywords
- `bucket` - Variable declaration
- `when if` / `when else` - Conditionals
- `while loop` - While loops
- `for loop` - For loops
- `make function` - Function definition
- `give back` - Return statement
- `show` - Output function
- `ask` - Input function
- `yes` / `no` - Boolean values
- `note:` - Comments

### Operators
- Arithmetic: `+`, `-`, `*`, `/`
- Comparison: `==`, `!=`, `>`, `<`, `>=`, `<=`
- Assignment: `=`
- Logical: `&&`, `||` (planned)

## Control Structures

### Conditionals
```xorlang
when if (condition) {
    # code
} when else {
    # code
}
```

### Loops
```xorlang
# While loop
while loop (condition) {
    # code
}

# For loop
for loop (init; condition; update) {
    # code
}
```

### Functions
```xorlang
make function name(params) {
    # code
    give back value;
}
```

## Standard Library Modules

### Math Module
- `math_sqrt(x)` - Square root
- `math_pow(base, exp)` - Power
- `math_abs(x)` - Absolute value
- `math_max(a, b)` - Maximum
- `math_min(a, b)` - Minimum
- `math_round(x)` - Round
- `math_random()` - Random 0-1
- `math_random_range(min, max)` - Random in range

### String Module
- `string_to_upper(str)` - Uppercase
- `string_to_lower(str)` - Lowercase
- `string_contains(str, substr)` - Contains check
- `string_starts_with(str, prefix)` - Starts with
- `string_trim(str)` - Remove whitespace
- `string_split(str, delim)` - Split string
- `string_join(arr, sep)` - Join array
- `string_replace(str, old, new)` - Replace

### Array Module
- `len(array)` - Array length
- `push(array, element)` - Add element
- `pop(array)` - Remove last
- `array_sort(array)` - Sort array
- `array_reverse(array)` - Reverse
- `array_unique(array)` - Remove duplicates
- `array_find(array, element)` - Find index
- `array_slice(array, start, end)` - Extract portion

### File Module
- `file_read(filename)` - Read file
- `file_write(filename, content)` - Write file
- `file_exists(filename)` - Check existence
- `file_delete(filename)` - Delete file
- `file_size(filename)` - Get size

### Network Module
- `is_online()` - Check connectivity
- `http_get(url)` - GET request
- `http_post(url, data)` - POST request
- `download(url, filename)` - Download file

### Time Module
- `time_now()` - Current timestamp
- `time_format(time, format)` - Format time
- `time_sleep(seconds)` - Sleep

### System Module
- `system_run(command)` - Execute command
- `system_get_env(var)` - Get environment variable

### Error Handling
- `safe_divide(a, b)` - Safe division (returns 0 on division by zero)
- `error(message)` - Print error and return -1

## Token Types (from token.h)

### Basic Tokens
- `TOKEN_ID` - Identifiers
- `TOKEN_EQUALS` - Assignment (=)
- `TOKEN_STRING` - String literals
- `TOKEN_NUMBER` - Integer literals
- `TOKEN_FLOAT` - Float literals
- `TOKEN_SEMI` - Semicolon (;)

### Delimiters
- `TOKEN_LPAREN` - Left parenthesis (
- `TOKEN_RPAREN` - Right parenthesis )
- `TOKEN_LBRACE` - Left brace {
- `TOKEN_RBRACE` - Right brace }
- `TOKEN_LBRACKET` - Left bracket [
- `TOKEN_RBRACKET` - Right bracket ]
- `TOKEN_COMMA` - Comma ,

### Operators
- `TOKEN_PLUS` - Addition (+)
- `TOKEN_MINUS` - Subtraction (-)
- `TOKEN_MULTIPLY` - Multiplication (*)
- `TOKEN_DIVIDE` - Division (/)
- `TOKEN_GT` - Greater than (>)
- `TOKEN_LT` - Less than (<)
- `TOKEN_GTE` - Greater or equal (>=)
- `TOKEN_LTE` - Less or equal (<=)
- `TOKEN_EQ` - Equality (==)
- `TOKEN_NEQ` - Not equal (!=)

## AST Node Types (from AST.h)

- `AST_VARIABLE_DEFINITION` - Variable declarations
- `AST_VARIABLE` - Variable references
- `AST_ASSIGNMENT` - Variable assignments
- `AST_FUNCTION_CALL` - Function calls
- `AST_STRING` - String literals
- `AST_NUMBER` - Integer literals
- `AST_FLOAT` - Float literals
- `AST_BOOLEAN` - Boolean values
- `AST_BINARY_OP` - Binary operations
- `AST_WHEN_IF` - Conditional statements
- `AST_WHILE_LOOP` - While loops
- `AST_FOR_LOOP` - For loops
- `AST_FUNCTION_DEFINITION` - Function definitions
- `AST_RETURN` - Return statements
- `AST_ARRAY` - Array literals
- `AST_ARRAY_ACCESS` - Array indexing
- `AST_IMPORT` - Import statements
- `AST_COMPOUND` - Statement blocks

## Import System
```xorlang
putlib function_name from module;
putlib * from module;
putlib func1, func2 from module;
```

## Examples

### Basic Program
```xorlang
bucket name = ask('Enter name: ');
show('Hello ' + name);
```

### Math Operations
```xorlang
bucket result = math_sqrt(25);
bucket power = math_pow(2, 3);
show(result);
```

### File Operations
```xorlang
when if (file_exists('data.txt')) {
    bucket content = file_read('data.txt');
    show(content);
}
```

### Network Request
```xorlang
when if (is_online()) {
    bucket response = http_get('https://api.example.com');
    show(response);
}
```

## Compilation
```bash
# Compile XorLang program
./xorlang program.xor

# Run executable
./program.xor.out
```

## Architecture
- **Lexer**: Tokenizes source code
- **Parser**: Builds Abstract Syntax Tree
- **Codegen**: Generates C code with standard library integration
- **Compiler**: Links with libcurl and libm for full functionality
