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


<!--
* [Dropwizard](http://www.dropwizard.io/1.0.2/docs/) - The web framework used
* [Maven](https://maven.apache.org/) - Dependency Management
* [ROME](https://rometools.github.io/rome/) - Used to generate RSS Feeds

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags). 
-->
