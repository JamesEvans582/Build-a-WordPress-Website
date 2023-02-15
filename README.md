# Build-a-WordPress-Website
Deploy and host a production-ready WordPress website on AWS

For this project I will be following an AWS tutorial. 

'In this project, you will learn how to deploy and host WordPress, an open-source blogging tool and content management system (CMS) based on PHP and MySQL. You will implement an architecture to host WordPress for a production workload with minimal management responsibilities required from you. To accomplish this, you will use AWS Elastic Beanstalk and Amazon Relational Database Service (RDS). Once you upload the WordPress files, Elastic Beanstalk automatically handles the deployment, from capacity provisioning, load balancing, auto-scaling to application health monitoring. Amazon RDS provides cost-efficient and resizable capacity, while managing time-consuming database administration tasks for you.'

Firstly let's create an MySQL database using the aws console. We also want enable multi AZ.  
<img width="1792" alt="Screenshot 2023-02-15 at 10 12 30" src="https://user-images.githubusercontent.com/71371405/219024432-967331d2-9674-4b55-b6cc-a8efec42a317.png">

<img width="1792" alt="Screenshot 2023-02-15 at 10 43 37" src="https://user-images.githubusercontent.com/71371405/219027269-07403a03-b854-4e7a-b8e5-764ed0b0db7b.png">


For the Master username and Master password – The database username and password. Make a note of these settings because you will use them later, so the security string connection. 

In the Connectivity section under Security, you can see the security group that's associated with the DB instance. Open the link to view the security group in the Amazon EC2 console.

In the security group details, choose Inbound.

Choose Edit.

Choose Add Rule.

For Type, choose the DB engine that your application uses.

For Source, type sg- to view a list of available security groups. Choose the security group that's associated with the Auto Scaling group that's used with your Elastic Beanstalk environment. This is so that Amazon EC2 instances in the environment can have access to the database.
![image](https://user-images.githubusercontent.com/71371405/219026349-74fec791-8ef8-4674-bf24-b6bf7abec7b5.png)
Then click save 

So now we have an RDS in place. We need have the wordpress files downloaded before Elastic Beanstalk can use them.
Using the Aws console I connected to the powershell and followed these instructions

<img width="1792" alt="Screenshot 2023-02-15 at 12 26 17" src="https://user-images.githubusercontent.com/71371405/219030141-324422d0-2b10-46db-8573-cc44959eeec1.png">

Now another fun bit. Create an Elastic Beanstalk environment using the managed PHP platform. On aws' actua tutorial site they have a preconfigure link if you want. For Application code, choose Sample application, then review and launch  


<img width="1792" alt="Screenshot 2023-02-15 at 11 01 50" src="https://user-images.githubusercontent.com/71371405/219031928-f2396fd7-14fd-4ae6-b570-e399a8979caa.png">
<img width="1792" alt="Screenshot 2023-02-15 at 10 10 52" src="https://user-images.githubusercontent.com/71371405/219032025-bedac6bd-4b43-4d3c-9803-e1f2b15eded5.png">
<img width="1792" alt="Screenshot 2023-02-15 at 10 27 54" src="https://user-images.githubusercontent.com/71371405/219032177-1c213171-5332-4292-af13-2a2703238901.png">

Next we have to configure the security, with this production can like RDS can communicate between them.

<img width="1792" alt="Screenshot 2023-02-15 at 12 53 22" src="https://user-images.githubusercontent.com/71371405/219033744-ac1990a8-75ec-49a1-b85a-04be95aafef5.png">

<img width="1792" alt="Screenshot 2023-02-15 at 10 54 46" src="https://user-images.githubusercontent.com/71371405/219034394-c690e065-f545-410e-9c77-8516eb647079.png">


<img width="1792" alt="Screenshot 2023-02-15 at 12 59 04" src="https://user-images.githubusercontent.com/71371405/219033976-049a1bf8-f078-47ae-8715-c78c4c82a9aa.png">

So right now we have an RDS, wordpress files, Elastic Beanstalk with correct security credentials, now we need to deploy.

In the navigation pane, choose Environments, and then choose the name of your environment from the list.
On the environment overview page, choose Upload and deploy.Use the on-screen dialog box to upload the source bundle.

Choose Deploy.

<img width="1792" alt="Screenshot 2023-02-15 at 11 57 27" src="https://user-images.githubusercontent.com/71371405/219035732-6e26140a-991c-4ea0-b588-6a91b2ee8d47.png">

Finally to complete your WordPress installation. Choose the environment URL to open your site in a browser. You are redirected to a WordPress installation wizard because you haven't configured the site yet.

Perform a standard installation. The wp-config.php file is already present in the source code and configured to read the database connection information from the environment. You shouldn't be prompted to configure the connection.

There's more you can do to:
Remove access restrictions
Configure your Auto Scaling group
Upgrade WordPress

This tutorial can be followed on the AWS site, if you want to follow the same as I did. 
If you have finished don't forgot to clean up your environment!

Happy Clouding! 








