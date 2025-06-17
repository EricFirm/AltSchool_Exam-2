# Setting up a dynamic Prototype of a Web Application  

### 1. Provision an EC2 Instance on AWS - 
I signed in to AWS Console, navigated to EC2 and clicked on "Launch Instance" - Chose AMI: Ubuntu (e.g., Ubuntu 20.04 LTS) - Selected Instance Type: t2.micro - Configured Instance Details by using default settings - Storage: 8GB, configured Security Group: - Create new security group - Add rules: SSH (port 22) from your IP, HTTP (port 80), HTTPS (port 443) from 0.0.0.0/0. Then I launched.

### 2. Connect to the Instance - SSH into the Instance:   
I ssh-in my instance using my key-pair and Public IP address.   

### 3. Updating the System, Installing Nginx and Configuring Nginx:
I updated the system by using ``sudo apt update && sudo apt upgrade -y ``
Installing, starting and enabling Nginx was done using the following commands:  
 ``sudo apt install nginx -y``
 
  ``sudo systemctl start nginx``
  
  ``sudo systemctl enable nginx``

  Nginx was configured to listen to port 80 for it to run the website.

### 4. Setting Inbound rules and firewalls
  
I edited the inbound rules on the instance to allow for traffic into HTTP, TCP, Port 80 and 443 and also set rules to allow "ping" and "curl".

I also edited the firewall to allow port 80 and 443 using:

  ``sudo ufw allow 80``
  
  ``sudo ufw allow 443``
  
  ``sudo ufw enable``  

### 5. Designing and building the Website

The website was designed using HTML; the structure of the website nad CSS; for the look, feel and a bit of animation.

### 6. Deploying the website
After building the website using HTML and CSS on VSCode, the file was pushed to GitHub. The repository is then cloned on to my server and changes are pulled using the command ``git pull origin master``. 

To automate this process of ``git pull orign master``, a cronjob was setup to check for changes to the repository and effect the changes. The cronjob was set up to take place every 5 minutes. 

### 7. Screenshot of the rendered page
Below is a picture showing the screenshot of the rendered page:
![Rendered_page](assets/images/Screenshot_rendered_page)
