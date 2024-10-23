# **Content Management System**
### **Project Overview**
The **Content Management System (CMS)** is a platform designed to simplify the creation, management, and publication of digital content on websites. It allows administrators to manage users, control site settings, and organize content, while editors can create, edit, and publish content. Viewers, on the other hand, can access and view published content. The system ensures a seamless content management experience with role-based access control and easy-to-use features for all users.

---

### **Features**

#### **Admin Features**:
1. **User Authentication**:
   - Secure login and registration with role-based access control for admins, editors, and viewers.

2. **User Management**:
   - Admins can add, update, and delete users, assigning different roles such as admin, editor, or viewer.
   - Manage user permissions based on roles.

3. **Site Configuration**:
   - Admins can configure site-wide settings including themes, SEO configurations, and content visibility.
   - Manage overall site layout and custom settings.

4. **Content Management**:
   - Create, edit, and delete content including articles, pages, and media files (images, videos).
   - Publish content immediately or save as drafts for future publication.

5. **Categories and Tags**:
   - Organize content into categories and tags for easier navigation and searchability.

6. **View Reports**:
   - Generate reports on content performance, including views, likes, and comments.

#### **Editor Features**:
1. **Content Creation**:
   - Editors can create, edit, and delete content (text, images, videos).
   - Manage content drafts and review before publishing.

2. **Content Publishing**:
   - Editors have the option to publish content immediately or save it as a draft for further editing.
   - Assign tags and categories to content for better organization.

3. **Media Management**:
   - Upload and manage media files, such as images and videos, within the content editor.

#### **Viewer Features**:
1. **View Published Content**:
   - Viewers can browse the published content on the platform.
   - Access content categories and tagged articles for easy navigation.
   
2. **Restricted Content Access**:
   - Some content may be restricted and require the viewer to sign in or upgrade their role to access it.

#### **Security Features**:
- **Role-Based Access Control (RBAC)**: Permissions are granted based on user roles (admin, editor, viewer) to ensure secure access to functionalities.
- **Password Encryption**: All passwords are encrypted for secure user authentication.
- **Content Moderation**: Admins can review content before it is published to ensure quality and consistency.

---

### **Technology Stack**

#### **Frontend**:
- **HTML5**, **CSS3**, **JavaScript** (frameworks like **React.js** or **Vue.js** for dynamic UI).
- **Bootstrap** or **Tailwind CSS** for responsive and modern design.
- Rich text editors like **CKEditor** or **TinyMCE** for content creation.

#### **Backend**:
- **Node.js** with **Express.js** for handling server-side operations and APIs.
- **RESTful API** for communication between frontend and backend.

#### **Database**:
- **MySQL** or **PostgreSQL** for relational data management, storing users, content, categories, tags, and media.

#### **Authentication and Security**:
- **JWT (JSON Web Token)** for secure authentication.
- **Encryption** for sensitive data such as passwords.

### Flowchart  

![alt text](<Content Management System.jpg>)  


### **System Architecture**

1. **User Authentication**:
   - Role-based access control ensures that users with different roles (admin, editor, viewer) have specific permissions.
   
2. **Content Creation and Management**:
   - Admins and editors can create content by providing a title, description, and body text, and uploading media files.
   - Content can be saved as drafts or published immediately.

3. **Categories and Tagging**:
   - Content is organized into categories and tagged to improve searchability and filter options.

4. **Media Management**:
   - The platform provides a central location for uploading and managing media files (images, videos) to be used within the content.

5. **Content Display and Access Control**:
   - Viewers can browse and access content based on their roles and permissions.
   - Some content may be restricted to specific users based on roles.

---

### **Database Schema (Simplified)**

#### **Users Table**:
| Field      | Type    | Description                                   |
|------------|---------|-----------------------------------------------|
| user_id    | INT     | Primary key for user identification.          |
| name       | VARCHAR | Full name of the user.                        |
| email      | VARCHAR | Email used for login.                         |
| password   | VARCHAR | Hashed password for secure login.             |
| role       | ENUM    | Role of the user (Admin, Editor, Viewer).     |

#### **Content Table**:
| Field         | Type      | Description                               |
|---------------|-----------|-------------------------------------------|
| content_id    | INT       | Primary key for content identification.   |
| title         | VARCHAR   | Title of the content.                     |
| body_text     | TEXT      | Main body of the content (article, page). |
| status        | ENUM      | Published or draft status of the content. |
| published_at  | DATETIME  | Date and time when the content is published. |

#### **Categories Table**:
| Field          | Type      | Description                              |
|----------------|-----------|------------------------------------------|
| category_id    | INT       | Primary key for category identification. |
| category_name  | VARCHAR   | Name of the category.                    |

#### **Tags Table**:
| Field          | Type      | Description                              |
|----------------|-----------|------------------------------------------|
| tag_id         | INT       | Primary key for tag identification.      |
| tag_name       | VARCHAR   | Name of the tag.                         |

#### **Media Table**:
| Field          | Type      | Description                              |
|----------------|-----------|------------------------------------------|
| media_id       | INT       | Primary key for media identification.    |
| media_type     | VARCHAR   | Type of media (image, video).            |
| media_url      | VARCHAR   | URL/path of the media file.              |

---

### **API Endpoints**

| Method | Endpoint                   | Description                                  |
|--------|----------------------------|----------------------------------------------|
| POST   | `/api/login`                | User login for authentication.               |
| POST   | `/api/register`             | User registration for new accounts.          |
| GET    | `/api/content`              | Fetch all published content.                 |
| POST   | `/api/content`              | Create new content (for admins/editors).     |
| PUT    | `/api/content/:id`          | Update content (for admins/editors).         |
| DELETE | `/api/content/:id`          | Delete content (for admins).                 |
| GET    | `/api/categories`           | Fetch all content categories.                |
| POST   | `/api/categories`           | Create new categories (for admins).          |
| GET    | `/api/tags`                 | Fetch all content tags.                      |
| POST   | `/api/tags`                 | Create new tags (for admins).                |

---

### **Usage Instructions**

#### **Admin**:
1. **Login as Admin**: Use admin credentials to access the dashboard.
2. **Manage Users**: Add, update, and delete users, assigning roles and permissions.
3. **Create/Manage Content**: Create articles, manage categories, and publish content.
4. **Manage Site Settings**: Configure site appearance, settings, and SEO options.

#### **Editor**:
1. **Login as Editor**: Use editor credentials to access the dashboard.
2. **Create/Edit Content**: Create new articles or edit existing ones.
3. **Publish or Save as Draft**: Publish content immediately or save it for future updates.

#### **Viewer**:
1. **Browse Content**: View published articles and browse through categories.
2. **Login for Restricted Access**: For restricted content, log in to view.

---
