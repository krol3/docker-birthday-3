#Notes

##pull images and run
docker pull alpine
docker run alpine echo "hello from alpine"
docker run alpine uptime
docker run alpine /bin/sh
docker run -it alpine /bin/sh

docker inspect alpine

###image single-page website 
docker run seqvence/static-site

###run in detached mode
docker ps
docker stop a7a0e504ca3e
docker rm   a7a0e504ca3e

-d will create a container with the process detached from our terminal
-P will publish all the exposed container ports to random ports on the Docker host,
-e is how you pass environment variables to the container
--name allows you to specify a container name

docker run --name static-site -e AUTHOR="Carol Guival" -d -P seqvence/static-site

docker port static-site
443/tcp -> 0.0.0.0:32768
80/tcp -> 0.0.0.0:32769

docker run --name static-site-2 -e AUTHOR="Carol Guival" -d -p 8888:80 seqvence/static-site
docker stop static-site static-site-2
docker rm static-site static-site-2

##run the flask-app
docker build -t krol/myfirstapp .
docker run -p 8888:5000 --name myfirstapp krol/myfirstapp
docker stop myfirstapp
docker rm myfirstapp

docker-compose up -d

docker build --no-cache -t <YOUR_DOCKER_ID>/votingapp_voting-app .
docker build --no-cache -t krol/votingapp_voting-app .
docker build --no-cache -t krol/votingapp_result-app .

docker push krol/votingapp_voting-app
docker push krol/votingapp_result-app

docker ps -a | grep votingapp_result-app

docker logs -f 1e3e71900b7c

570341acdbfe43020220e060