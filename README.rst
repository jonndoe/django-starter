django-starter
=============================

env38_dj_by_ex_blog





# OPTION 1: RUNNING THE POSTGRES DATABASE ONLY LOCALLY WITH DOCKER
1. Install docker image postgres:11

2. Start a docker container with that postgres image.
    $ sudo docker run --rm   --name pg-docker -e POSTGRES_PASSWORD=docker -e POSTGRES_DB=somebase -e POSTGRES_USER=docker -p 5432:5432 -v $home/docker/volumes/postgres:/var/lib/postgresql/data  postgres:11

3. Create a databe with name 'everycheese' in potgresql
    $ createdb -h localhost --username=docker everycheese


4. SET env variable directly to the system:
    $ export DATABASE_URL=postgres://docker:docker@127.0.0.1:5432/everycheese

5. $ pip install -r requirements.txt

6. $ python manage.py migrate








# OPTION 2: RUNNING POSTGRES AND DJANGO WITH DIFF. DOCKER CONTAINERS:
This is a simple blog project. We use docker-containers here, one for django project and one
for postgresql database.

To RUN:

 - conda activate env38_dj_by_ex_blog

 - sudo docker-compose up (or sudo docker-compose up --build)

 - coverage run -m pytest ==> i perfom it from conda_env, since from docker it
                              it doesnt work yet..To be fixed.

 - to successfully run tests from conda_env we have to be able to run python manage.py runsever 8001
                              from conda_env just to be sure db is running ok.(we use the same database
                              for docker_image as well as for conda_env).





TODO:
 - run pytest from docker_container itself(now I run it from conda_env).


# SUGGESTIONS:
 -- Setting up a docker-driven postgres is a better and simple-configurable idea.

