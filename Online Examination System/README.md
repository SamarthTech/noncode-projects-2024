## **Online Examination System (OES)**

### **Project Overview**
The **Online Examination System (OES)** is a web-based platform designed to facilitate the administration and taking of exams in an online environment. The system provides a user-friendly interface for both administrators (teachers/exam coordinators) to create and manage exams, and for students to take exams and view results. The platform offers features such as exam scheduling, question management, result tracking, and real-time exam monitoring, ensuring a streamlined, secure, and efficient examination process.

---

### **Features**

#### **Admin Features**:
1. **User Authentication**:
   - Secure login and role-based access for exam administrators and students.

2. **Create and Manage Exams**:
   - Admins can create new exams by specifying parameters like exam duration, total marks, and pass marks.
   - Admins can manage active and completed exams, including scheduling and student access.

3. **Question Management**:
   - Admins can create, edit, and delete questions.
   - Support for multiple question types (e.g., multiple-choice, true/false, short answer).
   - Add questions from a question bank to exams, or create custom questions.

4. **Set Exam Rules and Schedules**:
   - Specify the time duration for exams, passing marks, and randomized questions if needed.
   - Schedule exams for specific dates and times.

5. **Manage Users and Results**:
   - Admins can manage student accounts and assign exams to students.
   - View and manage exam results, track individual performance, and generate reports.

6. **Exam Reports**:
   - Generate detailed reports of student performance and overall exam statistics.

#### **Student Features**:
1. **User Authentication**:
   - Students can securely log in to the system.
   - Access available exams, view exam history, and review performance.

2. **View and Take Exams**:
   - Students can browse the list of available exams, including information such as start time, duration, and instructions.
   - Take exams within the specified time limit and submit answers for evaluation.

3. **Result Viewing**:
   - View detailed exam results after submission, including score breakdowns, correct answers, and performance analytics.

4. **Exam History**:
   - Review previous exam results and track progress over time.

#### **Security and Integrity**:
- **Timed Exams**: Exams are automatically submitted when the time limit is reached.
- **Randomized Questions**: To prevent cheating, exams can feature randomized questions for each student.
- **Real-Time Monitoring**: Admins can monitor ongoing exams and ensure compliance with exam rules.

---

### **Technology Stack**

#### **Frontend**:
- **HTML5**, **CSS3**, **JavaScript** (with a framework like **React.js** or **Vue.js** for dynamic components).
- **Bootstrap** or **Tailwind CSS** for responsive design and easy styling.

#### **Backend**:
- **Node.js** with **Express.js** for handling server-side logic and APIs.
- **RESTful API** for communication between the frontend and backend services.

#### **Database**:
- **MySQL** or **PostgreSQL** for relational data management, including user accounts, exams, questions, and results.

#### **Authentication and Security**:
- **JWT (JSON Web Tokens)** for secure user authentication and role-based access control.
- **Encryption** for sensitive data, such as user passwords and exam results.

#### **Additional Services**:
- **Socket.io** for real-time updates during exams (such as auto-submitting upon time expiration).

### Flowchart  

![alt text](<Online Examination System.jpg>)  


### **System Architecture**

1. **User Authentication and Authorization**:
   - Role-based access control ensures that students and admins have specific permissions and access rights.

2. **Exam Creation and Management**:
   - Admins can create exams by defining exam metadata (duration, number of questions, passing marks).
   - The question bank allows easy management and categorization of questions for reuse.

3. **Question Assignment and Randomization**:
   - Admins can assign questions from the bank to exams, with options to randomize questions to prevent cheating.

4. **Taking the Exam**:
   - Students log in, view available exams, and take them within the assigned time frame.
   - Real-time tracking of progress and time is maintained.

5. **Results Calculation and Display**:
   - Upon submission, the system calculates the student's score based on correct answers and displays the result.
   - Detailed performance statistics are provided, including correct/incorrect answers, total marks, and passing status.

6. **Monitoring and Reporting**:
   - Admins can monitor ongoing exams and generate detailed reports on exam performance across students.

---

### **Database Schema**

#### **Users Table**:
| Field      | Type    | Description                                  |
|------------|---------|----------------------------------------------|
| user_id    | INT     | Primary key for user identification.          |
| name       | VARCHAR | Full name of the user.                       |
| email      | VARCHAR | Email used for login.                        |
| password   | VARCHAR | Hashed password for user authentication.     |
| role       | ENUM    | Role of the user (Admin, Student).           |

#### **Exams Table**:
| Field          | Type      | Description                            |
|----------------|-----------|----------------------------------------|
| exam_id        | INT       | Primary key for exam identification.   |
| title          | VARCHAR   | Title of the exam.                     |
| duration       | INT       | Duration of the exam in minutes.       |
| total_marks    | INT       | Total marks for the exam.              |
| pass_marks     | INT       | Minimum passing marks.                 |
| scheduled_date | DATETIME  | Scheduled date and time for the exam.  |

#### **Questions Table**:
| Field          | Type      | Description                            |
|----------------|-----------|----------------------------------------|
| question_id    | INT       | Primary key for question identification.|
| exam_id        | INT       | Foreign key referencing the exam.      |
| question_text  | TEXT      | The actual question.                   |
| option_a       | TEXT      | Option A for multiple-choice questions.|
| option_b       | TEXT      | Option B for multiple-choice questions.|
| option_c       | TEXT      | Option C for multiple-choice questions.|
| option_d       | TEXT      | Option D for multiple-choice questions.|
| correct_answer | CHAR(1)   | The correct answer for the question.   |

#### **Results Table**:
| Field          | Type      | Description                            |
|----------------|-----------|----------------------------------------|
| result_id      | INT       | Primary key for result identification. |
| exam_id        | INT       | Foreign key referencing the exam.      |
| student_id     | INT       | Foreign key referencing the student.   |
| total_score    | INT       | The score obtained by the student.     |
| status         | ENUM      | Pass or Fail based on total score.     |

---

### **API Endpoints**

| Method | Endpoint                   | Description                                  |
|--------|----------------------------|----------------------------------------------|
| POST   | `/api/login`                | User login for authentication.               |
| POST   | `/api/register`             | User registration for new accounts.          |
| GET    | `/api/exams`                | Fetch all available exams for students.      |
| POST   | `/api/exams`                | Admin can create a new exam.                 |
| GET    | `/api/exams/:id`            | Get exam details and questions for a student.|
| POST   | `/api/exams/:id/submit`     | Submit answers for an exam and calculate score.|
| GET    | `/api/results/:studentId`   | View results of exams taken by the student.  |
| GET    | `/api/admin/results/:examId`| Admin can view results of all students for an exam.|
| PUT    | `/api/admin/exams/:id`      | Admin can update exam details or questions.  |

---
