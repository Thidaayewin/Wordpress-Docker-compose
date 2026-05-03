WordPress Docker Setup with Custom Theme
-------------------------------------------
This project runs WordPress, MySQL, and phpMyAdmin using Docker Compose.
It also includes a custom theme (my-theme) that prints Hello to Pico SBS.

Services
-----------------------------
WordPress → http://localhost:8080

phpMyAdmin → http://localhost:8081

MySQL → internal Docker network

Project Structure
------------------
docker-compose.yaml → container definitions

my-theme/ → custom WordPress theme

style.css → theme metadata

index.php → theme output

.gitignore → excludes runtime volumes

Usage
--------
Run the following command to start the stack:

bash
docker compose up -d
Then visit:

WordPress: http://localhost:8080

phpMyAdmin: http://localhost:8081

Custom Theme
-------------
To activate the theme in WordPress:

Log in at http://localhost:8080/wp-admin

Go to Appearance → Themes

Select My Hello World Theme

The site will display: Hello to Pico SBS


How Docker Compose Works Internally!
-----------------------------------

docker compose up -d
   ↓
Create Docker Network
 Docker automatically sets up a default network so containers can talk to each other.


   ↓
Start db (MySQL)
Pulls the mysql:8.0 image, builds the container, initializes database files,
     creates the 'wordpress' database, and sets up a user/password.


   ↓
Start wordpress (App)
Pulls the wordpress:latest image, builds the container, connects to MySQL on port 3306,
     verifies credentials, and installs WordPress tables.

   ↓
Start phpMyAdmin (UI)
Pulls the phpmyadmin:latest image, builds the container, connects to the same database,
     and exposes the admin panel at localhost:8081.

     
   ↓
Running State
   → WordPress available at localhost:8080
   → phpMyAdmin available at localhost:8081
   → MySQL running internally on the Docker network

