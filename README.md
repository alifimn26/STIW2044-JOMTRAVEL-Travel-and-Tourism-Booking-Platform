# ✈️ JOMTRAVEL — Travel and Tourism Booking Platform

A full-stack web application that allows users to discover travel destinations, explore tour packages, and book trips online. Built with PHP, MySQL, and vanilla JavaScript.

## 📸 Overview

JOMTRAVEL provides an end-to-end travel booking experience — from user registration and authentication to destination browsing, package selection, booking management, and interactive map exploration.

## ✨ Features

- **User Authentication** — Register, sign in, and sign out with secure password hashing
- **Password Recovery** — Reset passwords using security questions
- **Destination Discovery** — Browse 8 curated destinations (Kashmir, Istanbul, Paris, Bali, Dubai, Geneva, Port Blair, Rome)
- **Tour Packages** — Choose from 4 tiers: Bronze (2★), Silver (3★), Gold (4★), Platinum (5★)
- **Booking Management** — Create, view, search, and delete bookings
- **Interactive Maps** — Explore destinations with Mapbox GL JS integration
- **Responsive Design** — Mobile-friendly layout with adaptive navigation

## 🛠️ Tech Stack

| Layer     | Technology                                  |
| --------- | ------------------------------------------- |
| Frontend  | HTML5, CSS3, JavaScript (vanilla)           |
| Backend   | PHP (MySQLi)                                |
| Database  | MySQL                                       |
| Maps      | Mapbox GL JS                                |
| Icons     | FontAwesome, Boxicons, Bootstrap Icons      |
| Fonts     | Google Fonts (Kumbh Sans, Paytone One, Poppins) |

## 🚀 Getting Started

### Prerequisites

- [PHP](https://www.php.net/) 7.4 or higher
- [MySQL](https://www.mysql.com/) 5.7 or higher (or MariaDB)
- A local server environment such as [XAMPP](https://www.apachefriends.org/), [WAMP](https://www.wampserver.com/), or [MAMP](https://www.mamp.info/)

### Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/alifimn26/STIW2044-JOMTRAVEL-Travel-and-Tourism-Booking-Platform.git
   ```

2. **Move the project** into your local server's web root (e.g., `htdocs` for XAMPP).
   You can copy the folder manually or use the command line:

   ```bash
   # macOS / Linux
   cp -r STIW2044-JOMTRAVEL-Travel-and-Tourism-Booking-Platform /path/to/htdocs/jomtravel

   # Windows (Command Prompt)
   xcopy STIW2044-JOMTRAVEL-Travel-and-Tourism-Booking-Platform C:\xampp\htdocs\jomtravel /E /I
   ```

3. **Create the database**

   Open phpMyAdmin or a MySQL client and create the database and tables:

   ```sql
   CREATE DATABASE travel_app;
   USE travel_app;

   CREATE TABLE users (
       id INT AUTO_INCREMENT PRIMARY KEY,
       name VARCHAR(255) NOT NULL,
       email VARCHAR(255) UNIQUE NOT NULL,
       phone VARCHAR(20),
       age INT,
       gender VARCHAR(10),
       address TEXT,
       password VARCHAR(255) NOT NULL,
       security_question VARCHAR(255),
       security_answer VARCHAR(255)
   );

   CREATE TABLE bookings (
       id INT AUTO_INCREMENT PRIMARY KEY,
       user_id INT NOT NULL,
       name VARCHAR(255),
       email VARCHAR(255),
       phone VARCHAR(20),
       age INT,
       gender VARCHAR(10),
       departure_date DATE,
       return_date DATE,
       destination VARCHAR(100),
       package_type VARCHAR(50),
       FOREIGN KEY (user_id) REFERENCES users(id)
   );
   ```

4. **Configure the database connection**

   Open `db.php` and update the credentials if needed:

   ```php
   $conn = new mysqli("localhost", "root", "", "travel_app");
   ```

5. **Start your local server** and open the application in a browser:

   ```
   http://localhost/jomtravel/index.html
   ```

## 📁 Project Structure

```
├── index.html                      # Welcome / landing page
├── signup.html                     # User registration page
├── signin.html                     # User sign-in page
├── home.html                       # Main dashboard (post-login)
├── packages.html                   # Tour package tiers
├── locations.html                  # Destination showcase
├── Booking.html                    # Trip booking form
├── map.html                        # Interactive Mapbox map
├── reset_password.html             # Password recovery page
│
├── db.php                          # Database connection
├── register.php                    # User registration handler
├── login.php                       # Authentication handler
├── logout.php                      # Session destruction
├── insert_booking.php              # Create booking (AJAX)
├── BookingList.php                 # View & manage bookings
├── list_bookings.php               # List bookings endpoint
├── search_booking.php              # Search bookings
├── remove_booking.php              # Delete a booking
├── reset_password_with_security.php # Password reset handler
├── verify_security_question.php    # Security question verification
├── update_password.php             # Password update endpoint
│
├── styles.css                      # Main stylesheet
├── app.js                          # Client-side JavaScript
├── files/                          # Images & media assets
├── Img/                            # Icons & logos
└── html/                           # Alternate page versions
```

## 🔄 User Workflow

1. **Land** on `index.html` — the welcome page
2. **Register** via `signup.html` — creates an account with a security question
3. **Sign in** via `signin.html` — authenticates and starts a session
4. **Browse** destinations on `locations.html` and packages on `packages.html`
5. **Explore** the interactive map on `map.html`
6. **Book** a trip via `Booking.html` — selects a destination, package, and travel dates
7. **Manage** bookings on `BookingList.php` — view, search, or delete bookings
8. **Sign out** via `logout.php`

## 📄 License

This project was developed for the **STIW2044** course. Please refer to the course guidelines for usage and distribution policies.
