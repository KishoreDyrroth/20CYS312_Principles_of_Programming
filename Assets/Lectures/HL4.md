# 20CYS312 - Principles of Programming Languages
![](https://img.shields.io/badge/Batch-21CYS-lightgreen) ![](https://img.shields.io/badge/UG-blue) ![](https://img.shields.io/badge/Subject-PPL-blue) <br/>
![](https://img.shields.io/badge/Lecture-2-orange) ![](https://img.shields.io/badge/Practical-3-orange) ![](https://img.shields.io/badge/Credits-3-orange)

## Lecture 4 - Introduction to Functional Programming (Continued)
![](https://img.shields.io/badge/-07th_Feb-orange)

### Currying
**Currying** refers to the technique of transforming a function that takes multiple arguments into a sequence of functions, each taking a single argument. 

**Currying** is the process of transforming a function that takes multiple arguments in a tuple as its argument, into a function that takes just a single argument and returns another function which accepts further arguments, one by one, that the original function would receive in the rest of that tuple.

```
f :: a -> b -> c     -- same as   f :: a -> (b -> c)
```

In simple,

``` f x y ``` is actually processed as ```(f x) y```.

Considering and applying this logic to the below example:

```
rollnumber :: String -> Int -> String -- same as rollnumber :: String -> (Int -> String)
```

```rollnumber prefix num ``` is processed as ``` (rollnumber prefix) num ```

### Parital Applications

Partial application in Haskell refers to the process of applying a function to some, but not all, of its arguments, resulting in a new function that takes fewer arguments than the original. 

```
-- Define a function 'rollnumber' that takes a String and an Int and concatenates them
rollnumber :: String -> Int -> String
rollnumber prefix num = prefix ++ show num

-- Define the main function, which is the entry point of the program
main :: IO ()
main = do
    -- Create a new function 'rollnumberT' by partially applying 'rollnumber' with the string "CB.EN.U4CYS210"
    let rollnumberT = rollnumber "CB.EN.U4CYS210"
    -- Prompt the user to enter a roll number
    putStrLn "Enter a Roll Number:"
    -- Read a line of input from the user and bind it to the variable 'input'
    input <- getLine
    -- Convert the input string to an Int using 'read', with type annotation to specify the expected type
    let num = read input :: Int
    -- Print a message showing the result of concatenating the user's input number to the provided string
    putStrLn $ "Your Complete Roll Number: " ++ show (rollnumberT num)
```

JavaScript supports **Partial Application** but does not support **Currying**.

```
// Define a function rollNumber that concatenates a string and a number
function rollNumber(prefix, number) {
  return prefix + number;
}

// Partially apply the 'rollNumber' function to create a new function with the prefix "CB.EN.U4CYS210"
const rollNumberCB = rollNumber.bind(null, "CB.EN.U4CYS210");

// Use the partially applied function
const num = 44;
console.log("Your Complete Roll Number: " + rollNumberCB(num));
```

## Home work

Write a Haskell Program with a function **`multiplyBy`** that takes an `Int` and returns a function that multiplies its argument by that integer. 
For example, multiplyBy 5 should return a function that multiplies its argument by 5. Then, use partial application to create a new function **`double`** that doubles its argument, and a new function **`triple`** that triples its argument.
