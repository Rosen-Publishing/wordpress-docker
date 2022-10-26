# Wordpress Setup with Docker
This is a simple setup with docker-compose.yml

## Initial Setup
- Download docker https://www.docker.com 
- Start Docker
- Clone this repo

## For a New Site
- Open terminal and type `docker compose up`
- Open chosen browser and navigate to 
http://localhost:8032 and go through the Wordpress setup.

## Setting up Existing Site Locally
- Add plugins and themes from existing site to wp-content folder and have a copy of the existing sites database
- Do all same steps as above for a New site
- Update the database that was created with the db script from the existing site (you can drop tables and then run script with insert or you can run an update script on the tables)
- Navigate to wp_options table and update site_url and home with http://localhost:8032
- Sign in http://localhost:8032/wp-admin (with the credentials from the existing site)
- Go to Settings - Permalinks and click save changes twice
- Download and activate Better Search Replace plugin - Located under Tools once active
- Run search for previous URL and replace with http://localhost:8032

** Note If needing to run more than once instance of Wordpress you will need to update the docker-compose.yml by changing db info, the port being used, and the volume location.

***
If the existing site uses a different prefix from wp_ then you will need to do the following after the Wordpress install:
- Open wp-config.php and wp-config-docker.php line 96, update 'wp_' to the altered prefix

  `$table_prefix = getenv_docker('WORDPRESS_TABLE_PREFIX', 'wp_');`