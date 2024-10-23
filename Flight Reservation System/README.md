## **Flight Reservation System**
### **Project Overview**
The **Flight Reservation System** is a web-based application that allows customers to search and book flights, and provides admin users with the ability to manage flights, bookings, and customer information. The system ensures a seamless user experience for both flight booking and management, offering a user-friendly interface and efficient backend support.

---

### **Features**

#### **Customer (User) Features**:
1. **User Authentication**:
   - Secure user login and sign-up system.
   - Role-based authentication for customers and admins.

2. **Search for Flights**:
   - Search flights based on source, destination, date, and number of passengers.
   - View a list of available flights with details such as airline, price, and seat availability.

3. **Flight Booking**:
   - Select flights and seat preferences.
   - Proceed to payment gateway for secure transactions.

4. **View Booking Details**:
   - After booking, users can view details of their reservation.
   - Option to modify or cancel bookings if needed.

5. **Make Payment**:
   - Integration with payment gateway to process ticket payments securely.

6. **Booking History**:
   - Users can track past and upcoming reservations in their account dashboard.

#### **Admin Features**:
1. **Manage Flights**:
   - Admins can add new flights, update flight schedules, or cancel existing flights.
   - Manage details such as source, destination, timings, seat availability, and pricing.

2. **Manage Bookings**:
   - Admins can view and manage customer bookings.
   - Handle cancellations, modifications, and generate booking reports.

3. **Manage Users**:
   - Admins can manage registered users, including viewing user profiles and resolving account issues.

4. **Generate Reports**:
   - Admins can generate reports on flight bookings, revenue, and seat availability.

5. **System Dashboard**:
   - Admins have access to an integrated dashboard to oversee all system activities.

---

### **Technology Stack**

#### **Frontend**:
- **HTML5**, **CSS3**, **JavaScript** (React.js or Vue.js) for creating an interactive, responsive user interface.
- **Bootstrap** or **Material UI** for responsive and sleek design.

#### **Backend**:
- **Node.js** with **Express.js** for server-side operations.
- **RESTful API** for communication between the frontend and backend.

#### **Database**:
- **MySQL** or **PostgreSQL** for handling relational data such as flight schedules, user details, and bookings.

#### **Authentication & Security**:
- **JWT (JSON Web Tokens)** for user authentication and session management.
- **Encryption** for securing sensitive data such as passwords and payment details.

### **Flowchart**  
![alt text](<Flight Reservation System.jpg>)  


### **System Architecture**

1. **User Authentication**:
   - Secure login system with role-based access for both customers and admins.
   - Passwords are encrypted and stored in the database using hashing algorithms.

2. **Flight Search & Booking**:
   - Users can search for available flights by specifying source, destination, and date.
   - The system queries the database and retrieves a list of available flights matching the criteria.

3. **Booking & Payment**:
   - Users can book a flight and proceed to make payments via an integrated payment gateway.
   - After successful payment, a booking reference is generated, and users can view or modify their bookings.

4. **Admin Control**:
   - Admins can manage flight schedules, handle booking requests, and generate various reports.
   - The admin dashboard provides real-time updates on bookings, flight availability, and other relevant data.

---

### **Database Schema (Simplified)**

#### **Users Table**:
| Field      | Type    | Description                              |
|------------|---------|------------------------------------------|
| user_id    | INT     | Primary key for user identification.      |
| name       | VARCHAR | Full name of the user.                   |
| email      | VARCHAR | Email for login purposes.                |
| password   | VARCHAR | Hashed password for user authentication. |
| role       | ENUM    | Role of the user (Admin or Customer).    |

#### **Flights Table**:
| Field          | Type      | Description                          |
|----------------|-----------|--------------------------------------|
| flight_id      | INT       | Primary key for flight identification.|
| source         | VARCHAR   | Starting location of the flight.     |
| destination    | VARCHAR   | Ending location of the flight.       |
| departure_time | DATETIME  | Scheduled departure time.            |
| arrival_time   | DATETIME  | Scheduled arrival time.              |
| price          | DECIMAL   | Price of the flight ticket.          |
| available_seats| INT       | Number of seats available for booking.|

#### **Bookings Table**:
| Field          | Type      | Description                          |
|----------------|-----------|--------------------------------------|
| booking_id     | INT       | Primary key for booking identification.|
| user_id        | INT       | Foreign key referencing the user who booked. |
| flight_id      | INT       | Foreign key referencing the flight.  |
| seat_number    | INT       | The seat number assigned to the booking.|
| payment_status | ENUM      | Status of payment (Pending, Completed).|

---

### **API Endpoints**

| Method | Endpoint                   | Description                                  |
|--------|----------------------------|----------------------------------------------|
| POST   | `/api/login`                | User login for authentication.               |
| POST   | `/api/register`             | User registration for new accounts.          |
| GET    | `/api/flights`              | Get available flights based on search criteria. |
| POST   | `/api/bookings`             | Create a new booking after selecting a flight. |
| GET    | `/api/bookings/:userId`     | View user's bookings (requires authentication).|
| PUT    | `/api/bookings/:bookingId`  | Modify or cancel a booking.                  |
| GET    | `/api/admin/flights`        | Admin access to manage flight data.          |
| POST   | `/api/admin/flights`        | Admin can add new flights.                   |
| PUT    | `/api/admin/flights/:id`    | Admin can update flight details.             |
| DELETE | `/api/admin/flights/:id`    | Admin can delete a flight.                   |

---

### **Usage Instructions**

#### **Customer**:
1. **Login**: Use your credentials to log in or sign up if you're a new user.
2. **Search Flights**: Enter your flight search criteria (source, destination, travel date).
3. **Book Flight**: Select a flight, choose your seat, and proceed to payment.
4. **View Bookings**: Check the details of your booked flights and manage them if necessary.
5. **Payment**: Complete your booking with a secure payment method.

#### **Admin**:
1. **Login as Admin**: Use admin credentials to log in to the admin dashboard.
2. **Manage Flights**: Add, update, or remove flights from the schedule.
3. **View Bookings**: Monitor flight bookings and manage customer reservations.
4. **Generate Reports**: Generate booking reports, revenue stats, and flight schedules.

---
