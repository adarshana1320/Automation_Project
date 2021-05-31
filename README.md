# Automation_Project
This Repo hosts 2 scripts Automation-v0.1 and Automation-v0.2.

Below is the description of the Project.

Motive: 
The main motive of this project is to upload the apache access and error logs to the S3 bucket and provide a detailed bookkeeping of the compressed logs being uploaded to S3 with the files' names, time, type and size through a webpage.

Description:
Step-1) In this Project I have created an Ubuntu EC2 instance with version 18.04 with a security group attached to it having the inbound rules open for port 80,443 and 22.
I also created an S3 bucket and attached an IAM Role giving S3FullAccess to the EC2 instance.

Step-2) Creation of the script Automation-v0.1 which performs the below steps-
1.Perform an update of the package details and the package list at the start of the script.
2.Install the apache2 package if it is not already installed.
3.Ensure that the apache2 service is running. 
4.Ensure that the apache2 service is enabled.
5.Create a tar archive of apache2 access logs and error logs that are present in the /var/log/apache2/ directory and place the tar into the /tmp/ directory. The name of tar archive should have following format:  <your _name>-httpd-logs-<timestamp>.tar.
6.Install AWS CLI manually.
7.The script runs the AWS CLI command and copy the archive to the s3 bucket. 
  
Step-3) Creation ofthe script Automation-v0.2 with updates which does bookkeeping of the compressed logs being uploaded to S3 with the files' names, time, type and size through a webpage and automates the execution of the script using cron job so that the script doesn't have to be run manually.
1.The script checks for the presence of the inventory.html file in /var/www/html/; if not found, creates it. This file will essentially serve as a web page to get the metadata of the archived logs.When your script runs, it should create a new entry in the inventory.html file about the following: 
What log type is archived?
Date when the logs were archived 
The type of archive
The size of the archive
2.Your script should create a cron job file in /etc/cron.d/ with the name 'automation' that runs the script /root/<git repository name>/automation.sh every day via the root user.
