This is a Drupal 8 starter project. It combines the best of both:

https://github.com/wodby/docker4drupal

https://github.com/drupal-composer/drupal-project

##For a new Drupal 8 site (on a Mac with Docker Community Edition installed):

1. Create empty directory (e.g., docker-sites or docker), cd into this directory (or, if one already exists with another Docker project, cd into this, and see #11 below for traefik.yml configuration)

2. From within this directory, run git clone https://github.com/sstose/oi_dd8.git project-name

3. Move traefik.yml file up one directory (mv traefik.yml ../.) (unless one is already there, networking an existing project)

4. Edit environmental variables in .env.modify and rename to .env

5. Edit docker-compose.yml and docker-sync.yml, replacing docker-sync with project-name-sync where appropriate (1x in each file)

6. Run docker-sync start (this requires having run gem install docker-sync on host machine); then run docker-compose up -d (can view containers by running docker ps or docker-compose ps)

7. Run docker-compose exec php sh (UNCLEAR difference with docker-compose exec --user 82 php sh and docker exec -ti project-name_php sh); run ls -lah to make sure directories owned by wodby (uid=501, same as your Mac uid)

8. Run composer update (this installs Drupal Core within the web folder it creates, and runs composer install)

9. Add 127.0.01 project-name to /etc/hosts on host machine

10. Edit traefik.yml and change site1 to project-name (3x)

11. If more than one project exists, before editing #10 above run docker-compose -f traefik.yml down (if already running); then, edit #10 above, and run docker-compose -f traefik.yml up -d

12. Visit site URL (http://project-name), configure site to install Drupal (make sure database details on install match .env settings file)





##Rough guide to deploying an existing Drupal 8 site on a new Docker container

1. Follow all the steps above, to the letter

2. Integrate the `composer.json` from your project with the one already present in the directory; this can be tricky -- most importantly, include the required modules and their versions in the `require` and `require-dev` sections

3. Remove the existing `composer.lock` 

2. Remove or rename the `vendor` folder (e.g., `mv vendor _vendor`)

3. Copy over (e.g., `rsync -avz`) the `modules` and `themes` and `libraries` directories

4. Copy over the `sites` folder, careful not to override the `settings.php` database connection details

5. Copy over any other important files relevant to the site

6. 

