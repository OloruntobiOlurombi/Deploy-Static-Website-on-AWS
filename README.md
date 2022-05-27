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


#### STEP 2: Upload files to S3 Bucket
> 1. Once the bucket is open to its contents, click the “Upload” button.

![image](https://user-images.githubusercontent.com/40290711/170717664-7e664a26-bd63-464f-9900-f6c2dbcc95df.png)
- > Click on the ***Upload button***

> 2. Click the "Add files" and “Add folder” button, and upload the [Student-ready starter code](https://drive.google.com/open?id=15vQ7-utH7wBJzdAX3eDmO9ls35J5_sEQ) folder content from your local computer to the S3 bucket.

![image](https://user-images.githubusercontent.com/40290711/170719332-d83aaf33-c739-4eb3-8571-761d8f761812.png)
- > Click "Add files" to upload the ***index.html*** file, and click "Add folder" to upload the ***css***, ***img***, and ***vendor*** folders.

![image](https://user-images.githubusercontent.com/40290711/170721361-fc19a12f-b39f-40a5-8a38-53734a09baba.png)

> 2. Confirm that the file and folders are uploaded successfully

![image](https://user-images.githubusercontent.com/40290711/170726225-cb0d7141-2cb2-4a10-a610-cbebe52b3118.png)
- > Successfully uploaded starter code in the bucket.

#### STEP 3: Secure Bucket via IAM
> 1. Click on the ***"Permissions"*** tab.

![image](https://user-images.githubusercontent.com/40290711/170728510-2ac1202a-344a-4e61-8629-92028d931efb.png)

> 2. The “Bucket Policy” section shows it is empty. Click on the Edit button.

![image](https://user-images.githubusercontent.com/40290711/170730492-32cef71e-1df0-41ed-bbd8-1eb0a9993efa.png)
- > Empty bucket policy. Check this policy again after setting up the CloudFront distribution.

> 3. Enter the following bucket policy replacing ***your-website*** with the name of your bucket and click “Save”.

```
{
"Version":"2012-10-17",
"Statement":[
 {
   "Sid":"AddPerm",
   "Effect":"Allow",
   "Principal": "*",
   "Action":["s3:GetObject"],
   "Resource":["arn:aws:s3:::your-website/*"]
 }
]
}

```

![image](https://user-images.githubusercontent.com/40290711/170732739-6f9ed393-aee8-4817-acc7-70c30f346b2f.png)

![image](https://user-images.githubusercontent.com/40290711/170733149-3c67bd58-73f5-4c0b-ae86-3638e14395a6.png)

> 4. Confirm that bucket policy was edited successfully.

![image](https://user-images.githubusercontent.com/40290711/170735193-54b64b93-bdb7-4602-9d4c-5a20e58a84a5.png)
- > You will see warnings about making your bucket public, but ***this step is required for static website hosting***.

#### Tips
>  If we were not learning about static website hosting, we could have made the bucket private and wouldn't have to specify any bucket access policy explicitly. In such a case, once we set up the CloudFront distribution, it will automatically update the current bucket access policy to access the bucket content. The CloudFront service will make this happen by using the Origin Access Identity user.

#### STEP 4: Configure S3 Bucket

> 1. Go to the ***Properties*** tab and then scroll down to edit the ***Static website hosting*** section.

![image](https://user-images.githubusercontent.com/40290711/170737721-7e660e4e-9e2c-4a6f-b501-0610e58365cb.png)
- > Go to the ***Properties*** tab

![image](https://user-images.githubusercontent.com/40290711/170738615-67d45d11-acc7-4f43-9242-22458d73d9b2.png)
- > Edit the Static website hosting section

> 2. Click on the “Edit” button to see the ***Edit static website hosting*** screen. Now, enable the ***Static website hosting***, and provide the default home page and error page for your website. 

![image](https://user-images.githubusercontent.com/40290711/170740243-e1089661-0f38-467a-8210-62a7724068fe.png)
- > Enable the static website hosting, and provide the home page and error page.

> Did you notice that enabling the static website hosting requires you to make your bucket public?
> In the snapshot above, it says "For your customers to access the content at the website endpoint, you must make all your content ***publicly readable***."

> 3. For both “Index document” and “Error document”, enter “index.html” and click “Save”. 

![image](https://user-images.githubusercontent.com/40290711/170741841-ea22f487-4931-44dd-bada-a0530646ac55.png)


> 4. Confirm that the static website hosting was edited successfully

![image](https://user-images.githubusercontent.com/40290711/170742352-d4146a8e-9889-425b-b0ff-04c32c44763a.png)

> 5. After successfully saving the settings, check the ***Static website hosting*** section again under the Properties tab. You must now be able to view the website endpoint as shown below:

![image](https://user-images.githubusercontent.com/40290711/170743029-a15c7bfa-6ec8-4209-99e9-29713d106d08.png)
- > Copy the website enpoint for future use.

#### STEP 5: Distribute Website via CloudFront

> 1. Select “Services” from the top left corner and enter “cloud front” in the “Find a service by name or feature” text box and select “CloudFront”.

![image](https://user-images.githubusercontent.com/40290711/170760257-8ccbc82d-c8ad-46a9-a8af-9e5a4b7a3a60.png)

> 2. From the CloudFront dashboard, click ***"Create Distribution"***.

![image](https://user-images.githubusercontent.com/40290711/170762279-5ac8561d-23eb-4823-9d3e-be819661fa78.png)

> 3. Use the following details to create a distrution:

>                  Field                                          Value
>                  Origin > Domain Name                           Don't select the bucket from the dropdown list. Paste the Static website hosting endpoint of the form <bucket-name>.s3-website-region.amazonaws.com
 >                  Origin > Enable Origin Shield                  No
 >                  Default cache bahavior                         Use default settings
 >                  Cache key and origin requests                  Use default settings
 
 ![image](https://user-images.githubusercontent.com/40290711/170767616-eeaf0b01-a803-4c25-8ea9-af1d713746f1.png)
- > Configurations - Origin details

![image](https://user-images.githubusercontent.com/40290711/170768702-094ab937-7d97-43c0-b92c-7de5aa583940.png)
![image](https://user-images.githubusercontent.com/40290711/170768912-dc8b27af-391d-4b32-812a-3125234b3a84.png)

> 4. Leave the defaults for the rest of the options, and click “Create Distribution”. It may take up to 10 minutes for the CloudFront Distribution to get created.
 
![image](https://user-images.githubusercontent.com/40290711/170769277-331c2168-26c8-4cf7-ad3e-64d9021f5266.png)
 - > ***Note:*** It may take up to ***10 minutes*** for the CloudFront Distribution to be created.

 > 5. Once the status of your distribution changes from “In Progress” to “Deployed”, copy the endpoint URL for your CloudFront distribution found in the “Domain Name” column.

 - > Note - Remember, as soon as your CloudFront distribution is Deployed, it attaches to S3 and starts caching the S3 pages. CloudFront may take 10-30 minutes (or more) to cache the S3 page. Once the caching is complete, the CloudFront domain name URL will stop redirecting to the S3 object URL
 
![image](https://user-images.githubusercontent.com/40290711/170770841-bbe89168-3030-4eff-9767-4d3114f15d6f.png
- > In this example, the Domain Name value is ***d17nmn15xw4rzh.cloudfront.net***, but yours will be different. 
