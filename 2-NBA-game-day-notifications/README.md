Building an NBA Game Notification System with AWS: A Step-by-Step Guide

Introduction

Are you an NBA fan who never wants to miss a game update? Imagine receiving timely notifications about daily games right in your inbox. In this blog, I'll walk you through how I built an NBA Game Notification System using AWS services and NBA APIs. This system allows users to subscribe via email and receive automated game updates. Let's dive in!

Tech Stack & AWS Services Used

To build this system, I leveraged the following tools:

Amazon SNS: Manages email subscriptions and notifications (Pub/Sub model).

AWS Lambda: Runs backend logic to fetch NBA data and send notifications.

Amazon EventBridge: Schedules and triggers Lambda functions.

API Gateway: Exposes our backend service to the web.

NBA APIs (SportsData.io): Fetches real-time NBA game data.

HTML/CSS/JavaScript: Powers the frontend for user subscriptions.

Part 1: Setting Up the Backend

Step 1: Create an SNS Topic

Navigate to AWS SNS and create a new topic (NBA_TODAY).

Add an email subscription and confirm via email.

Users will now appear in the SNS subscription list.

Step 2: Configure IAM Roles & Policies

Create an SNS Publish Policy to allow publishing to the topic.

Assign this policy to an IAM Role for our Lambda function.

Attach the AWSLambdaBasicExecutionRole for Lambda permissions.

Step 3: Build the NBA Notification Lambda

Create an AWS Lambda function in Python.

Fetch NBA game data from SportsData.io.

Format the data and send it to subscribed users via SNS.

Store API keys and SNS Topic ARN as environment variables.

Deploy the function!

Step 4: Automate Notifications with EventBridge

Set up a scheduled rule in EventBridge.

Use a CRON expression to trigger the Lambda function every two hours.

✅ Now, subscribers will receive automatic NBA updates in their inbox!

Part 2: Subscribing Users via API & Frontend

Step 5: Create a Subscription Lambda Function

This function will subscribe users to SNS when they enter their email.

Store SNS Topic ARN as an environment variable.

Deploy and test using sample JSON:

{ "endpoint": "test@example.com" }

Users will receive a confirmation email upon subscribing.

Step 6: Expose APIs via API Gateway

Create a REST API in API Gateway.

Add a POST method linked to the subscription Lambda.

Enable CORS for frontend communication.

Deploy the API and obtain the Invoke URL.

Step 7: Build a Web Interface

Create a simple HTML form where users enter their email.

Use JavaScript to make a POST request to the API Gateway.

Run the frontend on a local server:

python3 -m http.server 8080

Users can now subscribe and receive confirmation emails instantly!

✅ The system is now fully functional, sending real-time NBA updates to subscribers.

Security Best Practices

Security is a top priority when handling user data. Here’s how I ensured a secure setup:

Environment Variables: Store API keys and SNS ARNs securely.

IAM Least Privilege: Grant only necessary permissions to Lambda.

SNS Access Control: Restrict topic access to authenticated users.

API Gateway Security: Implement rate limiting & throttling.

CORS Restrictions: Allow trusted domains only in production.

Input Validation: Verify email inputs before processing.

Monitoring & Auditing: Enable CloudWatch Logs and AWS CloudTrail.

Conclusion

Building this NBA Game Notification System was an exciting experience! With AWS services like SNS, Lambda, API Gateway, and EventBridge, automating real-time updates becomes seamless.

💡 Have an idea for a similar project? Give it a try and let me know your thoughts! 🚀

🔗 Feel free to connect with me on LinkedIn and share your feedback!

