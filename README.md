# Recommender System with AWS and Terraform

## Project Overview
This project demonstrates a basic recommender system built using AWS services. The system suggests recommendations (e.g., movies) based on user preferences stored in a database. It uses machine learning to generate recommendations and exposes them via an API.

---

## Architecture
The system architecture includes the following AWS components:

- **Amazon S3**: Stores datasets, including movies and user preferences.
- **AWS Lambda**: Handles data preprocessing and API logic.
- **Amazon DynamoDB**: Stores user preferences and metadata.
- **Amazon SageMaker**: Trains and deploys the recommendation model.
- **Amazon API Gateway**: Exposes the recommendation API.

### High-Level Flow:
1. Datasets are uploaded to **S3**.
2. **Lambda** preprocesses the data and saves it back to S3.
3. **SageMaker** trains a collaborative filtering model using the preprocessed data.
4. The trained model is deployed as a SageMaker endpoint.
5. **API Gateway** and **Lambda** provide an API to query recommendations for users.
6. **DynamoDB** stores user preferences and metadata for personalized results.

---

## Prerequisites
1. AWS account with appropriate permissions.
2. Terraform installed locally ([download here](https://www.terraform.io/downloads)).
3. Basic knowledge of Python, machine learning, and AWS services.

---

## Features
- **Recommendation Engine**: Trained using collaborative filtering.
- **API Access**: Query recommendations via a RESTful API.
- **Infrastructure as Code**: Fully automated deployment using Terraform.
- **Cost Optimization**: Uses lightweight AWS resources to minimize costs.

---

## Deployment Steps

### 1. Clone the Repository
```bash
git clone https://github.com/your-repo/recommender-system.git
cd recommender-system
```

### 2. Set Up AWS Credentials
Configure your AWS CLI with credentials:
```bash
aws configure
```

### 3. Initialize Terraform
```bash
terraform init
```

### 4. Deploy Infrastructure
Plan and apply Terraform configuration to create resources:
```bash
terraform plan
terraform apply
```

### 5. Upload Datasets to S3
1. Download the MovieLens dataset from [here](https://grouplens.org/datasets/movielens/).
2. Upload the dataset to the S3 bucket created by Terraform.

### 6. Train the Model
1. Open the SageMaker notebook instance created by Terraform.
2. Run the training script to preprocess data and train the model.
3. Deploy the model as a SageMaker endpoint.

### 7. Test the API
Use a tool like Postman to query the API Gateway endpoint. Example:
```bash
curl -X GET 'https://your-api-endpoint/recommendations?user_id=123'
```

---

## Repository Structure
```
.
├── terraform/
│   ├── main.tf              # Terraform main configuration
│   ├── modules/             # Reusable Terraform modules
│   ├── variables.tf         # Terraform variables
│   ├── outputs.tf           # Terraform outputs
│   └── preprocessor.zip     # Lambda function code
├── sagemaker/
│   └── train_model.ipynb    # SageMaker notebook for training
├── README.md                # Project documentation
└── data/
    └── movielens/           # Dataset files (e.g., movies.csv, ratings.csv)
```

---

## Cost Optimization Tips
- Use the AWS **Free Tier** for eligible services.
- Use **Spot Instances** for SageMaker training jobs.
- Stop the SageMaker notebook instance when not in use.
- Remove resources with `terraform destroy` after testing.

---

## Future Enhancements
- Add a user interface for a better demo experience.
- Extend the system to handle real-time updates for user preferences.
- Implement a hybrid recommendation model combining collaborative and content-based filtering.

---

## License
This project is licensed under the MIT License. See the LICENSE file for details.

---

## Acknowledgments
- Dataset provided by [MovieLens](https://grouplens.org/datasets/movielens/).
- Built using Terraform and AWS.

