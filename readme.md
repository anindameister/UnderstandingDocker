# understanding docker

## scenario- when did the speaker first need to use docker

![begining](https://github.com/anindameister/UnderstandingDocker/blob/master/snaps/1.PNG)

#### project

- webServer: node js
- database: mongoDB
- messaging system: Redis
- orchestration tool: ansible

##### the issues that came up during the development process using all the above conponents

1. compatibility with the underlying OS
- all the services were compatible with the versions of OS, that was being planned to use
- situation came up, when some services weren't compatible with some OS, and the speaker had to go back to find a different OS

2. compatibility between services and libraries,dependencies of the OS
- issues where one version required one version of dependent library whereas another service required another version
- the architecture of the applications changed over times. The speaker had to upgrade to newer versions of these components or change the database etc
- and everytime, something changed; the speaker had to go the same process of checking compatibility between these various components and the underlying infrastructure	
- this compatible matrix issue issue is usually referred to as "The Matrix from Hell!!"

![The Matrix from Hell!!](https://github.com/anindameister/UnderstandingDocker/blob/master/snaps/2.PNG)
