# Protected-Website-using-S3-Lambda-CloudFront
![0](https://github.com/panwar100/Protected-Website-using-S3-Lambda-CloudFront/assets/134361823/a6aa9ac8-9a18-4ab3-b0c1-32cc4cf36445)
### Step 1: Create an S3 Bucket for Your Website (Private)
* Log in to the AWS Management Console.
* Go to the Amazon S3 service.
* Click on the “Create bucket” button.
* Choose a unique and meaningful name for your bucket, e.g., “password-protected-website-1”
* Select a region US East (N. Virginia) us-east-1
* leave all of the default settings as-is  
![1](https://github.com/panwar100/Protected-Website-using-S3-Lambda-CloudFront/assets/134361823/34095a03-da87-4b37-9e1d-bd7cf26dcc29)
*Upload all the static website files (HTML, CSS, JS, images, etc.) to the bucket.

### Step 2: Create a Lambda@Edge Function for Authentication
* Go to the AWS Lambda service. 
* Click “Create function.”
* Select the option “Use a blueprint.”
Locate and choose the blueprint titled “Blueprint for generating a response from viewer-request trigger implemented in NodeJS.” Then, provide a function name of your choice.
![2](https://github.com/panwar100/Protected-Website-using-S3-Lambda-CloudFront/assets/134361823/e81c7f3d-82d5-4dd4-8c8e-6a12e1f6e067)
* Name the role as per your preference. Next, choose the “Basic Lambda@Edge permissions (for CloudFront trigger)” from the Policy Templates, and finally, click “Create function” following these steps.
 ![3](https://github.com/panwar100/Protected-Website-using-S3-Lambda-CloudFront/assets/134361823/cf2ee07c-4664-437e-b804-05fb353d12a2)
* After creating your Lambda function, follow these steps:
`1.Copy the provided code in file index.js
2.Open the “index.js” file in the Function Code section.
3.Replace the values of the authUser and authPass variables with the desired username and password.
4.Save your changes by clicking the “Save” button.`
  ![4](https://github.com/panwar100/Protected-Website-using-S3-Lambda-CloudFront/assets/134361823/c36d40c0-0292-4f87-b5b0-a56e6a5b555d)
* Proceed by clicking on “Test,” then configure the Test Event, naming it “TestEvent,” and finally, save the configuration.
 ![5](https://github.com/panwar100/Protected-Website-using-S3-Lambda-CloudFront/assets/134361823/8c5713ae-a626-45f6-baa4-ae180c67f07b)
* Now, click on “Deploy” to publish the latest code, ensuring it is not using the default code.
  ![6 1](https://github.com/panwar100/Protected-Website-using-S3-Lambda-CloudFront/assets/134361823/3efaeb09-3c0a-4f4d-b017-a0935b994d01)
* Subsequently, go to “Actions” and select “Publish New Version.”
  ![7](https://github.com/panwar100/Protected-Website-using-S3-Lambda-CloudFront/assets/134361823/6c1f1ca4-1238-42ed-bc74-69c8a707dbb7)
* Enter “$LATEST,” and a new version will be generated.
  ![8](https://github.com/panwar100/Protected-Website-using-S3-Lambda-CloudFront/assets/134361823/04d110c3-3f7b-4bb6-83a9-bda29b35e482)
* Please select and copy the Function ARN, specifically for Version 1, as you will need to paste it into the CloudFront Distribution for Function associations.

### Step 3: Create a CloudFront Distribution
* Go to the AWS CloudFront service.
* Click “Create Distribution.”
* Configure your distribution settings:
`For “Origin Domain Name,” select the S3 bucket you created earlier.`
![9](https://github.com/panwar100/Protected-Website-using-S3-Lambda-CloudFront/assets/134361823/d79fbbc8-61d7-4f59-b568-9b41b97d70e9)
* You can leave the Origin Path as optional. Enter the name of the origin. Select “Legacy access identities,” then create a new Origin Access Identity (OAI). Next, choose the second option in the bucket policy, which is “Yes, update the bucket policy.
![10](https://github.com/panwar100/Protected-Website-using-S3-Lambda-CloudFront/assets/134361823/35f70642-c959-4fe4-98d3-bf68b2e7fd02)
![11](https://github.com/panwar100/Protected-Website-using-S3-Lambda-CloudFront/assets/134361823/bad9351b-cbd2-46a6-9235-0c4717867187)
* In the Lambda Function Associations section, opt for “Viewer Request” and specify the Function ARN/Name of the Lambda@Edge function you established for authentication, utilizing the Version 1 Function ARN mentioned previously during the Lambda Function creation.
![12](https://github.com/panwar100/Protected-Website-using-S3-Lambda-CloudFront/assets/134361823/f6c32e1a-c30d-4a3e-8afd-629f33b565f1)
* Specify “index.html” as the Default Root object and provide a description as required.
* leave all of the default settings as-is.
* Click on “Create Distribution” to create the distribution. Then, go to the Lambda Service Page and confirm that Cloudfront is associated with the Lambda Function as illustrated in the image below.
*  After ensuring the distribution and Lambda Function is correctly configured and deployed, make a note of the CloudFront domain name provided in the distribution’s details.
 ![13](https://github.com/panwar100/Protected-Website-using-S3-Lambda-CloudFront/assets/134361823/93d03c0e-e9ed-4a0f-868a-f3bee473b5d3)

### Step 4: Testing and Deployment
* Access your password-protected website using the CloudFront domain name, e.g., https://d10lg18frwsf4.cloudfront.net/
* You should be prompted for basic authentication credentials. Enter the username and password configured in the Lambda@Edge function.
* Test the website thoroughly to ensure the password protection is working as expected.
![14](https://github.com/panwar100/Protected-Website-using-S3-Lambda-CloudFront/assets/134361823/63f18fec-9ac1-48c4-bb52-127af8485a17)
![15](https://github.com/panwar100/Protected-Website-using-S3-Lambda-CloudFront/assets/134361823/66a59b38-6847-48b2-b150-93e93a64513e)
<p align="center">
  <img src="https://github.com/panwar100/Protected-Website-using-S3-Lambda-CloudFront/assets/134361823/7de51f34-20c9-4250-a664-e9ee965a61ee" alt="Congratulations" />
</p>
Congratulations, you have successfully accomplished and completed this task!





  



  
