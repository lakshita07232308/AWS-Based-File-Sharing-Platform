# AWS Based File Sharing Platform 

A secure, scalable, and cost-effective file sharing platform built entirely on AWS serverless technologies. This project allows users to securely upload and download files through a simple HTTP API, with authentication managed by AWS Cognito.

---

## About The Project

The goal of this project is to provide a robust solution for file management without the need to provision or manage traditional servers. It leverages the power of serverless computing to create an efficient, event-driven system. Users can interact with the platform using any HTTP client, like Postman, after authenticating to get a secure token.

### Key Features

* **Secure File Uploads & Downloads:** Transfer files using authenticated POST and GET requests.
* **User Authentication:** Secure user management, registration, and sign-in handled by **AWS Cognito**.
* **Durable Storage:** Files are stored in **Amazon S3**, ensuring high durability and scalability.
* **RESTful API:** A clean API interface managed by **AWS API Gateway** provides a central entry point for all requests.
* **Serverless Compute:** All backend logic is executed by **AWS Lambda** functions, scaling automatically with demand.
* **Team Collaboration:** Facilitates secure sharing of project resources and documents for teams.

---

## System Architecture

The platform's architecture is designed to be fully serverless, relying on managed AWS services to handle the entire workflow from user authentication to file storage.

---

### How It Works

1.  **Authentication:** A user first authenticates with **AWS Cognito** to receive a secure JWT (JSON Web Token).
2.  **API Request:** The user makes a request to **API Gateway** (e.g., to upload or download a file), including the JWT in the `Authorization` header.
3.  **Authorization:** API Gateway uses a Cognito Authorizer to validate the JWT, ensuring the request is from an authenticated user.
4.  **Lambda Execution:**
    * A `POST /files` request triggers the `UploadFunction`, which stores the file in an **S3 bucket**.
    * A `GET /files?fileName=<filename>` request triggers the `DownloadFunction`, which retrieves the requested file from S3.
5.  **Storage & Retrieval:** The Lambda functions interact directly with the **Amazon S3** bucket to store and retrieve files securely.
6.  **Response:** The API Gateway returns a response to the user, such as a success message for an upload or the file content for a download.

---

## Technology Stack

This project is built using the following services and technologies:

* **Cloud Services**:
    * **AWS Lambda**: For serverless compute logic.
    * **Amazon S3**: For scalable and durable object storage.
    * **AWS API Gateway**: To create and manage the RESTful API endpoints.
    * **AWS Cognito**: For user authentication and access control.
* **Programming Language**:
    * **Python 3.9**: Used for developing the Lambda functions.
* **Security**:
    * **IAM Roles & Policies**: To grant necessary permissions for Lambda functions to access S3.
    * **Cognito Authorizer**: To protect API endpoints by validating JWTs.
* **Development & Testing**:
    * **Postman**: For API testing and sending HTTP requests.
    * **AWS Console & CLI**: For deploying and managing all cloud resources.

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
    * Set up a User Pool in **AWS Cognito**.
    * Create an **S3 bucket** to store the files.
    * Deploy the `UploadFunction` and `DownloadFunction` **AWS Lambda** functions written in Python.
    * Configure **API Gateway** with `POST` and `GET` methods, linking them to the respective Lambda functions.
    * Secure the API Gateway endpoints using a **Cognito Authorizer**.

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

