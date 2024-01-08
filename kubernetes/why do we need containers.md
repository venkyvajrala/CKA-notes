![[Pasted image 20221208122015.png]]

- compatability issues - each tool may requuires different version of a OS librarry
- Long setup time - make sure they are using right OS, right version of all the tools ,etc
- Different Dev/Test/Prod environments  - each developer will like different OS to work with


Solution: containerizing applications
![[Pasted image 20221208122317.png]]
different containers - run with each of them having it's own libs and dependencies

containers - isolated environments -> their own network interface, their own and have shared OS  kernel



Docker uses shared OS kernel 
In below image we can see on top of OS kernel we will install different OS like ubuntu,centos,debian ,etc. all this Operating systems can work on Linux kernel.
docker uses directly this linux kernel instead of depending on guset os which is installed on top of OS kernel. So container built on ubuntu can run on other linux type OS but it can't run on windows which is not a linux kernel using OS.
 docker or any containerization tool responsibility is not to virtualize OS rather create isolated containers

![[Pasted image 20221208122802.png]]




