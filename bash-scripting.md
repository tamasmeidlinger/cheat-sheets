# Todo

- [ ] Continue on fcc from Random Numbers and Mathematical Operations
- [ ] How to create your own flags (`getopts`?)

# Bash Scripting Basics

- **Bash scripting**: Writing a sequence of Bash commands in a file, which you can then execute with Bash to run the contents of the file.

- **Shebang**: The commented line at the beginning of a script (e.g., `#!/bin/bash`) that indicates what interpreter should be used for the script.

```bash
#!/bin/bash
```

## Variable assignment

- **Variable assignment**: Instantiate variables using the syntax `variable_name=value`.

- **Variable creation rules**: Create variables with `VARIABLE_NAME=VALUE` syntax. No spaces are allowed around the equal sign (`=`). Use double quotes if the value contains spaces.

```bash
NAME=John
MESSAGE="Hello World"
COUNT=5
TEXT="The next number is, "
```

- **Variable usage**: Access variable values by placing `$` in front of the variable name.
- **Variable interpolation**: Use `$variable_name` to access the value of a variable within strings and commands.

```bash
NAME=Tamas
MESSAGE="Hello from $NAME"
MESSAGE_FLEX="Greetings from"

echo $NAME
echo "The message is: $MESSAGE"
echo $MESSAGE_FLEX $NAME

# Tamas
# The message is: Hello from Tamas
# Greetings from Tamas
```

## User input

- **User input**: Use `read` to accept input from users and store it in a variable.

```bash
#!/bin/bash

echo -e "-- Login --\n"
printf "Username:\n"
read -p "> " username

printf "Password:\n"
read -sp "> " password

printf "\nUsername: %s\nPassword: %s\n" $username $password

# -- Login --
#
# Username:
# > tamas
# Password:
# >
# Username: tamas
# Password: password
```

## Comments

- **Comments**: Add comments to your scripts using `#` followed by your comment text.
- **Multi-line comments**: Comment out blocks of code using colon and quotes.

```bash
# Single line comment

: '
Multiline
comment
'
```

## Script arguments

**Script arguments**: Programs can accept arguments that are accessible using $ variables.

- `$*` prints all arguments passed to the script
- `$@` prints all arguments passed to the script as separate quoted strings
- `$<number>` accesses specific arguments by position (e.g., `$1`, `$2`, `$3`)
- `$#` accesses the number of arguments
- `${!<number>}` = indirect expansion, retrieves the positional parameter at position `<number>`.

```bash
printf "$*\n"
printf "1: %s, 2: %s, 3: %s\n" $@
echo $1
echo $2

: '
~ bash script.sh hello there
hello there
1: hello, 2: there, 3:
hello
there
'
```

```bash
echo "Number of args: $#"
echo $0 # Name of the script

for arg in $@
do
    echo $arg
done

: '
bash script.sh hello bello
Number of args: 2
script.sh
hello
bello
'
```

```bash
# Print args to terminal
if [[ $# -eq 0 ]]; then
    echo "No args given"
elif [[ $# -eq 1 ]]; then
    echo $1
else
    i=1
    for arg in $@
    do
        echo "$i: $arg"
        (( i++ ))
    done
fi
```

```bash
#!/bin/bash

# Print args to terminal
if [[ $# -eq 0 ]]; then
    echo "No args given"
elif [[ $# -eq 1 ]]; then
    echo $1
else
    for (( i=1; i<=$#; i++))
    do
        echo "$i: ${!i}"
    done
fi
```

# Double Bracket Expressions `[[ ]]`

**Double bracket syntax**: Use `[[ ]]` for conditional testing and pattern matching.

- Must have spaces inside the brackets and around operators
- Returns exit status `0` (true) or `1` (false) based on the test result

## String comparison operators

**String comparison operators**: Compare strings using various operators within `[[ ]]`.

- `==` (equal): Tests if two strings are identical
- `!=` (not equal): Tests if two strings are different
- `<` (lexicographically less): String comparison in alphabetical order
- `>` (lexicographically greater): String comparison in alphabetical order

## Numeric comparison operators

**Numeric comparison operators**: Compare numbers using specific numeric operators.

- `-eq` (equal): Numeric equality comparison
- `-ne` (not equal): Numeric inequality comparison
- `-lt` (less than): Numeric less than comparison
- `-le` (less than or equal): Numeric less than or equal comparison
- `-gt` (greater than): Numeric greater than comparison
- `-ge` (greater than or equal): Numeric greater than or equal comparison

## Logical operators

**Logical operators**: Combine multiple conditions using logical operators.

- `&&` (and): Both conditions must be true
- `||` (or): At least one condition must be true
- `!` (not): Negates the condition (makes true false, false true)

## File test operators

**File test operators**: Test file properties and existence.

- `-e` file: True if file exists
- `-f` file: True if file exists and is a regular file
- `-d` file: True if file exists and is a directory
- `-r` file: True if file exists and is readable
- `-w` file: True if file exists and is writable
- `-x` file: True if file exists and is executable
- `-s` file: True if file exists and has size greater than zero

## Pattern matching with `=~`

**Pattern matching with `=~`**: Use regular expressions for advanced pattern matching.

- `=~` operator enables regex pattern matching
- Pattern should not be quoted when using regex metacharacters
- Supports full regular expression syntax
- Case-sensitive by default

## Variable existence testing

**Variable existence testing**: Check if variables are set or empty.

- Test if variable is empty: `[[ ! $variable ]]`

# Double Parentheses Expressions `(( ))`

## Arithmetic evaluation

**Arithmetic evaluation**: Use `(( ))` for mathematical calculations and numeric comparisons.

- Evaluates arithmetic expressions using C-style syntax
- Variables don't need `$` prefix inside double parentheses
- Returns exit status `0` if result is non-zero, `1` if result is zero
- Supports all standard arithmetic operators

## Arithmetic operators

**Arithmetic operators**: Mathematical operators available in `(( ))`.

- `+` (addition): Add two numbers
- `-` (subtraction): Subtract second number from first
- `*` (multiplication): Multiply two numbers
- `/` (division): Divide first number by second (integer division)
- `%` (modulo): Remainder after division
- `**` (exponentiation): Raise first number to power of second

## Assignment operators

**Assignment operators**: Modify variables using arithmetic assignment operators.

- `=` (assignment): Assign value to variable
- `+=` (add and assign): Add value to variable
- `-=` (subtract and assign): Subtract value from variable
- `*=` (multiply and assign): Multiply variable by value
- `/=` (divide and assign): Divide variable by value
- `%=` (modulo and assign): Set variable to remainder

## Increment and decrement operators

**Increment and decrement operators**: Modify variables by one.

- `++variable` (pre-increment): Increment before use
- `variable++` (post-increment): Increment after use
- `--variable` (pre-decrement): Decrement before use
- `variable--` (post-decrement): Decrement after use

## Comparison operators

**Comparison operators**: Compare numbers using arithmetic comparison.

- `==` (equal): Numbers are equal
- `!=` (not equal): Numbers are not equal
- `<` (less than): First number is less than second
- `<=` (less than or equal): First number is less than or equal to second
- `>` (greater than): First number is greater than second
- `>=` (greater than or equal): First number is greater than or equal to second

## Logical operators

**Logical operators**: Combine arithmetic conditions.

- `&&` (and): Both conditions must be true
- `||` (or): At least one condition must be true
- `!` (not): Negates the condition

## Bitwise operators

**Bitwise operators**: Perform bit-level operations on integers.

- `&` (bitwise AND): AND operation on each bit
- `|` (bitwise OR): OR operation on each bit
- `^` (bitwise XOR): XOR operation on each bit
- `~` (bitwise NOT): Invert all bits
- `<<` (left shift): Shift bits to the left
- `>>` (right shift): Shift bits to the right

## Conditional (ternary) operator

**Conditional (ternary) operator**: Use `condition ? true_value : false_value` syntax.

- Provides a concise way to assign values based on conditions
- Similar to the ternary operator in C-style languages
- Evaluates condition and returns one of two values

## Command substitution with arithmetic

**Command substitution with arithmetic**: Use `$(( ))` to capture arithmetic results.

- Returns the result of the arithmetic expression as a string
- Can be used in assignments or command arguments
- Useful for calculations that need to be used elsewhere

# Control Flow and Conditionals

## Conditional statements

**Conditional statements**: Use `if` statements to execute code based on conditions.

- Basic syntax: `if [[ CONDITION ]] then STATEMENTS fi`
- Full syntax: `if [[ CONDITION ]] then STATEMENTS elif [[ CONDITION ]] then STATEMENTS else STATEMENTS fi`
- Can use both `[[ ]]` and `(( ))` expressions for different types of conditions
- `elif` (else if): Optional, can be repeated multiple times to test additional conditions in sequence
- `else`: Optional, executes when all previous conditions are false
- Can mix double parentheses `(( ... ))` and double brackets `[[ ... ]]` in same conditional chain

# Command Execution and Process Control

## Command separation

**Command separation**: Use semicolon (`;`) to run multiple commands on a single line.

- Commands execute sequentially from left to right
- Each command's exit status can be checked individually

## Exit status

**Exit status**: Every command has an exit status that indicates success or failure.

- Access exit status of the last command with `$?`
- Exit status `0` means success (true/no errors)
- Any non-zero exit status means failure (false/errors occurred)
- Common error codes: `127` (command not found), `1` (general error)

```bash
echo $?
[[ 4 -le 5 ]]; echo $?
ls; echo $?
bad_command; echo $?

: '
0
0
{list of files}
0
script.sh: line 6: bad_command: command not found
127
'
```

## Subshells and command substitution

**Subshells and command substitution**: Different uses of parentheses for execution contexts.

- Single parentheses `( ... )` create a subshell
- `$( ... )` performs command substitution
- Subshells run in separate environments and don't affect parent shell variables

```bash
( cd ~/.config; echo "Current dir: $(pwd)" )

current_date=$(date)
file_count=$(ls -1 | wc -l | tr -d '[:blank:]')

echo "Today is $current_date"
echo "Found $file_count files"

: '
Current dir: /Users/tamasm/.config
Today is Sun Nov 22 19:15:27 CET 2026
Found 5 files
'
```

## Sleep command

**Sleep command**: Pause script execution for a specified number of seconds.

- Useful for creating delays in scripts
- Can be used with decimal values for subsecond delays

```bash
sleep 3
sleep 0.5
sleep 1
```

```bash
echo Starting in...
sleep 1
echo 3
sleep 1
echo 2
sleep 1
echo 1
sleep 1
echo START
```

# Loops

## While loops

**While loops**: Execute code repeatedly while a condition is true.

- Syntax: `while [[ CONDITION ]] do STATEMENTS done`

```bash
I=5
while [[ $I -ge 0 ]]
do
    echo $I
    (( I-- ))
    sleep 1
done
```

## Until loops

**Until loops**: Execute code repeatedly until a condition becomes true.

- Syntax: `until [[ CONDITION ]] do STATEMENTS done`

```bash
until [[ $QUESTION =~ \?$ ]]
do
    echo "Please enter a question ending with ?"
    read QUESTION
done
```

## For loops

**For loops**: Iterate through arrays or lists using `for` loops with `do` and `done` to define the loop's logical block.

```bash
#!/bin/bash

# FIRST
NAMES=("Tamas" "Anna" "Muci" "Ocsi")

for name in ${NAMES[@]}
do
    echo $name
done

# SECOND
for ((i = 1; i < 5; i++))
do
    echo "Number: $i"
done

# THIRD
for i in {1..5}
do
    echo "Count: $i"
done

```

# Arrays

**Arrays**: Store multiple values in a single variable.

- Create arrays with parentheses: `ARRAY=("value1" "value2" "value3")`
- Access elements by index: `${ARRAY[0]}`, `${ARRAY[1]}`
- Access all elements: `${ARRAY[@]}` or `${ARRAY[*]}`
- Array indexing starts at 0

```bash
RESPONSES=("Yes" "No" "Maybe" "Ask again later")
echo ${RESPONSES[0]}     # Yes
echo ${RESPONSES[1]}     # No
echo ${RESPONSES[5]}     # Index 5 doesn't exist; empty string
echo ${RESPONSES[@]}     # Yes No Maybe Ask again later
echo ${RESPONSES[*]}     # Yes No Maybe Ask again later
```

## Array expansion

**Array expansion**: Use `"${array_name[@]}"`, `${array_name[@]}` syntax to expand an array into individual elements.

```bash
NAMES=("Tamas" "Anna" "Muci" "Ocsi")

for name in ${NAMES[@]}
do
    echo $name
done
```

## Array inspection with `declare`

**Array inspection with declare**: Use `declare -p` to view array details.

- Shows the array type with `-a` flag
- Displays all array elements and their structure

```bash
ARR=("a" "b" "c")
declare -p ARR
# declare -a ARR='([0]="a" [1]="b" [2]="c")'
```

# Functions

**Functions**: Create reusable blocks of code.

- Define with `FUNCTION_NAME() { STATEMENTS }`
- Call by using the function name
Can accept arguments accessible as `$1`, `$2`, etc.

## Function arguments

**Function arguments**: Functions can accept arguments just like scripts.

- Arguments are passed when calling the function
- Access arguments inside function using `$1`, `$2`, etc.
- Use conditional logic to handle different arguments

```bash
# $# contains the number of args
MY_FUNCTION() {
    if [[ $# -eq 0 ]]; then
        echo "This function needs arguments"
    else
        echo $@
    fi
}

MY_FUNCTION
MY_FUNCTION hello
MY_FUNCTION hello again
```

# Random Numbers and Mathematical Operations
