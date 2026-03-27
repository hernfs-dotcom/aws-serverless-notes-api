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

After fixing the initial error, I updated the Lambda function so it could correctly connect to my DynamoDB table and handle incoming data from the API.

The function is written in Python and uses the `boto3` library to communicate with DynamoDB. When a request is sent to the API, the function reads the data from the request body, extracts the note title and content, and generates a unique ID using the `uuid` module.

It then creates a new item with this data and stores it in the DynamoDB table.

This step was important because it built the core backend logic of the application. It allows the system to accept user input and store it reliably in the database, making the API fully functional.

The screenshot below shows the Lambda function code after the issue was resolved.

![Lambda Function Code](lambda-function-resolved.png)
