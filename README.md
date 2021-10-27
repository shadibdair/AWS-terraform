# AWS-terraform
Build Nginx docker image, Using services as CodeCommit ECR ECS LoadBalancer and Cloud9.
----

## The command I've used inside the Cloud9
> Create new environment, Started run the image ...
> <img width="1344" alt="Screen Shot 2021-10-27 at 2 17 07" src="https://user-images.githubusercontent.com/43513994/138974482-9e85d121-44f0-4b29-bf29-aa7d4868169e.png">


### To build nginx docker image, and replace the index.html inside the nginx image :

```
$ docker pull nginx
```

### The index.html that I need to replace him inside the image nginx :

```
<!DOCTYPE html>
<html>

<head>
  <title>Hello World</title>
</head>

<body>

  <h1>Always Smile</h1> 
  <h2>Never give up</h2>

  <p>Have a nice day</p>

</body>

</html>

```

### To replace the index.html inside the image, I've build a Dockerfile :

```
$ nano Dockerfile

  FROM  nginx:latest

  COPY ./index.html /usr/share/nginx/html/index.html

# [Build the Dockerfile]
$ docker build --tag="nginx-docker" .

# [Login inti AWS account]
$ aws ecr get-login-password --region eu-west-2 | docker login --username AWS --password-****n 00********00.dkr.ecr.eu-west-2.amazonaws.com

# [Tag the image]
$ docker tag nginxdocker 00********00.dkr.ecr.eu-west-2.amazonaws.com/last-repo-euwest2:latest

# [Pushed the image into CodeCommit repo]
$ docker push 00********00.dkr.ecr.eu-west-2.amazonaws.com/last-repo-euwest2:latest
```

### I've pushed the nginx image that built to ECR :
> The result :
<img width="1400" alt="Screen Shot 2021-10-27 at 2 21 20" src="https://user-images.githubusercontent.com/43513994/138974949-82dcda11-6dd9-4289-8cb4- 

### The services in AWS :
<img width="1400" alt="Screen Shot 2021-10-27 at 2 41 46" src="https://user-images.githubusercontent.com/43513994/138976979-dd678b35-04eb-4c4c-bbe1-695755849ae3.png">

### The Instances :
<img width="1424" alt="Screen Shot 2021-10-27 at 3 14 22" src="https://user-images.githubusercontent.com/43513994/138979383-c966aa00-c104-497a-837c-deb1d55bc459.png">

### Why I've created the LoadBalancer service :
> serves as the single point of contact for clients. The load balancer distributes incoming application traffic across multiple targets, such as EC2 instances, in multiple Availability Zones, This increases the availability of your application. You add one or more listeners to your load balancer.

<img width="1322" alt="Screen Shot 2021-10-27 at 3 27 36" src="https://user-images.githubusercontent.com/43513994/138980511-4718a2da-de7c-4e09-a750-7c787c4ca2d6.png">




