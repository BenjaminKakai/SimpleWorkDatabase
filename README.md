**Client Management System - Backend**

**Overview**

This is the backend for the Client Management System, developed using Node.js, Express, and PostgreSQL. The application handles client data, including login authentication with JWT, and supports document uploads associated with each client.

**Prerequisites**

Node.js installed
PostgreSQL installed
A database named clientdb
Installation

**To run this project locally, follow these steps:**

1. Clone the Repository:
git clone https://github.com/BenjaminKakai/clientmanagementbackend.git

cd clientmanagementbackend

2. Install Dependencies: Make sure you have Node.js installed. Then, run:
   npm install

3. Set Up Environment Variables: Create a .env file in the root directory and add the following:
   DATABASE_URL_POOLED=your_database_url
   JWT_SECRET=your_jwt_secret
   
5. Usage
   To start the development server, run:
   node server.js
   This will open the application in your default web browser at http://localhost:3000.

**Database Setup**

**PostgreSQL Commands
**
**1. Database Setup**
PostgreSQL Commands
Connect to the PostgreSQL Database
Open your terminal and run the following command to connect to PostgreSQL as the postgres user:

sudo -u postgres psql

Enter the password for the postgres user when prompted.

Note: You may see a warning message about a collation version mismatch. This is generally not a blocking issue, but you can consider rebuilding the objects in the database if necessary.

**2. Connect to Your Database**
Once in the PostgreSQL command line, connect to your desired database (e.g., clientdb) with the following command:

\c clientdb;

**3. List All Tables**

To view all tables in the clientdb, run:

\dt

**4. Create Tables**
CREATE TABLE clients (
    id SERIAL PRIMARY KEY,
    project VARCHAR(255),
    bedrooms INT,
    budget DECIMAL,
    schedule DATE,
    email VARCHAR(255),
    fullname VARCHAR(255),
    phone VARCHAR(20),
    quality VARCHAR(20),
    conversation_status VARCHAR(50)
);

CREATE TABLE payment_details (
    id SERIAL PRIMARY KEY,
    client_id INT REFERENCES clients(id),
    amount_paid DECIMAL,
    payment_duration INT,
    total_amount DECIMAL,
    balance DECIMAL,
    payment_date DATE
);

CREATE TABLE client_documents (
    id SERIAL PRIMARY KEY,
    client_id INT REFERENCES clients(id),
    document_name VARCHAR(255),
    document_path VARCHAR(255)
);

**5. Query Data**

You can query the tables to view the data:

To view all clients:

SELECT * FROM clients;

To view payment details:

SELECT * FROM payment_details;

To view client documents:

SELECT * FROM client_documents;































