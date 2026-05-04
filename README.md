**Phase 1" Creating EC2 instance.** In setting up a Linux server on which Apache is deployed, a server which is accessible over the internet, scalable and always available is needed. An amazon EC2 instance was created and hosted within the public subnet in the VPC (prod-web-vpc) as a cloud-based Linux server
<img width="614" height="353" alt="creating my environment(VPC)" src="https://github.com/user-attachments/assets/491c2ff0-d981-4e47-8b5c-c5445a3322f1" />

An amazon Linux server with the following configuration was create; Amazon Linux was used and the AMI, instance type was set to the basic t2.micro, a keypair was created to enable secured connection and a security group for restrictions and security. In other to grant remote access and manage configurations on the Linux server, SSH (on port 22) was allowed. To access Apache from browser, HTTP (on port 80) was allowed.
<img width="613" height="350" alt="Apache Server" src="https://github.com/user-attachments/assets/fcff2188-1bc4-4ed5-905f-0483fb068d3c" />

**Phase 2: SSH into server.** Create and attach an internet gate way to the VPC allowing traffic to browsers. Create route tout table linking internet gate way and public subnet. Connect to server though SSH while applying restricted assess using the command “chmod 400 "key.pem". then connect to the server through “ssh -i "key.pem" ec2-user@54.163.22.219”
<img width="456" height="263" alt="image" src="https://github.com/user-attachments/assets/8be4251e-f862-427a-b010-dc7ba2178706" />

**Phase 3: Install apache.** To install apache, it is neccessary to undate the system so to avoid any installation conflict. Run "sudo yum update -y" to update the system then "sudo yum intall httpd -y" to install apache httpd server. 
<img width="718" height="616" alt="installing apache 1" src="https://github.com/user-attachments/assets/8a1eb387-d2c5-433b-9208-8de8042851c8" />
<img width="720" height="372" alt="installing apache 2" src="https://github.com/user-attachments/assets/72c491f9-e5f9-4610-88d6-c942bcb2ed44" />
After installing Apache, I started and enabled the service to ensure availability across reboots.
Then run "sudo systemctl status httpd" to confirm that apache is active. Then copy ec2 ip and paste in you broswer to confirm that apache listens to port 80.
<img width="721" height="408" alt="apache status check" src="https://github.com/user-attachments/assets/6b1e19d7-7f2f-45cf-9617-2fd5218efbe5" />

