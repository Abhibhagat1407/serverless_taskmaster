# Serverless Task Master Three Tiear Application
## This project follows the Event-Driven architecture


### What is serverless?
Serverless means a cloud-native development model that allows developers to build and run applications without having to manage servers. servers are only created when someone hits the URL or API Gateway makes a request.

### What is Serverless Framework?
The Serverless Framework helps you develop and deploy AWS Lambda functions, along with the AWS infrastructure resources they require.
The Serverless Framework translates all syntax in serverless. yml to a single AWS CloudFormation template. By depending on CloudFormation for deployments, users of the Serverless Framework get the safety and reliability of CloudFormation. An AWS CloudFormation template is created from your serverless.


#### Technologies We are using in this project:
- Lambda Functions
- API Gateway
- S3
- DynamoDB
- CloudFormation
- Serverless Framework

  

### Architecture Diagram
![Blank diagram (3)](https://github.com/Abhibhagat1407/serverless_taskmaster/assets/109520000/54396e88-eee9-412a-8c54-b48ae55cedb8)


### Step-by-step guide for the project 

- Provisioned EC2 micro instance just to clone the project repo.
> Note: Use any instance you want. But don't use paid resources until it's not required.
- We are using a serverless Framework in this project, so first sign up and make an account on Serverless Framework.

 [Click Here To Sign Up On AWS Serverless Framework](https://www.serverless.com/framework/docs/providers/aws/cli-reference/login)
 > In my case i have authorised my serverless framework using Github

- Update your Ec2 instance with `sudo apt update` and install nodeJs also install npm with `sudo apt install npm`
    [NodeJs Installation Guid](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-20-04)
  Check the installation with `node -v` for nodejs and `npm -v` for npm.







