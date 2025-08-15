# 01-mysql-crud-operations

CRUD:
C - Create
R - Read
U - Update
D - Delete

SQL Database Operations Demo

Programming Language: SQL

Libraries/Frameworks: None (standard SQL, likely for a relational database like MySQL or MariaDB)

Description: This SQL script demonstrates basic database operations (CRUD: Create, Read, Update, Delete) on a users table in a database called test_db. It starts by resetting the database (dropping and recreating test_db), then creates a users table with columns for id (auto-incremented primary key), name, email (unique), and created_at (timestamp). The script inserts three sample users, reads all records, updates one user's email, deletes another user, and counts the remaining users. Finally, it adds two more users and displays the updated table. This showcases fundamental SQL operations for managing a simple database.

~ EXAMPLE QUERIES ~

-- ================================
-- 1. Reset the database
-- This ensures we start fresh each time
-- Drops the database if it exists, then creates a new one
-- ================================
DROP DATABASE IF EXISTS test_db;
CREATE DATABASE test_db;
USE test_db;

-- ================================
-- 2. Create a sample table: users
-- id: unique identifier, auto-incremented
-- name: user's name
-- email: user's email, must be unique
-- created_at: timestamp when the record is created
-- ================================
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    email VARCHAR(50) NOT NULL UNIQUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- ================================
-- 3. Insert sample data (CREATE)
-- Adding three users to demonstrate inserts
-- ================================
INSERT INTO users (name, email) VALUES
('Matt Hartstein', 'matt@example.com'),
('Jane Doe', 'jane@example.com'),
('John Smith', 'john@example.com');

-- ================================
-- 4. Read data (READ)
-- Display all users in the table
-- ================================
SELECT * FROM users;

-- ================================
-- 5. Update data (UPDATE)
-- Change Jane Doe's email to demonstrate updating
-- ================================
UPDATE users
SET email = 'jane.doe@example.com'
WHERE name = 'Jane Doe';

-- Verify the update
SELECT * FROM users;

-- ================================
-- 6. Delete data (DELETE)
-- Remove John Smith to demonstrate deleting
-- ================================
DELETE FROM users
WHERE name = 'John Smith';

-- Verify the deletion
SELECT * FROM users;

-- ================================
-- 7. Advanced query example
-- Count how many users are currently in the table
-- ================================
SELECT COUNT(*) AS total_users FROM users;

-- ================================
-- 8. Optional: Add more sample data
-- Adding two more users for demonstration
-- ================================
INSERT INTO users (name, email) VALUES
('Alice Johnson', 'alice@example.com'),
('Bob Brown', 'bob@example.com');

-- Verify new inserts
SELECT * FROM users;
