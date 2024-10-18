## **School Management System**
### **Project Overview**
The **School Management System** is a web-based application designed to manage various school operations efficiently, including student enrollment, attendance, grading, scheduling, and communication between teachers, students, and parents. It automates administrative tasks and provides an integrated platform for schools to manage academic and non-academic activities in a streamlined manner.

---

### **Features**
1. **Admin Dashboard**:
   - Manage student, teacher, and parent records.
   - Create and assign classes, subjects, and schedules.
   - Generate detailed reports on student performance, attendance, and overall school statistics.

2. **Teacher Dashboard**:
   - Manage class schedules, record attendance, and assign grades.
   - View and update student progress.
   - Communicate directly with students and parents through messaging features.

3. **Student Dashboard**:
   - View personal profile, schedules, and grades.
   - Track assignments and project deadlines.
   - Communicate with teachers.

4. **Parent Dashboard**:
   - Monitor their child’s attendance, grades, and performance.
   - Communicate with teachers regarding their child’s progress.
   - View upcoming school events and schedules.

5. **Role-Based Authentication**:
   - Secure login for admins, teachers, students, and parents with specific access permissions based on their roles.

6. **Attendance Management**:
   - Record student attendance daily or per subject.
   - Generate attendance reports for individual students or entire classes.

7. **Grading System**:
   - Teachers can assign grades to students based on assignments, quizzes, and exams.
   - Students and parents can view grades and performance reports.

8. **School Scheduling**:
   - Manage school timetables for different classes and subjects.
   - Teachers and students can view their schedules in their dashboards.

---

### **Technology Stack**
- **Frontend**:
  - HTML5, CSS3, JavaScript (React or Vue.js for dynamic interface components).
  - Bootstrap or Material UI for responsive design.
  
- **Backend**:
  - Node.js with Express.js to handle server-side logic.
  - RESTful API for communication between client and server.

- **Database**:
  - MySQL or PostgreSQL for managing relational data, including student, teacher, and parent records, attendance, grades, and schedules.

- **Authentication**:
  - JWT (JSON Web Token) for secure user authentication.

### Flowchart  

![alt text](<School Management System.jpg>)  


### **System Architecture**
1. **User Authentication & Role-Based Access**:
   - Secure login system with role-based access for admins, teachers, students, and parents.

2. **Data Management**:
   - CRUD operations for managing students, teachers, classes, subjects, schedules, attendance, and grades.

3. **Communication**:
   - Integrated messaging system for communication between teachers, students, and parents.

4. **Reporting**:
   - Dynamic reports for attendance, grades, and performance tracking.

---

### **Usage Instructions**

#### **Admin**:
1. **Login as Admin** to manage school data such as student records, teacher assignments, classes, and schedules.
2. **Manage Students**: Add, update, or delete student information.
3. **Manage Teachers**: Assign teachers to classes and subjects.
4. **Generate Reports**: View student performance, attendance, and other statistics.

#### **Teacher**:
1. **Login as Teacher** to view class schedules and manage student records.
2. **Record Attendance**: Mark daily attendance for each class.
3. **Assign Grades**: Enter student grades and provide feedback on assignments.

#### **Student**:
1. **Login as Student** to view class schedules, grades, and assignments.
2. **Track Progress**: View academic performance and teacher feedback.
3. **Communicate**: Contact teachers for assistance or clarifications.

#### **Parent**:
1. **Login as Parent** to monitor your child’s academic progress.
2. **View Grades and Attendance**: Stay updated on your child's performance.
3. **Communicate**: Contact teachers directly if necessary.

---

### **API Endpoints**

| Method | Endpoint                        | Description                                    |
|--------|----------------------------------|------------------------------------------------|
| POST   | `/api/login`                     | User login (Admin, Teacher, Student, Parent)   |
| GET    | `/api/students`                  | Get list of students (Admin access)            |
| POST   | `/api/students`                  | Add new student (Admin access)                 |
| PUT    | `/api/students/:id`              | Update student information (Admin access)      |
| DELETE | `/api/students/:id`              | Delete a student (Admin access)                |
| GET    | `/api/teachers`                  | Get list of teachers (Admin access)            |
| POST   | `/api/teachers`                  | Add new teacher (Admin access)                 |
| PUT    | `/api/teachers/:id`              | Update teacher information (Admin access)      |
| DELETE | `/api/teachers/:id`              | Delete a teacher (Admin access)                |
| GET    | `/api/classes`                   | Get list of classes and schedules (All users)  |
| POST   | `/api/attendance`                | Record student attendance (Teacher access)     |
| GET    | `/api/attendance/:classId`       | Get attendance for a class (Teacher/Parent access) |
| POST   | `/api/grades`                    | Record student grades (Teacher access)         |
| GET    | `/api/grades/:studentId`         | Get grades for a student (Student/Parent access)|

---

### **Database Schema (Simplified)**

#### **Users Table**:
| Field    | Type      | Description                              |
|----------|-----------|------------------------------------------|
| id       | INT       | Primary key                              |
| name     | VARCHAR   | Full name of the user                    |
| email    | VARCHAR   | Email address for login                  |
| password | VARCHAR   | Hashed password                          |
| role     | ENUM      | Role of the user (Admin, Teacher, Student, Parent) |

#### **Students Table**:
| Field        | Type      | Description                           |
|--------------|-----------|---------------------------------------|
| id           | INT       | Primary key                           |
| user_id      | INT       | Foreign key to Users table            |
| grade_level  | VARCHAR   | Current grade level (e.g., 10th Grade)|
| guardian_contact | VARCHAR| Guardian's contact number             |

#### **Teachers Table**:
| Field        | Type      | Description                           |
|--------------|-----------|---------------------------------------|
| id           | INT       | Primary key                           |
| user_id      | INT       | Foreign key to Users table            |
| subject      | VARCHAR   | Subject the teacher specializes in    |

#### **Classes Table**:
| Field        | Type      | Description                           |
|--------------|-----------|---------------------------------------|
| id           | INT       | Primary key                           |
| name         | VARCHAR   | Class name (e.g., Math 101)           |
| teacher_id   | INT       | Foreign key to Teachers table         |
| schedule     | VARCHAR   | Timetable for the class               |

---
