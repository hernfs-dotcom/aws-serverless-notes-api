# aws-serverless-notes-api
Serverless notes API built with AWS Lambda, API Gateway, and DynamoDB
## DynamoDB Table Setup

I created a DynamoDB table to store notes for the application.

The table uses a primary key named `id`, which allows each note to be uniquely identified and retrieved.

The screenshot below shows the DynamoDB table after creation.

![DynamoDB Table](dynamodb-table.png)
## Creating the Lambda Function

After creating the DynamoDB table, I moved to AWS Lambda to build the backend logic for the Notes API. I created a Lambda function named `createNote` to handle incoming requests and store note data in DynamoDB.

At this stage, I was testing the connection between Lambda and DynamoDB to ensure the function could successfully write data to the table.

The screenshot below shows an initial test failure. This was an important troubleshooting step, as it helped me identify that the function was not correctly connected to the DynamoDB table.

The issue was caused by referencing the wrong table name in the Lambda code. After correcting the table name and redeploying the function, the test succeeded and the function was able to store data properly.

![Lambda Initial Test Failure](failed-function.png)
