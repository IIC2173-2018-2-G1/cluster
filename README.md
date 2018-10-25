# Cluster Configuration/Development files

This repo contains the docker-compose file and (possibly) other important configuration files for the cluster and for its local development.

The docker-compose file is pretty autoexplicative. To execute the services in your local machine just:

`docker-compose --remove-orphans`

An explication of what you can do in the current version:

In your browser:
- web.localhost
    - accesses our front end web service
- admindb.localhost
    - accesses the mongo-express service. There you can view and edit the mongo database
    - note that it has no password just for development purposes but you should anyways try and read the enviroment variables defined in the docker-compose file (dont use directly the value in the docker file because that wont be the final value)
    - you can uncomment the enviroment setters in the dockerfile to check if your implementation will work in the swarm
- api.localhost/test2
    - accesses a whoami service. this was created to show how to route the paths to services in the docker-compose
- api.localhost/[0-9]
    - same as above but this shows how to use regular expressions to match paths to services

**It is important to add an `expose portnumber` to your service's dockerfile in order for our reverse-proxy service (traefik) to detect it automagically**