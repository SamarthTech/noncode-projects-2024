# **Loan Management System**
### **Project Overview**
The **Loan Management System** is a web-based platform designed to facilitate the process of managing loans for financial institutions, loan officers, and borrowers. It provides a seamless process for applying for loans, reviewing loan applications, managing loan disbursements, tracking repayments, and closing loans. The system enables efficient handling of loan-related activities with real-time updates and secure management of user information.

---

### **Features**

#### **For Borrowers**:
1. **User Registration and Login**:
   - Secure user authentication with password encryption.
   - Role-based access: Borrower and Loan Officer.

2. **Loan Application**:
   - Borrowers can apply for a loan by filling in details like loan amount, tenure, income information, etc.
   - View application status in real time (approved, rejected, or pending).

3. **Loan Status**:
   - Borrowers can track the status of their loan applications (under review, approved, rejected).
   - Once approved, borrowers can view the loan disbursement details.

4. **Loan Repayment**:
   - Track upcoming repayment schedules, make payments, and view repayment history.
   - Automated reminders for upcoming due dates.

5. **Payment History**:
   - Borrowers can access detailed loan and repayment history, including amounts paid and outstanding balance.

6. **Loan Closure**:
   - Once all loan installments are paid, the borrower receives confirmation of loan closure.

---

#### **For Loan Officers**:
1. **Loan Application Review**:
   - Loan officers can review all loan applications, verifying borrower details and documentation.
   - Approve or reject applications based on eligibility and provided information.

2. **Loan Disbursement**:
   - On approval, loans are disbursed directly to borrowers’ accounts.
   - The system tracks disbursement details and links them to the borrower’s account.

3. **Repayment Tracking**:
   - Loan officers can monitor repayments made by borrowers and check for any outstanding balances.
   - Automated notifications for missed or delayed payments.

4. **Loan Reports**:
   - Generate reports on the total number of approved, rejected, and pending loan applications.
   - Track total loans disbursed, repayment success rates, and overall performance.

---

### **Technology Stack**

#### **Frontend**:
- **HTML5**, **CSS3**, **JavaScript** for the basic structure and interactivity of the user interface.
- **React.js** or **Vue.js** for building dynamic and modular components for the borrower and loan officer dashboards.
- **Bootstrap** or **Material UI** for styling and responsiveness, ensuring the platform works on all devices.

#### **Backend**:
- **Node.js** with **Express.js** for building the backend, handling API requests, and processing loan application data.
- **RESTful API** for connecting the frontend with the backend, ensuring data flow between the user interface and the server.

#### **Database**:
- **MySQL** or **PostgreSQL** for managing borrowers, loans, repayments, and transaction data.
- **Schema** includes tables for users, loan applications, repayments, and transactions.

#### **Authentication**:
- **JWT (JSON Web Token)** for secure user authentication and session management.
- **Password Encryption** with bcrypt to ensure user credentials are securely stored.

#### **Payment Gateway**:
- Integration with **Stripe** or **PayPal** for processing loan repayments securely.

### Flowchart  

![alt text](<Loan Management System.jpg>)  


### **System Architecture**

1. **User Authentication and Role Management**:
   - The system authenticates users (borrowers and loan officers) using credentials.
   - Role-based access control ensures borrowers can only apply for and manage their loans, while loan officers have administrative access.

2. **Loan Application Workflow**:
   - Borrowers submit loan applications which are then stored in the database for review.
   - Loan officers can access pending applications, review documentation, and approve or reject applications.

3. **Loan Disbursement and Repayment**:
   - Upon approval, the loan amount is disbursed to the borrower’s account.
   - Borrowers are provided with a repayment schedule and can make payments online through the system.

4. **Payment and Loan Tracking**:
   - The system tracks all repayments, updating loan balances in real-time.
   - Once the loan is fully paid, it is marked as closed, and the borrower receives a notification.

---

### **Database Schema (Simplified)**

#### **Users Table**:
| Field        | Type      | Description                              |
|--------------|-----------|------------------------------------------|
| user_id      | INT       | Primary key for user identification.     |
| name         | VARCHAR   | Full name of the user.                   |
| email        | VARCHAR   | Email used for login.                    |
| password     | VARCHAR   | Hashed password for secure login.        |
| role         | ENUM      | User role (borrower, loan officer).      |

#### **Loan Applications Table**:
| Field             | Type      | Description                              |
|-------------------|-----------|------------------------------------------|
| loan_id           | INT       | Primary key for loan identification.     |
| user_id           | INT       | Foreign key linking to the users table.  |
| loan_amount       | DECIMAL   | Amount of loan applied for.              |
| loan_tenure       | INT       | Loan tenure in months.                   |
| application_date  | DATETIME  | Date of loan application.                |
| status            | ENUM      | Status of the loan (pending, approved, rejected).|

#### **Repayments Table**:
| Field             | Type      | Description                              |
|-------------------|-----------|------------------------------------------|
| repayment_id      | INT       | Primary key for repayment identification.|
| loan_id           | INT       | Foreign key linking to the loan table.   |
| amount_paid       | DECIMAL   | Amount paid by the borrower.             |
| payment_date      | DATETIME  | Date of repayment.                       |
| outstanding_balance | DECIMAL | Remaining balance after payment.         |

---

### **API Endpoints**

| Method | Endpoint                          | Description                                  |
|--------|-----------------------------------|----------------------------------------------|
| POST   | `/api/login`                      | User login for authentication.               |
| POST   | `/api/register`                   | User registration for new accounts.          |
| POST   | `/api/apply-loan`                 | Borrower applies for a new loan.             |
| GET    | `/api/loan-status/:user_id`       | Get the status of loan applications.         |
| POST   | `/api/review-loan/:loan_id`       | Loan officer reviews a loan application.     |
| POST   | `/api/approve-loan/:loan_id`      | Approve a loan application.                  |
| POST   | `/api/reject-loan/:loan_id`       | Reject a loan application.                   |
| POST   | `/api/make-payment`               | Borrower makes a loan repayment.             |
| GET    | `/api/loan-history/:user_id`      | Fetch loan repayment history.                |

---

### **Usage Instructions**

#### **For Borrowers**:
1. **Login/Sign Up**: Log in with your credentials or sign up for a new account.
2. **Apply for Loan**: Fill in loan details (amount, tenure) and submit your application.
3. **Repay Loans**: Once approved, track repayments and make payments through the system.

#### **For Loan Officers**:
1. **Review Applications**: Access pending loan applications and review borrower details.
2. **Approve/Reject Loans**: Decide whether to approve or reject the application based on the borrower’s eligibility.

---
