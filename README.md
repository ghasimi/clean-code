# clean-code
Towards writing cleaner codes.

## General 

- Don't Repeat Yourself (DRY)

- Separation of Concerns (SOC)

- Single Point of Truth (SPOT)

- Keep it Simple (KISS)



## [SOLID](https://en.wikipedia.org/wiki/SOLID)

A mnemonic acronym of five principles. 

1. The single-responsibility principle: "Every class should have only one responsibility.", very similar to the Seperation of Concerns (SOC), while SRP is more about classes and objects, and SOC is more about features.

2. The open–closed principle: Open for extension, but closed for modification.

3. The Liskov substitution principle: "Functions that use pointers or references to base classes must be able to use objects of derived classes without knowing it."

<details>
    <summary>Sample code</summary>
    
```
/*
A example of violation of SOLID's Liskov substitution principle (LSP), which states:
"Functions that use pointers or references to base classes must be able to 
use objects of derived classes without knowing it." ~Wikipedia

2022, D. Ghasimi
*/

#include <iostream>

// Base class   
class Base {
public:
  std::string getName() {
      return "Base"; // Name is a string
  };
};

// Derived class
class Derived : public Base {
  int getName() {
      return 123;   // Name is an int
  };
};

// Client function
void client(Base* basePtr)
{
    std::string message;
    
    message = "The object name is " + basePtr->getName();
    
    std::cout << message << std::endl;
};

int main() {
    
    // Pointer to the base class
    Base* basePtr;
    
    // OK with the base class...
    basePtr = new Base();
    client(basePtr); // "The object name is Base"
    
    // ... but unexpected behaviour with thederived class
    basePtr = new Derived();
    client(basePtr); // "The object name is Base", because the client
        // expects a string. So it uses getName() of the Base class
        // instead of that of the Derived class.
    return 0;
}
```
</details>


4. The interface segregation principle: "Clients should not be forced to depend upon interfaces that they do not use."
    
5. The dependency inversion principle: "Depend upon abstractions, [not] concretions."


## Other principles

- You aren't gonna need it (YAGNI): Avoid adding functionality until deemed necessary; a derivative of the KISS.


