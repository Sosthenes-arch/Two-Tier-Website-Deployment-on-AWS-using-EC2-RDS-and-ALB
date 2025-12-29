# Two-Tier Website Deployment on AWS (EC2, RDS, ALB)

## 📋 Project Overview
**Uche's To-Do List** is a full-stack web application designed to demonstrate a **Two-Tier Architecture** deployment on AWS. The application allows users to manage tasks (create, read, update, delete) and stores data persistently in a MySQL database.

This project showcases the integration of a frontend, a Node.js API backend, and a relational database, making it suitable for deploying on cloud infrastructure using services like **Amazon EC2** (for the application server) and **Amazon RDS** (for the database).

## 🚀 Features
- **Task Management**: Add new tasks with descriptions and due dates.
- **Status Tracking**: Mark tasks as completed (visual feedback).
- **Deletion**: Remove tasks from the list permanently.
- **Persistent Storage**: All data is stored in a MySQL database.
- **Responsive Design**: Simple and clean UI.

## 🛠️ Tech Stack
- **Frontend**: HTML5, CSS3, Vanilla JavaScript
- **Backend**: Node.js, Express.js
- **Database**: MySQL (using `mysql2` library)
- **Cloud (AWS)**:
  - **EC2**: Hosting the Node.js application.
  - **RDS**: Managed MySQL Database instance.
  - **ALB**: Application Load Balancer for distributing traffic (deployment target).

## 📂 Project Structure
```
├── public/              # Frontend static files
│   ├── index.html       # Main HTML file
│   ├── style.css        # Stylesheets
│   ├── script.js        # Frontend logic (Fetch API)
├── index.js             # Backend Express server & API routes
├── package.json         # Project dependencies and scripts
└── README.md            # Project documentation
```

## ⚙️ Setup & Installation
### Prerequisites
- [Node.js](https://nodejs.org/) (v16 or higher)
- [MySQL](https://www.mysql.com/) (Local server or AWS RDS instance)

### 1. Clone the Repository
```bash
git clone <repository-url>
cd Two-Tier-Website-Deployment-on-AWS-using-EC2-RDS-and-ALB
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Configure Database
Create a MySQL database and a table for the tasks:
```sql
CREATE DATABASE todo_db;
USE todo_db;

CREATE TABLE Tasks (
    id INT AUTO_INCREMENT PRIMARY KEY,
    task_name VARCHAR(255) NOT NULL,
    task_description TEXT,
    due_date DATE,
    completed BOOLEAN DEFAULT FALSE
);
```

### 4. Environment Variables
Create a `.env` file in the root directory and add your database configuration:
```env
DB_HOST=localhost       # Or your RDS Endpoint
DB_USER=root            # Your database username
DB_PASSWORD=yourpassword # Your database password
DB_NAME=todo_db
API_BASE_URL=http://localhost:3000
```

### 5. Run the Application
Start the development server:
```bash
npm start
```
The server will start on `http://localhost:3000`. Open your browser and navigate to this URL to view the application.

## 📡 API Endpoints
| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/tasks` | Retrieve all tasks |
| `GET` | `/tasks/:id` | Retrieve a specific task |
| `POST` | `/tasks` | Create a new task |
| `PUT` | `/tasks/:id` | Update task status or details |
| `DELETE` | `/tasks/:id` | Delete a task |

## ☁️ Deployment Guide (AWS)
1. **Database**: Launch an **RDS MySQL** instance and configure security groups to allow traffic on port 3306.
2. **Compute**: Launch an **EC2 instance** (e.g., Ubuntu/Linux 2).
   - Install Node.js and Git.
   - Clone the repo and install dependencies.
   - Set environment variables for RDS connection.
3. **Load Balancing (Optional)**: Set up an **ALB** to forward traffic to your EC2 instance(s) for high availability.

## 📄 License
This project is licensed under the ISC License.