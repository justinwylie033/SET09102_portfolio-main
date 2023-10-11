# Documentation

This section is related to your work on clean code and documentation in week 5.

First, choose six rules of clean code and explain them. For each one,

* Summarise the rule in your own words.
* Provide an example from the code that you wrote in week 2 and then refined in week 4.
* Explain how your code implements the rule. 

Second, copy the doxygen comments from your code into your portfolio and provide some 
descriptive commentary on their purpose and structure. Use screenshots showing the HTML 
content that is generated from your code to illustrate your explanation.

Finally, highlight three examples from your code where you have eliminated the need
for comments by adhering to the principles of clean code.
 
Six Rules Of Clean Code

1. Meaningful Names
Summary
Select descriptive and unambiguous names for variables, methods, and classes to clearly communicate their purpose or function.

Example
Before (Week 2)

csharp
Copy code
public class DatabaseInitialiser { }
After (Week 4)

csharp
Copy code
public class SqliteDbTableInitializer { }
Explanation
The refined name SqliteDbTableInitializer indicates that the class is related to initializing tables in an SQLite database, providing more explicit information than DatabaseInitialiser.

2. Small Functions
Summary
Construct functions to be succinct and focused on a single responsibility to enhance readability.

Example
Before

csharp
Copy code
public void InitialiseTables() { /*... logic of opening connection, creating tables, and closing connection ...*/ }
After

csharp
Copy code
public void InitialiseTables() {
    OpenConnection();
    ExecuteTableCreationCommands();
    CloseConnection();
}
Explanation
In the refined version, InitialiseTables() has been simplified into smaller functions, each performing a single operation, adhering to the principle of small functions.

3. Avoid Output Arguments
Summary
Return results from functions instead of using output parameters to simplify function usage and avoid unexpected side effects.

Example
Before

csharp
Copy code
public void GetRecordId(string tableName, string name, out int id) { /*... logic ...*/ }
After

csharp
Copy code
public int GetRecordId(string tableName, string name) { /*... logic ...*/ }
Explanation
GetRecordId now returns the ID directly, eliminating the need for an output parameter and enhancing clarity.

4. Error Handling is One Thing
Summary
Separate error handling and primary logic within functions to improve readability and maintainability.

Example
Before

csharp
Copy code
public void AddRecord(string tableName, string name) { /*... logic and error handling...*/ }
After

csharp
Copy code
public void AddRecord(string tableName, string name) {
    try {
        // primary logic
    } catch (Exception e) {
        // error handling
    }
}
Explanation
Error handling and main logic are distinctly separated in the refined function, adhering to the principle that a function should address error handling as a singular concern.

5. Don't Repeat Yourself (DRY)
Summary
Avoid code duplication to ensure easier maintenance and consistency in logic application.

Example
Before

csharp
Copy code
public void AddContinent(string name) { /*... logic ...*/ }
public void AddCountry(string name) { /*... similar logic ...*/ }
After

csharp
Copy code
public void AddRecordToTable(string tableName, string name) { /*... logic ...*/ }
Explanation
The method AddRecordToTable provides a generalized solution, preventing repetitive logic and ensuring a single point of modification.

6. Comments Only When Necessary
Summary
Use comments judiciously for explaining the rationale or intricacies behind a code segment, not to describe what it does.

Example
Before

csharp
Copy code
// Adding record
public void AddRecord(string tableName, string name) { /*... logic ...*/ }
After

csharp
Copy code
public void AddRecord(string tableName, string name) { /*... logic ...*/ }
Explanation
The refined version removes the unnecessary comment since the method name AddRecord is already descriptive, adhering to the principle that code should be self-documenting when possible.

The applied refinements from Week 2 to Week 4 illustrate adherence to clean coding principles, enhancing the readability, maintainability, and overall quality of the code.
