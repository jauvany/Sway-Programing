# Prompt: You’re a seasoned blockchain developer with over 15 years of experience in creating smart contracts on various platforms, including Sway. You have a deep understanding of the Sway programming language and possess the ability to break down complex concepts into simple, digestible exercises for new programmers. 

Your task is to create a Sway programming exercise focused on writing a simple Sway smart contract. This exercise should not exceed 10 lines of code, ensuring clarity and conciseness while still being educational.

Please keep in mind the following details:  
- The exercise should introduce the core concepts of Sway, including variables, functions, and basic control flow.  
- The focus should be on practical application, allowing learners to see immediate results after implementing the code.  
- Provide clear instructions on what the smart contract should accomplish, along with any constraints or guidelines to follow.

Here’s how I would like the exercise to be structured:  
1. A brief introduction explaining the purpose of the contract.  
2. The expected functionality of the contract, including any variables that need to be defined.  
3. Sample output that shows what a successful execution of this contract would look like.

### Sway Programming Exercise: Writing a Simple Smart Contract

#### 1. Introduction:
In this exercise, you will write a basic Sway smart contract that demonstrates variable declaration, a simple function, and conditional logic. The goal is to introduce you to core Sway concepts while creating a practical, minimal contract.

#### 2. Expected Functionality:
- The contract will have a state variable to store an integer.
- There will be a function `set_number` to assign a value to the variable.
- Another function, `is_even`, will return a boolean indicating whether the stored number is even or odd.

#### 3. Code (Sway Smart Contract):
```sway
contract;

storage {
    number: u64 = 0,
}

abi SimpleContract {
    fn set_number(new_number: u64);
    fn is_even() -> bool;
}

impl SimpleContract for Contract {
    fn set_number(new_number: u64) {
        storage.number = new_number;
    }

    fn is_even() -> bool {
        storage.number % 2 == 0
    }
}
```

#### 4. Sample Output:
- **Input**: `set_number(4)`  
- **Output**: `is_even()` returns `true` (since 4 is even).
  
- **Input**: `set_number(3)`  
- **Output**: `is_even()` returns `false` (since 3 is odd).

#### Constraints and Guidelines:
- The `number` is stored in the contract’s state.
- You can modify the stored number using the `set_number` function.
- The `is_even` function performs a basic modulo operation to check if the number is even or odd.

This exercise introduces variable management, function creation, and conditional logic in Sway, while ensuring immediate feedback with practical applications.

# White Rabbit Response 

You’re a seasoned blockchain developer with over 15 years of experience in creating smart contracts on various platforms, including Sway. You have a deep understanding of the Sway programming language and possess the ability to break down complex concepts into simple, digestible exercises for new programmers. 

Your task is to create a Sway programming exercise focused on writing a simple Sway smart contract. This exercise should not exceed 10 lines of code, ensuring clarity and conciseness while still being educational.

Please keep in mind the following details:  
- The exercise should introduce the core concepts of Sway, including variables, functions, and basic control flow.  
- The focus should be on practical application, allowing learners to see immediate results after implementing the code.  
- Provide clear instructions on what the smart contract should accomplish, along with any constraints or guidelines to follow.

Here’s how I would like the exercise to be structured:  
1. A brief introduction explaining the purpose of the contract.  
2. The expected functionality of the contract, including any variables that need to be defined.  
3. Sample output that shows what a successful execution of this contract would look like.

Here's an example Sway programming exercise that focuses on writing a simple smart contract:

```sway
// 1. Brief Introduction
// This contract allows users to store and retrieve a value.

// 2. Expected Functionality
// - Define a variable to store the value.
// - Create a function to store the value.
// - Create a function to retrieve the value.

// 3. Sample Output
// When the contract is executed successfully, it should print:
// "Value stored: 42"
// "Retrieved value: 42"

#[contract]
mod my_contract {
    use super::*;

    // Define the variable to store the value
    #[storage(default)]
    pub let stored_value: u64 = 0;

    // Function to store a value
    #[mut]
    pub fn store_value(value: u64) {
        stored_value = value;
    }

    // Function to retrieve the value
    pub fn retrieve_value() -> u64 {
        stored_value
    }

    // Test the contract
    #[test]
    fn test() {
        let _ = store_value(42);
        assert_eq!(retrieve_value(), 42);
    }
}
```

In this exercise:
- The contract introduces the purpose and explains the expected functionality.
- The `stored_value` variable is defined to store the value.
- Two functions, `store_value` and `retrieve_value`, are created to set and retrieve the value, respectively.
- The `test` function demonstrates how to test the contract and ensures that the value is correctly stored and retrieved.
- The expected output is provided as comments in the code.

This exercise is concise and focused on the core concepts of Sway, such as variables, functions, and basic control flow. It allows learners to see immediate results after implementing the code and understand how to store and retrieve values in a smart contract.
