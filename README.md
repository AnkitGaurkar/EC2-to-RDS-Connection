📘 RDS in AWS – MySQL Connectivity from EC2
4

This project demonstrates how an Ubuntu EC2 instance connects securely to a MySQL database hosted on AWS RDS — a standard production cloud architecture.

☁️ Cloud Platform

Built on Amazon Web Services

Services used:

EC2 – Ubuntu Server

RDS (MySQL) – Managed Database

🧩 Architecture
[ Ubuntu EC2 ]
       |
       |  MySQL (TCP 3306)
       |
[ AWS RDS – MySQL ]

🎯 Objective

Install MySQL client on EC2

Connect EC2 to AWS RDS

Verify database access

🛠️ Step 1 — Install MySQL Client
sudo apt-get update
sudo apt install mysql-client -y

🌐 Step 2 — RDS Endpoint

(Kept hidden for security)

Format:

<rds-endpoint>.rds.amazonaws.com

🔑 Step 3 — Connect to RDS
mysql -h <rds-endpoint> -u admin -P 3306 -p


Enter the password when prompted.

🧪 Step 4 — Validate Connection

After login:

SHOW DATABASES;


If databases appear, the connection is successful.

🔐 Step 5 — RDS Security Group

Inbound rule required:

Type	Port	Source
MySQL	3306	EC2 Security Group

This allows secure communication between EC2 and RDS.

🧠 What This Project Demonstrates

This setup reflects a real DevOps production model:

Layer	AWS Service
Application Server	EC2
Database	RDS
Security	Security Groups
📄 Resume-Ready Line

Configured secure EC2-to-RDS MySQL connectivity using AWS networking and Linux MySQL client in a production-grade cloud environment.
