# Management Services

## CloudFormation
Allows you to use a text file to define your infrastructure and deploy resources on the AWS cloud (infrastructure as code, which then allows for version control). 

## AWS Service Catalog
Allows enterprises to catalog resources that can be deployed on the AWS cloud (to comply common governance and compliance for its IT resources by clearly defining what is allowed to be deployed on the cloud). 

## AWS CloudWatch
A monitoring service for the deployed cloud resources and applications. Provides insights for deployed resources and can trigger scaling operations. 

## AWS Systems Manager
Provides a unified UI for you to view operational data from multiple AWS services/resources and automate tasks across them. Makes detecting and resolving operational problems easier. 

## AWS CloudTrail
Monitors and logs account activity, including actions happened via AWS management console, the AWS software development kits, the command line tools, and other AWS services. Simplifies security and analysis of users of the account. 

## AWS Config
Let you assess, audit and evaluate the configs of your resources. Simplifies compliance auditing, security analysis, change management and control, operational troubleshooting. 

## AWS OpsWorks
Provides managed instances of chef and puppet, which can be used to configure and automate the deployment of resources. 

## AWS Trusted Advisor
Online expert system that can analyze your account and its resources, and advise you on how to best achieve high security and best performance from them. 

## Example
CloudTrail provides monitoring and logging of all the API calls made not only from the outside of the account, but also inside. This is important because attacks coming from within your account will be be picked up on your external firewalls. E.g., if you have a malicious employee doing damage to your infrastructure, CloudTrail could monitor and pick this up before it becomes a major problem, and can also initiate automatic corrective action, such as restricting the user's access. 

## Using Cloudtrail to monitor activities
Search for CloudTrail in the console -> Create a trail -> Trail name: trail-events -> Create trail. It also creates a S3 buckets that contains log events. 

Go to S3 in the console, so you can see a list of buckets, one of them is created from this trail. To create some events for the trail to log, create a another bucket and then delete it: Create bucket -> Bucket name: temp-bucket -> Create bucket, then delete this bucket. 

Open the trail bucket, and see a folder named AWSLogs, navigate to the most nested folder, and see some json.jz files. Select a file, and click Download. Unzip the file, and put the content into a JSON editor for better readability. We can then see in the tree view of who did what and when. 

To delete, first delete the trail, then empty the S3 bucket created by it, the delete the bucket. 



































