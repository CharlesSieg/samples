# basic-dockerize
This is a barebones project with a Dockerfile that, essentially, creates a container that starts with a Node.js image and installs the Node.js web service source code in this folder.

To build the Docker container:

`docker build -t simple-node-service .`

Don't miss the period at the end of that statement.

Once the container has been created, you can verify its existence with:

`docker images`

To run the container:

`docker run -p 8181:8080 -d simple-node-service`

Verify that the web service is responding by using curl:

`curl http://127.0.0.1:8181`

Get the container ID of the container:

`docker ps`

Stop the container with:

`docker stop <CONTAINER ID>`





