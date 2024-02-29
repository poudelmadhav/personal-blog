---
title: Starting docker in rails 7.1 with a separate MySQL container
date: 2024-02-29 13:30:28 +0545
layout: post
permalink: starting-docker-in-rails-7-with-separate-mysql-container/
category:
- rails
- docker
meta_description: Starting docker in rails 7.1 with a separate MySQL container
meta_keywords: Starting docker in rails 7.1 with a separate MySQL container, rails, docker, docker in rails, rails in docker
comments: true
---

## Setting Up MySQL

1. **Pull the MySQL image:**

   ```shell
   docker pull mysql/mysql-server
   ```

2. **Run the MySQL container:**
   
   ```shell
   docker run -it -d \
     --name=mysql_container \
     -p 3307:3306 \
     -e MYSQL_ROOT_PASSWORD=password \
     -e MYSQL_ROOT_HOST=% \
     mysql/mysql-server \
     --default-authentication-plugin=mysql_native_password
   ```

   - Explanation:
     - -it: Run in interactive.
     - -d: Run the container in the background.
     - --name=mysql_container: Name the container for easier management.
     - -p 3307:3306: Map the container port 3306 (MySQL) to host port 3307.
     - -e MYSQL_ROOT_PASSWORD=password: Set the root password for the MySQL user.
     - -e MYSQL_ROOT_HOST=%: Allow connections from any host.
     - --default-authentication-plugin=mysql_native_password: Use the traditional password authentication plugin.

3. **Get the container's IP Address:** 

   ```shell
   docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' mysql_container
   ```

   This will display the container's IP address, which will be used later.

4. **Set environment variables:**

   ```shell
   export DATABASE_URL='mysql2://root:password@<container_ip>/<db_name>:3306?encoding=utf8mb4'
   export RAILS_MASTER_KEY=<rails_master_key>
   ```
   - Replace `<container_ip>` with the IP address obtained in the previous step.
   - Replace `<db_name>` with the name of the database you want to use.
   - Replace `<rails_master_key>` with the master key from `config/master.key`.

## Running project

1. **Build the project image:** 

   ```shell
   docker-compose build -t <rails_app> .
   ```
   - Replace `<rails_app>` with the name you want to give to the image.
   - This will build the image using the Dockerfile.

2. **Run the project container:**

   ```shell
   docker run --rm -it -p 3000:3000 --name=<rails_app_container> \
     -e DATABASE_URL=$DATABASE_URL \
     -e RAILS_MASTER_KEY=$RAILS_MASTER_KEY \
     <rails_app>
   ```
   - Replace `<rails_app_container>` with the name you want to give to the container.
   - Replace `<rails_app>` with the name of the image you built in the previous step.
   - Explanation:
     - --rm: Remove the container when it stops.
     - -it: Run in interactive.
     - -p 3000:3000: Map the container port 3000 (Rails) to host port 3000.
     - -e DATABASE_URL=$DATABASE_URL: Set the database URL environment variable.
     - -e RAILS_MASTER_KEY=$RAILS_MASTER_KEY: Set the Rails master key environment variable.

## Debugging

- **View MySQL container logs:**

  ```shell
  docker logs mysql_container
  ```

- **Enter the MySQL container:**

  ```shell
  docker exec -it mysql_container bash
  ```
  - This will open a bash shell inside the container.
  - You can then run `mysql -u root -p` to enter the MySQL command line.
  - Use `exit` to leave the container.

## Controlling the MySQL container

- **Stop the container:**
  
    ```shell
    docker stop mysql_container
    ```

- **Start the container:**
  
    ```shell
    docker start mysql_container
    ```

- **Remove the container:**
  
    ```shell
    docker rm mysql_container
    ```
