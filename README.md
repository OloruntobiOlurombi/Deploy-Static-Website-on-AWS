# Project: Deploy-Static-Website-on-AWS

The cloud is perfect for hosting static websites that only include HTML, CSS, and JavaScript files that require no server-side processing. The whole project has two major intentions to implement:  
> 1. Hosting a static website on AWS S3 service.
> 2. Accessing the cached website pages using AWS CloudFront content delivery network (CDN) service. Recall that CloudFront offers low latency and high transfer speeds during website rendering.

### Prerequisites:
> AWS Account

> [Student-ready starter code](https://drive.google.com/open?id=15vQ7-utH7wBJzdAX3eDmO9ls35J5_sEQ) - Download and unzip this file.

### Tasks

- In this project, you will deploy a static website to AWS by performing the following steps:

> You will create a public S3 bucket and upload the website files to your bucket.
> You will configure the bucket for website hosting and secure it using IAM policies.
> You will speed up content delivery using AWS’s content distribution network service, CloudFront.
> You will access your website in a browser using the unique CloudFront endpoint.

### STEPS
> Follow the exercise instructions described below:

#### STEP 1: Create S3 Bucket

> 1. Navigate to the “AWS Management Console” page, type “S3” in the “Find Services” box and then select “S3”.

![image](https://user-images.githubusercontent.com/40290711/170674902-2e8d18cf-562e-4525-b2b8-16ed957dd5e0.png)

> 2. The Amazon S3 dashboard displays. Click “Create bucket”.

![image](https://user-images.githubusercontent.com/40290711/170675491-1446bf29-2481-432b-9f9c-faa0f7f4f09d.png)

> 3. In the General configuration, enter a “Bucket name” and a region of your choice. Note: Bucket names must be globally unique.

![image](https://user-images.githubusercontent.com/40290711/170682076-9a259ff6-1b61-4d52-95ac-167a405a1de8.png)

> 4. In the Bucket settings for Block Public Access section, uncheck the “Block all public access”. It will enable the public access to the bucket objects via the S3 object URL.

![image](https://user-images.githubusercontent.com/40290711/170684235-0b5f819e-33f0-476d-a374-27c1d634f9c8.png)

> **Allow the public access to the bucket contents**

> 5. Click on “Create bucket”.

![image](https://user-images.githubusercontent.com/40290711/170684572-a17e1806-0bec-437f-98ab-dcb12c8f7de3.png)

> 6. Confirmed that the bucket is created. 

![image](https://user-images.githubusercontent.com/40290711/170684785-e72845c6-3363-494c-8351-41cb369d0be4.png)

> 7. Click on the name of the bucket to open the bucket to the contents.

![image](https://user-images.githubusercontent.com/40290711/170685090-8dabbb1a-d368-438d-817f-b32024bfe7c9.png)





