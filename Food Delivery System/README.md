## **Food Delivery System**
### **Project Overview**
The **Food Delivery System** is a web-based platform that allows users to order food online, browse various restaurants, and track their delivery in real-time. The system also allows administrators to manage restaurants, orders, and users, and delivery personnel to view and handle assigned orders. The project is built to provide a seamless food delivery experience for both customers and administrators, offering intuitive interfaces, secure transactions, and efficient delivery handling.

---

### **Features**

#### **Customer Features**:
1. **User Authentication**:
   - Customers can securely log in or sign up.
   - Role-based access for customers and delivery personnel.

2. **Browse Restaurants and Menu**:
   - Browse multiple restaurants and their respective menus.
   - View ratings, prices, and availability of food items.

3. **Place Orders**:
   - Add food items to the cart, modify the cart, and proceed to checkout.
   - Secure payment gateway integration for transactions.

4. **Order Tracking**:
   - Real-time tracking of order preparation and delivery status.

5. **Order History & Feedback**:
   - View past orders and leave reviews for restaurants and delivery personnel.

#### **Admin Features**:
1. **Manage Restaurants**:
   - Admins can add, update, or delete restaurant profiles and menus.
   - Monitor restaurant performance and order history.

2. **Manage Orders**:
   - Admins can view all orders, update their status, and resolve any issues.

3. **User Management**:
   - Manage customer and delivery personnel accounts.
   - Handle user permissions and resolve account-related queries.

4. **Report Generation**:
   - Generate reports for order history, restaurant performance, and user activity.

#### **Delivery Personnel Features**:
1. **View and Accept Orders**:
   - View assigned orders and accept them for delivery.
   
2. **Pick-up and Deliver Orders**:
   - Pick up orders from restaurants and update the system when the order is delivered.

3. **Delivery History**:
   - View delivery history and ratings from customers.

---

### **Technology Stack**

#### **Frontend**:
- **HTML5**, **CSS3**, **JavaScript** (React.js or Vue.js) for creating dynamic user interfaces.
- **Bootstrap** or **Tailwind CSS** for responsive design.

#### **Backend**:
- **Node.js** with **Express.js** for handling server-side logic.
- **RESTful API** for communication between frontend and backend.

#### **Database**:
- **MySQL** or **MongoDB** for storing data related to users, restaurants, orders, and deliveries.

#### **Authentication & Security**:
- **JWT (JSON Web Tokens)** for user authentication and session management.
- **Encryption** for sensitive data (passwords, payment details).

#### **Payment Integration**:
- **Stripe** or **PayPal** for secure payment processing.

### **Flowchart**  

![alt text](<Food Delivery System.jpg>)  


### **System Architecture**

1. **User Authentication**:
   - Users can log in and sign up with secure password hashing and JWT-based session management.

2. **Restaurant and Menu Management**:
   - Admins can add restaurants, update menus, and manage food items and pricing.

3. **Order Processing**:
   - Customers can browse restaurants, select items, and place orders.
   - After payment, orders are sent to the respective restaurant, and delivery agents are notified.

4. **Real-Time Order Tracking**:
   - Customers can track their orders in real-time, from preparation to delivery.

5. **Delivery Management**:
   - Delivery personnel can view assigned orders, pick them up, and mark them as delivered once completed.

---

### **Database Schema (Simplified)**

#### **Users Table**:
| Field      | Type    | Description                              |
|------------|---------|------------------------------------------|
| user_id    | INT     | Primary key for user identification.      |
| name       | VARCHAR | Full name of the user.                   |
| email      | VARCHAR | Email used for login.                    |
| password   | VARCHAR | Hashed password for user authentication. |
| role       | ENUM    | Role of the user (Customer, Admin, Delivery). |

#### **Restaurants Table**:
| Field          | Type      | Description                          |
|----------------|-----------|--------------------------------------|
| restaurant_id  | INT       | Primary key for restaurant identification.|
| name           | VARCHAR   | Name of the restaurant.              |
| location       | VARCHAR   | Location of the restaurant.          |
| menu_items     | JSON      | Menu details (items, prices, etc.).  |

#### **Orders Table**:
| Field          | Type      | Description                          |
|----------------|-----------|--------------------------------------|
| order_id       | INT       | Primary key for order identification.|
| user_id        | INT       | Foreign key referencing the customer who placed the order. |
| restaurant_id  | INT       | Foreign key referencing the restaurant.|
| items          | JSON      | List of food items ordered.          |
| total_price    | DECIMAL   | Total order price.                   |
| status         | ENUM      | Status of the order (Pending, In Progress, Delivered). |
| delivery_id    | INT       | Foreign key referencing delivery personnel handling the order.|

#### **Deliveries Table**:
| Field          | Type      | Description                          |
|----------------|-----------|--------------------------------------|
| delivery_id    | INT       | Primary key for delivery identification. |
| order_id       | INT       | Foreign key referencing the associated order. |
| delivery_status| ENUM      | Status of the delivery (Assigned, Picked, Delivered). |

---

### **API Endpoints**

| Method | Endpoint                   | Description                                  |
|--------|----------------------------|----------------------------------------------|
| POST   | `/api/login`                | User login for authentication.               |
| POST   | `/api/register`             | User registration for new accounts.          |
| GET    | `/api/restaurants`          | Fetch all restaurants and their menu items.  |
| POST   | `/api/orders`               | Place an order for selected menu items.      |
| GET    | `/api/orders/:userId`       | View customer order history.                 |
| PUT    | `/api/orders/:orderId`      | Update the status of an order.               |
| GET    | `/api/admin/orders`         | Admin access to manage all orders.           |
| POST   | `/api/admin/restaurants`    | Admin can add a new restaurant.              |
| PUT    | `/api/admin/restaurants/:id`| Admin can update restaurant details.         |
| GET    | `/api/deliveries`           | Delivery personnel can view assigned orders. |
| PUT    | `/api/deliveries/:id`       | Delivery personnel can update the status of an order. |


### **Usage Instructions**

#### **Customer**:
1. **Sign Up / Login**: Use credentials to log in or sign up if you're a new user.
2. **Browse Restaurants**: Explore the restaurants and menus available for ordering.
3. **Place an Order**: Add desired items to the cart and proceed to payment.
4. **Track Orders**: Follow the progress of your order from preparation to delivery.
5. **Leave Feedback**: Review the restaurant and delivery experience.

#### **Admin**:
1. **Login as Admin**: Use admin credentials to log in to the admin dashboard.
2. **Manage Restaurants**: Add, update, or remove restaurants and menus.
3. **View Orders**: Manage and monitor all orders placed in the system.
4. **Generate Reports**: Create reports on order statistics, restaurant performance, and user activity.

#### **Delivery Personnel**:
1. **Login as Delivery Personnel**: Access the delivery portal to view assigned orders.
2. **Manage Deliveries**: Accept orders, update status, and complete deliveries.
3. **Track Delivery History**: View your past deliveries and ratings.

---
