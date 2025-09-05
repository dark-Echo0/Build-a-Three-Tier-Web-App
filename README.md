<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Three-Tier Web App

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-compute-threetier)

**Author:** Rico  
**Email:** ojoararico.me@gmail.com

---

## Build a Three-Tier Web App

![Image](http://learn.nextwork.org/sympathetic_silver_noble_jaguar/uploads/aws-compute-threetier_2b3c4d5e)

---

## Introducing Today's Project!

In this project, I demonstrated the process building a scalable web application using AWS services such as S3, CloudFront, Lambda, API Gateway, and DynamoDB. I'm doing this project to learn the concept and gain hands-on experience about three-tier architecture comprising the presentation, logic, and data tiers which is fundamental to designing efficient and maintainable software systems.

### Tools and concepts

Services I used are S3 bucket, Cloudfront, Lambda, API Gateway, and DynamoDB. Key concepts I learned includes storing website files in S3 bucket, deliver my content globally using CloudFront, write serverless code with Lambda, create and manage APIs with API Gateway, store and retrieve data with DynamoDB and connect all these services together to build a fully functional three-tier web application.

### Project reflection

This project took me approximately five hours of troubleshooting. The most challenging part was resolving an error in step 5, which occurred after I edited my script file to specify the Invoke URL and uploaded it to the S3 bucket. The most rewarding aspect was seeing my output match the expected results based on the instructions, confirming that I correctly configured the resources across the presentation, logic, and data tiers.

I did this project to gain a comprehensive understanding of building a three-tier web application, encompassing the presentation, logic, and data tiers. Yes, this project meet my goal because the knowledge  I gained is crucial for a DevOps Engineer, whose key responsibilities include optimizing website performance and ensuring scalable, efficient content delivery.

---

## Presentation tier

For the presentation tier, I configured my website files by storing it in the s3 bucket and cloudfront for faster content delivery because presentation tier is responsible for displaying the website to the users.

I accessed my delivered website by adding a policy on my S3 bucket a read access to cloudfront origin access control.

![Image](http://learn.nextwork.org/sympathetic_silver_noble_jaguar/uploads/aws-compute-threetier_3a4b5c6d)

---

## Logic tier

For the logic tier, I configured AWS Lambda functions in combination with API Gateway. Lambda should serve as the "brain" of the application, handling business logic and facilitating communication between the presentation tier and the data tier. API Gateway should receive user requests, route them to the appropriate Lambda functions, and return the responses, enabling dynamic interactions within the application.

The Lambda function retrieves data by AWS SDK service, which allows it to interact directly with the DynamoDB table. Through this integration, the Lambda function can query the database and return the requested data to the user via API Gateway, enabling real-time, serverless data retrieval.



![Image](http://learn.nextwork.org/sympathetic_silver_noble_jaguar/uploads/aws-compute-threetier_6a7b8c9d)

---

## Data tier

For the data tier, I configured a user data storage using Amazon DynamoDB because it is a fully managed NoSQL database that offers high scalability, low-latency performance, and seamless integration with other AWS services.

The partition key for my DynamoDB table is a required attribute that use to group similar items which means the partition where
 the data will be stored

![Image](http://learn.nextwork.org/sympathetic_silver_noble_jaguar/uploads/aws-compute-threetier_u1v2w3x4)

---

## Logic and Data tier

Once all three layers of the three-tier architecture are set up, the next step is to integrate them to ensure seamless communication between the presentation, logic, and data tiers. This integration completes the architecture, allowing user interactions from the front-end to be processed by the logic tier and fulfilled with data from the back-end.

To test my API, I copied the invocation URL provided by API Gateway and appended the query string '/users?userId=1' to the end of the URL. This simulated a request for a specific user’s data. The results were, the API successfully returned the expected data from DynamoDB, confirming that the integration between API Gateway, Lambda, and DynamoDB is working correctly.

![Image](http://learn.nextwork.org/sympathetic_silver_noble_jaguar/uploads/aws-compute-threetier_a112c3d5)

---

## Console Errors

The error in my distributed site occurred because I did not specify the API URL in my JavaScript code, which resulted in the error message: 'Failed to fetch user data'.

To resolve the error, I updated script.js by adding my API URL and reuploaded it to S3, because the initial code in script.js did not specify the API URL, which caused an error on my distributed site.

I ran into a second error after updating script.js. This error was related to Cross-Origin Resource Sharing (CORS) because my API Gateway only allows requests made directly to the invoke URL, not requests coming from my CloudFront URL.

![Image](http://learn.nextwork.org/sympathetic_silver_noble_jaguar/uploads/aws-compute-threetier_a1b2c3d5)

---

## Resolving CORS Errors

To resolve the CORS error, I first went into my API in API Gateway and enabled CORS on the /users resource. I, then made sure Get requests are enabled, and referenced my cloudfront domain getting access.

I also updated my Lambda function code to include the 'Access-Control-Allow-Origin' header in the response. This change ensures that the function can be invoked by the API's URL and return a response to the user.

![Image](http://learn.nextwork.org/sympathetic_silver_noble_jaguar/uploads/aws-compute-threetier_1qthryj2)

---

## Fixed Solution

I verified the fixed connection between API Gateway and CloudFront by refreshing my CloudFront domain name and saw the data fetched from DynamoDB displayed on the website.

![Image](http://learn.nextwork.org/sympathetic_silver_noble_jaguar/uploads/aws-compute-threetier_2b3c4d5e)

---

---
