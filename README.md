# Docker-LoadBalancer
Load Balancing between docker containers using AWS Application Load Balancer and Nginx Load Balancer

# Description

Here I have created a setup to use flask application in 3 docker containers and to load balance them using either AWS [Application load balancer](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html) or Using [Nginx Load balancer](https://docs.nginx.com/nginx/admin-guide/load-balancer/http-load-balancer/). The flask application uses [ipstack](https://ipstack.com/) API key to get details about any public IP address and shows its country when called on any browser. The data received from ipstack is cached on a redis database and reused if the same ip is looked up again.In AWS load balancer setup one redis container and 3 application containers are created. The ACM SSL certifictae is used for application load balancer. In the Nginx load balancer setup a Nginx container is also added and currently a selfsigned SSL is used (you can add your SSL certificate and key during creation). You can add your SSL certificate by editing the 'ssl.crt' and 'ssl.key' files. 

## How to use

1.AWS Load Balancer
-------------------

```
1. Install docker-compose
# curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
# chmod +x /usr/local/bin/docker-compose

2. Clone this Repo to your server
# git clone https://github.com/MarkAntonyGit/Docker-LoadBalancer.git
# cd Docker-LoadBalancer/AWS_ALB

3. Run following command to start the Containers
# docker-compose up -d

4. Create Application Load Balancer and Target group in AWS and add same instance based on ports '8081', '8082' and '8083' on the target group
```

2.Nginx Load Balancer
----------------------

```
1. Install docker-compose
# curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
# chmod +x /usr/local/bin/docker-compose

2. Clone this Repo to your server
# git clone https://github.com/MarkAntonyGit/Docker-LoadBalancer.git
# cd Docker-LoadBalancer/NGINX_LB

3. Add your SSL certificate and Private Key to the ‘ssl.crt’ and ‘ssl.key’ files.

4. Run following command to start the Containers
# docker-compose up -d
```

This is it! Your new Docker application with load balancer is ready to use.

### Sample Screenshots

##### AWS Load Balancer

-- Docker Containers 

![](https://raw.githubusercontent.com/MarkAntonyGit/MarkAntonyGit/main/Uploads/Docker%20Flask_IP/containers.JPG)

-- Website

![](https://raw.githubusercontent.com/MarkAntonyGit/MarkAntonyGit/main/Uploads/Docker%20Flask_IP/website1.jpg)
![](https://raw.githubusercontent.com/MarkAntonyGit/MarkAntonyGit/main/Uploads/Docker%20Flask_IP/website%202.JPG)

-- Target Group

![](https://raw.githubusercontent.com/MarkAntonyGit/MarkAntonyGit/main/Uploads/Docker%20Flask_IP/ALB_TG.JPG)

##### Nginx Load Balancer

-- Docker Containers

![](https://raw.githubusercontent.com/MarkAntonyGit/MarkAntonyGit/main/Uploads/Docker%20Flask_IP/Nginx_Containers.JPG)

-- Website

![](https://raw.githubusercontent.com/MarkAntonyGit/MarkAntonyGit/main/Uploads/Docker%20Flask_IP/Nginx_LB1.jpg)
![](https://raw.githubusercontent.com/MarkAntonyGit/MarkAntonyGit/main/Uploads/Docker%20Flask_IP/Nginx_LB2.JPG)

### Connect with me

--------<img src="https://img.shields.io/badge/-Mark%20Antony-brightgreen"/> ----------------------------------------------------------------------------------------------------------------------------------- <a href="https://www.linkedin.com/in/profile-markantony/"><img src="https://img.shields.io/badge/-Linkedin%20Profile-blue"/></a> ------------------------------------------------------------------------------------------------------------------------------------ <a href="mailto:markantony.alenchery@gmail.com"><img src="https://img.shields.io/badge/-markantony.alenchery@gmail.com-D14836?style=flat&logo=Gmail&logoColor=white"/></a>-------------------------------------------------------
