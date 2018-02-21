# basic-dockerize
This is a barebones project with a Dockerfile that creates a image from the latest Node.js image and installs the Node.js web service source code from this folder.

To build the Docker image:

`docker build -t basic-dockerize .`

Don't miss the period at the end of that statement. Docker will chug for awhile as it downloads the various layers it needs for the image.

Once the image has been created, its existence can be verified in the local repository:

```
docker images

REPOSITORY          TAG                 IMAGE ID            CREATED              SIZE
basic-dockerize     latest              43ea15c8a66f        About a minute ago   680MB
node                carbon              292a11903b0d        4 days ago           676MB
```

To run a new container using the image:

```
docker run -p 8181:8080 -d basic-dockerize

e2299030ac2ab0e9fc976dc774870e3668e2bf4b86cbef4ca560ac85d965b298
```

The *-p* option maps port 8181 of the host to port 8080 of the container. The *-d* option causes the container to be run in the background and to output a long identifier that is the unique identifier of the container.

Verify that the web service running in the container is responding by using *curl*:

```
curl http://127.0.0.1:8181

Hello World!
```

To obtain a list of containers:

```
docker ps

CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS                    NAMES

e2299030ac2a        basic-dockerize     "npm start"         12 minutes ago      Up 12 minutes       0.0.0.0:8181->8080/tcp   keen_raman
```

Stop the container with:

```
docker stop e2299030ac2a

e2299030ac2a
```

Confirm that the container has stopped by running `docker ps` again and verifying the absence of the container's process in the list.



