# **Banking System**
### **Project Overview**
The **Banking System** is a web-based platform designed to manage and automate various banking operations, allowing users to perform transactions such as deposits, withdrawals, fund transfers, and view account balance and transaction history. This system ensures a secure and user-friendly environment for handling multiple bank accounts while providing real-time updates for all operations.

---

### **Features**

#### **User Account Management**:
1. **User Registration and Login**:
   - Users can securely register and log in using their email and password.
   - Encrypted credentials ensure user data protection.
   
2. **Account Management**:
   - View account balance and personal information.
   - Option to update personal details and account preferences.

#### **Banking Transactions**:
1. **Deposit Funds**:
   - Allows users to deposit funds into their account by entering the deposit amount.
   - The system validates the input and updates the account balance accordingly.

2. **Withdraw Funds**:
   - Users can withdraw funds from their account.
   - The system checks whether the withdrawal amount is within the available balance before proceeding.

3. **Transfer Funds**:
   - Enables users to transfer money to another account by providing recipient details (account number).
   - The system validates recipient details and ensures sufficient balance before processing the transfer.

4. **Transaction History**:
   - Users can view a complete log of all past transactions, including deposits, withdrawals, and fund transfers.

#### **Notifications**:
- Users receive notifications for important actions like successful transfers, low balances, and other critical events.

#### **Security Features**:
- **Encryption**: All sensitive information, including passwords and transaction details, is encrypted to ensure security.
- **Session Management**: User sessions are managed securely to prevent unauthorized access.

---

### **Technology Stack**

#### **Frontend**:
- **HTML5**, **CSS3**, **JavaScript** for designing a responsive user interface.
- **React.js** or **Vue.js** for creating dynamic, modular, and reusable components for different pages like the dashboard, transaction forms, and history.

#### **Backend**:
- **Node.js** with **Express.js** to handle API requests, user authentication, and business logic for banking transactions.
- **RESTful API**: Designed to handle communication between the frontend and backend efficiently.

#### **Database**:
- **MySQL** or **PostgreSQL** for storing user information, account details, and transaction records.
- **Schema** includes tables for users, accounts, transactions, and notifications.

#### **Authentication and Authorization**:
- **JWT (JSON Web Token)** for user authentication and session handling.
- **bcrypt** for password encryption and secure storage.

### Flowchart  

![alt text](<Banking System.jpg>)  


### **System Architecture**

1. **User Authentication and Role Management**:
   - Secure login and registration system with role-based access control to differentiate between different types of users (bank employees, customers, etc.).
   
2. **Banking Transactions**:
   - The system processes banking transactions (deposits, withdrawals, transfers) by validating the inputs, checking for sufficient balance, and updating account details in real-time.

3. **Account Balance and Transaction History**:
   - Users can check their real-time account balance, and transaction history is stored and can be retrieved anytime for future reference.

4. **Error Handling and Notifications**:
   - Robust error handling for invalid inputs, insufficient balance, or failed transactions.
   - System alerts users in real-time if any issue occurs during a transaction.

---

### **Database Schema (Simplified)**

#### **Users Table**:
| Field        | Type      | Description                              |
|--------------|-----------|------------------------------------------|
| user_id      | INT       | Primary key for user identification.     |
| name         | VARCHAR   | Full name of the user.                   |
| email        | VARCHAR   | Email used for login.                    |
| password     | VARCHAR   | Hashed password for secure login.        |

#### **Accounts Table**:
| Field        | Type      | Description                              |
|--------------|-----------|------------------------------------------|
| account_id   | INT       | Primary key for account identification.  |
| user_id      | INT       | Foreign key linking to the users table.  |
| balance      | DECIMAL   | Current balance of the user account.     |
| account_type | ENUM      | Type of account (savings, current, etc.).|

#### **Transactions Table**:
| Field           | Type      | Description                              |
|-----------------|-----------|------------------------------------------|
| transaction_id  | INT       | Primary key for transaction identification.|
| account_id      | INT       | Foreign key linking to the accounts table.|
| type            | ENUM      | Type of transaction (deposit, withdrawal, transfer).|
| amount          | DECIMAL   | Amount involved in the transaction.      |
| transaction_date| DATETIME  | Date and time the transaction occurred.  |

---

### **API Endpoints**

| Method | Endpoint                             | Description                                      |
|--------|--------------------------------------|--------------------------------------------------|
| POST   | `/api/register`                      | User registration for customers.                 |
| POST   | `/api/login`                         | User login and authentication.                   |
| GET    | `/api/accounts/:user_id`             | Fetch details of a user's bank account.          |
| POST   | `/api/accounts/:user_id/deposit`     | Deposit funds into a user’s account.             |
| POST   | `/api/accounts/:user_id/withdraw`    | Withdraw funds from a user’s account.            |
| POST   | `/api/accounts/:user_id/transfer`    | Transfer funds to another account.               |
| GET    | `/api/transactions/:user_id`         | Retrieve a user’s transaction history.           |

---

### **Usage Instructions**

#### **For Customers**:
1. **Login/Sign Up**: Register or log in to access your account.
2. **View Account Balance**: Check your real-time balance.
3. **Deposit and Withdraw**: Perform secure deposits and withdrawals.
4. **Transfer Funds**: Transfer money to other accounts.
5. **View Transaction History**: Track your past transactions anytime.

---
