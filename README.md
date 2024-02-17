# Deploying-Serverless-Application-with-AWS-SAM
Deploying  Serverless Application with AWS SAM Serverless Application Model: A Step-by-Step

##  What is SAM

Enabling you to save time and build, test, and deploy serverless applications faster.

![image](https://github.com/felixdagnon/Deploying-Serverless-Application-with-AWS-SAM-/assets/91665833/3bd85a74-8ffa-45cc-a49e-14d82f277884)

# Install SAM with Cloud9

I wiil use Cloud9 terminal and local desktop 

Check SAM version in Cloud9

![image](https://github.com/felixdagnon/Deploying-Serverless-Application-with-AWS-SAM-/assets/91665833/f0f64cae-fc02-4f55-9229-912e92369a0a)

### AWS SAM template Concept

![image](https://github.com/felixdagnon/Deploying-Serverless-Application-with-AWS-SAM-/assets/91665833/eaf75ddf-e533-4396-8099-7728550b1649)

# Creating the AWS SAM Template

The AWS SAM template is the heart of our serverless application deployment. It defines the resources and configurations required for our application. 

## Create dynamo table with SAM 

Here's an example of a simple AWS SAM template: Dynamo Table

```json
AWSTemplateFormatVersion: '2010-09-09'
Transform: 'AWS::Serverless-2016-10-31'
Description: Test Dynamo Table
Resources:
  Dynamosam:
    Type: AWS::Serverless::SimpleTable
    Properties:
      PrimaryKey: 
          Name: id
          Type: String
      ProvisonedThroughput:
        ReadCapacityUnits: 5 
        WriteCapacityUnits: 5 
```

![image](https://github.com/felixdagnon/Deploying-Serverless-Application-with-AWS-SAM-/assets/91665833/8dafde76-732a-4297-aa6c-bf449f7e4683)





 

 


