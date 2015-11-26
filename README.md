<h1>About this</h1>
A docker container for PAPI

<h1>Guidelines</h1>
<h2>To build Docker image</h2>
Under the folder with dockerfile

Command:
> docker build -t papi-poc:<version tag> .

Example:
> docker build -t papi-poc:0.3 .

<h2>To Run Docker Container under Interaction Terminal</h2>
Command:
> docker run -it --cap-add SYS_PTRACE --rm -p 8081:80 -p 28081:9001 -p 18081:8008 -v /home/vagrant/queues:/data --name papi-poc papi-poc:0.3

Example:
> docker run -it --cap-add SYS_PTRACE --rm -p 8081:80 -p 28081:9001 -p 18081:8008 -v /home/vagrant/queues:/data --name papi-poc papi-poc:0.3

<h2>To Run Docker Container under Detach Mode</h2>
Command:
> docker run -d --cap-add SYS_PTRACE --restart=always -p 8081:80 -p 28081:9001 -p 18081:8008 -v /home/vagrant/queues:/data --name papi-poc papi-poc:0.3

Example:
> docker run -d --cap-add SYS_PTRACE --restart=always -p 8081:80 -p 28081:9001 -p 18081:8008 -v /home/vagrant/queues:/data --name papi-poc papi-poc:0.3

<h2>To SSH into Container</h2>
First, find the container ID:
> docker ps 

Next, login to the container
> docker exec -i -t <container ID> bash 

Example:
> docker exec -i -t b9584c8a4893 bash 

<h2>To copy a file from container</h2>
docker cp myapp-web:/etc/nginx/sites-available/laravel /vagrant/laravel

<h2>To remove a container</h2>
## Clean up inactive container - need 4 cores vagrant instances and 2 GB Ram
docker rm $(docker ps -a | grep '2 days ago' | awk '{print $1}')

# or Remove all
docker rm $(docker ps -a -q)

