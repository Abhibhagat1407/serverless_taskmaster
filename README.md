# Serverless Task Master Three Tiear Application
## This project follows the Event-Driven architecture


### What is serverless?
Serverless means a cloud-native development model that allows developers to build and run applications without having to manage servers. servers are only created when someone hits the URL or API Gateway makes a request.

### What is a Serverless Framework?
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

##### Why nodeJs Installation is required?
Because Serverless Framework requires the node to run so it is the prerequisite. 
  
 [NodeJs Installation Guid](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-20-04)
  Check the installation with `node -v` for nodejs and `npm -v` for npm.
- Also install awscli `sudo apt install awscli` to get the AWS console access.

  
- Then Go to the serverless documentation and pick the first command from the setup `sudo npm install -g serverless `to set and configure your ec2 instance with the serverless framework.
- After entering the above command it will show some options to choose like what kind of project do want to work with. choose the appropriate option as per your need. (To choose the required option use arrow keys for navigation.)
> In my case I have choose ` NodeJs HTTP API request ` because I just want to check the API.

- After hitting enter it will ask you to give a particular name to your project. give any name you want.
- It will Download HTTP API template code for you to work with it.
- Then it will ask for AWS credentials to get access of your aws-console
> No need to select the console access. but create the access keys.

- Then give the access key ID and access key in the console. and you will be done with the configuration
- Then it will ask you `Do you want to deploy now?` to which press `Y` and `enter`. after this will see the message something like " Deploying my-second-serverless-proj to stage dev (us-east-1, "default" provider) " Which shows that it started the deployment of the project.
- Then you can see the deployment result in AWS serverless Framework
  
![alt text](file:///home/abhishek/Pictures/Screenshots/Screenshot%20from%202023-12-15%2015-16-38.png)

- If you want to see what and how manay components and resources serverless projet is using to deploy this application or test the HTTP API.
- Go to ` CloudFormation>stacks>resources ` and if you want to see the architecture or Flow diagram
- Go to: ` CloudFormation>stacks>update>Edit template in designer>View in Designer `

Now we can see that our code has been packaged using S3. Go to the S3 bucket section to see it visually. and in the above decription you can see that your infrastructure has been set up by cloudformation automation. 


##### How does serverless automate all the deployment processes?
It automates the deployment process by using the IAC( infrastructure as code ), Which is AWS CloudFormation, But as we are using the serverless framework we do not need to directly interact with the cloud formation. We can do all the automation by using the `serverless.yml` file.

In the ` index.js ` file, all the code of our project is present we make any changes if we want like we can change the display message. This file is known as a handler.
  

- Using `serverless deploy` command we can deploy our project or using this command we can update the pre-existing stack or code.
- After successful execution of the ` serverless deploy ` we will get the endpoint, copy that endpoint, and open it on the web browser you will see the output of your code.

![alt text](file:///home/abhishek/Pictures/Screenshots/Screenshot%20from%202023-12-15%2018-50-18.png)

#### How is security managed in the serverless framework? 
API Gateway is connected to the Lamda function  and in the API Gateway there is authentication and authorization. Also, we can manually set up or attach the authorizer. That is why it has strong security inbuilt.


### Let's get started with the actual Three tier taskmaster application
In this project, we will deploy the three-tier taskmaster application using the AWS serverless framework, The actual demonstration of the project starts from here on.
The above project that we have discussed was the testing project of the HTTP API which serverless provides inbuild


#### step-by-step guide

- Clone the GitHub repo of the project from here: [https://github.com/Abhibhagat1407/serverless-taskmaster-aws-app.git]
  for deploying applications using serverless it requires creating serveless. yml file for deployment configuration
- Create a serverless.yml file in the above-provided repo you will get the serverless file you can use for the reference and modify it accordingly.
- Before the deployment starts you need to set the org like this ( `serverless --org=<username-of-serverless-famework>`)
 * It will ask for to choose the option for the deployment. Choose according to your requirements. You will get an output something like this:

[output](![Screenshot from 2023-12-16 13-46-44](https://github.com/Abhibhagat1407/serverless_taskmaster/assets/109520000/6069803e-9741-488e-bcc5-d6aa3aea8e62)
)

 * after choosing the particular option it will start the deployment. it will be reflected on the serverless apps dashboard

 [output](file:///home/abhishek/Pictures/Screenshots/Screenshot%20from%202023-12-16%2014-10-36.png)

 * Now you can check your CloudFormation stack to see the created resources after applying the serverless.yml file. here is the DynamoDB table created using the above configuration of the serverless.yml
   ![results](file:///home/abhishek/Pictures/Screenshots/Screenshot%20from%202023-12-16%2014-21-32.png)

- Up until now we have just created the table required for the project, in the next demonstration I will be creating the lambda functions. The Lambda function will be created for the Hello service.
- Then I wrote the lambda function to add a new service to it. in the previous example, we just had a dynamodb as a resource, now this Dynamodb table will get attached to the functions automatically.
- That lambda function contains the service to display the hello message. To see that message copy the endpoint serverless gave you on the terminal and open it on the browser to see the message.
  ![endpoint](file:///home/abhishek/Pictures/Screenshots/Screenshot%20from%202023-12-16%2014-56-39.png)
  
- After pasting this endpoint will see the Hello message.
  ![message](file:///home/abhishek/Pictures/Screenshots/Screenshot%20from%202023-12-16%2015-01-00.png)

- Several resources have been created after creating the lambda function.
   * S3 is created for code packaging and marinating and creating the new versions as we update our cloud formation stack it creates the new versions of the packaging
   * Also S3 is maintaining the state file.
   * It automatically creates cloud watch log groups for logging.
     ![cloudwatch logs](file:///home/abhishek/Pictures/Screenshots/Screenshot%20from%202023-12-16%2015-19-59.png)

- Added more Three services like kaamkaro, Kaambharo, and Kaamdikhao these will be created as separate objects and every object uses each lambda for each service or object. That means we will be required to type Lamda functions for each service.
- After deploying all of these services you will see the endpoint for each service on the terminal like this:
  ![Screenshot from 2023-12-17 08-55-08](https://github.com/Abhibhagat1407/serverless_taskmaster/assets/109520000/b14c4295-551b-42f8-ba12-215e250cba7b)




### API Testing With Postman
Postman is a tool or software that provides a user-friendly UI for testing API easily.

##### Stetps of testing 
* To get started first click on the + sign to create a new collection click on add request and enter the URL that we wanted to test.
* 

  
  

 





