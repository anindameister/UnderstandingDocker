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
- meaning
1. Situation:- ubuntu system with docker installed on it. 










