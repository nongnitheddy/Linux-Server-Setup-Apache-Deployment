# Install and deploy Apache on EC2 using Linux
## Phase 1: Creating EC2 instance
In setting up a Linux server on which Apache is deployed, a server which is accessible over the internet, scalable and always available is needed. An amazon EC2 instance was created and hosted within the public subnet in the VPC (prod-web-vpc) as a cloud-based Linux server
<img width="614" height="353" alt="creating my environment(VPC)" src="https://github.com/user-attachments/assets/491c2ff0-d981-4e47-8b5c-c5445a3322f1" />

An amazon Linux server with the following configuration was create; Amazon Linux was used and the AMI, instance type was set to the basic t2.micro, a keypair was created to enable secured connection and a security group for restrictions and security. In other to grant remote access and manage configurations on the Linux server, SSH (on port 22) was allowed. To access Apache from browser, HTTP (on port 80) was allowed.
<img width="613" height="350" alt="Apache Server" src="https://github.com/user-attachments/assets/fcff2188-1bc4-4ed5-905f-0483fb068d3c" />

## Phase 2: SSH into server
Create and attach an internet gate way to the VPC allowing traffic to browsers. Create route tout table linking internet gate way and public subnet. Connect to server though SSH while applying restricted assess using the command “chmod 400 "key.pem". then connect to the server through “ssh -i "key.pem" ec2-user@54.163.22.219”
<img width="456" height="263" alt="image" src="https://github.com/user-attachments/assets/8be4251e-f862-427a-b010-dc7ba2178706" />

## Phase 3: Install apache
To install apache, it is neccessary to undate the system so to avoid any installation conflict. Run "sudo yum update -y" to update the system then "sudo yum intall httpd -y" to install apache httpd server. 
<img width="718" height="616" alt="installing apache 1" src="https://github.com/user-attachments/assets/8a1eb387-d2c5-433b-9208-8de8042851c8" />
.
<img width="724" height="372" alt="installing apache 2" src="https://github.com/user-attachments/assets/2b099ca9-caeb-4adf-a8a4-6a3631f3721b" />

After installing Apache, I started "sudo systemcl start httpd" and enabled the service "sudo systemctl enable httpd" to ensure availability across reboots.
Then run "sudo systemctl status httpd" to confirm that apache is active. Then copy ec2 ip and paste in you broswer to confirm that apache listens to port 80.
<img width="721" height="408" alt="apache status check" src="https://github.com/user-attachments/assets/6b1e19d7-7f2f-45cf-9617-2fd5218efbe5" />

Create an index.html page within Apache’s root directory. Run "touch index.html" to create a file into which the index.html page file will be set up withing the system directory
<img width="1281" height="904" alt="index html" src="https://github.com/user-attachments/assets/e36d740b-eff7-4833-8bdf-f52ccd1ac6f9" />

## Phase 4: Granting permissions
Apache runs as a different user than the file owner, so it needs read access under the ‘others’ category. Setting permissions to 644 ensures the owner can modify the file while Apache can safely read and serve it without exposing write permissions, which maintains security.
<img width="880" height="526" alt="granting permisson for index html" src="https://github.com/user-attachments/assets/75ab3d1c-8b5f-45ef-a82c-6ea8e75449c7" />

Grant "755" permission to the directory allowing access for Apache to read files inside the directory /var/www/html/index.html
<img width="954" height="252" alt="granting directory permission" src="https://github.com/user-attachments/assets/f364fa27-f735-44d4-87ae-2fff982484e8" />

## Launching your website
Restart apache http server "sudo systemctl restart httpd" and reload the website to view the changes displayed in the index.html file
<img width="1914" height="886" alt="launchin website" src="https://github.com/user-attachments/assets/af27c9ca-990b-47e2-90ef-df3fcb0247d0" />




