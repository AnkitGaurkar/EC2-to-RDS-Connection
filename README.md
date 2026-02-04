# EC2-to-RDS-Connection
📘 RDS in AWS – MySQL Connectivity from EC2
4

This project demonstrates how an Ubuntu EC2 instance connects securely to a MySQL database hosted on AWS RDS.

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

Connect to AWS RDS using endpoint & credentials

Verify database connectivity

🛠️ Step 1 — Install MySQL Client
sudo apt-get update
sudo apt install mysql-client -y

🌐 Step 2 — RDS Endpoint

For security reasons, the actual RDS endpoint is hidden.

Format:

<rds-endpoint>.rds.amazonaws.com


Example:

mydb.xxxxxxxx.us-east-2.rds.amazonaws.com

🔑 Step 3 — Connect to RDS
mysql -h <rds-endpoint> -u admin -P 3306 -p


Enter password when prompted.

❌ Common Mistake (From Lab)

Wrong:

mysql -u admin -h <rds-endpoint> -p 3306


Correct:

mysql -h <rds-endpoint> -u admin -P 3306 -p

Option	Meaning
-p	Ask for password
-P	Port number
🔐 Step 4 — RDS Security Group

Inbound rule required:

Type	Port	Source
MySQL	3306	EC2 Security Group

Without this, EC2 cannot connect to RDS.

🧠 What This Proves

This setup reflects a real production DevOps architecture:

Layer	AWS Service
Application Server	EC2
Database	RDS
Security	Security Groups
📄 Resume-Ready Line

Configured secure EC2-to-RDS MySQL connectivity using AWS networking and Linux MySQL client for cloud-based production workloads.
