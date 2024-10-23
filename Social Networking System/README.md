# **Social Networking System**
### **Project Overview**

The **Social Networking System** is a web-based platform that allows users to connect with others, share posts, and interact with content. Users can manage profiles, create and view posts, like, comment, or share, as well as send and receive friend requests. The platform provides real-time notifications and messaging, making it a comprehensive social networking experience.

---

### **Features**

#### **User Authentication**:
1. **Sign-Up & Login**:
   - Users can sign up by providing basic information (email, username, password).
   - Secure login with encrypted credentials.
   
2. **Password Recovery**:
   - Users can recover their password via email if they forget their login credentials.

#### **User Profile Management**:
1. **View and Edit Profile**:
   - Users can create and edit personal profiles, including adding profile pictures, bio, contact information, etc.
   
2. **Account Settings**:
   - Change account details like password, privacy settings, and notification preferences.

#### **Post Management**:
1. **Create Posts**:
   - Users can create text posts, upload images, and share videos.
   - Real-time post publishing, making it immediately visible on their timeline and the timelines of their friends or followers.

2. **Interact with Posts**:
   - Users can like, comment, and share posts from other users.
   - Real-time updates for likes and comments, allowing users to engage actively with content.

#### **Friend Management**:
1. **Friend Requests**:
   - Users can search for other users and send friend requests.
   - Accept or decline incoming friend requests.

2. **Manage Friends**:
   - Add, remove, or block friends easily.
   - View a list of friends and their profiles.

#### **Search and Discover**:
- **User Search**: Allows users to search for others by name or email, making it easy to find and connect with new friends.

#### **Notifications**:
1. **Post Interactions**:
   - Real-time notifications for likes, comments, and shares on user posts.
   
2. **Friendship Activities**:
   - Notifications for new friend requests, accepted requests, and profile views.
   
3. **System Alerts**:
   - Notify users of important actions like new messages or updates.

#### **Messaging System**:
- **Direct Messaging**: Users can send and receive private messages with friends.
- **Group Messaging**: Allows users to create group chats with multiple friends.

#### **News Feed**:
1. **View Posts**:
   - The news feed displays a live stream of posts from friends and people the user follows.
   
2. **Trending Posts**:
   - Highlights trending content based on user engagement (likes, comments, shares).

#### **Security Features**:
- **Encryption**: All sensitive data, such as passwords and messages, is encrypted.
- **Session Management**: Users' sessions are managed securely to prevent unauthorized access.

---

### **Technology Stack**

#### **Frontend**:
- **HTML5**, **CSS3**, **JavaScript**: For designing a responsive and interactive user interface.
- **React.js** or **Vue.js**: For dynamic rendering of the user dashboard, profile, and post updates.

#### **Backend**:
- **Node.js** with **Express.js**: To handle API requests, authentication, and the overall business logic of user interactions and data storage.
- **RESTful API**: For communication between the frontend and backend.

#### **Database**:
- **MongoDB** or **MySQL**: To store user information, posts, comments, likes, and friend connections.
- **Schema** includes tables for users, posts, likes, comments, friends, and notifications.

#### **Authentication and Security**:
- **JWT (JSON Web Token)**: For user authentication and secure session management.
- **bcrypt**: To hash and securely store user passwords.

### Flowchart  
![alt text](<Social Networking System.jpg>)  


### **System Architecture**

1. **User Authentication and Management**:
   - Secure login and registration with role-based access control for users.
   
2. **Post and Interaction Management**:
   - Manage posts, likes, comments, and shares with real-time updates on user timelines.

3. **Friend Management and Social Interactions**:
   - Allow users to connect with friends, send friend requests, and interact with content.

4. **Messaging and Notifications**:
   - Real-time messaging and notifications system to keep users engaged with the platform.

5. **Error Handling**:
   - Comprehensive error handling for invalid inputs, security issues, and system errors with feedback to the user.

---

### **Database Schema (Simplified)**

#### **Users Table**:
| Field       | Type      | Description                         |
|-------------|-----------|-------------------------------------|
| user_id     | INT       | Primary key for user identification.|
| name        | VARCHAR   | Full name of the user.              |
| email       | VARCHAR   | Email for login and identification. |
| password    | VARCHAR   | Hashed password for secure login.   |
| bio         | TEXT      | User’s personal biography.          |
| profile_pic | BLOB      | User’s profile picture.             |

#### **Posts Table**:
| Field       | Type      | Description                               |
|-------------|-----------|-------------------------------------------|
| post_id     | INT       | Primary key for post identification.      |
| user_id     | INT       | Foreign key linking to the users table.   |
| content     | TEXT      | The post content (text, image, video).    |
| created_at  | DATETIME  | Time the post was created.                |

#### **Friends Table**:
| Field         | Type      | Description                               |
|---------------|-----------|-------------------------------------------|
| friend_id     | INT       | Primary key for friend relation.          |
| user_id       | INT       | Foreign key linking to the users table.   |
| friend_user_id| INT       | ID of the user’s friend.                  |

#### **Likes and Comments Table**:
| Field         | Type      | Description                               |
|---------------|-----------|-------------------------------------------|
| like_id       | INT       | Primary key for like identification.      |
| comment_id    | INT       | Primary key for comment identification.   |
| post_id       | INT       | Foreign key linking to the posts table.   |
| user_id       | INT       | Foreign key linking to the users table.   |
| like_or_comment | ENUM    | Defines if it’s a like or comment action. |

---

### **API Endpoints**

| Method | Endpoint                            | Description                                      |
|--------|-------------------------------------|--------------------------------------------------|
| POST   | `/api/register`                     | User registration for new accounts.              |
| POST   | `/api/login`                        | User login and authentication.                   |
| GET    | `/api/users/:user_id/profile`       | Fetch the profile details of a user.             |
| POST   | `/api/posts`                        | Create a new post.                               |
| GET    | `/api/posts/:post_id`               | Retrieve a specific post.                        |
| POST   | `/api/posts/:post_id/like`          | Like a specific post.                            |
| POST   | `/api/posts/:post_id/comment`       | Comment on a specific post.                      |
| GET    | `/api/friends/:user_id`             | Retrieve a user’s friends list.                  |

---

### **Usage Instructions**

1. **Register and Login**: Sign up or log in to access your account.
2. **Create a Post**: Share your thoughts by creating posts, including text, images, and videos.
3. **Interact with Content**: Like, comment, and share posts from your friends.
4. **Search for Friends**: Use the search feature to find and connect with new users.
5. **Send Messages**: Use direct messaging to communicate privately with other users.

---
