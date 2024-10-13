# Assignment Deadline Notification System

## **Overview**  
This project is an automation system that helps students manage their assignment deadlines by providing timely notifications on both desktop and mobile devices. The system is built using a Python-based GUI for user input, Firebase Firestore as the backend for storing assignment details, and Firebase Cloud Messaging (FCM) for push notifications.  

## **Key Features**  
- **User Input via Python GUI**: Students can input assignment details like the subject, description, and due date through a user-friendly Python interface.
- **Firebase Integration**: Assignment details are stored in Firebase Firestore, which serves as a reliable backend.
- **Automatic Deadline Checks**: A scheduler periodically checks for upcoming deadlines (e.g., within 24 hours).
- **Cross-Platform Notifications**: Notifications are sent to the user’s desktop (using `plyer`) and mobile device (using Firebase Cloud Messaging) when a deadline is approaching.

## **Use Case**
The system helps students stay on top of their assignments by providing automatic reminders, ensuring that they are alerted before deadlines. This reduces the likelihood of missing due dates and enhances time management.  

## **Plan Flowchart**

![alt text](<Automated Assignment Reminder.jpg>)

---