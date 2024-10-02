Here are 20 exercises to help you learn to code smart contracts in Sway, along with explanations of their solutions:

### Exercise 1: Hello World Contract
**Task:** Create a simple contract that returns "Hello, World!" when called.

**Solution:**
```sway
contract HelloWorld {
    public fn say_hello() -> String {
        return "Hello, World!";
    }
}
```
*Explanation:* This contract defines a public function `say_hello` that returns a string.

### Exercise 2: Basic Storage
**Task:** Create a contract that stores and retrieves a number.

**Solution:**
```sway
contract Storage {
    private number: u32;

    public fn set_number(value: u32) {
        self.number = value;
    }

    public fn get_number() -> u32 {
        return self.number;
    }
}
```
*Explanation:* This contract has a private variable `number`. The `set_number` function sets its value, and `get_number` retrieves it.

### Exercise 3: Simple Counter
**Task:** Implement a counter that can be incremented.

**Solution:**
```sway
contract Counter {
    private count: u32;

    public fn increment() {
        self.count += 1;
    }

    public fn get_count() -> u32 {
        return self.count;
    }
}
```
*Explanation:* The contract has a private counter `count`. The `increment` function increases it by 1.

### Exercise 4: Event Emission
**Task:** Emit an event when a value is set.

**Solution:**
```sway
contract EventExample {
    event ValueSet(value: u32);

    public fn set_value(value: u32) {
        emit ValueSet(value);
    }
}
```
*Explanation:* This contract defines an event `ValueSet`. The `set_value` function emits the event when a value is set.

### Exercise 5: Basic Math Operations
**Task:** Create a contract that performs basic arithmetic operations.

**Solution:**
```sway
contract BasicMath {
    public fn add(a: u32, b: u32) -> u32 {
        return a + b;
    }

    public fn subtract(a: u32, b: u32) -> u32 {
        return a - b;
    }
}
```
*Explanation:* The contract contains functions for addition and subtraction, returning the result of the operations.

### Exercise 6: Conditional Logic
**Task:** Implement a function that checks if a number is even or odd.

**Solution:**
```sway
contract EvenOdd {
    public fn is_even(n: u32) -> bool {
        return n % 2 == 0;
    }
}
```
*Explanation:* The function `is_even` uses the modulus operator to check if a number is even.

### Exercise 7: String Manipulation
**Task:** Create a contract that concatenates two strings.

**Solution:**
```sway
contract StringManipulator {
    public fn concatenate(str1: String, str2: String) -> String {
        return str1 + str2;
    }
}
```
*Explanation:* This function uses the `+` operator to concatenate two strings and return the result.

### Exercise 8: Basic Voting System
**Task:** Implement a simple voting system where users can vote for candidates.

**Solution:**
```sway
contract Voting {
    struct Candidate {
        name: String,
        votes: u32,
    }

    private candidates: Vec<Candidate>;

    public fn add_candidate(name: String) {
        self.candidates.push(Candidate { name, votes: 0 });
    }

    public fn vote(index: usize) {
        self.candidates[index].votes += 1;
    }

    public fn get_votes(index: usize) -> u32 {
        return self.candidates[index].votes;
    }
}
```
*Explanation:* This contract uses a `Candidate` struct and allows adding candidates, voting, and retrieving vote counts.

### Exercise 9: Access Control
**Task:** Implement a contract with access control for administrative actions.

**Solution:**
```sway
contract AccessControl {
    private admin: Address;

    public fn new(admin: Address) {
        self.admin = admin;
    }

    public fn only_admin(fn: fn()) {
        require(msg.sender == self.admin, "Not authorized");
        fn();
    }
}
```
*Explanation:* The contract checks if the caller is the admin before executing certain functions.

### Exercise 10: Array Operations
**Task:** Create a contract that manages a list of items.

**Solution:**
```sway
contract ItemList {
    private items: Vec<String>;

    public fn add_item(item: String) {
        self.items.push(item);
    }

    public fn get_items() -> Vec<String> {
        return self.items;
    }
}
```
*Explanation:* The contract maintains a dynamic array of items and provides functions to add and retrieve them.

### Exercise 11: Structs and Functions
**Task:** Create a contract that uses structs to represent a user profile.

**Solution:**
```sway
contract UserProfile {
    struct Profile {
        username: String,
        age: u32,
    }

    private profiles: Vec<Profile>;

    public fn add_profile(username: String, age: u32) {
        self.profiles.push(Profile { username, age });
    }

    public fn get_profile(index: usize) -> Profile {
        return self.profiles[index];
    }
}
```
*Explanation:* The contract uses a `Profile` struct and provides functions to add and retrieve user profiles.

### Exercise 12: Error Handling
**Task:** Implement error handling in a function that retrieves a candidate's votes.

**Solution:**
```sway
contract SafeVoting {
    struct Candidate {
        name: String,
        votes: u32,
    }

    private candidates: Vec<Candidate>;

    public fn get_votes(index: usize) -> Result<u32, String> {
        if index >= self.candidates.len() {
            return Err("Candidate index out of range".to_string());
        }
        Ok(self.candidates[index].votes)
    }
}
```
*Explanation:* The function uses a `Result` type to handle errors gracefully, returning an error message if the index is out of bounds.

### Exercise 13: Mapping Data
**Task:** Create a contract that maps addresses to their balances.

**Solution:**
```sway
contract BalanceTracker {
    private balances: Map<Address, u32>;

    public fn deposit(amount: u32) {
        let sender = msg.sender;
        self.balances.insert(sender, self.balances.get(sender).unwrap_or(0) + amount);
    }

    public fn get_balance(address: Address) -> u32 {
        return self.balances.get(address).unwrap_or(0);
    }
}
```
*Explanation:* This contract uses a mapping to track user balances and provides functions to deposit and check balances.

### Exercise 14: Inheritance
**Task:** Create a contract that inherits from another contract.

**Solution:**
```sway
contract Base {
    public fn greet() -> String {
        return "Hello from Base";
    }
}

contract Derived: Base {
    public fn greet_derived() -> String {
        return "Hello from Derived";
    }
}
```
*Explanation:* The `Derived` contract inherits from `Base` and can access its methods.

### Exercise 15: Interface Implementation
**Task:** Create an interface and implement it in a contract.

**Solution:**
```sway
interface Greeter {
    fn greet() -> String;
}

contract SimpleGreeter: Greeter {
    public fn greet() -> String {
        return "Hello, Interface!";
    }
}
```
*Explanation:* The contract implements the `Greeter` interface by defining the `greet` function.

### Exercise 16: Token Contract
**Task:** Implement a simple token contract with transfer functionality.

**Solution:**
```sway
contract SimpleToken {
    struct Token {
        balance: u32,
    }

    private balances: Map<Address, Token>;

    public fn transfer(to: Address, amount: u32) -> bool {
        let sender = msg.sender;
        if self.balances.get(sender).unwrap_or(0) < amount {
            return false; // Insufficient balance
        }
        self.balances.get_mut(sender).unwrap().balance -= amount;
        self.balances.get_mut(to).unwrap().balance += amount;
        return true;
    }
}
```
*Explanation:* This contract allows users to transfer tokens, checking for sufficient balance before proceeding.

### Exercise 17: Multi-signature Wallet
**Task:** Create a contract that requires multiple signatures to execute a transaction.

**Solution:**
```sway
contract MultiSigWallet {
    private owners: Vec<Address>;
    private required_signatures: u32;

    public fn add_owner(owner: Address) {
        self.owners.push(owner);
    }

    public fn execute_transaction(transaction: Transaction) {
        let signature_count = count_signatures(transaction);
        require(signature_count >= self.required_signatures, "Not enough signatures");
        // Execute transaction
    }
}
```
*Explanation:* This contract requires a certain number of signatures to execute a transaction.

### Exercise 18: Time-based Access Control
**Task:** Implement a contract that restricts access based on time.

**Solution:**
```sway
contract TimeRestricted {
    private access_start: u64;
    private access_end: u64;

    public fn set_access_times(start: u64, end: u64) {
        self.access_start = start;
        self.access_end = end;
    }

    public fn is_accessible() -> bool {
        let current_time = get_current_time();
        return current_time >= self.access_start && current_time

Here are 20 exercises to help you learn to code smart contracts in Sway, along with explanations of their solutions:

### Exercise 1: Hello World Contract
**Task:** Create a simple contract that returns "Hello, World!" when called.

**Solution:**
```sway
contract HelloWorld {
    public fn say_hello() -> String {
        return "Hello, World!";
    }
}
```
*Explanation:* This contract defines a public function `say_hello` that returns a string.

### Exercise 2: Basic Storage
**Task:** Create a contract that stores and retrieves a number.

**Solution:**
```sway
contract Storage {
    private number: u32;

    public fn set_number(value: u32) {
        self.number = value;
    }

    public fn get_number() -> u32 {
        return self.number;
    }
}
```
*Explanation:* This contract has a private variable `number`. The `set_number` function sets its value, and `get_number` retrieves it.

### Exercise 3: Simple Counter
**Task:** Implement a counter that can be incremented.

**Solution:**
```sway
contract Counter {
    private count: u32;

    public fn increment() {
        self.count += 1;
    }

    public fn get_count() -> u32 {
        return self.count;
    }
}
```
*Explanation:* The contract has a private counter `count`. The `increment` function increases it by 1.

### Exercise 4: Event Emission
**Task:** Emit an event when a value is set.

**Solution:**
```sway
contract EventExample {
    event ValueSet(value: u32);

    public fn set_value(value: u32) {
        emit ValueSet(value);
    }
}
```
*Explanation:* This contract defines an event `ValueSet`. The `set_value` function emits the event when a value is set.

### Exercise 5: Basic Math Operations
**Task:** Create a contract that performs basic arithmetic operations.

**Solution:**
```sway
contract BasicMath {
    public fn add(a: u32, b: u32) -> u32 {
        return a + b;
    }

    public fn subtract(a: u32, b: u32) -> u32 {
        return a - b;
    }
}
```
*Explanation:* The contract contains functions for addition and subtraction, returning the result of the operations.

### Exercise 6: Conditional Logic
**Task:** Implement a function that checks if a number is even or odd.

**Solution:**
```sway
contract EvenOdd {
    public fn is_even(n: u32) -> bool {
        return n % 2 == 0;
    }
}
```
*Explanation:* The function `is_even` uses the modulus operator to check if a number is even.

### Exercise 7: String Manipulation
**Task:** Create a contract that concatenates two strings.

**Solution:**
```sway
contract StringManipulator {
    public fn concatenate(str1: String, str2: String) -> String {
        return str1 + str2;
    }
}
```
*Explanation:* This function uses the `+` operator to concatenate two strings and return the result.

### Exercise 8: Basic Voting System
**Task:** Implement a simple voting system where users can vote for candidates.

**Solution:**
```sway
contract Voting {
    struct Candidate {
        name: String,
        votes: u32,
    }

    private candidates: Vec<Candidate>;

    public fn add_candidate(name: String) {
        self.candidates.push(Candidate { name, votes: 0 });
    }

    public fn vote(index: usize) {
        self.candidates[index].votes += 1;
    }

    public fn get_votes(index: usize) -> u32 {
        return self.candidates[index].votes;
    }
}
```
*Explanation:* This contract uses a `Candidate` struct and allows adding candidates, voting, and retrieving vote counts.

### Exercise 9: Access Control
**Task:** Implement a contract with access control for administrative actions.

**Solution:**
```sway
contract AccessControl {
    private admin: Address;

    public fn new(admin: Address) {
        self.admin = admin;
    }

    public fn only_admin(fn: fn()) {
        require(msg.sender == self.admin, "Not authorized");
        fn();
    }
}
```
*Explanation:* The contract checks if the caller is the admin before executing certain functions.

### Exercise 10: Array Operations
**Task:** Create a contract that manages a list of items.

**Solution:**
```sway
contract ItemList {
    private items: Vec<String>;

    public fn add_item(item: String) {
        self.items.push(item);
    }

    public fn get_items() -> Vec<String> {
        return self.items;
    }
}
```
*Explanation:* The contract maintains a dynamic array of items and provides functions to add and retrieve them.

### Exercise 11: Structs and Functions
**Task:** Create a contract that uses structs to represent a user profile.

**Solution:**
```sway
contract UserProfile {
    struct Profile {
        username: String,
        age: u32,
    }

    private profiles: Vec<Profile>;

    public fn add_profile(username: String, age: u32) {
        self.profiles.push(Profile { username, age });
    }

    public fn get_profile(index: usize) -> Profile {
        return self.profiles[index];
    }
}
```
*Explanation:* The contract uses a `Profile` struct and provides functions to add and retrieve user profiles.

### Exercise 12: Error Handling
**Task:** Implement error handling in a function that retrieves a candidate's votes.

**Solution:**
```sway
contract SafeVoting {
    struct Candidate {
        name: String,
        votes: u32,
    }

    private candidates: Vec<Candidate>;

    public fn get_votes(index: usize) -> Result<u32, String> {
        if index >= self.candidates.len() {
            return Err("Candidate index out of range".to_string());
        }
        Ok(self.candidates[index].votes)
    }
}
```
*Explanation:* The function uses a `Result` type to handle errors gracefully, returning an error message if the index is out of bounds.

### Exercise 13: Mapping Data
**Task:** Create a contract that maps addresses to their balances.

**Solution:**
```sway
contract BalanceTracker {
    private balances: Map<Address, u32>;

    public fn deposit(amount: u32) {
        let sender = msg.sender;
        self.balances.insert(sender, self.balances.get(sender).unwrap_or(0) + amount);
    }

    public fn get_balance(address: Address) -> u32 {
        return self.balances.get(address).unwrap_or(0);
    }
}
```
*Explanation:* This contract uses a mapping to track user balances and provides functions to deposit and check balances.

### Exercise 14: Inheritance
**Task:** Create a contract that inherits from another contract.

**Solution:**
```sway
contract Base {
    public fn greet() -> String {
        return "Hello from Base";
    }
}

contract Derived: Base {
    public fn greet_derived() -> String {
        return "Hello from Derived";
    }
}
```
*Explanation:* The `Derived` contract inherits from `Base` and can access its methods.

### Exercise 15: Interface Implementation
**Task:** Create an interface and implement it in a contract.

**Solution:**
```sway
interface Greeter {
    fn greet() -> String;
}

contract SimpleGreeter: Greeter {
    public fn greet() -> String {
        return "Hello, Interface!";
    }
}
```
*Explanation:* The contract implements the `Greeter` interface by defining the `greet` function.

### Exercise 16: Token Contract
**Task:** Implement a simple token contract with transfer functionality.

**Solution:**
```sway
contract SimpleToken {
    struct Token {
        balance: u32,
    }

    private balances: Map<Address, Token>;

    public fn transfer(to: Address, amount: u32) -> bool {
        let sender = msg.sender;
        if self.balances.get(sender).unwrap_or(0) < amount {
            return false; // Insufficient balance
        }
        self.balances.get_mut(sender).unwrap().balance -= amount;
        self.balances.get_mut(to).unwrap().balance += amount;
        return true;
    }
}
```
*Explanation:* This contract allows users to transfer tokens, checking for sufficient balance before proceeding.

### Exercise 17: Multi-signature Wallet
**Task:** Create a contract that requires multiple signatures to execute a transaction.

**Solution:**
```sway
contract MultiSigWallet {
    private owners: Vec<Address>;
    private required_signatures: u32;

    public fn add_owner(owner: Address) {
        self.owners.push(owner);
    }

    public fn execute_transaction(transaction: Transaction) {
        let signature_count = count_signatures(transaction);
        require(signature_count >= self.required_signatures, "Not enough signatures");
        // Execute transaction
    }
}
```
*Explanation:* This contract requires a certain number of signatures to execute a transaction.

### Exercise 18: Time-based Access Control
**Task:** Implement a contract that restricts access based on time.

**Solution:**
```sway
contract TimeRestricted {
    private access_start: u64;
    private access_end: u64;

    public fn set_access_times(start: u64, end: u64) {
        self.access_start = start;
        self.access_end = end;
    }

    public fn is_accessible() -> bool {
        let current_time = get_current_time();
        return current_time >= self.access_start && current_time

 <= self.access_end;
    }
}
```
*Explanation:* The contract checks the current time against predefined start and end times to determine access.

### Exercise 19: Upgradeable Contract
**Task:** Create an upgradeable contract using a proxy pattern.

**Solution:**
```sway
contract Proxy {
    private implementation: Address;

    public fn upgrade(new_implementation: Address) {
        self.implementation = new_implementation;
    }

    public fn delegate_call() {
        // Delegate calls to the implementation contract
    }
}
```
*Explanation:* This proxy contract allows for upgrading to a new implementation address, enabling contract upgrades.

### Exercise 20: CRUD Operations
**Task:** Implement a contract that performs basic CRUD operations on user profiles.

**Solution:**
```sway
contract UserProfileManager {
    struct Profile {
        username: String,
        age: u32,
    }

    private profiles: Map<Address, Profile>;

    public fn create_profile(username: String, age: u32) {
        let sender = msg.sender;
        self.profiles.insert(sender, Profile { username, age });
    }

    public fn read_profile(address: Address) -> Profile {
        return self.profiles.get(address).unwrap();
    }

    public fn update_profile(username: String, age: u32) {
        let sender = msg.sender;
        self.profiles.get_mut(sender).unwrap().username = username;
        self.profiles.get_mut(sender).unwrap().age = age;
    }

    public fn delete_profile() {
        let sender = msg.sender;
        self.profiles.remove(sender);
    }
}
```
*Explanation:* This contract allows creating, reading, updating, and deleting user profiles using a mapping.

### Summary
These exercises will give you a well-rounded understanding of Sway programming language and smart contract development, covering fundamental concepts such as storage, data types, access control, events, and error handling.
