In setting up a Linux server on which Apache is deployed, a server which is accessible over the internet, scalable and always available is needed. An amazon EC2 instance was created and hosted within the public subnet in the VPC (prod-web-vpc) as a cloud-based Linux server
<img width="614" height="353" alt="creating my environment(VPC)" src="https://github.com/user-attachments/assets/491c2ff0-d981-4e47-8b5c-c5445a3322f1" />

An amazon Linux server with the following configuration was create; Amazon Linux was used and the AMI, instance type was set to the basic t2.micro, a keypair was created to enable secured connection and a security group for restrictions and security. In other to grant remote access and manage configurations on the Linux server, SSH (on port 22) was allowed. To access Apache from browser, HTTP (on port 80) was allowed.
<img width="613" height="350" alt="Apache Server" src="https://github.com/user-attachments/assets/fcff2188-1bc4-4ed5-905f-0483fb068d3c" />
