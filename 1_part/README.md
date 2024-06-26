## Submissions for part 1

### Exercise 1.1

![ex 1.1](./pics/ex_1_1.png)

### Exercise 1.2

Before
![ex 1.1 before](./pics/ex_1_2_1.png)

and after
![ex 1.1 after](./pics/ex_1_2_2.png)

### Exercise 1.3
The commands used and the secret message can be seen in the picture.
![Ex 1.3](./pics/ex_1_3.png)

### Exercise 1.4
To start the container i used:
```
$ docker run -d -it --name script ubuntu sh -c 'while true; do echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website; done'
```
After that, I attached the container with the following command:
`$ docker attach script`

When prompted for an input, I answered 'helsinki.fi'. This, however, did not work, because curl was not yet installed. I then started a bash-session in the container with `$ docker exec -it script bash`, where I first updated the package manager and all installed packages and then installed curl (`$ apt update && apt upgrade && apt install curl`). After this, when reattaching to the container, I re-entered 'helsinki.fi' and the whole thing worked as intended (here I attached to the container ID instead of name). Screenshot of the result below...
![ex 1.4](./pics/ex_1_4.png)

### Exercise 1.5
Downloaded both images with docker pull
```
$ docker pull devopsdockeruh/simple-web-service:ubuntu && docker pull devopsdockeruh/simple-web-service:alpine
```

Looking at the image sizes, we can see that the ubuntu one is quite a lot heavier. This makes sense, as Alpine is made to be a super lightweight distribution.
![Picture 1, exercise 1.5](./pics/ex_1_5_1.png)

After that I spun 2 new containers, one running ubuntu and the other one running alpine.
```
$ docker run -d --name alpine devopsdockeruh/simple-web-service:alpine
$ docker run -d --name ubuntu devopsdockeruh/simple-web-service:ubuntu
```

Now I went inside the alpine container to check if the program was running, and surely enough it seems to be working fine:
![Picture 2, exercise 1.5](ex_1_5_2.png)

## Exercise 1.6
Started by pulling the container given in the material, with the command:
`$ docker pull devopsdockeruh/pull_exercise`

When running the container I was prompted for a password that I did not know. Upon opening the DockerHub-page for the image, this came up. Seems that the password the container is looking for could be "basics".
![Picture 1, exercise 1.6](./pics/ex_1_6_1.png)

And surely enough, the password was correct!
![Picture 2, exercise 1.6](./pics/ex_1_6_2.png)

## Exercise 1.7
The files for this exercise can be found in the [ex_1_7-directory](./ex_1_7).

## Exercise 1.8
The files for this exercise can be found in the [ex_1_8-directory](./ex_1_8).

## Exercise 1.9
I started by creating a file to put the logs into:
`$ touch text.log`

Then I started the container with my logfile as an outside volume:
`$ docker run -d -v "$(pwd)/text.log:/usr/src/app/text.log" devopsdockeruh/simple-web-service:ubuntu`

Now I can access the logs made by the container in my own filesystem with the command `cat text.log`

## Exercise 1.10
Ran the following command to start the web server:
`$ docker run -d -p 127.0.0.1:3000:8080 web-server:latest`


## Exercise 1.11
[Here is the link to the Dockerfile.](./ex_1_11/Dockerfile)
Afterwards I built it as `spring-simple-button` and ran it with
```bash
$ docker run -d -p 127.0.0.1:3000:8080 spring-simple-button:latest
```

## Exercise 1.12
[Here is the link to the Dockerfile.](./ex_1_12/Dockerfile)

## Exercise 1.13
[Here is the link to the Dockerfile.](./ex_1_13/Dockerfile)
I named the image `hello-backend`.

Then I started the container with the following command:
```bash
$ docker run -d -p 8080:8080 hello-backend:latest
```

## Exercise 1.14
* [Here is the Frontend-Dockerfile](./ex_1_14/frontend/Dockerfile)
* [Here is the Backend-Dockerfile](./ex_1_14/backend/Dockerfile)

Built them as a v2-tag of the older image and started both the backend and the frontend with the following commands:
```bash
$ docker run -d -p 5000:5000 hello-frontend:v2
```
```bash
$ docker run -d -p 8080:8080 hello-backend:v2
```

After spinning up both containers I went to check `localhost:5000` in my browser, and when clicking the button for this exercise, I was greeted with this sight:
![Exercise 1.14](./pics/ex_1_14.png)

## Exercise 1.15
I didn't have a great project (that wasn't super broken) for this, but I made a simple webapp with Flask that I hope will suffice for this. I assume the point of this exercise is more on learning to push to DockerHub, than creating a magnificent Dockerfile from a megaproject we have laying around.

[Here is the link to DockerHub](https://hub.docker.com/r/sinyman/hello-flask/tags)

As for instructions on how to run the project, check out [the GitHub repo for the project.](https://github.com/sinyman/hello-flask)

#### TL;DR
```bash
$ docker pull sinyman/hello-flask && docker run -d -p 5000:5000 sinyman/hello-flask
```

## Exercise 1.16
Using my right to skip one exercise per part on this one :D



