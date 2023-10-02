# Code review

This section documents your practical work from week 4 in which you attempt a series of 
code review challenges. For your portfolio, do the following:

1. Choose the code review challenge which best demonstrates your skills.
2. Copy the code into your portfolio using a Markdown
   [fenced code block](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-and-highlighting-code-blocks).
3. Provide some descriptive commentary that identifies the problems.
4. Show your improved version of the code in a second code block.
5. Explain in one or more paragraphs why your solution is a good one.

**DO**

* Use grammatically correct sentences and paragraphs for your commentary.
* Make clear reference to the code in your commentary. GitHub Markdown does not support
  line numbers and so you need to make sure that the reader knows which line you are
  referring to from your description.
* Refer to recognised principles or rules when describing your solution. "I thought it
  would be better that way" is not sufficient: you need to have specific reasons.

**DON'T**

* Include multiple examples. Make the decision about which example shows your best
  work and use that one.

Code Review Challenge:

```csharp
using System;

namespace MyApplication
{
  class Program
  {
    static bool check(Int i) 
    {
        if (i % 2 == 0)
        {
            return true;
        }
        return false;
    }

    static void Main(string[] args)
    {
        //... Code not shown - ignore this line
    }  
  }
}
```

The first issue with the existing code is that it lacks proper commenting. Commenting is crucial for understanding code context and maintenability. The function name 'check' as well as the variable 'i' are not descriptive enough, causing understanding difficulties. Proper naming enhances readability. The import of the entire System namespace is not necessary for the current extent of functionality, and could potentially lead to namespace collision. 

The violation of the Open/Closed Principle occurs in the use of `int` where `double` would have been more inclusive. The function declaration does not follow the standard C# naming conventions. 

Improved Version:

```csharp
using System;  // Include the System namespace to access core functionality.

class NumberOperations  // Define a class named NumberOperations.
{
    // Define a static method named “IsEven” that takes a double 'number' as parameter and returns a boolean
    static bool IsEven(double number) 
    {
        // Check if 'number' is even by checking if it's divisible by 2 with no remainder.
        if (number % 2 == 0)  
        {
            return true;  // If it's even, return true.
        }
        return false;  // If it's not even, return false.
    }

    // Define the entry point of the program, the Main method
    static void Main()
    {
        // Example usage: Define a double variable 'num' and set its value to 6. 
        double num = 6.00;  
        // Call the IsEven method to check if 'num' is even and store the result in 'result'.
        bool result = IsEven(num);  
        // Output the result using Console.WriteLine.
        Console.WriteLine($"Is {num} even? {result}");  
    }  
}
```
The improved version of the code is significantly enhanced in terms of readability and maintainability. I've added descriptive comments to explain each component of the code, thus making it easier to understand. The function name is now self-explanatory ('IsEven'), and it takes a more inclusive 'double' parameter allowing for a wider range of inputs. Furthermore, the function and variable names are in compliance with standard C# naming conventions. By including an exemplary usage inside the Main method, one can understand what the function does even quicker. Thus, the code now adheres to principles such as KISS (Keep it Simple, Stupid) and DRY (Don't Repeat Yourself) and largely improves in terms of coding best practices.
