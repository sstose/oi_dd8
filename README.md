This is a Drupal 8 starter project. It combines the best of both:

https://github.com/wodby/docker4drupal

https://github.com/drupal-composer/drupal-project


##For a new Drupal 8 site (on a Mac with Docker Community Edition installed):

1. Create empty directory (e.g., `docker-sites` or `docker`), `cd` into this directory

2. From within this directory, run `git clone https://github.com/sstose/oi_dd8.git project-name`

3. Move `traefik.yml` file up one directory (`mv traefik.yml ../.`)

4. Edit environmental variables in `.env.modify` and rename to `.env`

5. Edit `docker-compose.yml` and `docker-sync.yml`, replacing `"docker"-sync` with `"project-name"-sync` where appropriate

6. Edit `traefik.yml` and change `site1` to `project-name`; if more than one project, configure as required (see notes below on running multiple projects)

7. Run `docker-sync start` (this requires having run `gem install docker-sync` on host machine)

8. Run `docker ps` -- to get name of php container (e.g., project-name_php)

9. Run `docker exec -ti project-name_php bash` (better: run `docker-compose exec --user 82 php sh` )

10. Run `composer update` (this installs Drupal Core within the `web` folder it creates, and runs `composer install`)

9. Add `127.0.01 project-name` to /etc/hosts on host machine

10. Visit site URL, install Drupal, may require you to copy `settings.php` file, configure site (make sure database details on install match `.env` settings file)


##To configure multiple projects


##To startup an existing Drupal 8 site (on a Mac with Docker Community Edition installed):

