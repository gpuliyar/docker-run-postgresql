# docker-run-postgresql
Help document to run PostgreSQL as a Docker Container

## What this document is about and what you should know before?
1. You should be familiar with Docker and it's commands;
2. You should know PostgreSQL Database
3. You want to install PostgreSQL quick and easy, so you chose Docker;
> Now you want to find the commands that can help you to get started. So, if you are, then you landed on the right page. The commands are simple and easy. Give it a try!

## What now?
### Pull the image
```
docker pull postgres
```

### Next create a volume in Docker so you can externalize the data
```
docker volume create <volume name>
```

### Final step, run the PostgreSQL
```
docker run --rm \
        --name <container name> \
        -e POSTGRES_PASSWORD=<give a password> \
        -d \
        -p 5432:5432 \
        -v <put the volume name here>:/var/lib/postgresql/data \
        postgres
```
#### Now, let's see what those options mean:
1. --rm -> If you want Docker to automatically clean up the container and remove the file system when the container exits;
2. --name -> Name the Container;
3. -e -> Set the environment variable value. In our case, we are setting the PostgreSQL password. You don't want to use the default password;
4. -d -> Start the Container in detached mode;
5. -p -> Publish a Container Port. In our case, if we are publishing the default port `5432` as `5432`. You can publish it to any port as you wish or whatever is available in your host;
6. -v -> Set which volume to use. In our case, you have to give the same volume name whatever volume name you gave in step 2;
7. And the final one is the Image name

### That's it. You are done!
