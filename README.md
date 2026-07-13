# student-management-api

🎓 Student Management System API

A production-ready, containerized RESTful API built with Spring Boot, MySQL, Flyway, and Docker.

📋 Table of Contents

Project Overview

Key Features

Architecture & Workflow

Database Schema

API Documentation

Local Setup & Installation

Screenshots

🚀 Project Overview

This project was developed as an internship task to demonstrate modern backend software engineering practices. It provides a RESTful web service for managing student records.

Instead of relying on manual database creation, this project utilizes Flyway for strict version control of the database schema. Furthermore, the entire application is containerized using Docker, ensuring that it runs identically across any local or cloud environment without dependency conflicts.

✨ Key Features

RESTful Architecture: Clean, stateless communication handling JSON payloads.

Database Migrations: Automated schema creation and versioning using Flyway.

Data Persistence: Spring Data JPA and Hibernate for seamless Object-Relational Mapping (ORM).

Containerization: Fully packaged into a Docker image bridging to the host machine's database.

🏗️ Architecture & Workflow

Client (Postman): Sends HTTP requests (GET, POST) to the designated endpoints.

Docker Container: Hosts the compiled Spring Boot .jar file, isolated from the host OS. Listens on port 8084.

Spring Boot Layers:

StudentController: Handles routing and HTTP responses.

StudentService: Manages business logic.

StudentRepository: Interfaces with the database.

MySQL Database: Runs on the host machine. The Docker container reaches it via the host.docker.internal bridge. On startup, Flyway automatically executes .sql scripts to build the tables before the server accepts traffic.

🗄️ Database Schema

The database relies on a single students table, managed by Flyway (V1__create_students_table.sql).

Column Name

Data Type

Constraints

Description

id

BIGINT

PRIMARY KEY, AUTO_INCREMENT

Unique identifier for the student

name

VARCHAR(255)

NOT NULL

Full name of the student

email

VARCHAR(255)

NOT NULL, UNIQUE

Student's contact email

course

VARCHAR(255)



The program the student is enrolled in

(Note: An additional flyway_schema_history table is automatically generated to track migration versions).

📡 API Documentation

The API runs locally on http://localhost:8084.

1. Retrieve All Students

URL: /api/students

Method: GET

Success Response (200 OK):

[
    {
        "id": 1,
        "name": "Chandra Shekhar Azad",
        "email": "csazad@university.edu",
        "course": "Spring Boot Backend"
    }
]


2. Create a New Student

URL: /api/students

Method: POST

Request Body:

{
    "name": "Chandra Shekhar Azad",
    "email": "csazad@university.edu",
    "course": "Spring Boot Backend"
}


Success Response (200 OK / 201 Created): Returns the saved student object including the newly generated database id.

🛠️ Local Setup & Installation

Prerequisites

Docker Desktop installed and running.

A local MySQL instance running on port 3306 with a blank database named student_db.

Run Instructions

Clone the repository:

git clone https://github.com/YourUsername/your-repo-name.git
cd your-repo-name


Package the Application:

./mvnw clean package -DskipTests


Build the Docker Image:

docker build -t student-api-backend .


Run the Docker Container:

docker run -p 8084:8084 student-api-backend


📸 Project Screenshots


<img width="1919" height="1079" alt="Screenshot 2026-06-08 200216" src="https://github.com/user-attachments/assets/ca8d8d5b-da35-4886-8172-945968a28c29" />
<img width="1919" height="1079" alt="Screenshot 2026-06-08 201707" src="https://github.com/user-attachments/assets/cf1e785f-6ddd-4ea1-8b51-2acde66997f0" />
<img width="1919" height="1070" alt="Screenshot 2026-06-08 200224" src="https://github.com/user-attachments/assets/499931b6-e005-4d3b-80c8-7af0c7875908" />
<img width="1919" height="1079" alt="Screenshot 2026-06-08 201714" src="https://github.com/user-attachments/assets/01099e4d-c89b-4cc5-84ae-46e56ea53f06" />
<img width="1918" height="1079" alt="Screenshot 2026-06-08 201744" src="https://github.com/user-attachments/assets/1330f485-91a8-4e0d-9721-16478703054d" />
<img width="1919" height="1079" alt="Screenshot 2026-06-08 201802" src="https://github.com/user-attachments/assets/a73c03da-535e-4d49-9c7a-fe0222004d4f" />




   


Developed by Chandra Shekhar Azad
