### Dockerise Address Book

A framework for deploying Django projects on Docker

##### Installation

First, `install Docker`__
.. __install Docker: https://docs.docker.com/installation/

Next, clone this repo:
::

    $ git clone https://github.com/kumarisneha/address_book.git
    $ cd address_book

To get the containers running, build the images and then start the services:
::

    $ docker-compose build
    $ docker-compose up -d
    OR
    $ docker-compose up --build -d

Once the services are running, we need to create the database migrations:
::

    $ docker-compose run web python manage.py migrate
   
Open up a web browser and point it to http://127.0.0.1:8000 or http://0.0.0.0:8000 and you’ll see the home page. Awesome!

Check for errors in the logs if this doesn't work via docker-compose logs -f
::

    sneha@Sneha-Aspire-4752:~/Desktop/dockerise_add_book/projects/address_book/addrbookproj$ docker-compose logs
    Starting addrbookproj_web_1 ... done
    Attaching to addrbookproj_web_1
    web_1  | Watching for file changes with StatReloader
    web_1  | Performing system checks...
    web_1  | 
    web_1  | System check identified no issues (0 silenced).
    web_1  | 
    web_1  | You have 4 unapplied migration(s). Your project may not work properly until you apply the migrations for app(s): admin, auth.
    web_1  | Run 'python manage.py migrate' to apply them.
    web_1  | June 07, 2020 - 18:06:23
    web_1  | Django version 3.0.7, using settings 'addrbookproj.settings'
    web_1  | Starting development server at http://0.0.0.0:8000/
    web_1  | Quit the server with CONTROL-C.

Bring down the development containers by:
::

    $ docker-compose down
    
Bring down the development containers by:
::

    $ docker-compose down
    
If you want to stop your container and remove associated volumes you can do this with the -v flag:
::

    $ docker-compose down -v

Ensure the default Django tables were created:
::

    $ docker-compose exec db psql --username=sneha --dbname=mydb



You can check that the volume was created as well by running:
::

    $ docker volume inspect addrbookproj_pgdata
