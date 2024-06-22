# Project: Phonebook Application (Python Flask) deployed on AWS Application Load Balancer with Auto Scaling and Relational Database Service using Terraform

## Description

The Phonebook Application project aims to create a scalable phonebook application using Python Flask, deployed on AWS using an Application Load Balancer and an Auto Scaling Group of EC2 instances, with a MySQL database hosted on RDS. The deployment process is managed with Terraform to ensure a robust and automated infrastructure setup.

## Problem Statement

- Your company has initiated a project to develop a Phonebook web application. The initial UI and backend code have been developed by your team, and you are responsible for deploying the application in a development environment.

  The application should allow users to:

  - Search for contacts
  - Add new contacts
  - Update existing contacts
  - Delete contacts

  The phonebook records are stored in a MySQL database hosted on AWS RDS. The data format is as follows:

  - id: unique identifier for the phone record, type is numeric.

  - person: full name of person for the phone record, type is string.

  - number: phone number of the person. type is numeric.

### Input Validation

- All user interactions should be case-insensitive, and names should be formatted with the first letter of each word capitalized. The application should validate inputs and display appropriate warnings for invalid inputs.

- Example Inputs and Formats:

```text
Input in username field          Format/Warning
--------------                   -----------------
''                               Warning -> 'Invalid input: Name can not be empty'
callahan                         Callahan
joHn doE                         John Doe
62267                            Warning -> 'Invalid input: Name of person should be text'

Input in number field            Format/Warning
--------------                   -----------------
''                               Warning -> 'Invalid input: Phone number can not be empty'
1234567890                       1234567890
546347                           546347
thousand                         Warning -> 'Invalid input: Phone number should be in numeric format'
```

### Deployment

- Transform the application into a web application using Python Flask. The web application should be accessible via a web browser from anywhere. Use the provided HTML templates for the web interface.

  - index.html: For searching phonebook records.

  - add-update.html: For adding or updating records.

  - delete.html: For deleting records.

Deploy the application using Terraform on AWS, which includes setting up an Application Load Balancer, Auto Scaling Group, and RDS. Ensure the infrastructure is secure and follows best practices.

- Lastly, after transforming your code into web application, you are requested to push your program to the project repository on the Github and deploy your solution in the development environment on AWS Cloud using Terraform to showcase your project. In the development environment, you can configure your Terraform file using the followings,

  - The application should be created with new AWS resources.

  - Template should create Application Load Balancer with Auto Scaling Group of Amazon Linux 2 EC2 Instances within default VPC.

  - Application Load Balancer should be placed within a security group which allows HTTP (80) connections from anywhere.

  - EC2 instances should be placed within a different security group which allows HTTP (80) connections only from the security group of Application Load Balancer.

  - The Auto Scaling Group should use a Launch Template in order to launch instances needed and should be configured to;

    - use all Availability Zones.

    - set desired capacity of instances to `2`

    - set minimum size of instances to `1`

    - set maximum size of instances to `3`

    - set health check grace period to `300 seconds`

    - set health check type to `ELB`

  - The Launch Template should be configured to;

    - prepare Python Flask environment on EC2 instance,

    - download the Phonebook Application code from Github repository,

    - deploy the application on Flask Server.

  - EC2 Instances type can be configured as `t2.micro`.

  - Instance launched by Terraform should be tagged `Web Server of Phonebook App`

  - For RDS Database Instance;
  
    - Instance type can be configured as `db.t3.micro`

    - Database engine can be `MySQL` with version of `8.0.19`.

  - Phonebook Application Website URL should be given as output by Terraform, after the resources created.

## Project Skeleton 

```text
Phonebook Web Application (Python Flask) with MySQL on AWS using Terraform (folder)
|
|----readme.md               # Given to the students (Definition of the project)
|----main.tf                 # To be delivered by students (Terraform Configuration) 
|----phonebook-app.py        # Given to the students (Python Flask Web Application)
|----templates
        |----index.html      # Given to the students (HTML template)
        |----add-update.html # Given to the students (HTML template)
        |----delete.html     # Given to the students (HTML template)
```

## Expected Outcome

![Phonebook App Search Page](./search-snapshot.png)

### Topics Covered;

- Algorithm design

- Programming with Python

- Programming with SQL

- Web application programming with Python Flask Framework

- MySQL Database Configuration

- Bash scripting

- AWS EC2 Launch Template Configuration

- AWS EC2 Application Load Balancer Configuration

- AWS EC2 ALB Target Group Configuration

- AWS EC2 ALB Listener Configuration

- AWS EC2 Auto Scaling Group Configuration

- AWS Relational Database Service Configuration

- AWS EC2 Security Groups Configuration

- Terraform Configuration with AWS

- Terraform Configuration with Github

- Git & Github for Version Control System

### Skills Developed;

- Writing Python code for CRUD operations

- Developing web applications with Flask

- Configuring MySQL database connections

- Using SQL within Flask applications

- Scripting with bash for automated setup

- Configuring AWS infrastructure with Terraform

- Using git commands and GitHub for version control

- Deploying web applications on AWS EC2 instances

## Steps to Solution
  
- Clone the project definition from the `F3525-Ice` repo on Github 

- Set up the project folder for a local public repository on your PC.

- Write the Phonebook Application in Python.

- Transform the application into a web application using Flask.

- Prepare Terraform templates to deploy the app with an Application Load Balancer and RDS.

- Initialize Terraform in your project folder.

- Run Terraform commands to deploy the application on AWS.

- Destroy the infrastructure using terraform destroy when done.


## Notes

- Use the jinja templating engine within Flask for HTML templates.

- Validate user inputs and show warnings for invalid entries using provided HTML templates.

- Customize the application by setting your name as the developer_name variable.

- Use AWS CLI commands to get subnet IDs of the default VPCs.

### AWS CLI Command Example:

```bash
aws ec2 describe-subnets --no-paginate --filters "Name=default-for-az,Values=true" | egrep "(VpcId)|(SubnetId)"
```

## Resources

- [Python Flask Framework](https://flask.palletsprojects.com/en/1.1.x/quickstart/)

- [Python Flask Example](https://realpython.com/flask-by-example-part-1-project-setup/)

- [Terraform AWS Provider Documentaion](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)

- [AWS CLI Command Reference](https://docs.aws.amazon.com/cli/latest/index.html)
