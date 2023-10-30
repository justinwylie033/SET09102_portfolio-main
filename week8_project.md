
    <h1>Operational Decision Tracking</h1>

    <section>
        <h2>Introduction and Issue Description</h2>
        <p>In the eighth week of our software engineering module, we delved into a practical application of the principles and techniques we've been exploring throughout the course. The task at hand involved enhancing our software to ensure robust tracking of operational decisions, resource requests, and the subsequent authorisations. Our end goal was clear: to uphold accountability for mission-critical decisions and to streamline the management of operational resources. This report provides a detailed account of my engagement with this task, focusing on the integration of various software engineering dimensions, the implementation of good design practices, and a reflective analysis of the peer review process.</p>
    </section>

    <section>
        <h2>Code Implementation and Design Practices</h2>
        <h3>Database Schema Enhancement</h3>
        <p>To accommodate the new feature requirements, we needed to introduce a new table into our database schema. Here's how I went about it:</p>
        <ol>
            <li>First I wrote the code - Engineering Centric.</li>
```csharp
private static List&lt;string&gt; GetTableCreationCommands()
{
    return new List&lt;string&gt;
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
            <li>Second I consulted with my organisation on the changes: <a href="https://github.com/Software-Engineering-Red/MAUI-APP/pull/96">GitHub Pull Request</a></li>
            <li>Third, A Co-Worker reviewed and approved my changes.</li>
        </ol>
        <p>In this code snippet, we've defined a completed table to store all the necessary information related to operational decisions, resource requests, and their authorizations. This approach reflects good software design practices:</p>
        <ul>
            <li><strong>Modularity:</strong> By encapsulating the table creation commands within a method, we've ensured that our code remains modular and easy to maintain.</li>
            <li><strong>Clarity:</strong> The SQL commands are laid out clearly and understandably, ensuring that anyone reviewing the code can quickly grasp its purpose.</li>
            <li><strong>Data Integrity:</strong> The use of foreign keys ensures that our data remains consistent and reliable across different parts of the database.</li>
        </ul>
    </section>

    <section>
        <h2>Testing and Validation</h2>
        <p>To ensure the integrity of our implementation, we developed a suite of unit tests covering various scenarios:</p>
        <ul>
            <li>Inserting new operational decisions and verifying their correct storage.</li>
            <li>Requesting operational resources and checking their proper recording in the database.</li>
            <li>Authorizing resource requests and ensuring that these authorizations are accurately logged.</li>
        </ul>
    </section>

    <section>
        <h2>Reflective Analysis on Code Review</h2>
        <h3>Requested Changes and Adaptations</h3>
        <p>The code review process brought several critical points to light:</p>
        <ul>
            <li><strong>Lack of Comments:</strong> The code was sparse on comments, making it difficult to understand certain segments of the implementation.</li>
            <li><strong>Hard-Coded Values:</strong> There were instances of hard-coded values, which could pose challenges if these values need to be altered in the future.</li>
        </ul>
        <p>However, the code was superbly written and readable, so comments may be unnecessary provided we continue best practices.</p>
    </section>

    <section>
        <h2>General Reflective Summary</h2>
        <h3>New Insights and Realizations</h3>
        <p>This week's activities underscored the paramount importance of clear communication and meticulous documentation in collaborative development environments. Proper commenting and documentation practices significantly facilitate the code review process and enhance overall team efficiency.</p>

        <h3>Common Challenges in Team Development</h3>
        <ul>
            <li><strong>Communication Gaps:</strong> Misunderstandings and lack of clarity can emerge when communication is not prioritised, leading to wasted time, effort and potential errors.</li>
            <li><strong>Code Inconsistency:</strong> The absence of comprehensive commentary can lead to lower team efficiency as it can be hard to understand convoluted, underdocumented code blocks.</li>
        </ul>
        <p>Reflecting on my practices in comparison to my peers, I observed varied approaches to commenting and documentation. This disparity highlighted the necessity for established coding and documentation standards to ensure uniformity and ease of understanding across the team.</p>
    </section>

