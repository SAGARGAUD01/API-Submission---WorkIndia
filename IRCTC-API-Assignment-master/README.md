## Railway Management System
A Railway Management System like IRCTC, where users can check train availability, seat availability, and book seats. It handles user registration, login, and provides role-based access for admin operations.

## Features
User Registration & Login: Allows users to register and log in to their accounts.
Role-Based Access: Admin users can add and update train details, while regular users can book seats.
Real-Time Booking: Ensures seat availability is managed in real-time to prevent overbooking.
Secure Endpoints: Protects endpoints with JWT for authenticated users and API keys for admin operations.

## Tech Stack
Backend: Node.js, Express.js
Database: PostgreSQL
Authentication: JWT (JSON Web Tokens)
Environment Management: dotenv

## Setup
Prerequisites
Node.js and npm installed
PostgreSQL installed and running

## Database Schema
### Users Table

```sh
Column	Type	Constraints
id	SERIAL	PRIMARY KEY
username	VARCHAR	UNIQUE, NOT NULL
password	VARCHAR	NOT NULL
role	VARCHAR	NOT NULL, CHECK (role IN ('admin', 'user'))
```

## Trains Table
```sh
Column	Type	Constraints
id	SERIAL	PRIMARY KEY
name	VARCHAR	NOT NULL
source	VARCHAR	NOT NULL
destination	VARCHAR	NOT NULL
total_seats	INTEGER	NOT NULL
available_seats	INTEGER	NOT NULL
```

Bookings Table
```sh
Column	Type	Constraints
id	SERIAL	PRIMARY KEY
user_id	INTEGER	REFERENCES users(id)
train_id	INTEGER	REFERENCES trains(id)
booking_date	TIMESTAMP	DEFAULT CURRENT_TIMESTAMP
```

## Installation

Install dependencies:
```sh
npm install
Set up environment variables:
```
env
```sh
PORT=3000
DATABASE_URL=postgresql://user:password@localhost:5432/railway
JWT_SECRET=your_jwt_secret
ADMIN_API_KEY=your_admin_api_key
```