# **Job Portal System**
### **Project Overview**
The **Job Portal System** is a web-based platform designed to connect job seekers with employers in an efficient and streamlined manner. Job seekers can browse and apply for jobs based on their skills and preferences, while employers can post job openings, review applications, and manage the recruitment process. This system simplifies the job search and hiring process with features like user authentication, job search filters, application tracking, and notifications.

---

### **Features**

#### **For Job Seekers**:
1. **User Registration and Login**:
   - Secure user registration and login for job seekers using email and password.
   - User profile creation with personal details, skills, experience, and resume upload.

2. **Job Search**:
   - Job seekers can search for jobs using keywords, location, category, and other filters.
   - View detailed job descriptions, including job requirements, salary, and company details.

3. **Apply for Jobs**:
   - Job seekers can apply for jobs by submitting their resumes directly through the portal.
   - Track the status of job applications (pending, reviewed, shortlisted, or rejected).

4. **Job Alerts**:
   - Set up job alerts to receive notifications when new jobs matching the user's criteria are posted.
   - Get updates on new job opportunities in specific categories or locations.

5. **Application Status Notifications**:
   - Job seekers receive notifications when their applications are reviewed or updated by employers.

#### **For Employers**:
1. **Employer Registration and Login**:
   - Employers can register and log in securely to post jobs and manage applications.
   - Create a company profile with relevant information like industry, location, and website.

2. **Post Job Listings**:
   - Employers can post job openings with detailed job descriptions, requirements, and salary range.
   - Jobs can be edited, updated, or deleted as needed.

3. **View Applicants**:
   - Employers can view all the applicants for a specific job listing.
   - Access each applicant's profile, resume, and cover letter for review.

4. **Shortlist or Reject Applicants**:
   - Employers can shortlist applicants for interviews or reject them with automated notifications sent to candidates.
   - Track the status of each application and manage the recruitment process.

5. **Notifications for New Applicants**:
   - Employers receive notifications when new job applications are submitted for their listings.

---

### **Technology Stack**

#### **Frontend**:
- **HTML5**, **CSS3**, **JavaScript** for the basic structure and interactivity of the user interface.
- **React.js** or **Vue.js** for creating dynamic, modular components for job search, application forms, and job listings.
- **Bootstrap** or **Tailwind CSS** for responsive design and enhanced UI/UX.

#### **Backend**:
- **Node.js** with **Express.js** for handling API requests, user authentication, and job data management.
- **RESTful API** for enabling communication between the frontend and backend components.

#### **Database**:
- **MySQL** or **MongoDB** for managing user data (job seekers and employers), job listings, applications, and resumes.
- **Schema** includes tables for users, jobs, applications, and notifications.

#### **Authentication**:
- **JWT (JSON Web Token)** for secure user authentication and session management.
- **Password Encryption** with bcrypt to ensure user credentials are securely stored.

#### **File Storage**:
- Integration with **AWS S3** or **Google Cloud Storage** for storing user resumes and company logos securely.

### Flowchart  

![alt text](<Job Portal System.jpg>)  


### **System Architecture**

1. **User Authentication and Role Management**:
   - The system uses role-based access control to differentiate between job seekers and employers.
   - After login, users are directed to their respective dashboards where they can perform actions like applying for jobs or posting job listings.

2. **Job Search and Application**:
   - Job seekers can use search filters (keywords, location, category) to find relevant job opportunities.
   - Once a suitable job is found, job seekers can apply by submitting their resume and application details.

3. **Job Posting and Review**:
   - Employers post jobs by providing job details such as title, description, qualifications, and salary.
   - Employers can view submitted applications, review resumes, and either shortlist candidates for interviews or reject applications.

4. **Notifications and Alerts**:
   - Job seekers receive real-time notifications for job alerts and application updates.
   - Employers receive notifications for new job applications or updates on existing job listings.

---

### **Database Schema (Simplified)**

#### **Users Table**:
| Field        | Type      | Description                              |
|--------------|-----------|------------------------------------------|
| user_id      | INT       | Primary key for user identification.     |
| name         | VARCHAR   | Full name of the user.                   |
| email        | VARCHAR   | Email used for login.                    |
| password     | VARCHAR   | Hashed password for secure login.        |
| role         | ENUM      | User role (job_seeker, employer).        |

#### **Jobs Table**:
| Field        | Type      | Description                              |
|--------------|-----------|------------------------------------------|
| job_id       | INT       | Primary key for job identification.      |
| employer_id  | INT       | Foreign key linking to the users table.  |
| title        | VARCHAR   | Title of the job.                        |
| description  | TEXT      | Detailed job description.                |
| requirements | TEXT      | Required qualifications and skills.      |
| salary       | DECIMAL   | Salary range for the job.                |
| location     | VARCHAR   | Location of the job.                     |
| post_date    | DATETIME  | Date the job was posted.                 |

#### **Applications Table**:
| Field           | Type      | Description                              |
|-----------------|-----------|------------------------------------------|
| application_id  | INT       | Primary key for application identification.|
| job_id          | INT       | Foreign key linking to the jobs table.   |
| job_seeker_id   | INT       | Foreign key linking to the users table.  |
| resume          | VARCHAR   | URL to the uploaded resume.              |
| status          | ENUM      | Application status (pending, reviewed, shortlisted, rejected). |
| application_date| DATETIME  | Date of job application submission.      |

#### **Notifications Table**:
| Field          | Type      | Description                              |
|----------------|-----------|------------------------------------------|
| notification_id| INT       | Primary key for notification identification.|
| user_id        | INT       | Foreign key linking to the users table.  |
| message        | TEXT      | Notification message.                    |
| read_status    | BOOLEAN   | Indicates if the notification has been read.|
| sent_date      | DATETIME  | Date the notification was sent.          |

---

### **API Endpoints**

| Method | Endpoint                             | Description                                      |
|--------|--------------------------------------|--------------------------------------------------|
| POST   | `/api/register`                      | User registration for job seekers and employers. |
| POST   | `/api/login`                         | User login and authentication.                   |
| GET    | `/api/jobs`                          | Fetch a list of all available jobs.              |
| POST   | `/api/jobs`                          | Employers post new job listings.                 |
| GET    | `/api/jobs/:job_id`                  | Fetch details for a specific job.                |
| POST   | `/api/apply/:job_id`                 | Job seekers apply for a specific job.            |
| GET    | `/api/applications/:employer_id`     | Employers view applications for their job listings. |
| POST   | `/api/applications/:application_id`  | Update the status of a job application.          |
| GET    | `/api/notifications/:user_id`        | Fetch notifications for a user.                  |

---

### **Usage Instructions**

#### **For Job Seekers**:
1. **Login/Sign Up**: Register or log in to your account.
2. **Search for Jobs**: Use filters to find jobs based on keywords or location.
3. **Apply for Jobs**: Submit your resume and track the status of your applications.

#### **For Employers**:
1. **Post Jobs**: Post job openings with detailed descriptions and requirements.
2. **Review Applicants**: Access and review applications from job seekers.

---
