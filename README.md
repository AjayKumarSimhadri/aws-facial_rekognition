# 🤖 AWS Facial Rekognition

This project provides a complete face recognition system using **Amazon Rekognition**, **DynamoDB**, and **Amazon S3**, integrated with **Python**. It allows you to:

- Detect faces in uploaded images  
- Index faces into a Rekognition collection  
- Search and compare faces  
- Store face metadata in DynamoDB  
- Manage image files via Amazon S3

---

## 🧰 Prerequisites

Before you begin, make sure you have the following:

- An **AWS account**
- **Python 3.7+** installed
- **AWS CLI** installed and configured
- An **IAM user** with access to:
  - Amazon Rekognition  
  - Amazon DynamoDB  
  - Amazon S3


## 🚀 Step 1: Clone the Repository and Set Up the Project

Follow the steps below to get your environment ready:

### ✅ 1.1 Clone the Repository

```bash
git clone https://github.com/AjayKumarSimhadri/aws-facial_rekognition.git
cd aws-facial_rekognition
````

### ✅ 1.2 Install the Necessary Python Packages Using pip

```bash
pip install boto3 aws-shell
```

### ✅ 1.3 Configure AWS Credentials

Run the following command to configure your AWS CLI:

```bash
aws configure
```

You will be prompted to enter:

* **AWS Access Key ID**
* **AWS Secret Access Key**
* **Default region name** (e.g., `us-east-1`)
* **Default output format** (e.g., `json`)

---

## ☁️ Step 2: Create AWS Resources

### 🔹 2.1 Create a Rekognition Collection

```bash
aws rekognition create-collection \
--collection-id facerecognition_collection \
--region us-east-1
```

This command creates a face collection where facial features will be indexed and stored.

---

### 🔹 2.2 Create a DynamoDB Table

```bash
aws dynamodb create-table \
--table-name facerecognition \
--attribute-definitions AttributeName=RekognitionId,AttributeType=S \
--key-schema AttributeName=RekognitionId,KeyType=HASH \
--provisioned-throughput ReadCapacityUnits=1,WriteCapacityUnits=1 \
--region us-east-1
```

This table stores metadata for each detected face.

---

### 🔹 2.3 Create an S3 Bucket

```bash
aws s3 mb s3://your-unique-bucket-name --region us-east-1

> ⚠️ Replace `your-unique-bucket-name` with a globally unique name (e.g., `facial-rekognition-demo-ajay`).

 bucket will store image files to be processed by Amazon Rekognition.
```


### ✅ Features

* **Face Detection** – Detect faces in uploaded images
* **Face Indexing** – Store face data in Rekognition collection
* **Face Search** – Compare faces against stored entries
* **Metadata Storage** – Save face details in DynamoDB
* **Image Handling** – Upload images using Amazon S3

---

### 📌 Notes

* Use the **same AWS region** (e.g., `us-east-1`) for Rekognition, DynamoDB, and S3.
* Ensure your IAM user has required permissions for all services.
* Use only `.jpg` or `.png` image formats for uploads.

---

🔗 Click on the link to get a [Gitdiagram](https://gitdiagram.com/ajaykumarsimhadri/aws-facial_rekognition).
  
![AWS Facial Rekognition git diagram](https://github.com/user-attachments/assets/0f20cb55-df52-4735-851b-db38a52b7ca6)

---

### 📞 Support

For issues or contributions, feel free to raise an issue on the [GitHub repository](https://github.com/AjayKumarSimhadri/aws-facial_rekognition) or contact me on [LinkedIn](https://www.linkedin.com/in/ajaykumarsimhadri/).

