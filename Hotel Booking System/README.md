## **Hotel Booking System**
### **Project Overview**
The **Hotel Booking System** is a web-based platform designed to manage hotel room reservations for guests and administrators. It allows guests to search for available rooms, view details, make bookings, and manage their reservations. Administrators can manage room inventory, confirm or cancel guest bookings, and generate reports on hotel occupancy and revenue. The system ensures a smooth and efficient booking process, providing users with a seamless experience.

### **Features**
1. **User Authentication & Role-Based Access**:
   - Secure login system for Guests and Admins.
   - Role-specific dashboards: Guest and Admin functionalities are separated.

2. **Guest Functionalities**:
   - **Search for Rooms**: Guests can search for available rooms based on dates, room type, and preferences.
   - **View Room Details**: View room amenities, size, price, and availability.
   - **Make Bookings**: Select room, enter personal information, and confirm the booking with payment.
   - **Booking History**: View and manage previous and upcoming bookings.
   - **Modify or Cancel Bookings**: Guests can modify or cancel their bookings before the check-in date.

3. **Admin Functionalities**:
   - **Manage Hotel Information**: Add or update hotel details, including services, contact info, and policies.
   - **Manage Rooms**: Add, update, or remove rooms, set room availability, and adjust pricing.
   - **Manage Bookings**: View guest bookings, confirm or cancel reservations.
   - **Generate Reports**: Admins can generate reports on room occupancy, revenue, and guest activity.


### **Technology Stack**
- **Frontend**: 
  - HTML5, CSS3, JavaScript (React or Vue.js for interactive elements).
  - Bootstrap or Tailwind CSS for responsive design.
- **Backend**: 
  - Node.js with Express.js for server-side functionality.
  - RESTful APIs to handle user authentication, bookings, and room management.
- **Database**: 
  - MySQL or PostgreSQL for storing hotel data, bookings, room information, and user details.
- **Authentication**: 
  - JWT (JSON Web Token) for secure user authentication and role-based access.
- **Payment Processing** (optional): 
  - Integration with Stripe or PayPal for processing payments during bookings.

### Flowchart  

![alt text](<Hotel Booking System.jpg>)  


### **Usage**
#### **Admin**:
1. **Login as Admin** to manage hotel rooms, view bookings, and generate reports.
2. Navigate to "Hotel Management" to update hotel details such as room types, rates, and services.
3. Use "Room Management" to add new rooms, update pricing, or mark rooms as unavailable.
4. View guest bookings in "Booking Management" to confirm or cancel bookings.
5. Generate occupancy and revenue reports for a specific period in "Reports."

#### **Guest**:
1. **Login as Guest** or create an account to start booking hotel rooms.
2. Use the search functionality to find available rooms based on check-in and check-out dates.
3. View room details such as price, amenities, and availability before making a reservation.
4. After booking, view and manage your reservation in "Booking History," where you can also cancel or modify the booking.

### **API Endpoints**
| Method | Endpoint                        | Description                                |
|--------|----------------------------------|--------------------------------------------|
| POST   | `/api/login`                     | Login to the system                        |
| POST   | `/api/register`                  | Register a new user                        |
| GET    | `/api/rooms`                     | Get a list of available rooms              |
| GET    | `/api/rooms/:id`                 | Get details of a specific room             |
| POST   | `/api/bookings`                  | Make a new room booking                    |
| GET    | `/api/bookings`                  | Get list of bookings (for admins)          |
| GET    | `/api/bookings/:userId`          | Get bookings for a specific user (for guests)|
| PUT    | `/api/bookings/:id`              | Modify a booking                           |
| DELETE | `/api/bookings/:id`              | Cancel a booking                           |
| GET    | `/api/reports/occupancy`         | Generate occupancy report (for admins)     |
| GET    | `/api/reports/revenue`           | Generate revenue report (for admins)       |

### **Database Schema (Simplified)**
#### **Users**:
| Field        | Type      | Description                              |
|--------------|-----------|------------------------------------------|
| id           | INT       | Primary key, auto-incremented            |
| name         | VARCHAR   | Name of the user                         |
| email        | VARCHAR   | User's email address (for login)         |
| password     | VARCHAR   | Hashed password                          |
| role         | ENUM      | Role of the user (admin/guest)           |

#### **Rooms**:
| Field        | Type      | Description                              |
|--------------|-----------|------------------------------------------|
| id           | INT       | Primary key, auto-incremented            |
| room_number  | VARCHAR   | Unique room number                       |
| room_type    | VARCHAR   | Type of room (single, double, suite)     |
| price        | DECIMAL   | Price per night                          |
| availability | BOOLEAN   | Room availability status                 |

#### **Bookings**:
| Field        | Type      | Description                              |
|--------------|-----------|------------------------------------------|
| id           | INT       | Primary key, auto-incremented            |
| user_id      | INT       | Foreign key (references Users table)     |
| room_id      | INT       | Foreign key (references Rooms table)     |
| check_in     | DATE      | Check-in date                            |
| check_out    | DATE      | Check-out date                           |
| status       | ENUM      | Booking status (confirmed/canceled)      |

---
