# AWS-terraform 🌦 !
Build Nginx docker image, Using services as CodeCommit ECR ECS LoadBalancer and Cloud9.
----

## The command I've used inside the Cloud9
__*Create new environment, Started run the image ...*__
> <img width="1344" alt="Screen Shot 2021-10-27 at 2 17 07" src="https://user-images.githubusercontent.com/43513994/138974482-9e85d121-44f0-4b29-bf29-aa7d4868169e.png">

## Login inside the Cloud9
<img width="1282" alt="Screen Shot 2021-10-27 at 4 26 59" src="https://user-images.githubusercontent.com/43513994/138985182-94afabe4-8097-4807-9f76-8906f654a4d9.png">


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
__*The result :*__
<img width="1400" alt="Screen Shot 2021-10-27 at 2 21 20" src="https://user-images.githubusercontent.com/43513994/138982066-007b3a91-c924-4b1c-8169-49ee93b07e25.png">


### The services in AWS :
<img width="1400" alt="Screen Shot 2021-10-27 at 2 41 46" src="https://user-images.githubusercontent.com/43513994/138976979-dd678b35-04eb-4c4c-bbe1-695755849ae3.png">


### Then I've created the task definition :
__*A task definition is required to run Docker containers in Amazon ECS.*__
<img width="1412" alt="Screen Shot 2021-10-27 at 3 43 24" src="https://user-images.githubusercontent.com/43513994/138981712-19185afa-f189-4ec8-93d8-ff4325521934.png"> 

### Inside the cluster, Service, Task and Instance :
__*An Amazon ECS service allows you to run and maintain a specified number of instances of a task definition simultaneously in an Amazon ECS cluster.*__
<img width="1169" alt="Screen Shot 2021-10-27 at 4 02 14" src="https://user-images.githubusercontent.com/43513994/138982720-36a19c5b-02a0-49cf-ab6f-6e13de36f21d.png">
<img width="1169" alt="Screen Shot 2021-10-27 at 4 06 40" src="https://user-images.githubusercontent.com/43513994/138983129-d07578ee-f576-4155-a9ba-44b0f862da51.png">
<img width="1144" alt="Screen Shot 2021-10-27 at 4 10 45" src="https://user-images.githubusercontent.com/43513994/138983333-5ac60a1b-70ca-4fb1-a4c7-757a32a642ec.png">



### The Instances :
<img width="1424" alt="Screen Shot 2021-10-27 at 3 14 22" src="https://user-images.githubusercontent.com/43513994/138979383-c966aa00-c104-497a-837c-deb1d55bc459.png">

### Why I've created the LoadBalancer service :
__*serves as the single point of contact for clients. The load balancer distributes incoming application traffic across multiple targets, such as EC2 instances, in multiple Availability Zones, This increases the availability of your application. You add one or more listeners to your load balancer.*__

<img width="1322" alt="Screen Shot 2021-10-27 at 3 27 36" src="https://user-images.githubusercontent.com/43513994/138980511-4718a2da-de7c-4e09-a750-7c787c4ca2d6.png">

### The final result :

<img width="1101" alt="Screen Shot 2021-10-27 at 4 40 30" src="https://user-images.githubusercontent.com/43513994/138986082-128592d7-c8ef-46b6-8bef-d0bb39eccfb8.png">


#### Thank you for your time 😄.
__*-Shadi Badir 🕺.*__


