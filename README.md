For a new Drupal 8 site:

1. Git clone https://github.com/sstose/oi_dd8.git name_of_project

2. Edit environmental variables in .env

3. Edit docker-compose.yml and docker-sync.yml, replacing "docker"-sync with "project-name"-sync where appropriate

4. Run "docker-sync start" (this requires having run "gem install docker-sync" on host machine)

5. Run "docker-compose up -d" (runs as a daemon)

6. Run "docker ps" -- to get name of php container (e.g., dfd-1_php)

7. Run "docker exec -ti container-name bash

8. Run "composer create-project drupal/drupal web" (this installs Drupal Core within the "web" folder it creates, and runs "composer install"

9. Add "127.0.01 PROJECT_NAME" to /etc/hosts

10. Visit site URL, install Drupal, may require you to copy settings.php file, configure site (make sure database details on install match .env settings file)