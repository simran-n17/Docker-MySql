# MySQL Using Docker

Docker allows us to run MySQL databases in isolated containers, making it easy to deploy and manage databases without interfering with the host system. In this guide, we'll walk through setting up MySQL using Docker.

---

## 📄 Documentation
- [Docker Official Docs](https://docs.docker.com/)
- [MySQL Documentation](https://dev.mysql.com/doc/)
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)

---

## 🚀 Installation & Setup

### 1️⃣ Create an SQL File
First, create a `.sql` file that contains the database schema and initial data.

```sql
CREATE DATABASE student;
USE student;
CREATE TABLE students (
    StudentID INT NOT NULL AUTO_INCREMENT,
    FirstName VARCHAR(100) NOT NULL,
    Surname VARCHAR(100) NOT NULL,
    PRIMARY KEY (StudentID)
);

INSERT INTO students (FirstName, Surname) 
VALUES ("John", "Andersen"), ("Emma", "Smith");
```

### 2️⃣ Create a Dockerfile
Now, create a `Dockerfile` to configure the MySQL container.

```dockerfile
FROM mysql:latest

ENV MYSQL_ROOT_PASSWORD=root

COPY ./database_students.sql /docker-entrypoint-initdb.d/
```

---

## 📦 Deployment

### 1️⃣ Verify Running Containers
Before building the image, check if any MySQL containers are running.
```bash
docker container ls
```

### 2️⃣ Build the Docker Image
Run the following command to build the MySQL Docker image.
```bash
docker build -t mysql_db .
```

### 3️⃣ Check Available Images
Ensure that the image has been created successfully.
```bash
docker images
```

### 4️⃣ Run the MySQL Container
Now, start the container using the created image.
```bash
docker run -d --name mysql_container mysql_db
```

### 5️⃣ Access the Running Container
Use the following command to interact with the MySQL container.
```bash
docker exec -it mysql_container /bin/bash
```

### 6️⃣ Navigate to the SQL File
```bash
cd docker-entrypoint-initdb.d/
```

### 7️⃣ Access the MySQL Database
To log in to MySQL inside the container:
```bash
mysql -u root -p
```
Enter the password (`root` in this case) when prompted.

### 8️⃣ Verify the Database
Once inside MySQL, run the following command to check the stored data.
```sql
USE student;
SELECT * FROM students;
```

---

Now, your MySQL database is successfully running inside a Docker container! 🚀

