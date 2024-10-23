# **Bus Reservation System**
### **Project Overview**
The **Bus Reservation System** is a web-based platform that allows users to search for buses, book tickets, and manage their reservations seamlessly. The system is designed to enhance the user experience by providing features such as real-time seat availability, secure payments, and booking history management. It offers different functionalities based on user roles, such as travelers, administrators, and operators, ensuring that bus reservations are handled efficiently.

---

### **Features**

#### **User Features**:
1. **User Registration and Login**:
   - Secure login and registration process for new and returning users.
   - Password encryption and role-based access for security.

2. **Bus Search**:
   - Users can search for buses by providing details such as the source, destination, and travel date.
   - View available buses with details like bus type, fare, and seat availability.

3. **Seat Selection**:
   - Interactive seat selection feature where users can choose their preferred seats from available ones.
   - View bus layout and availability in real-time.

4. **Payment Processing**:
   - Secure payment gateway integration to handle payments for ticket bookings.
   - Payment confirmation and ticket generation upon successful payment.

5. **Booking History**:
   - Users can view their booking history, including previous and upcoming reservations.
   - Details such as journey date, bus details, and fare are displayed.

6. **Ticket Management**:
   - After booking, users receive an electronic ticket via email or can view it directly from the dashboard.
   - Option to download or print the ticket.

7. **Booking Cancellation**:
   - Users can cancel their upcoming bookings if allowed by the system’s policies.
   - Refund processing is handled based on the cancellation rules.

---

### **Admin/Operator Features**:
1. **Bus Management**:
   - Add, update, and delete bus schedules, including routes, timings, and pricing.
   - Manage bus capacity, seat configuration, and availability.

2. **Route and Fare Management**:
   - Define and manage routes, including source and destination points.
   - Set and update fares for different routes and bus categories (e.g., AC, non-AC).

3. **Booking Management**:
   - View and manage all bookings made on the platform.
   - Oversee user cancellations and refund processing.

4. **Reports**:
   - Generate reports on total bookings, cancellations, and revenue generated.
   - View bus occupancy rates and seat utilization metrics.

---

### **Technology Stack**

#### **Frontend**:
- **HTML5**, **CSS3**, **JavaScript** for basic web structure and interactivity.
- **React.js** or **Vue.js** for dynamic user interfaces and smooth navigation.
- **Bootstrap** or **Tailwind CSS** for responsive and modern design.
- **Interactive seat selection feature** using JavaScript or jQuery.

#### **Backend**:
- **Node.js** with **Express.js** for server-side operations, handling APIs, and user authentication.
- **RESTful API** to connect the frontend to the backend, facilitating real-time data exchange.

#### **Database**:
- **MySQL** or **PostgreSQL** for managing users, bus schedules, bookings, payments, and more.
- **Database tables** are structured to handle users, buses, routes, bookings, and transaction data.

#### **Payment Integration**:
- **Stripe**, **PayPal**, or similar secure payment gateways for processing payments during ticket booking.
  
#### **Authentication and Security**:
- **JWT (JSON Web Token)** for secure user authentication and session management.
- **Password Encryption** using bcrypt or a similar library for security.

### Flowchart  

![alt text](<Bus Reservation System.jpg>)  


### **System Architecture**

1. **User Authentication and Authorization**:
   - Users log in using credentials or sign up with personal information (name, email, password).
   - Authentication using JWT ensures secure login sessions.

2. **Bus Search and Booking**:
   - Users enter search parameters (source, destination, date) to view a list of available buses.
   - The system queries the database for buses that match the user's search and returns relevant results.

3. **Seat Selection and Payment**:
   - Users select available seats, proceed to payment, and confirm their booking.
   - Upon successful payment, the system stores the booking and generates a ticket.


---

### **Database Schema (Simplified)**

#### **Users Table**:
| Field        | Type      | Description                              |
|--------------|-----------|------------------------------------------|
| user_id      | INT       | Primary key for user identification.     |
| name         | VARCHAR   | Full name of the user.                   |
| email        | VARCHAR   | Email used for login.                    |
| password     | VARCHAR   | Hashed password for secure login.        |
| role         | ENUM      | Role of the user (Admin, User, Operator).|

#### **Buses Table**:
| Field          | Type      | Description                              |
|----------------|-----------|------------------------------------------|
| bus_id         | INT       | Primary key for bus identification.      |
| bus_name       | VARCHAR   | Name or type of the bus (e.g., AC, Non-AC).|
| total_seats    | INT       | Total number of seats in the bus.        |
| fare_per_seat  | DECIMAL   | Fare per seat for this bus.              |

#### **Routes Table**:
| Field          | Type      | Description                              |
|----------------|-----------|------------------------------------------|
| route_id       | INT       | Primary key for route identification.    |
| source         | VARCHAR   | Starting point of the journey.           |
| destination    | VARCHAR   | End point of the journey.                |

#### **Bookings Table**:
| Field          | Type      | Description                              |
|----------------|-----------|------------------------------------------|
| booking_id     | INT       | Primary key for booking identification.  |
| user_id        | INT       | Foreign key linking to the users table.  |
| bus_id         | INT       | Foreign key linking to the buses table.  |
| seats_booked   | INT       | Number of seats booked.                  |
| payment_status | ENUM      | Payment status (Pending, Completed).     |

#### **Payments Table**:
| Field          | Type      | Description                              |
|----------------|-----------|------------------------------------------|
| payment_id     | INT       | Primary key for payment identification.  |
| booking_id     | INT       | Foreign key linking to the bookings table.|
| amount_paid    | DECIMAL   | Total amount paid by the user.           |
| payment_date   | DATETIME  | Date and time of the payment.            |

---

### **API Endpoints**

| Method | Endpoint                     | Description                                  |
|--------|------------------------------|----------------------------------------------|
| POST   | `/api/login`                  | User login for authentication.               |
| POST   | `/api/register`               | User registration for new accounts.          |
| GET    | `/api/buses`                  | Fetch available buses based on user input.   |
| POST   | `/api/booking`                | Create a new booking (seat selection and payment).|
| GET    | `/api/bookings/:user_id`      | Fetch booking history for a user.            |
| DELETE | `/api/bookings/:booking_id`   | Cancel a specific booking.                   |
| GET    | `/api/admin/bookings`         | Fetch all bookings for the admin.            |

---

### **Usage Instructions**

#### **User**:
1. **Login/Sign Up**: Log in with your credentials or sign up for a new account.
2. **Search for Buses**: Enter travel details (source, destination, date) and view available buses.
3. **Book Tickets**: Select your preferred seats, proceed with payment, and receive a ticket.
4. **Manage Bookings**: View your booking history and cancel tickets if needed.

---
