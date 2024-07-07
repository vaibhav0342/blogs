---
title: "Configuring a Terraform remote backend with S3 and DynamoDB"
datePublished: Sun Jul 07 2024 07:09:43 GMT+0000 (Coordinated Universal Time)
cuid: clyb7quf500000al83nl597ux
slug: configuring-a-terraform-remote-backend-with-s3-and-dynamodb
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720336071120/840cb2da-4449-4cdb-a664-2f4a60a8ccd2.webp
tags: linux, aws, automation, devops, terraform

---

**State:** A file that keeps track of the current state of the infrastructure managed by Terraform.

**Remote Backends :** A remote backend stores the Terraform state file outside of your local file system and version control. Using S3 as a remote backend is a popular choice due to its reliability and scalability.

*Here's how to set it up:*

**1. Create an S3 Bucket:** Create an S3 bucket in your AWS account to store the Terraform state. Ensure that the appropriate IAM permissions are set up.

**2. Create a DynamoDB Table:** DynamoDB is used for state locking when a remote backend is configured.

## **Setting Up AWS S3 Bucket and DynamoDB Table with Terraform**

**Step 1: Provider Configuration**

```plaintext
provider "aws" {
  region = "us-east-1"
}
```

**Step 2: Create an S3 Bucket**

```plaintext
resource "aws_s3_bucket" "s3_bucket" {
  bucket = "vaibhav-s3-demo-xyz" # Change this to a unique bucket name
}
```

**Step 3: Create a DynamoDB Table**

Now, create a DynamoDB table to be used for Terraform state locking. This table uses `PAY_PER_REQUEST` billing mode and has a primary key named `LockID`**.**

```plaintext
resource "aws_dynamodb_table" "terraform_lock" {
  name         = "terraform-lock"
  billing_mode = "PAY_PER_REQUEST"
  hash_key     = "LockID"

  attribute {
    name = "LockID"
    type = "S"
  }
}
```

### Step 4: Configure Terraform Backend

Finally, configure the Terraform backend to use the S3 bucket and DynamoDB table.

```plaintext
# backend.tf
terraform {
  backend "s3" {
    bucket         = "vaibhav-s3-demo-xyz" # Change this BUCKET NAME
    key            = "vaibhav/terraform.tfstate" # Create a folder inside the S3 bucket and state file
    region         = "us-east-1" # S3 bucket region
    encrypt        = true
    dynamodb_table = "terraform-lock"
  }
}
```