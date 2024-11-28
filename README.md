#<**LIBRARY MANAGEMENT API**>

The **Library Management API** is a backend solution built using PHP and the Slim framework, designed for managing library operations. It offers endpoints for user registration, authentication, and efficient management of authors, books, and their associations. The API employs **JSON Web Tokens (JWT)** to ensure secure authentication and token handling.
---

**Features**
- **User Management**: Register, authenticate, view, update, and delete users.
- **Author Management**: Register, view, update, and delete author details.
- **Book Management**: Register, view, update, and delete books.
- **Book-Author Association**: Manage relationships between books and authors.
- **Token Management**: Securely generate and validate tokens for access control.

---

**Requirements**
- **PHP** 7.4 or higher
- **MySQLyog**
- **XAMPP**
- **Slim Framework**
- **Git**
- **Firebase** (for JWT)
- **Composer**
- **Node.js**

---

**Installation**
1. **Clone the Repository**  
   ```bash
   git clone https://github.com/aplejoy/Library_API.git
   cd Library_API
   ```

2. **Install Dependencies**  
   ```bash
   composer require slim/slim:3.*
   composer require firebase/php-jwt
   ```

---

**API Endpoints**

**User Management**
- **Register User**  
  **Endpoint**: `/user/register`  
  **Method**: `POST`  
  **Payload**:
  ```json
  { "username": "your_username", "password": "your_password" }
  ```

- **Authenticate User**  
  **Endpoint**: `/user/auth`  
  **Method**: `POST`  
  **Payload**:
  ```json
  { "username": "your_username", "password": "your_password" }
  ```

- **View Users**  
  **Endpoint**: `/user/show`  
  **Method**: `GET`  
  **Header**:
  ```json
  { "Authorization": "Bearer your_token" }
  ```

- **Update User**  
  **Endpoint**: `/user/update`  
  **Method**: `PUT`  
  **Payload**:
  ```json
  { "token": "your_token", "userid": "user_id", "username": "new_username", "password": "new_password" }
  ```

- **Delete User**  
  **Endpoint**: `/user/delete`  
  **Method**: `DELETE`  
  **Payload**:
  ```json
  { "token": "your_token", "userid": "user_id" }
  ```

---

**Author Management**
- **Register Author**  
  **Endpoint**: `/author/register`  
  **Method**: `POST`  
  **Payload**:
  ```json
  { "token": "your_token", "name": "author_name" }
  ```

- **View Authors**  
  **Endpoint**: `/author/show`  
  **Method**: `GET`  
  **Header**:
  ```json
  { "Authorization": "Bearer your_token" }
  ```

- **Update Author**  
  **Endpoint**: `/author/update`  
  **Method**: `PUT`  
  **Payload**:
  ```json
  { "token": "your_token", "authorid": "author_id", "name": "new_name" }
  ```

- **Delete Author**  
  **Endpoint**: `/author/delete`  
  **Method**: `DELETE`  
  **Payload**:
  ```json
  { "token": "your_token", "authorid": "author_id" }
  ```

---

**Book Management**
- **Register Book**  
  **Endpoint**: `/book/register`  
  **Method**: `POST`  
  **Payload**:
  ```json
  { "token": "your_token", "title": "book_title", "authorid": "author_id" }
  ```

- **View Books**  
  **Endpoint**: `/book/show`  
  **Method**: `GET`  
  **Header**:
  ```json
  { "Authorization": "Bearer your_token" }
  ```

- **Update Book**  
  **Endpoint**: `/book/update`  
  **Method**: `PUT`  
  **Payload**:
  ```json
  { "token": "your_token", "bookid": "book_id", "title": "new_title", "authorid": "author_id" }
  ```

- **Delete Book**  
  **Endpoint**: `/book/delete`  
  **Method**: `DELETE`  
  **Payload**:
  ```json
  { "token": "your_token", "bookid": "book_id" }
  ```

---

**Book-Author Association**
- **Associate Book and Author**  
  **Endpoint**: `/book_author/register`  
  **Method**: `POST`  
  **Payload**:
  ```json
  { "token": "your_token", "bookid": "book_id", "authorid": "author_id" }
  ```

- **View Associations**  
  **Endpoint**: `/book_author/show`  
  **Method**: `GET`  
  **Header**:
  ```json
  { "Authorization": "Bearer your_token" }
  ```

- **Update Association**  
  **Endpoint**: `/book_author/update`  
  **Method**: `PUT`  
  **Payload**:
  ```json
  { "token": "your_token", "bookid": "book_id", "authorid": "author_id" }
  ```

- **Delete Association**  
  **Endpoint**: `/book_author/delete`  
  **Method**: `DELETE`  
  **Payload**:
  ```json
  { "token": "your_token", "bookid": "book_id", "authorid": "author_id" }
  ```

---

**Token Management**
- **Generate Token**: Tokens are automatically created during user authentication and stored in the database with an `active` status.
- **Validate Token**: The `validateToken` function ensures token validity by decoding and verifying its status while extracting user details.
