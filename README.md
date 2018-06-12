This is a Drupal 8 starter project. It combines the best of both:

https://github.com/wodby/docker4drupal

https://github.com/drupal-composer/drupal-project


##For a new Drupal 8 site (on a Mac with Docker Community Edition installed):

1. Run `git clone https://github.com/sstose/oi_dd8.git project-name`

2. Edit environmental variables in `.env`

3. Edit `docker-compose.yml` and `docker-sync.yml`, replacing `"docker"-sync` with `"project-name"-sync` where appropriate

4. Run `docker-sync start` (this requires having run `gem install docker-sync` on host machine)

5. Run `docker-compose up -d` (runs as a daemon)

6. Run `docker ps` -- to get name of php container (e.g., project-name_php)

7. Run `docker exec -ti project-name_php bash` (better: run `docker-compose exec --user 82 php sh` )

8. Run `composer update` (this installs Drupal Core within the `web` folder it creates, and runs `composer install`)

9. Add `127.0.01 project-name` to /etc/hosts on host machine

10. Visit site URL, install Drupal, may require you to copy `settings.php` file, configure site (make sure database details on install match `.env` settings file)


##To startup an existing Drupal 8 site (on a Mac with Docker Community Edition installed):

