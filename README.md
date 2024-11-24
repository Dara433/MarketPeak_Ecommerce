<<<<<<< HEAD
readme file
# Objective

The goal of this project is to create an e-commerce website called Marketpeak, enhancing its functionality and resolving bugs through continuous integration and deployment workflow. Utilizing Git for version control, the platform was built using  a pre=exising e-commerce website template, developed in a linux enviroment, and deployed on a AWS EC2 instance


# Version control and Implementation of Git repository

## Initializing Git Repository 

After downloading a pre-exisiting website template, The next step involved creating a directory named MarketPeak_Ecommerce.
The command `mkdir` is used to create a directory. 

After navigating to the directory, it was initized as a git repository using `git init`. This would be the master branch
![git init](<img/1. git initize git repository.png>)

The next step involved copying the already downloaded website template into the newly created directory (MarketPeak_Ecommerce).

The website template is in the downloads folder. the command`cd` takes us back to the parent folder where the website template files  can be accessed. As demonstrated in the code, files were extracted from website template to MarketPeak_Ecommerce using the `cp` command, the `-r` flag is used to copy directories and all the contents recussively.

![cp -r](<img/2. git extract website template into project directory.png>)

## Staging and commiting to git 

With the website files now in Marketpeak-Ecommerce directory, the command `git add` stages the files and prepares them for commit.
the command `git commit -m` commits the staged files as a new commit snapshot. 

![git add](<img/3. git add.png>)
![git commit -m](<img/4. git commit.png>)

### Configuring Git and Pushing to github repository 

Prior to pushing the website files to the remote repository, it is essential to configure Git on the local repository. Since the code will be shared among various contributors. Configuring Git ensures that each change is identified, tracked, and properly attributed. This greatly facilitates collaboration."

While still in the acitve directory "MarketPeak_Ecommerce", the command `git config --global user.name` and `git config --global user.email` were executed. Configuring git on the local termial is crucial. Git requires and authentication so as to enhancing security and Identity management on the project.


![alt text](<img/5. git config and push to remote repository.png>)


The next step after this involves pushing the code to a remote reposity on Github.
A new remote repository was created named "MarketPeak_Ecommerce" (this remote repository was created without a README.md file so as to keep the original content of the website files. The README file will be added later on in the project). 

`git remote add` enables us to add a new remote repositoy to the local repository using the url of the remote repository. 


`git push -u origin master` allows us to push committed files from the local repository to the remote repository 




# EC2 Instance  and git repository Setup 

An EC2 instance was lauched on AWS management console, with the amazon machine image (AMI) as Amazon Linux. Instance type is a t2.micro free tier eligible. The security group was configured to allow ALL TRAFFIC, for both inbound and outbound therefore allowing no restrictions on protocols and ports flows to and from the instance. 
A new key pair was created and downloaded, Key file called 'website_template'. Connected to the instance by using its public IP as shown below 


![](<img/6. connecting to instance.png>)

In other to deploy the website from the EC2 instance, the website repository needs to be placed on the instance. 

However, Amazon Linus Operating System does not have git installed. A command was executed to install git on the Virtual machine `sudo yum install git`

![sudo yum install git](<img/7. sudo yum install git.png>)

After installing git, the command `git clone` was run on the AMI, enabling us to retieve the remote repository using the URL  

![git clone](<img/8. git clone.png>)



# Installing and configuring  Apache Webserver on EC2

## Installing apache HTTP server on EC2

The first command `sudo yum update -y` checks available updates to all installed packages and automatically installs them, ensuring that the system has the latest software and security patches., 

`sudo yum install httpd -y` installs Apache (also known as httpd)

`sudo systemctl start httpd` starts the web server 

`sudo system enable httpd` ensures server is automatically started on server boot. 

![alt text](<img/9. install Apache.png>)

## Configuring apache
![alt text](<img/10. sudo configure apache.png>)


In the code above, the default httpd web directory /var/www/html/ is cleared using the code `sudo rm- rf`, "rf" enables recussive remove of all directory content and files. 

 The command `sudo cp-r ~/MarketPeak_Ecommerce/* /var/www/html/` copies all files from MarketPeak Ecommerce website directory to default directory of the Apache webserver. 
 
 changes made were applied and reloaded with the command `sudo systemctl reload` as shown below

![sudo systemctl reload](<img/11. sudo reload.png>)


# Accessing Website using Public DNS &  Website development workflow

With Apache websever installed and running on the instance, it was time to test if the Website is live and accessible on the internet

Using the public IP of the EC2 instance, we lauched the website, it was also necessary to include the sub directories of the website fodler in other to access the website  (website_template & 2130_waso_strategy). 

http://98.83.147.172/website_template/2130_waso_strategy/

## Developing New Features and Fixes 

Implementing new features and bug fixes were carried out, git version control system ensures continous integration and Deployment.

After navigating to the website directory, a new branch was created called 'Development', the command `git branch` and `git checkout` enables us to create a new branch on the repository

A file containing new features and bug fixes 'index.html' is added on this branch, the file was staged `git add` and ready to be committed. 

The file was committed using the git command `git commit -m` with a descriptive message as 'Add new features or fix bugs'


![git branch](<img/12. git branch.png>)

![git checkout](<img/13. git checkout development.png>)


![git commit -m](<img/14. git stage and commit.png>)


Committed files were pushed to the git remote repository, using the git command `git push`, to effectively manage the project  and enhance security, git asks for username and password authentication, User name is imputted and password is personal access token on Github website.

![git push ](<img/15. git push origin development.png>)


![alt text](<img/16. git username and password.png>)


After files were pushed to remote git repository, the next step is to merge changes to the master branch,

 a pull request was created, oncce the change on the branch 'Add new features or fix bugs' was satisfieed,  it was then merged to the master branch.

Before merging changes, it is essential that we are currently on the master branch ensuring that any change that is being merged in on the master branch, the command `git checkout master` enables us to stay on the master branch.

`git merge developemt` merges development branch to the current master branch 


 ![git merge](<img/17. git merge development to master branch.png>)

 Merged changes -containing the new updated feature - is now pushed to remote github repository. 

 The above workflow demonstrates Git's capability to facilitate continuous integration of new updates


 ## Deploying Updates to the Production Server

 ![git pull](<img/19. git pull origin master.png>)

To Deploy, git pull is used to pull updated changes 'if any' from the remote repository

We restarted the webserver to apply any changes that the remote repository may have possessed.

 ![sudo systemctl reload httpd](<img/20. sudo systemctl reload.png>)
=======

>>>>>>> 450d0a4d3157b9b9f3740903d6af69a95b9e7154
