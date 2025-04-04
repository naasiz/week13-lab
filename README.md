# Week 13 Lab – Remote Backend with Terraform and S3

## Overview

This lab demonstrates how to set up a remote backend using Amazon S3 for managing Terraform state and lock files. By storing the state file remotely, ensure safe collaboration and centralized infrastructure management. The lab includes working with existing Terraform scripts, creating and destroying an S3 bucket, modifying configuration files, and verifying state and lock behavior.

## Tasks Completed

- Cloned the starter repository
- Ran the `create-bucket` script to create a unique S3 bucket
- Configured a remote backend in the `provider.tf` file using the S3 bucket
- Initialized Terraform with the remote backend
- Ran `terraform apply` for the first time to create the state file in the S3 bucket
- Modified `server.tf` to add a dummy tag in order to trigger a change
- Ran `terraform apply` again to simulate a lock file
- Before typing `yes`, I refreshed the S3 console to confirm that the `.terraform.tfstate.lock.info` file was present
- Took screenshots showing the state file and the lock file
- Cleaned up resources using `terraform destroy` and the `delete-bucket` script

## Lab Questions

**1. When is the state file created?**  
After running `terraform apply` for the first time, the state file is created in the S3 bucket.

**2. When is the lock file present?**  
The lock file appears when a `terraform plan` or `terraform apply` is in progress and waiting for confirmation.

**3. Is the lock file always in the bucket after it is created?**  
No. The lock file is temporary and is automatically removed when the operation completes or is canceled.

## Screenshots

**State File in S3 Bucket**  
*only the state file present after the initial apply.*  
![Screenshot 2025-04-04 144058](https://github.com/user-attachments/assets/e6de379f-785a-44f8-be79-bfe3217ae77e)


**State File and Lock File in S3 Bucket**  
*both state and lock files while apply is in progress and before typing "yes".*  
![Screenshot 2025-04-04 144508](https://github.com/user-attachments/assets/2ed22795-2341-461f-9f5d-680682068db7)

