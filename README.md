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
## Lambda Function Code Implementation

After identifying and fixing the initial error, I updated the Lambda function to correctly reference the DynamoDB table and handle incoming request data.

The function uses Python along with the `boto3` library to interact with DynamoDB. It parses the incoming JSON request, generates a unique ID for each note using the `uuid` module, and stores the note in the DynamoDB table.

This step was important because it established the core backend logic of the application, allowing the API to dynamically create and store new notes.

The screenshot below shows the Lambda function code after the issue was resolved.

![Lambda Function Code](lambda-function-resolved.png)
