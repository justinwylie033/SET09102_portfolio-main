
<h1> Week 9: Continued Team Project Work </h1>
Summary of Worked Issues
This week, I continued refining our database interaction layer, focusing on the implementation of asynchronous database initialisation and table creation in our Database class. This work is part of our ongoing efforts to ensure thread safety and improve the responsiveness of our application.

<h1> Code Snippets and Design Practices: </h1>

I applied the async-await pattern to avoid blocking the UI thread, ensuring our app remains responsive during database operations.

```csharp
public async Task InitializeAsync()
{
    if (_isInitialized) return;

    await CreateTablesAsync();
    _isInitialized = true;
}
```
By using an async Task instead of void for asynchronous initialisation, I also enabled exception propagation, leading to better error handling and debugging.

<h2> Test Code Summary </h2>
I developed a suite of unit tests to ensure our database initialization and table creation were functioning as expected. This involved mocking the SQLiteAsyncConnection and verifying that the CreateTablesAsync method was called for each model.

<h2> Code Review Changes and Reflection</h2>
During the code review, a peer pointed out the lack of exception handling around the database initialisation. I added a try-catch block to gracefully handle potential exceptions and log them for further investigation.

<h3> Before: </h3>

```csharp
await _database.CreateTablesAsync(CreateFlags.None, GetModelTypes()).ConfigureAwait(false);
```
<h3> After: </h3>

```csharp
Copy code
try
{
    await _database.CreateTablesAsync(CreateFlags.None, GetModelTypes()).ConfigureAwait(false);
}
catch (Exception ex)
{
    // Log and handle exceptions
}
```
<h3> Reviewing Team Member's Code </h3>
I reviewed a teammate's implementation of property setters in model classes. I suggested utilising a helper method to reduce boilerplate code and improve readability, which they incorporated successfully.

<h3> Reflective Summary </h3>
New Realisations:

The importance of exception handling in asynchronous code.
The value of comprehensive unit tests to ensure reliability.
Common Team Issues:

Coordinating database schema changes.
Ensuring thread safety across different parts of the application.
Comparative Practices:

My practice of writing new features has been more systematic compared to some team members in terms of robustness and following of best practices overall.

<h3> Improvements Over Last Week: </h3>

I've applied clean code principles more consistently, particularly in naming and structuring asynchronous methods.
I've reduced repetitive patterns by abstracting common functionality into reusable methods.

Links to GitHub Repository Database Initialisation Code - https://github.com/Software-Engineering-Red/MAUI-APP/commit/8c1db9ca21efb7b560b08b3832b18fb233a4e6f0

<h3> Conclusion </h3>
This week's focus on async patterns and code review has bolstered our project's robustness and maintainability. I'm learning to balance new feature development with the essential groundwork of error handling and testing, which I believe will be crucial as the complexity of our project increases.

