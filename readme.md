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

