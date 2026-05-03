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

┌────────────────────────────┐
│ docker compose up -d       │
│ (Starting containers)      │
└──────────────┬─────────────┘
               │
               ▼
┌────────────────────────────┐
│ Create Docker Network      │
│ (Compose automatically creates a default network) │
└──────────────┬─────────────┘
               │
               ▼
┌────────────────────────────┐
│ Start db (MySQL)           │
│ - Pull mysql:8.0 image     │
│ - Build container          │
│ - Initialize DB files      │
│ - Create 'wordpress' DB    │
│ - Create user & password   │
└──────────────┬─────────────┘
               │
               ▼
┌────────────────────────────┐
│ Start wordpress (App)      │
│ - Pull wordpress:latest    │
│ - Build container          │
│ - Connect to db:3306       │
│ - Verify DB credentials    │
│ - Install WordPress tables │
└──────────────┬─────────────┘
               │
               ▼
┌────────────────────────────┐
│ Start phpMyAdmin (UI)      │
│ - Pull phpmyadmin:latest   │
│ - Build container          │
│ - Connect to db            │
│ - Expose admin panel 8081  │
└──────────────┬─────────────┘
               │
               ▼
┌────────────────────────────┐
│ Running State              │
│ - WordPress → localhost:8080 │
│ - phpMyAdmin → localhost:8081│
│ - MySQL → internal network  │
└────────────────────────────┘
