
# MYSQL Using Docker

Here we will run the database using the Docker.




## Documentation

[Docker](https://docs.docker.com/)

[My sqL](https://dev.mysql.com/doc/)

[Docker Desktop](https://www.docker.com/products/docker-desktop/)




## Installation

Now we will setup the my sql and Docker to run databse on System.

1. First of all we will create the .sql file for the database query which is going to be:

```bash
CREATE DATABASE student;
use student;
CREATE TABLE students (
StudentID int not null AUTO_ INCREMENT,
FirstName varchar(100) NOT NULL, Surname varchar (100) NOT NULL, PRIMARY KEY (StudentID)
INSERT INTO students(FirstName, Surname)
VALUES ("John", "Andersen"), ("Emma", "Smith");
```

2. Now we will create the Docker file for the same.

```bash
FROM mysql:latest

ENV MYSQL_ROOT_PASSWORD=root

COPY ./databse_students.sql /docker-entrypoint-initdb.d/
```
    
## Deployment

Now to deply our database using docker we have following commands.

1. First of all we will check our container.

```bash
  docker container ls
```

2. Now after that we will create the docker image for that we will run the command which is.

```bash
Docker build -t mysql_db .
```
3. Now we will run the images to check that image is created or not.

```bash
Docker images
```

4. Now we will run the images by using the command.

```bash
docker run mysql_db
```

5. Now after that we will execute the command which is going to run the database.

```bash
docker exec -it docker_images /bin/bash
```

6. Now we will run the command to go inside the query inside the database.

```bash
cd docker-entrypoint-initdb.d/
```

7. Now we are inside the database and we will run the query to do so.

```bash
select * from students.
```


