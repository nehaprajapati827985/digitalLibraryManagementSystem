# Digital Library Management System

A web-based **Digital Library Management System** developed using **Core Java, JDBC, Servlets, JSP, HTML, CSS, JavaScript, and MySQL**. The application helps manage library books, users, book issuing and returning, overdue tracking, fine management, and user queries through a web-based interface.

## Features

### Authentication
- **User Registration & Login** — User sign-up and login with session-based authentication.
- **Role-Based Access Control** — Separate access for Admin and User roles.
- **Logout** — Invalidates the user session and redirects to the login page.

### Book Management
- Add, update, view, and delete books from the library catalog.
- Search books by title or author.
- Filter books by category.
- Track total and available book copies.

### User Management
- Add, update, view, and delete library users.
- Maintain user details, including name, email, phone number, and address.

### Book Issue & Return
- **Issue Books** — Assign available books to registered users.
- **Return Books** — Record book returns and update book availability.
- Maintain issue dates, due dates, and return dates.
- Update book condition and maintain issue and return notes.
- Track book status as Active, Due Today, or Overdue.

### Fine Management
- **Automatic Fine Calculation** — Calculate overdue fines at ₹5 per day.
- **Fine Tracking** — View pending and paid fines.
- **Fine Payment Status** — Allow administrators to mark fines as paid.

### Contact & Query Management
- Provide a contact form for users to submit queries.
- Allow administrators to view submitted messages.

### Dashboard
- Display library statistics, including total books, issued books, returned books, and registered users.
- View currently issued books and their due-date status.

## Tech Stack

- **Language:** Core Java
- **Backend:** JDBC, Servlets (Jakarta EE)
- **Frontend:** JSP, JSTL, HTML, CSS, JavaScript, Bootstrap 5
- **Database:** MySQL
- **Server:** Apache Tomcat 10.x
- **Database Connectivity:** JDBC
- **Architecture:** DAO – Service – Controller (Layered Architecture)
- **Development Tool:** Eclipse IDE
- **Version Control:** Git and GitHub

## Project Architecture

The project follows a layered architecture to separate request handling, business logic, and database operations.

- **Controller Layer:** Handles HTTP requests and responses using Servlets.
- **Service Layer:** Implements business logic and application workflows.
- **DAO Layer:** Executes database operations using JDBC.
- **Entity Layer:** Contains POJO classes representing application data.
- **Filter Layer:** Protects routes and manages authentication checks.
- **Utility Layer:** Provides database connection functionality.

## Project Structure

```text
src/main/java/com/digitalLibraryManagementSystem/
├── controller/
│   ├── AuthController.java
│   ├── BookController.java
│   ├── UserController.java
│   ├── ContactController.java
│   └── DashboardController.java
├── service/
├── dao/
├── entity/
│   ├── Book.java
│   ├── User.java
│   ├── BookIssued.java
│   ├── ContactMessage.java
│   └── DashboardStats.java
├── filter/
│   └── AuthFilter.java
└── util/
    └── DbUtil.java

src/main/webapp/
├── jsp/
│   ├── login.jsp
│   ├── register.jsp
│   ├── bookList.jsp
│   ├── addBook.jsp
│   ├── editBook.jsp
│   ├── assignBook.jsp
│   ├── returnBook.jsp
│   ├── finesList.jsp
│   ├── contact.jsp
│   └── contactMessages.jsp
└── includes/
    ├── header.jsp
    └── sidebar.jsp
```

## Database Schema

The application uses MySQL with the following tables:

| Table | Description |
|---|---|
| `books` | Stores book details, categories, ISBN, total copies, and available copies. |
| `users` | Stores user details, login credentials, and roles. |
| `book_issued` | Stores book issue and return records, due dates, conditions, and fine information. |
| `contact_messages` | Stores queries submitted through the contact form. |

### Main Database Columns

**1. `books`**
- `book_id`, `title`, `author`, `category`, `isbn`, `publisher`
- `total_copies`, `available_copies`, `status`, `created_at`

**2. `users`**
- `user_id`, `first_name`, `last_name`, `email`, `password`
- `role`, `phone_no`, `address`, `created_at`

**3. `book_issued`**
- `issue_id`, `book_id`, `user_id`, `issue_date`, `due_date`, `return_date`
- `status`, `book_condition`, `assignment_notes`, `return_notes`
- `fine_amount`, `fine_paid`

**4. `contact_messages`**
- `message_id`, `name`, `email`, `message`, `created_at`

## Setup Instructions

### Prerequisites
- Java Development Kit (JDK)
- Eclipse IDE
- Apache Tomcat 10.x
- MySQL Server and MySQL Workbench
- Git

### Installation

1. **Clone the repository**

   ```bash
   git clone <your-repository-url>
   ```

2. **Import the project into Eclipse**

   Import the project using the appropriate Java web project or Maven project option, depending on its configuration.

3. **Create the database**

   Create the `library_db` database and the required tables: `books`, `users`, `book_issued`, and `contact_messages`.

4. **Configure database connectivity**

   Update the MySQL URL, username, and password in `DbUtil.java`.

5. **Configure Apache Tomcat**

   Configure Tomcat 10.x in Eclipse and deploy the application.

6. **Run the application**

   Start the server and open the following URL, adjusting the port and context path to match your configuration:

   ```text
   http://localhost:8082/<project-name>/AuthController?action=showLogin
   ```

## Future Enhancements

- **Book Reservation:** Allow users to reserve books that are currently unavailable.
- **Password Hashing:** Replace plain-text password storage with secure password hashing.
- **Email/SMS Notifications:** Notify users about upcoming due dates and overdue books.
- **Report Export:** Export library reports in PDF or CSV format.
- **Improved Security:** Strengthen session management, authorization, and input validation.

## Security Note

For production use, passwords should never be stored in plain text. Use a secure password-hashing algorithm such as Argon2id or bcrypt, and enforce server-side authorization and input validation.

## Author

Developed as a web-based project to simplify library operations and demonstrate Java web development, JDBC database connectivity, and layered application architecture.
