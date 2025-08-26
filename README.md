# AWS Based File Sharing Platform ☁️

A secure, scalable, and cost-effective file sharing platform built entirely on AWS serverless technologies. [cite_start]This project allows users to securely upload and download files through a simple HTTP API, with authentication managed by AWS Cognito. [cite: 11, 41]

---

## About The Project

[cite_start]The goal of this project is to provide a robust solution for file management without the need to provision or manage traditional servers. [cite: 21] [cite_start]It leverages the power of serverless computing to create an efficient, event-driven system. [cite: 21] [cite_start]Users can interact with the platform using any HTTP client, like Postman, after authenticating to get a secure token. [cite: 13]

### Key Features

* [cite_start]**Secure File Uploads & Downloads:** Transfer files using authenticated POST and GET requests. [cite: 23]
* [cite_start]**User Authentication:** Secure user management, registration, and sign-in handled by **AWS Cognito**. [cite: 12, 48]
* [cite_start]**Durable Storage:** Files are stored in **Amazon S3**, ensuring high durability and scalability. [cite: 24]
* [cite_start]**RESTful API:** A clean API interface managed by **AWS API Gateway** provides a central entry point for all requests. [cite: 25, 51]
* [cite_start]**Serverless Compute:** All backend logic is executed by **AWS Lambda** functions, scaling automatically with demand. [cite: 12, 70]
* [cite_start]**Team Collaboration:** Facilitates secure sharing of project resources and documents for teams. [cite: 17, 27]

---

## System Architecture

The platform's architecture is designed to be fully serverless, relying on managed AWS services to handle the entire workflow from user authentication to file storage.


### How It Works

1.  [cite_start]**Authentication:** A user first authenticates with **AWS Cognito** to receive a secure JWT (JSON Web Token). [cite: 45]
2.  [cite_start]**API Request:** The user makes a request to **API Gateway** (e.g., to upload or download a file), including the JWT in the `Authorization` header. [cite: 46]
3.  [cite_start]**Authorization:** API Gateway uses a Cognito Authorizer to validate the JWT, ensuring the request is from an authenticated user. [cite: 51, 78]
4.  **Lambda Execution:**
    * [cite_start]A `POST /files` request triggers the `UploadFunction`, which stores the file in an **S3 bucket**. [cite: 53, 57]
    * [cite_start]A `GET /files?fileName=<filename>` request triggers the `DownloadFunction`, which retrieves the requested file from S3. [cite: 54, 60]
5.  [cite_start]**Storage & Retrieval:** The Lambda functions interact directly with the **Amazon S3** bucket to store and retrieve files securely. [cite: 59, 60]
6.  [cite_start]**Response:** The API Gateway returns a response to the user, such as a success message for an upload or the file content for a download. [cite: 65, 66]

---

## Technology Stack

This project is built using the following services and technologies:

* **Cloud Services**:
    * [cite_start]**AWS Lambda**: For serverless compute logic. [cite: 70]
    * [cite_start]**Amazon S3**: For scalable and durable object storage. [cite: 71]
    * [cite_start]**AWS API Gateway**: To create and manage the RESTful API endpoints. [cite: 69]
    * [cite_start]**AWS Cognito**: For user authentication and access control. [cite: 72]
* **Programming Language**:
    * [cite_start]**Python 3.9**: Used for developing the Lambda functions. [cite: 74]
* **Security**:
    * [cite_start]**IAM Roles & Policies**: To grant necessary permissions for Lambda functions to access S3. [cite: 80]
    * [cite_start]**Cognito Authorizer**: To protect API endpoints by validating JWTs. [cite: 78]
* **Development & Testing**:
    * [cite_start]**Postman**: For API testing and sending HTTP requests. [cite: 82]
    * [cite_start]**AWS Console & CLI**: For deploying and managing all cloud resources. [cite: 83]

---

## Getting Started

To get a local copy up and running, follow these simple steps.

### Prerequisites

* An AWS Account
* AWS CLI configured with appropriate permissions
* Python 3.9
* Postman (or another API client)

### Installation & Deployment

1.  **Clone the repo**
    ```sh
    git clone [https://github.com/lakshita07232308/file-sharing-platform.git](https://github.com/lakshita07232308/file-sharing-platform.git)
    ```
2.  **Deploy AWS Resources**
    * [cite_start]Set up a User Pool in **AWS Cognito**. [cite: 77]
    * [cite_start]Create an **S3 bucket** to store the files. [cite: 62]
    * [cite_start]Deploy the `UploadFunction` and `DownloadFunction` **AWS Lambda** functions written in Python. [cite: 70]
    * [cite_start]Configure **API Gateway** with `POST` and `GET` methods, linking them to the respective Lambda functions. [cite: 53, 54]
    * [cite_start]Secure the API Gateway endpoints using a **Cognito Authorizer**. [cite: 51]

---

## Usage

1.  **Sign Up / Sign In:** Use the Cognito-hosted UI or an API call to register and sign in. You will receive a JWT access token.
2.  **Upload a File:**
    * Send a `POST` request to the `/files` endpoint.
    * Include the JWT in the `Authorization: Bearer <token>` header.
    * Provide the file in the request body.
    * You will receive a secret key upon successful upload.
3.  **Download a File:**
    * Send a `GET` request to the `/files?fileName=<your-secret-key>` endpoint.
    * Include the JWT in the `Authorization: Bearer <token>` header.
    * The file will be returned in the response body.

---

