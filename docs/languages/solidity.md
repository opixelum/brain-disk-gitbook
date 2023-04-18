# Solidity

## Version Pragma

All solidity source code should start with *pragma* keyword, telling the code
which Solidity compiler version should be used.

```sol
pragma solidity >=0.5.0 <0.6.0;
```

## Contracts

Solidity's code is encapsulated in ***contracts***.

```sol
contract HelloWorld {

    // Code goes here

}
```

## Libraries

- Similar to contracts, but **stateless** (no storage, so no state variables);
- Used for **code reuse**;
- Declared with `library` keyword.

```solidity
library StringUtils {
    struct String {
        bytes32 value;
        uint256 length;
    }
    
    function concat(String memory _self, String memory _other) internal pure returns (String memory) {
        String memory result = String({
            value: _self.value,
            length: _self.length
        });
        
        for (uint256 i = 0; i < _other.length; i++) {
            result.value |= bytes32(uint256(_other.value) * (2 ** (8 * (i + _self.length))));
            result.length++;
        }
        
        return result;
    }
}
```

### Deployed libraries

- If a library has at least one ***public*** or ***external*** function, it must
  be **deployed** to the blockchain;
- Function calls from contract to library use the **delegatecall** opcode, which
  means that the **library**'s **code** is **executed** in the **context** of the
  **contract** (execute library's code with contract's storage & state). For 
  instance, it keeps the same `msg.sender` and `msg.value` values;
- Contracts using deployed libraries have a **placeholder** for the **library** 
  **address** in their **bytecode** after compilation. Example of a placeholder:
  `__$30bbc0abd4d6364515865950d3e0d10953$__`;
- To replace the placeholder, deployed libraries must be **linked** to the 
  contract. This process can be done by frameworks like **Truffle**, **Hardhat**
  or **Foundry**, or by using the **solc** compiler. Example of a 
  deployment with linkage using Foundry:

```console
forge create --rpc-url <rpc-url> --private-key <private-key> --libraries <library-path>:<library-name>:<library-address> <contract-path>:<contract-name>
```

### Inlined libraries

- If a library has **no** ***public*** or ***external*** functions, it can be
  **inlined** (included) in the contract's bytecode, meaning that it will not be 
  deployed;
- Function calls from contract to library use the **JUMP** opcode (like normal
  function calls);
- Those libraries are inlined for **efficiency** (cheaper gas fees) &
  **simplicity** (no need to link libraries to contracts).

## Variables data location

- ***storage*** variables are stored permanently on the blockchain. State
variables (variables declared outside of functions) are by default
***storage***. However, those variables are really expensive in gas fees.

- ***memory*** variables are temporary. They're erased after exiting a local
scope (eg: a function). Those are called **local variables**.

- ***calldata*** is similar to ***memory***, but it's only available to
***external*** functions.

```sol
contract MyContract {

    function foo() public {
        // Stored in the blockchain forever
        uint storage permanentUint = 100; 

        // Will be deleted after exiting the function
        uint memory temporaryUint = 100; 
    }

    function bar(string calldata _text) external {
        // Do stuff with _text
    }
}
```

## Types

### Value types

#### Integers

- int/uint: Signed & unsigned integers of 256 bits.
- (u)int8 to (u)int256 in steps of 8 are for specifying the numberof bits to
use.

```sol
uint myUnsignedInteger = 100;
```

#### Addresses

Types holding a 20 byte value (size of an Ethereum address).

- address: for an address that cannot be sent Ether.
- address payable: for an address that can receive Ether.

### Reference types

#### Data location

Every reference type has a data location, either ***calldata***, ***memory*** or
***storage***.

##### Calldata

- Behaves mostly like ***memory***.
- Only valid for parameters of ***external*** functions.
- Non-modifiable variables.

##### Memory

- Not written to the blockchain.
- Must be defined inside a function or as a function parameter.
- Destroyed after exiting the function.
- Local scope only.

##### Storage

- Written to the blockchain (persistent).
- Accessible from anywhere (inside or outside the smart contract).
- Global variables are by default storage variables.
- Incur gas fees.

#### Arrays

There are two types of arrays:

- Fixed:
```sol
uint[2] fixedArray; // Fixed array of 2 unsigned integer elements
```
- Dynamic:
```sol
uint[] dynamicArray; // Array that can keep growing
```

To add an element to an array, we use de method ***push()***:
```sol
uint[] numbers;
numbers.push(5);
numbers.push(10);
numbers.push(15);
// Numbers is now equal to [5, 10, 15]
```

#### Strings

Arbitrary-length UTF-8 data.

```sol
string greeting = "Hello world!";
```

#### Structs

Structs let us create complex data types with multiple properties.

```sol
struct Person {
    uint age;
    string name;
}

Person satoshi = Person(172, "Satoshi");
```

### Mapping types

#### Iterable mappings

A mapping is a key-value store.

```sol
// For a financial app, storing a uint that holds the user's account balance:
mapping (address => uint) public accountBalance
// Or could be used to store / lookup usernames based on userId
mapping (uint => string) userIdToName
```

## Math operations

Same as most of the programming languages:

- Addition: ***x + y***
- Subtraction: ***x - y***
- Multiplication: ***x * y***
- Division: ***x / y***
- Modulus: ***x % y***
- Power: ***x\*\*y***

```sol
uint x = 5 ** 2; // Equal to 5^2 = 25
```

## Conditions

### *if*/*else*

```sol
uint a = 100;

if (a == 100) {
    // Instruction...
} else {
    // Instruction
}
```

### *require()*

Check if condition is true, in order to execute the rest of the code. If not,
it will throw an error, stop executing in the local scope and **refund** the user
the rest of the **gas**.

```sol
function hiVitalik(string memory _name) returns (string memory) {
    // Compares _name & "Vitalik". Throws an error if not true.
    // (Note: Solidity doesn't have native string comparison, so we
    // need to compare their keccak hashes to see if they're equal)
    require(keccak256(abi.encodePacked(_name))
        == keccak256(abi.encodePacked("Vitalik")));
    // If it's true, proceed with the function:
    return "Hi!";
}
```

### *assert()*

Similar to ***require***, but will not refund the user in case of error. It is
typically used when something has gone horribly wrong with the code (like a
***uint*** overflow).

```sol
function add(uint256 a, uint256 b) internal pure returns (uint256) {
    uint256 c = a + b;
    assert(c >= a);
    return c;
}
```

## Loops

- ***for*** loops:

```sol
for (uint i =0; i < 10; i++) {
    // Instructions...
}
```

## Visibility

- ***private*** keyword let a source code element to be callable within
the same contract only.

```sol
uint[] numbers;

function _addToArray(uint _number) private {
  numbers.push(_number);
}
```

- ***public*** keyword let an element of the source code to be callable for
any other contract (functions are public by default).

```sol
Zombie[] public zombies;
```

- ***internal*** keyword is the same as private, except that it's also
accessible to contracts that inherit from this contract. 

```sol
function foo() internal {
    // Instructions...
}
```

- ***external*** keyword is similar to public, except that these functions can
ONLY be called outside the contract — they can't be called by other functions
inside that contract.

```sol
function bar() external {
    // Instructions...
}
```

## Functions

Functions are declared with the *function* keyword:
```
function eatHamburgers(string memory _name, uint _amount) public {
    // Instructions
}
```
Two ways to pass an argument:
- By **value**: original variable value not changed (with *memory* keyword).
- By **reference**: original variable value changed.

*memory* keyword is required for all reference types such as arrays, structs,
mapping & strings.

It's convention (but not required) to start function parameter variable names
with an underscore (_) in order to differentiate them from global variables.

### Return values

To return a value from a function, we need the ***returns*** keyword in the
declaration, specifying the return type. Moreover, we need ***return***
(without the 's') in the function:
```sol
function sayHello() public returns () {
    return "Hello!";
}
```

Note that in Solidity, functions can return multiple values:

```sol
function getKitty(uint256 _id) external view returns (
    bool isGestating,
    bool isReady,
    uint256 cooldownIndex,
    uint256 nextActionAt,
    uint256 siringWithId,
    uint256 birthTime,
    uint256 matronId,
    uint256 sireId,
    uint256 generation,
    uint256 genes
) {
    Kitty storage kit = kitties[_id];

    // if this variable is 0 then it's not gestating
    isGestating = (kit.siringWithId != 0);
    isReady = (kit.cooldownEndBlock <= block.number);
    cooldownIndex = uint256(kit.cooldownIndex);
    nextActionAt = uint256(kit.cooldownEndBlock);
    siringWithId = uint256(kit.siringWithId);
    birthTime = uint256(kit.birthTime);
    matronId = uint256(kit.matronId);
    sireId = uint256(kit.sireId);
    generation = uint256(kit.generation);
    genes = kit.genes;
}
```

In this case, we can handle multiple return values like this:

```sol
function multipleReturns() internal returns(
    uint a,
    uint b,
    uint c
) {
    return (1, 2, 3);
}

function processMultipleReturns() external {
    uint a;
    uint b;
    uint c;
    // This is how you do multiple assignment:
    (a, b, c) = multipleReturns();
}

// Or if we only cared about one of the values:
function getLastReturnValue() external {
    uint c;
    // We can just leave the other fields blank:
    (,,c) = multipleReturns();
}
```

### Function modifiers

- ***view***: specifies that a function is only viewing the data but not
modifying it. 

If a ***view*** function is called **externally** (with the ***external***
visibility keyword), it doesnt' cost any gas. However, an **internally**
***view*** function will still cost gas because the other function creates a
transaction that will need to be verified from every Ethereum node.

```sol
string customGreeting = "'Sup bro!";

function printGreeting(string memory _greeting) view returns (string memory) {
    return _greeting; 
}
```

- ***pure***: specifies that a function is not even accesing any data in the
app:

```sol
function _multiply(uint a, uint b) private pure returns (uint) {
  return a * b;
}
```

- **payable**: allows a function to receive ether:

```sol
contract OnlineStore {
    function buySomething() external payable {
        // Check to make sure 0.001 ether was sent to the function call:
        require(msg.value == 0.001 ether);
        // If so, some logic to transfer the digital item to the caller of the
        // function:
        transferThing(msg.sender);
    }
}
```

- **custom modifiers with *modifier* keyword**: you can create your own
function modifier. It can take parameters.

```sol
// Examples taken from OpenZeppellin's "Ownable" contract
modifier onlyOwner() {
    require(isOwner());
    _;
}

function renounceOwnership() public onlyOwner {
    emit OwnershipTransferred(_owner, address(0));
    owner = address(0);
}


// Example with parameters
modifier olderThan(uint _age, uint _userId) {
  require(age[_userId] >= _age);
  _;
}
```

One of the most common use-cases is to add a quick require check, that will be
executed before a function executes.

The "**_;**" in the ***onlyOwner*** modifier is what tells the code to execute
the function at a given time (in this eg: ***renounceOwnership()***).

### Function overriding

Override a base function by inheriting from a parent contract.

- Base function must be **marked as *virtual***.
- Overriding function must have the **same function signature** as the base
function.
- Overriding function must **specify** which **parent contract** it is
overriding from.

```sol
contract Base1 {
    function foo() virtual public pure returns (string memory) {
        return "Base1";
    }
}

contract Base2 {
    function foo() virtual public pure returns (string memory) {
        return "Base2";
    }
}

contract Child is Base1, Base2 {
    function foo() override(Base1, Base2) pure public returns (string memory) {
        return "Child";
    }
}
```

### Function signature

- **First 4 bytes** of the **keccak-256 hash** of the **concatenation** of the
**function name** & its **ordered list of parameters types**;
- AKA **function selector**.

```sol
function foo(int8 a, uint256 b) public returns (bool) {
    // Function implementation
}

bytes4 functionSignature = bytes4(keccak256("foo(int8,uint256)"));
```

## Type casting

Let us convert between data types:
```sol
uint a = 8;
uint8 b = uint8(a); // A has been converted from uint to uint8
```

## Events

***event*** lets contract to communicate with the front-end, which can listen to it.
```sol
// Declare the event
event IntegersAdded(uint x, uint y, uint result);

function add(uint _x, uint _y) public returns (uint) {
  uint result = _x + _y;
  // Fire an event to let the app know the function was called:
  emit IntegersAdded(_x, _y, result);
  return result;
}
```

On the front-end, we can use it like this:
```sol
YourContract.IntegersAdded(function(error, result) {
  // Do something with result
})
```

By the way, there are JavaScript frameworks that help us for working with
contracts on the front-end, such as **web3.js** or **ether.js**.

## Inheritance

Inheritance let our code to be more manageable and organize. We can create
"sub"-contracts which have access to the inherited contract's content.

```sol
contract Doge {
    function catchphrase() public returns (string memory) {
        return "So Wow CryptoDoge";
    }
}

contract BabyDoge is Doge {
    function anotherCatchphrase() public returns (string memory) {
        return "Such Moon BabyDoge";
    }
}
```

In this exemple, ***BabyDoge*** inherits from ***Doge***, so if we use it, we
will have access to both ***catchphrase()*** and ***anotherCatchphrase()***. We
can also inherit from multiple contracts at once:

```sol
contract SatoshiNakamoto is NickSzabo, HalFinney {
  // Omg, the secrets of the universe revealed!
}
```

## Import

For a better codebase structure, we can divide our Solidity code in multiple
files. In order to link a file with another, we use the ***import*** keyword.

```sol
import "./someothercontract.sol";

contract newContract is SomeOtherContract {

}
```

## Interfaces

In order to interact with external contracts, we need to define an interface,
which is just a contract inside our code, with the functions we want by writing
their declaration only, and a quick setup:

External contract:
```sol
contract LuckyNumber {
    mapping(address => uint) numbers;

    function setNum(uint _num) public {
        numbers[msg.sender] = _num;
    }

    function getNum(address _myAddress) public view returns (uint) {
        return numbers[_myAddress];
    }
}
```

Our code:
```sol
contract NumberInterface {
    // We want to use "getNum"
    function getNum(address _myAddress) public view returns (uint);
}

contract MyContract {
    address NumberInterfaceAddress = 0xab38... 
    // ^ The address of the FavoriteNumber contract on Ethereum
    NumberInterface numberContract = NumberInterface(NumberInterfaceAddress);
    // Now `numberContract` is pointing to the other contract

    function someFunction() public {
      // Now we can call `getNum` from that contract:
      uint num = numberContract.getNum(msg.sender);
      // ...and do something with `num` here
    }
}
```

## Comments

Comments in Solidity are just like JS or C ones. We can use ***//*** for single
line comments or ***/\* \*/*** for multi line comments.

However, Solidity use a special form of comments to provide rich documentation,
NatSpec, which was inspired by Doxygen. To differenciate those type of comments
from the normal ones, we use ***///***.

```sol
/// @title A contract for basic math operations
/// @author H4XF13LD MORRIS 💯💯😎💯💯
/// @notice For now, this contract just adds a multiply function
contract Math {
  /// @notice Multiplies 2 numbers together
  /// @param x the first uint.
  /// @param y the second uint.
  /// @return z the product of (x * y)
  /// @dev This function does not currently check for overflows
  function multiply(uint x, uint y) returns (uint z) {
    // This is just a normal comment, and won't get picked up by natspec
    z = x * y;
  }
}
```

### Tags

| Tag               | Description                                                                            | Context                                                              |
|-------------------|----------------------------------------------------------------------------------------|----------------------------------------------------------------------|
| ***@title***      | A title that should describe the contract/interface                                    | Contract, library, interface                                         |
| ***@author***     | The name of the author                                                                 | Contract, library, interface                                         |
| ***@notice***     | Explain to an end user what this does                                                  | Contract, library, interface, function, public state variable, event |
| ***@dev***        | Explain to a developer any extra details                                               | Contract, library, interface, function, state variable, event        |
| ***@param***      | Documents a parameter just like in Doxygen (must be followed by parameter name)        | Function, event                                                      |
| ***@return***     | Documents the return variables of a contract’s function                                | Function, public state variable                                      |
| ***@inheritdoc*** | Copies all missing tags from the base function (must be followed by the contract name) | Function, public state variable                                      |
| ***@custom:...*** | Custom tag, semantics is application-defined                                           | Everywhere                                                           |

## Notable variables

### msg.sender (address)

Global variable available to all functions. It refers to the address of the
person (or smart contract) who called the current function.

```sol
mapping (address => uint) favoriteNumber;

function setMyNumber(uint _myNumber) public {
  // Update `favoriteNumber` mapping to store `_myNumber` under `msg.sender`
  favoriteNumber[msg.sender] = _myNumber;
  // ^ The syntax for storing data in a mapping is just like with arrays
}

function whatIsMyNumber() public view returns (uint) {
  // Retrieve the value stored in the sender's address
  // Will be `0` if the sender hasn't called `setMyNumber` yet
  return favoriteNumber[msg.sender];
}
```

### block.timestamp (uint256)

Returns current timestamp of the latest block (number of seconds that have
passed sicne January 1st 1970).

Solidity also has time units (***seconds, minutes, hours, days, weeks*** &
***years***). Each of them is converted to seconds (1 ***minutes*** = 60
***seconds***, ...)

```sol
uint32 nowPastFive = block.timestamp + 5 minutes;
```

## Notable functions

### keccak256(bytes *memory*) returns (bytes32)

Returns a 32 byte hash of *memory*.

```sol
// Hashing "aaaab' string:

keccak256(abi.encodePacked("aaaab"));

// Returns 6e91ec6b618bb462a4a6ee5aa2cb0e9cf30f7a052bb467b0ba58b8748c00d2e5
```
Note that our string needs to be converted to binary. That's why we use the
*abi.encodePacked()* method.

### *payable address*.transfer(*value*)

Transfers eth stored in the contract (*value*) to a **payable** address
(*object*).

```sol
address payable target = payable(msg.sender);
target.transfer(1 ether);
```

## Notable contracts

### Ownable

OpenZeppelin contract which provides a basic access control mechanism, where
there is an account (an owner) that can be granted exclusive access to specific
functions.

[Documentation](https://docs.openzeppelin.com/contracts/4.x/api/access#Ownable)

## Notable libraries

### SafeMath

OpenZeppelin library which provides mathematical functions that protect your
contract from overflows and underflows.

[Documentation](https://docs.openzeppelin.com/contracts/4.x/utilities#math)

## Optimization

In order to execute a function, users have to pay gas fees. The gas cost is
based on how much computing resources will be required to perform an operation.
That's why code optimization is really important in Ethereum.

Gas has been made in order to avoid people clogging up the network with
infinite loops, or hogging all the network resources with really intensive computation. 

### Struct packing for gas saving

Normally, Solidity reserves 256 bits of storage regardless of the type size,
except inside structs: use smallest sized types possible and cluster identical
data types together:

```sol
// Bad: no optimization
struct BadStruct {
  uint a;
  uint b;
  uint c;
}

// Better: small uint
struct BetterStruct {
  uint32 a;
  uint c;
  uint32 b;
}

// Best: small uint size & uint32 clustered together
struct BestStruct {
  uint32 a;
  uint32 b;
  uint c;
}
```

## Good to know

- **Token burning** is when a token is sent to address **0**, making it
unrecoverable. It can be used for raising the value of a token, but there is
many more reasons behind.
