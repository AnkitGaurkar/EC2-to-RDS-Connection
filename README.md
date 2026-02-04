📘 AWS RDS (MySQL) – Connect EC2 to Managed Database
4

This project shows how to create an AWS RDS MySQL database and connect it securely from a Linux EC2 instance.

This is how real production cloud applications connect to managed databases.

☁️ Cloud Platform

Built on Amazon Web Services

Services used:

EC2 (Ubuntu) – Application Server

RDS (MySQL) – Managed Database

🧩 Architecture
[ Ubuntu EC2 ]
       |
       |  MySQL (3306)
       |
[ AWS RDS (MySQL) ]

🔹 Step 1 — Create MySQL RDS in AWS

Go to AWS Console → RDS → Create Database

Choose:

Engine: MySQL

Template: Free Tier

DB instance identifier: mydb

Username: admin

Password: (your password)

Public access: No

VPC: Same as EC2

Database port: 3306

Click Create Database

After creation, copy:

RDS Endpoint → <rds-endpoint>.rds.amazonaws.com

🔹 Step 2 — Allow EC2 to Access RDS

Open RDS → Security Group → Inbound Rules

Add:

Type	Port	Source
MySQL	3306	EC2 Security Group

This allows EC2 to talk to RDS.

🔹 Step 3 — Install MySQL Client on EC2

Login to EC2:

sudo apt-get update
sudo apt install mysql-client -y

🔹 Step 4 — Connect EC2 to RDS
mysql -h <rds-endpoint> -u admin -P 3306 -p


Enter the RDS password.

🔹 Step 5 — Create Database & Table

Inside MySQL:

CREATE DATABASE devopsdb;
USE devopsdb;

CREATE TABLE users (
  id INT PRIMARY KEY,
  name VARCHAR(50)
);

🔹 Step 6 — Insert & Read Data
INSERT INTO users VALUES (1,'Ankit');
SELECT * FROM users;


Output:

+----+-------+
| id | name  |
+----+-------+
| 1  | Ankit |
+----+-------+

🧠 What This Project Proves
Component	Role
EC2	Application Server
RDS	Database Server
Security Groups	Firewall
MySQL Client	Database Access Tool

This is exactly how real production apps connect to cloud databases.

📄 Resume-Ready Line

Created AWS RDS MySQL database and configured secure EC2 connectivity, including database creation, user access, and live data operations.
