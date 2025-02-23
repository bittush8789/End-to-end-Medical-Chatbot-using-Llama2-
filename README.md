# End-to-End Medical Chatbot using Llama2

## How to Run

### Step 1: Clone the Repository

Clone the project repository from GitHub:
```sh
https://github.com/bittush8789/End-to-end-Medical-Chatbot-using-Llama2-.git
```

### Step 2: Create a Conda Environment

After opening the repository, create and activate a Conda environment:
```sh
conda create -n mchatbot python=3.8 -y
conda activate mchatbot
```

### Step 3: Install Dependencies

Install the required dependencies:
```sh
pip install -r requirements.txt
```

### Step 4: Set Up Environment Variables

Create a `.env` file in the root directory and add your Pinecone credentials:
```sh
PINECONE_API_KEY = "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
PINECONE_API_ENV = "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
```

### Step 5: Download the Quantized Llama 2 Model

Download the Llama 2 model and place it in the `model` directory.

#### Model File:
```
llama-2-7b-chat.ggmlv3.q4_0.bin
```

#### Download Link:
[Download from Hugging Face](https://huggingface.co/TheBloke/Llama-2-7B-Chat-GGML/tree/main)

### Step 6: Store Index

Run the following command to store the index:
```sh
python store_index.py
```

### Step 7: Start the Application

Run the application with:
```sh
python app.py
```

### Step 8: Open the Localhost

Once the application is running, open your browser and navigate to:
```
http://localhost:5000
```

---

## Tech Stack Used

- Python
- LangChain
- Flask
- Meta Llama2
- Pinecone
- AWS (CI/CD Deployment with GitHub Actions)

---

## Deployment on AWS

### Step 1: Login to AWS Console

### Step 2: Create IAM User for Deployment

Grant the following AWS permissions:
- **EC2 Access**: Virtual Machine for deployment
- **ECR Access**: Store Docker images

### Step 3: Create ECR Repository

Store and save your Docker image in AWS Elastic Container Registry (ECR):
```sh
970547337635.dkr.ecr.ap-south-1.amazonaws.com/medicalchatbot
```

### Step 4: Create EC2 Machine (Ubuntu)

Launch an EC2 instance and install Docker:
```sh
sudo apt-get update -y
sudo apt-get upgrade
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker ubuntu
newgrp docker
```

### Step 5: Configure EC2 as a Self-Hosted Runner

Go to GitHub:
1. Navigate to **Settings > Actions > Runner**
2. Click **New Self-Hosted Runner**
3. Choose **OS** and run the provided commands one by one

### Step 6: Set Up GitHub Secrets

In GitHub **Repository Settings**, add the following secrets:
```sh
AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
AWS_DEFAULT_REGION
ECR_REPO
PINECONE_API_KEY
OPENAI_API_KEY
```

---

## AWS Deployment Steps

1. **Build the Docker Image**
2. **Push the Docker Image to ECR**
3. **Launch an EC2 Instance**
4. **Pull the Docker Image from ECR in EC2**
5. **Launch the Docker Container in EC2**

### AWS IAM Policies Required

Assign the following policies to the IAM user:
```sh
AmazonEC2ContainerRegistryFullAccess
AmazonEC2FullAccess
```

---

## Conclusion

This guide provides all necessary steps to set up, run, and deploy the End-to-End Medical Chatbot using Llama2 on AWS. Follow the steps carefully to ensure a successful deployment.

