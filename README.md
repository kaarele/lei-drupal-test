# LEI Register Druapl Test Assignment #

## Assignment goals ##

1. Get a sense of how it would be to work together by communicating and choosing different ways to approach tasks.
2. Get to know the level of familiarity of different aspects of working with Drupal and PHP.
3. To see the code quality vs focus on completing as much sub-tasks as possible in the timeframe.
4. Front-end polish and styling will be completely ignored.

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


## Assignment tasks ##

1. Create a new content type named **application**.
2. The content type "title" should be renamed to **Company name**.
3. Create the following new fields for the **application** content type:
    * 3.1. **Registration number** - plain text 255 characters.
    * 3.2. **Country code** - plain text 2 characters (For example US for USA or EE for Estonia).
    * 3.3. **LEI code** - plain text maximum 20 characters.
    * 3.4. **Next renewal date** - Date only field.
    * 3.5. **LEI status** - plain text 255 characters.
    * 3.6. **GLEIF last update** - Date field with both date and time.
4. Create a new **custom** folder inside the **modules** folder inside the Docker Drupal project.
    * 4.1. Inside that folder create a new custom Drupal module called for example **lei**.
    * 4.2. Create the needed **lei.info.yml** and **lei.module** files to enable the new module in Drupal.
5. Create an **Update GLEIF data** function that could be run to update a specific **application**.
    * 5.1. The function should be able to run from an URL where the node ID is an URL argument.
    * 5.2. The function should do a request to fetch LEI data from **api.gleif.org** using the application company **registration number** and **country code**. The GLEFI LEI API documentation can be found here: https://documenter.getpostman.com/view/7679680/SVYrrxuU
    * 5.3. The function should find the matching **LEI code** for the application from the GLEIF API response. Update the following fields with the data from the GLEIF API data to the matched **application** node.
    * 5.4. **LEI code** *(id)*
    * 5.5. **Next renewal date** *(nextRenewalDate)*
    * 5.6. **LEI Status** *(attributes->registration->status)*
    * 5.7. Update the **GLEIF last update** field with the current time, to indicate when the GLEIF update function was last run.
6. Use whichever method you prefer to create a viewable listing of the applications. The listing should show:
    * 6.1. Application **company name** (title)
    * 6.2. **LEI code**
    * 6.3. **LEI status**, which should be colored green if "ACTIVE", red if "LAPSED" or yellow otherwise. (other detailed styling is not important).
    * 6.4. **Next renewal date**
    * 6.5. A link to fetch the application LEI code and other data from the GLEIF API for the specified application (step 5.1).


## LEI Codes for testing ##
* Lapsed LEI: https://search.gleif.org/#/record/549300ELERENIOHRKO73
* Active LEI: https://search.gleif.org/#/record/485100MX4O4LQTS45635
* Retired LEI: https://search.gleif.org/#/record/984500BA0AE5U0936B12
