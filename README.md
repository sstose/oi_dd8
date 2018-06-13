This is a Drupal 8 starter project. It combines the best of both:

https://github.com/wodby/docker4drupal

https://github.com/drupal-composer/drupal-project


##For a new Drupal 8 site (on a Mac with Docker Community Edition installed):

1. Create empty directory (e.g., `docker-sites` or `docker`), `cd` into this directory (or, if one already exists with another Docker project, `cd` into this)

2. From within this directory, run `git clone https://github.com/sstose/oi_dd8.git project-name`

3. Move `traefik.yml` file up one directory (`mv traefik.yml ../.`) (unless one is already there, networking an existing project)

4. Edit environmental variables in `.env.modify` and rename to `.env`

5. Edit `docker-compose.yml` and `docker-sync.yml`, replacing `docker-sync` with `project-name-sync` where appropriate (1x in each file)

6. Edit `traefik.yml` and change `site1` to `project-name` (3x); if more than one project exists, configure as required (see notes below on running multiple projects)

7. Run `docker-sync start` (this requires having run `gem install docker-sync` on host machine); then run `docker-compose up -d` (can view containers by running `docker ps` or `docker-compose ps`)

8. Run `docker-compose exec php sh` (UNCLEAR difference with `docker-compose exec --user 82 php sh` and `docker exec -ti project-name_php sh`); run `ls -lah` to make sure directories owned by `wodby` (uid=501, same as your Mac uid)

8. Run `composer update` (this installs Drupal Core within the `web` folder it creates, and runs `composer install`)

10. Add `127.0.01 project-name` to /etc/hosts on host machine

11. Visit site URL (`http://project-name`), configure site to install Drupal (make sure database details on install match `.env` settings file)


##To configure multiple projects


##To startup an existing Drupal 8 site (on a Mac with Docker Community Edition installed):

