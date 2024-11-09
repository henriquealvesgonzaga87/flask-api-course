## To build the docker image

'''
docker build -t flask-smorest-api .
'''

## To build the docker container

'''
docker run -dp 5000:5000 -w /app -v "$(pwd):/app" flask-smorest-api
'''

## To run the docker compose file

'''
docker compose up
'''

## To upgrade the data base with docker compose
'''
docker compose up -d
'''
### Then:

'''
docker compose exec web flask db upgrade
'''

## before to deploy the app change the docker file CMD

'''
from: ["gunicorn", "--bind", "0.0.0.0:80", "app:create_app()"]
to: ["/bin/bash", "docker-entrypoint.sh"]
'''

## to run the rq using docker
  ### first you need to build the docker image

'''
docker run -w /app <image-name> sh -c "rq worker -u <redis-url> emails"
'''

## to run the worker

'''
rq worker -c settings
'''