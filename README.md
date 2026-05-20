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

Docker Image link 
-----------------
docker pull thidaayewin/wordpress-docker-compose:c87a3c99d187a41d7709b83cb399110f90953cc7


