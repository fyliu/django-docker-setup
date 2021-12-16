# docker-django-postgres-rest

This repo follows the testdrive.io post on Dockerizing Django with Postgres except for the first part on installing django on the host machine. Here, we bypass that step by setting up the docker container first, then running django from inside it.

## Initial setup

1. Make sure docker and docker-compose is installed on your computer

```
    docker -v
    docker-compose -v
```

2. Checkout this repo

```
    git clone <repo url>
```

3. Create .env.dev from .env.dev-sample

```
    cp .env.dev-sample .env.dev
```

4. Build the image and run the containers

```
    docker-compose up -d --build
```

5. Run the default migrations from within the web container (prefix commands with `docker-compose exec web`)

```
    docker-compose exec web python manage.py migrate
```

6. Now we're ready to add apps to django. Follow the Django REST Framework examples for a start. Skip the setup until `python manage startapp`

```
    docker-compose exec web python manage.py startapp <app name>
```

## Branches

### Dev

This branch stops after setting up the development environment

### Main

This is essentially the Dev branch, with an added step of installing Django REST Framework. This is should be the starting point for development.

### Prod

This branch finishes the tutorial with gunicorn, nginx, serving static files, and image uploads.

### Drf-\*

These branches follow the Django REST Framework tutorials, using the Main branch as a base.

## References

    https://testdriven.io/blog/dockerizing-django-with-postgres-gunicorn-and-nginx/
    https://www.django-rest-framework.org/tutorial/quickstart/
