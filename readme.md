# understanding docker

## scenario- when did the speaker first need to use docker

![begining](https://github.com/anindameister/UnderstandingDocker/blob/master/snaps/1.PNG)

- url https://www.youtube.com/watch?v=wxxigbHwDGM

#### project

- webServer: node js
- database: mongoDB
- messaging system: Redis
- orchestration tool: ansible

##### the issues that came up during the development process using all the above conponents

1. compatibility with the underlying OS
- all the services weren't compatible with the versions of OS, that was being planned to use
- situation came up, when some services weren't compatible with some OS, and the speaker had to go back to find a different OS

2. compatibility between services and libraries,dependencies of the OS
- issues where one version required one version of dependent library whereas another service required another version
- the architecture of the applications changed over times. The speaker had to upgrade to newer versions of these components or change the database etc
- and everytime, something changed; the speaker had to go the same process of checking compatibility between these various components and the underlying infrastructure	
- this compatible matrix issue issue is usually referred to as "The Matrix from Hell!!"

![The Matrix from Hell!!](https://github.com/anindameister/UnderstandingDocker/blob/master/snaps/2.PNG)

3. whenever, there was a new developer on board, it was difficult to setup the new environment

![new developer intro!](https://github.com/anindameister/UnderstandingDocker/blob/master/snaps/3.PNG)

- difficult to setup a new environment
- developers have to follow a large set of instructions and run hundreds of commands to finally setup their environment
- developers had to check that they were using the right operating system, the right versions of each of these components
- each developer had to set all that up, by themself, each time 
- the group might also have a different test and development environment.
- one maybe comfortable to use one OS, and the other new developer maybe comfortable with some other one 
- and so there's no guarantee that the apps that the group is building is gonna run in the same way in different environments
- all of the above made the life of the group, in regards to developing,building and shipping the application; really difficult
- hence there was a requirement of something which would help the group with the compatibility issue, 
- something which would allow the group to modify or change these components without affecting the other components and even modify the underlying operating system as required
- and that search landed to docker

![new developer problems above](https://github.com/anindameister/UnderstandingDocker/blob/master/snaps/4.PNG)

4. The Docker

![The Docker](https://github.com/anindameister/UnderstandingDocker/blob/master/snaps/5.PNG)

- with docker, the speaker was able to learn each compoents in a separate container with it's own libraries and it's own dependencies
- all on the same VM and the OS, but within separate environment or containers

![The Docker](https://github.com/anindameister/UnderstandingDocker/blob/master/snaps/6.PNG)

- the group had to just build the docker configuration once 
- and now all the developers were able to get started with a simple docker run command irrespective of what the underlying operating system they were on; all they needed to make sure that they had docker installed on their systems

![The Docker](https://github.com/anindameister/UnderstandingDocker/blob/master/snaps/7.PNG)

5. what are containers

![containers](https://github.com/anindameister/UnderstandingDocker/blob/master/snaps/8.PNG)

- containers are completely isolated environments as in they can have their own processes or services, their own networking interfaces, their own mounts just like virtual machines except they all share the same operating system kernels
- kernels

![kernels](https://github.com/anindameister/UnderstandingDocker/blob/master/snaps/9.PNG)

- different types of containers are LXC/LXD/LX EFS etc
- docker utilises LXC containers
- setting up these containers is hard as they're very low level 
- so docker gives high level powerful tools, thereby easing the work of endusers like us
- types of OS https://www.geeksforgeeks.org/types-of-operating-systems/
- OS like ubuntu, fedora, CentOS, SUCI comnsists of two things- OS kernel and set of software
- os kernel is responsible to interact with the underlying hardware

![kernels](https://github.com/anindameister/UnderstandingDocker/blob/master/snaps/10.PNG)

- while the os kernel remains the same, which is linux in the case of ubuntu, fedora, CentOS, SUCI; it's the software above it which makes the OS different
- this software may consist of different user interface, drivers, compilers, file managers, developer tool etc.
- so therefore, we have a common linux kernel shared across all operating systems and some custom software that differentiates operating systems from each other

#### docker containers share the underlying kernel

![kernels](https://github.com/anindameister/UnderstandingDocker/blob/master/snaps/11.PNG)

- meaning
1. Situation:- ubuntu system with docker installed on it. 

![ubuntu system with docker installed on it](https://github.com/anindameister/UnderstandingDocker/blob/master/snaps/14.PNG)

- docker has the capability to run any flavour of OS on top it, as long as they are all based on the same kernel in this case, Linux
- if the underlying operating system is ubuntu, docker can run a container based on another distribution like Debian, Fedora, CentOS, SUCI.
- each docker container has that additional software that makes these OS different and docker utilises the underlying kernel of kernel host which works with all the OS above.

2. situation- OS that do not share the same kernel as this. Eg: Windows

- so you wont be able to run a windows based container on a docker host with Linux OS on it
- for that, you'd require docker on a windows server
- question: isn't the above situation, a disadvantage; not being able to run another kernel on the OS
- the answer is no, because unlike hypervisors; docker is not meant to virtualise and run different OS and kernels on the same hardware
- the main purpose of docker is containerise application and to ship them to run them
- Hypervisor : a tool which control and distributes the hardware resources to each OS according to their needs



- vitualisation details: 5/45 URL: https://github.com/anindameister/UnderstandingDocker/blob/master/files/cm2%20(1).pdf , seems that download is required

#### difference between virtual machines and containers

- docker, we have the 
1. underlying hardware
2. OS
3. docker installed on the OS
4. docker can then manager the libraries and dependencies,alone

![docker](https://github.com/anindameister/UnderstandingDocker/blob/master/snaps/15.PNG)

-vm
1. os on the underlying hardware
2. hypervisor like ESX or virtualisation of some kind
3. and then the VMs
4. as we can see, each VMs has it's own operating systems inside it; 
5. then the dependencies
6. and then the applications
7. this overhead causes higher utilisation of resources as there are mutiple virtual os and kernels running
8. VMs also consume higher disk space as each VM in heavy, like GBs in size
9. whereas docker containers are lightweight and usually in MBs in size
10. point 9. let's docker containers to boot up faster like in seconds whereas VMs take minutes to boot up because they need to boot up the entire OS

![difference between virtual machines and containers](https://github.com/anindameister/UnderstandingDocker/blob/master/snaps/16.PNG)

- handwritten docker status with absolutely comparison in regards to having OS as a parameter

![difference between virtual machines and containers](https://github.com/anindameister/UnderstandingDocker/blob/master/snaps/23.jpeg)

11. important to note that dockers has less isolation more resources are shared between the containers like the kernels whereas VMs have complete isolation from each other
12. since VMs dont rely on underlying OS or kernel, we can have different kinds of OS like windows based or linux based on the same hypervisor whereas it is not possible on a single docker host

#### how is it done??

1. there are a lot of containerised applications, readily available as of today
2. so most organisers get their product containerised and make it available in a public docker registry called dockerhub or docker store

![public docker registry called dockerhub or docker store](https://github.com/anindameister/UnderstandingDocker/blob/master/snaps/17.PNG)

3. we can find the images of most common OS, databases and other services and tools to identify the images, you need and you install docker on your host, bringing up an application stack is as easy as running the docker run command with the name of the image

![public docker registry called dockerhub or docker store](https://github.com/anindameister/UnderstandingDocker/blob/master/snaps/18.PNG)

![public docker registry called dockerhub or docker store](https://github.com/anindameister/UnderstandingDocker/blob/master/snaps/19.PNG)

4. in our case, running a docker run Ansible command  will run an instance of Ansible on the docker host

```
docker run ansible
```

5. we can also run instance of mongoDB, nodeJS, Redis with docker run command

6. when we run node js, we just need to point to the code repository on the host

7. if we need to run multiple instances of the webservice, simply add as many instances as you need and configure a load balancer of some kind in the front

![run multiple instances of the webservice](https://github.com/anindameister/UnderstandingDocker/blob/master/snaps/20.PNG)

8. in case one of the instance, is to fail, then we got to simply destroy that instance and launch a new instance

![simply destroy that instance and launch a new instance](https://github.com/anindameister/UnderstandingDocker/blob/master/snaps/21.PNG)

9. there are other solutions to handle such cases, LATERS

#### containers vs image

1. an image is a package of template just like a VM, that we mighgt have come across in the virtualisation world
2. an image is used to create one or more containers
3. containers are running instances of images that are isolated and have their own environment of set of processes
4. a lot of products have been dockerised already
5. in case you're not able to find what you're looking for; you can create an image yourself and push it to the dockerhub repository making it available for the public

![containers vs image](https://github.com/anindameister/UnderstandingDocker/blob/master/snaps/22.PNG)
 







