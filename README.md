<h1>About this</h1>
A docker container for PAPI

<h1>Guidelines</h1>
<h3>To build Docker image</h3>
Under the folder with dockerfile

Command:
> docker build -t papi-poc:< version tag > .

Example:
> docker build -t papi-poc:0.3 .

<h3>To Run Docker Container under Interaction Terminal</h3>
Command:
> docker run -it -p 8081:80 -p 28081:9001 -p 18081:8008 -v /docker/< service name >/data:/data --name papi-poc papi-poc:0.3

Example:
> docker run -it --cap-add SYS_PTRACE --restart=always --rm -p 8081:80 -p 28081:9001 -p 18081:8008 -v /home/vagrant/queues:/data --name papi-poc papi-poc:0.3

<h3>To Run Docker Container under Detach Mode</h3>
Command:
> docker run -d -p 8081:80 -p 28081:9001 -p 18081:8008 -v /docker/< service name >/data:/data --name papi-poc papi-poc:0.3

Example:
> docker run -d --cap-add SYS_PTRACE --restart=always -p 8081:80 -p 28081:9001 -p 18081:8008 -v /home/vagrant/queues:/data --name papi-poc papi-poc:0.3

<h3>To SSH into Container</h3>
First, find the container ID:
> docker ps 

Then, login to the container
> docker exec -i -t <container ID> bash 

Example:
> docker exec -i -t b9584c8a4893 bash 

<h3>To copy a file from container</h3>
Command:
> docker cp [OPTIONS] CONTAINER:PATH LOCALPATH
OR
> docker cp [OPTIONS] LOCALPATH|- CONTAINER:PATH

Example:
> docker cp papi-poc:/etc/nginx/nginx.conf /vagrant/nginx.conf

<h3>Clean up inactive container</h3>
You may need 4 cores vagrant instances and 2 GB RAM (Higher VM Spec)
> docker rm $(docker ps -a | grep '2 days ago' | awk '{print $1}')

OR Remove all
> docker rm $(docker ps -a -q)

