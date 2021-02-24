## Task 8.1

Installing Jenkins (long term release) on Ubuntu 20.04 (VM - paul-VirtualBox) (needed to install Java):
   
![Image1](screenshots/1.jpg "1")

![Image2](screenshots/2.jpg "2")

![Image3](screenshots/3.jpg "3")

Starting Jenkins and checking status:

![Image4](screenshots/4.jpg "4")

Entering 192.168.1.7 port 8080 to customize Jenkins ( to do this I had to enter initial key from var/lib/jenkins/secrets/initialAdminPassword):

![Image5](screenshots/5.jpg "5")

![Image6](screenshots/6.jpg "6")

Entering as a user jenkins and generating SSH key pair:

![Image7](screenshots/7.jpg "7")

Logging to another VM (VM1) as a root and copying SSH public ket into .ssh/authorized_keys:

![Image8](screenshots/8.jpg "8")

And checking connection from VM paul-VirtualBox to VM1:

![Image9](screenshots/9.jpg "9")



