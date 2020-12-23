# Task2.2

Created VM with **Amazon Lightsail** and connected to it:

![Image1](screenshots/Image1.jpg "Image1")

Launched Linux VM (t2.micro) with **EC2**, created snapshot, created and attached Disk_D (EBS) 10 GB:

![Image2](screenshots/Image2.jpg "Image2")

Loged to **EC2** instance, viewed list of available disks using ```lsblk```, checked if the volume has any data using ```sudo file -s /dev/xvdf```, formatted the volume to ext4 using ```sudo mkfs -t ext4 /dev/xvdf```, created dir “Disk_D”, mounted the volume to this dir using ```sudo mount /dev/xvdf /Disk_D/```, checked the disk space ```df -h .```, made 3 files “test-1, test-2, test-3”`:

![Image23](screenshots/Image23.jpg "Image23")
![Image25](screenshots/Image25.jpg "Image25")

To enable automount made entry in “/etc/fstab”:

![Image24](screenshots/Image24.jpg "Image24")

Launched another instance from snapshot, detached Disk_D and attached to the new instance:

![Image27](screenshots/Image27.jpg "Image27")

Launched and configured Amazon **Lightsail WordPress** instance:

![Image31](screenshots/Image31.jpg "Image31")

Stored, retrieved a file using Amazon **S3 bucket**:

![Image41](screenshots/Image41.jpg "Image41")

Created **S3 bucket**, added file from local dir, downloaded from bucket to local, deleted bucket using **CLI** (to do this I created IAM user - AWS_Admin):

![Image461](screenshots/Image461.jpg "Image461")
![Image462](screenshots/Image462.jpg "Image462")

Created a cluster on Amazon **ECS** and ran the online application:

![Image52](screenshots/Image52.jpg "Image52")

Created **a static website on Amazon S3** (publicly available):
http://khafazov-bucket.s3-website.eu-central-1.amazonaws.com












  
   
