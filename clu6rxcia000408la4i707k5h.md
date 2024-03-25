---
title: "🚀 AWS Resource Tracker Script 🚀"
datePublished: Mon Mar 25 2024 09:56:58 GMT+0000 (Coordinated Universal Time)
cuid: clu6rxcia000408la4i707k5h
slug: aws-resource-tracker-script
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1711360464663/38fe70b5-64f0-4c7d-abce-211f186a5c69.jpeg
tags: linux, aws, devops, hashnode, devops-articles

---

#### Pre-Requisites:

* AWS CLI
    
* Access key
    

#### Installation of prerequisites:

🔧 **AWS CLI:**

* On Ubuntu, use the following command:
    
    ```plaintext
    sudo apt install awscli
    ```
    

[Install AWS CLI for your OS](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)

**Create a**[**nd configure access key:**](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)

1. [**Step 1:**](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)
    
    * [Login into your AWS account.](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)
        
    * Click [on your AWS account name in the top ri](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)ght corner.
        
    * Select "Security Credentials".
        
    * [Scroll and find the access](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html) ke[y, then click "Create acces](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)s key".
        
2. [**Step 2:**](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)
    
    * [Open the terminal and t](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)ype:
        
        ```plaintext
        aws configure
        ```
        
    * Enter the access key ID and sec[ret when prompted.](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)
        

#### [Scr](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)ipt:

```plaintext
#!/bin/bash
###########################################################################
# 🛠️ This script tracks resources in our AWS account 🛠️ #
###########################################################################

##### List IAM Users #####
echo "IAM users are:" > resources.txt

echo "Before JSON Parsing" >> resources.txt
aws iam list-users >> resources.txt

echo "After JSON Parsing by filtering with username alone" >> resources.txt
aws iam list-users | jq '.Users[].UserName' >> resources.txt

##### List EC2 Instances #####
echo "EC2 Instances that we have:" >> resources.txt
aws ec2 describe-instances | jq '.Reservations[].Instances[].Tags[].Value' >> resources.txt

##### List IAM Group #####
echo "IAM Groups are:" >> resources.txt
aws iam list-groups >> resources.txt

##### List S3 Bucket #####
echo "S3 buckets are:" >> resources.txt
aws s3 ls >> resources.txt
```

**Usage:**

* Make a .sh filetouch aws\_resource\_tracker.sh chmod +x aws\_resource\_tracker.sh
    
* Open the script file: vim aws\_resource\_tracker.sh
    
* Paste the script and save it.
    
* Execute the script: ./aws\_resource\_tracker.sh
    

**Output:** 📝 **resources.txt:**

```plaintext
IAM users are:
Before JSON Parsing
... [IAM user details]
After JSON Parsing by filtering with username alone
... [Filtered usernames]

EC2 Instances that we have:
... [EC2 instance details]

IAM Groups are:
... [IAM group details]

S3 buckets are:
... [S3 bucket details]
```

**Automate Using CRON JOB:**

* Open crontab file:
    
    ```plaintext
    sudo nano /etc/crontab
    ```
    
* Add the job to run the script daily at 16:40 (4:40 pm):
    
    ```plaintext
    40 16 * * * ubuntu bash /home/ubuntu/aws_resource_tracker.sh
    ```