# AWS - Infrastructure as Code

## Objective:
Set up a highly available Wordpress website following “infrastructure as code” practices.

## Instructions:
1. Create a new AWS account or use an existing one (free tier for all but the Elastic IP).
2. Utilize AWS CLI\SDK’s to provision and deploy the infrastructure described below.
  Including: CloudFormation, IAM, VPC, EC2, ELB, RDS, Elastic IP
3. All of your configuration, scripts should be stored and utilized from a single source code repository. Add execution details in your repo on how to use your code.

## Specifics:
- Region: Oregon (us-west-2)
- EC2 Instances: Amazon Linux AMI, t2.micro

## Deliverables:
Once the objectives outlined above have been met, please send email with the following
information: Github repository, IP address to your ELB (Wordpress front door).

## Solution:
Deliverable:

[Link To Running Solution](http://wordpressha-884419035.us-west-2.elb.amazonaws.com/)

[Link To Running Solution Admin](http://wordpressha-884419035.us-west-2.elb.amazonaws.com/wp-login.php)

User and Pass sent in email.

## To Reproduce:
1. Download the file wordpress-ha.json to your computer
2. Run the following command on the commandline replacing appropriate placeholder values.
  (Placeholder values are surrouded by [ ]. Replace the value and the brackets)
  (requries awscli tools configured to aws account with proper permissions)
  
        aws --region us-west-2 cloudformation create-stack --stack-name [NameYourStack] --template-body file://[path/to/file/location/wordpress-ha.json] --capabilities CAPABILITY_NAMED_IAM --parameters ParameterKey=BlogAdminPassword,ParameterValue=[PasswordForWPAdmin] ParameterKey=WebServerKeyName,ParameterValue=[YourKeyName]

By default the script sends an email to shawn@progotta.com with the WordPress details when complete.  This can be over-ridden by adding this string to the parameters option:

        ParameterKey=BlogAdminEMail,ParameterValue=[your@email.com]

There are other parameters in the template, such as BlogTitle, that can be changed in the same way. 


When the Stack has succesfully started initalization, a StackId is returned.  It will look similar to this:

        {
          "StackId": "arn:aws:cloudformation:us-west-2:123456789012:stack/WordPress-HA1/58ad9f90-24df-11e7-ae72-503f2a2cee1e"
        }

To check the status of the the stack creation from the command line:

        aws cloudformation describe-stacks --stack-name [StackName]

You can also check the status of the stack creation through the AWS Web Console -> CloudFormation 


### Problems with the excercise or my understanding of what the excercise is looking for: 
  The exercise states that Elastic IP should be use in the solution.
  
  -and-
  
  The exercise asks for the the IP address of the Elastic Load Balancer to test from.


  Elastic Load Balancer does not support Elastic IP, nor a single ip address. Ip addresses are assigned to the ELB behind the scenes and could change over time.  So, an IP Address cannot be provided for testing, but the appropriate URL can be.
  
  Elastic IP address(es) could be attached to the running instances, so if this was the intent, it is not complete.  Please let me know if that is where the Elastic IP was intended to be placed, and I can modify. 


