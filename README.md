
#  Serverless File Sharing Platform

## Project Description:

A lightweight, serverless file-sharing application built with **AWS Lambda**, **Amazon S3**, and **API Gateway**. This platform allows users to securely upload and download files via a simple HTTP API, making it ideal for temporary file sharing, document portals, or backend storage for apps.

---

##  Architecture:


The system is built entirely on AWS serverless services:

- **API Gateway**: Works as a bridge between AWS Lambda and Amazon S3.
- **AWS Lambda**: Handles backend logic for uploading and retrieving files.
- **Amazon S3**: Stores files with high durability and availability.
- **GitBash**: used to perform commands.

Users interact with the platform using any HTTP client (e.g., Postman, curl, browser-based apps).

[Architecture Diagram]
<img width="1536" height="1024" alt="Image" src="https://github.com/user-attachments/assets/5120fc57-31e1-4d7e-81d6-e9b078db6bc9" />

---

##  Setup Instructions:

* Step 1: Create an S3 bucket to store uploaded files.
  
* Step 2: Create the Lambda functions to handle file uploads and file downloads.
        Create IAM role with S3 write permissions.
  
* Step 3: Create an API Gateway.
        Create two resources /files with POST and GET methods. For each method, configure Lambda integration with UploadFunction and DownloadFunction respectively.
  
* Step 4: Configure GET Method.
        
  ```bash
  {
    "queryStringParameters": {
        "fileName": "$input.params('fileName')"
    }
  }
  ```
* Step 5: Configure POST Method.

  ```bash
  {
    "body" : "$input.body",
    "queryStringParameters" : {
        "fileName" : "$input.params('fileName')"
    }
  }
  ```
* step 6: Deploy API Gateway.

* Step 7: Testing.\
       1. Upload a File.\
          I used GitBash with the command.
  
  ```bash
    curl --location 'https://ljesen33uc.execute-api.ap-south-1.amazonaws.com/dev/files?fileName=test.txt'
    --header 'Content-Type: text/plain'
    --data 'Welcome to the cloud world of Anantmati!'
  ```

    3. Download a File \
       Use CURL Utility

  ```bash
      curl --location 'https://ljesen33uc.execute-api.ap-south-1.amazonaws.com/dev/files?fileName=test.txt'
      --header 'Content-Type: text/plain'
  ```

  ---

##  Features:

- Upload files via HTTP POST
- Store files securely in Amazon S3
- Generate pre-signed URLs for secure downloads
- Fully serverless and scalable
- Minimal setup and cost-efficient

       
 
