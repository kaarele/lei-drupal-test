# LEI Register Druapl Test Assignment #

## Project Setup ##

1. Download and install Docker (if not already installed) https://www.docker.com
2. For windows, you would probably also need to install Windows Subsystem for Linux "WSL"
(if not already installed)
3. Create a Docker container by running the docker-compose.yml file in this folder
by running this command in the terminal:
~~~
docker-compose up -d
~~~
4. Go to http://localhost/ to access the created Drupal 9 site
5. Log in to admin with the username "user" and password "pass"
6. The mount point to edit the Drupal files should be by default in:
~~~
/var/lib/docker/volumes/drupal-test-lei_drupal_data/_data
~~~
OR in Windows WSL you can use the Explorer or your code editor to open the following directory:
~~~
\\wsl.localhost\docker-desktop-data\data\docker\volumes\drupal-test-lei_drupal_data\_data
~~~
7. You should find the folder and edit the files there or create a symlink
as you need for the purpose of this test assignment.

## Assignment ##

1. Create a new content type named **application**.
2. The content type "title" should be renamed to **Company name**.
3. Create the following new fields for the **application** content type:
  * 3.1. **Registration number** - plain text 255 characters.
  * 3.2. **Country code** - plain text 5 characters (For example US-AL for USA Alabama state or simply EE for Estonia).
  * 3.3. **LEI code** - plain text maximum 20 characters.
  * 3.4. **Next renewal date** - Date only field.
  * 3.5. **LEI status** - plain text 255 characters.
  * 3.6. **GLEIF last update** - Date field with both date and time.
4. Create a new **custom** folder inside the **modules** folder inside the Docker Drupal project.
  * 4.1. Inside that folder create a new custom Drupal module called for example **lei**.
  * 4.2. Create the needed **lei.info.yml** and **lei.module** files to enable the new module in Drupal.
5. Create either a button, link, cron job (your own preference), that could be accessed and triggered somehow in the Drupal admin interface that would run the function to **Update GLEIF data**, which is described below.
6. Create an **Update GLEIF data** for either a specific **application** or for all applications in a loop.
  * 6.1. The function should do a request to fetch LEI data from **api.gleif.org** using the application company **registration number** and **country code**. The GLEFI LEI API documentation can be found here: https://documenter.getpostman.com/view/7679680/SVYrrxuU
  * 6.2. The function should find the matching **LEI code** for the application from the GLEIF API response. Update the following fields with the data from the GLEIF API data to the matched **application** node.
  * 6.3. **LEI code** *(id)*
  * 6.4. **Next renewal date** *(nextRenewalDate)*
  * 6.5. **LEI Status** *(attributes->registration->status)*
  * 6.6. Update the **GLEIF last update** field with the current time, to indicate when the GLEIF update function was last run.
7. If the **LEI Status** field is saved with the value *LAPSED*....TODO


## Test applications ##
