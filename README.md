# lei-drupal-test

1. Download and install Docker (if not already installed) https://www.docker.com
2. Create a Docker container by running the docker-compose.yml file in this folder
by running this command in the terminal:
docker-compose up -d
3. Go to http://localhost/ to access the created Drupal 9 site
4. Log in to admin with the username "user" and password "pass"
5. The mount point to edit the Drupal files should be by default in:
/var/lib/docker/volumes/drupal-test-lei_drupal_data/_data
OR in Windows WSL you can use the Explorer or your code editor to open the following directory:
\\wsl.localhost\docker-desktop-data\data\docker\volumes\drupal-test-lei_drupal_data\_data
