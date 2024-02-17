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

# 1.Creating the AWS SAM Template: create dynamo table with SAM 

The AWS SAM template is the heart of our serverless application deployment. It defines the resources and configurations required for our application. 

![image](https://github.com/felixdagnon/Deploying-Serverless-Application-with-AWS-SAM-/assets/91665833/4b96c0d7-2317-4c87-8bc8-83827fbcc987)

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

Let's run this package:

$ sam package --template-file dynamo-sam.yml --s3-bucket demo-test-101 --output-template-file packaged-dynamo.yml

The pacckage is downloaded in SAM repo of Cloud9

This packaged-dynamo.yml is the same as dynamo-sam.yml

dynamo-sam.ym

![image](https://github.com/felixdagnon/Deploying-Serverless-Application-with-AWS-SAM-/assets/91665833/07bb7fca-8254-4078-a9b4-d0ae619a5766)

packaged-dynamo.yml

![image](https://github.com/felixdagnon/Deploying-Serverless-Application-with-AWS-SAM-/assets/91665833/ba01af36-e1e3-40b2-b393-484eaf21e5c2)

# Deploying package

To deploy the package rune the below command

$ sam deploy --template-file packaged-dynamo.yml --stack-name dynamosamcreate

The package is running and changeset created in cloudformation

![image](https://github.com/felixdagnon/Deploying-Serverless-Application-with-AWS-SAM-/assets/91665833/dbd84155-7da4-405e-948b-f8e9e28db067)

Let's see Cloudformation

![image](https://github.com/felixdagnon/Deploying-Serverless-Application-with-AWS-SAM-/assets/91665833/4a86aec3-c128-4110-beff-0fbd07907913)

Let's check in dynamo console

![image](https://github.com/felixdagnon/Deploying-Serverless-Application-with-AWS-SAM-/assets/91665833/5093a8f4-280b-4b96-af06-5107c479c937)


![image](https://github.com/felixdagnon/Deploying-Serverless-Application-with-AWS-SAM-/assets/91665833/f7a4c56a-1940-4d0a-bc23-ccf686d9980a)


# 1.Deploying basic lambda without any dependencies with SAM 

Let's create simple lambda function (hello_country)

```json
import json 
import datetime
def lambda_handler(event, context):
    # TODO implement 
    print(event)
    data = {
       'output': 'Hello from '+ event['Country'],
        'timestamp': datetime.datetime.utcnow().isoformat()
    }
    return {'statusCode': 200,
            'body': json.dumps(data),
            'headers': {'Content-Type': 'application/json'}}
```

Test event (test1)

```json
{
  "Country": "USA"
}
```

and lambda SAM (lambda-sam.yml)





















 

 


