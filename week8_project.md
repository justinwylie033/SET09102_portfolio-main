<h1> Operational Decision Tracking </h1>
Introduction and Issue Description
In the eighth week of our software engineering module, we delved into a practical application of the principles and techniques we've been exploring throughout the course. The task at hand involved enhancing our software to ensure robust tracking of operational decisions, resource requests, and the subsequent authorisations. Our end goal was clear: to uphold accountability for mission-critical decisions and to streamline the management of operational resources. This report provides a detailed account of my engagement with this task, focusing on the integration of various software engineering dimensions, the implementation of good design practices, and a reflective analysis of the peer review process.

Code Implementation and Design Practices
Database Schema Enhancement
To accommodate the new feature requirements, we needed to introduce a new table into our database schema. Here's how I went about it:

First I wrote the code - Engineering Centric.

```csharp
private static List<string> GetTableCreationCommands()
{
    return new List<string>
    {
        "CREATE TABLE IF NOT EXISTS completed_operations ("
        + "Id INTEGER PRIMARY KEY AUTOINCREMENT, "
        + "OperationName TEXT NOT NULL, "
        + "OperationStatus TEXT NOT NULL, "
        + "OperationDate DATETIME NOT NULL, "
        + "ResourceTypeId INTEGER, "
        + "ResourceQuantity INTEGER, "
        + "ResourceRequestStatus TEXT NOT NULL, "
        + "ResourceRequestDate DATETIME NOT NULL, "
        + "DeputyTeamLeaderId INTEGER, "
        + "AuthorizationDate DATETIME, "
        + "AuthorizationStatus TEXT NOT NULL, "
        + "FOREIGN KEY(ResourceTypeId) REFERENCES resource_types(Id), "
        + "FOREIGN KEY(DeputyTeamLeaderId) REFERENCES personnel(Id)"
        + ")"
    };
}
```

Second I consulted with my organisation on the changes: https://github.com/Software-Engineering-Red/MAUI-APP/pull/96

Third, A Co-Worker reviewed and approved my changes.

In this code snippet, we've defined a completed table to store all the necessary information related to operational decisions, resource requests, and their authorizations. This approach reflects good software design practices:

Modularity: By encapsulating the table creation commands within a method, we've ensured that our code remains modular and easy to maintain.
Clarity: The SQL commands are laid out clearly and understandably, ensuring that anyone reviewing the code can quickly grasp its purpose.
Data Integrity: The use of foreign keys ensures that our data remains consistent and reliable across different parts of the database.
Testing and Validation
To ensure the integrity of our implementation, we developed a suite of unit tests covering various scenarios:

Inserting new operational decisions and verifying their correct storage.
Requesting operational resources and checking their proper recording in the database.
Authorizing resource requests and ensuring that these authorizations are accurately logged.
Reflective Analysis on Code Review
Requested Changes and Adaptations

The code review process brought several critical points to light:

Upon reviewing a fellow student's code, I identified areas needing improvement:

Lack of Comments: The code was sparse on comments, making it difficult to understand certain segments of the implementation.
Hard-Coded Values: There were instances of hard-coded values, which could pose challenges if these values need to be altered in the future.
However, the code was superbly written and readable, so comments may be unnecessary provided we continue best practices. 

General Reflective Summary
New Insights and Realizations
This week's activities underscored the paramount importance of clear communication and meticulous documentation in collaborative development environments. Proper commenting and documentation practices significantly facilitate the code review process and enhance overall team efficiency.

Common Challenges in Team Development
Communication Gaps: Misunderstandings and lack of clarity can emerge when communication is not prioritised, leading to wasted time, effort and potential errors.
Code Inconsistency: The absence of comprehensive commentary can lead to lower team efficiency as it can be hard to understand convoluted, underdocumented code blocks.
Reflecting on my practices in comparison to my peers, I observed varied approaches to commenting and documentation. This disparity highlighted the necessity for established coding and documentation standards to ensure uniformity and ease of understanding across the team.



