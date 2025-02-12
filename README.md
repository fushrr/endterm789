Task Manager Application

This project is a Java-based task management application that allows users to add, view, update, delete, and search tasks stored in a PostgreSQL database. 
The tasks include a title, description, status, due date, and task ID.

Features

1. Add Task: Allows the user to add a new task with a title, description, due date, and status.
2. View Tasks: Displays a list of all tasks stored in the database.
3. Update Task: Enables the user to update an existing task by its ID.
4. Delete Task: Allows the user to delete a task by its ID.
5. Search Tasks: Provides search functionality by:
   - Task Title
   - Task ID
   - Task Due Date

Requirements

- JDK: Java 8 or higher
- Database: PostgreSQL (configured with the necessary tasks table)
- JDBC Driver: PostgreSQL JDBC Driver (included in the project)

Setup

1. Clone the repository
Clone the project to your local machine:

git clone <repository_url>
cd <project_directory>

2. Database Setup

- Install PostgreSQL: If not already installed, you can download and install PostgreSQL from (https://www.postgresql.org/download/).
- Create Database: Create a database called 'postgres' or configure the connection to your database.
- Create the 'tasks' Table:

Run the following SQL command to create the 'tasks' table:

sql
CREATE TABLE tasks (
    id SERIAL PRIMARY KEY,
    title VARCHAR(255) NOT NULL,
    description TEXT,
    status VARCHAR(50),
    due_date DATE
);

3. Configure Database Connection

The 'DatabaseConnection' class is configured to connect to a PostgreSQL database running on 'localhost' with the following credentials:
- URL: jdbc:postgresql://localhost:5432/postgres'
- Username: 'postgres'
- Password: '459'

Ensure the 'DB_URL', 'DB_USER', and 'DB_PASSWORD' in the 'DatabaseConnection' class are correct based on your PostgreSQL setup.

4. Run the Application

Once everything is set up, you can run the 'TaskManagerApplication' class. This will start the command-line interface where you can manage tasks.

javac *.java
java TaskManager


5. Available Options

- Add Task: Add a new task by providing the task details.
- View Tasks: View all tasks stored in the database.
- Update Task: Update an existing task by entering its ID and providing updated details.
- Delete Task: Delete a task by its ID.
- Search Tasks: Search tasks by title, date, or ID.

Example Usage

--- Task Manager ---
1. Add Task
2. View Tasks
3. Update Task
4. Delete Task
5. Search by...
6. Exit
Choose an option: 1

Enter Task ID: 1
Enter task title: Finish report
Enter task description: Complete the monthly report.
Enter task status (Pending, In Progress, Completed): In Progress
Enter due date (YYYY-MM-DD): 2025-02-28

Task added successfully!

Classes Overview

`BaseTaskSearcher`
Abstract base class for task searchers. Handles the execution of SQL queries and printing of results.

`DatabaseConnection`
Manages the connection to the PostgreSQL database.

`DateSearcher`, `TitleSearcher`, `IdSearcher`
Concrete classes that implement task search functionality by date, title, or ID, respectively.

`Task`
Represents a task with properties such as `title`, `description`, `status`, `dueDate`, and `id`.

`TaskInput`
A utility class for collecting task input from the user.

`TaskMapper`
Maps `ResultSet` rows to `Task` objects.

`TaskService`
Contains methods for adding, viewing, updating, and deleting tasks from the database.

`SearchCoordinator`
Coordinates the task search operations, providing a menu for selecting the search criteria.

`TaskManagerApplication`
The entry point of the application, responsible for handling user input and interacting with the `TaskService` and `SearchCoordinator`.
