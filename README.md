# ☁️ Cloud Security with AWS IAM  

This project demonstrates how to use **AWS Identity and Access Management (IAM)** to control access and permissions for AWS resources, with a focus on **Amazon EC2 instances**. It covers IAM users, groups, policies, account aliases, tags, and the IAM Policy Simulator.  

## 📌 Project Overview  
The goal of this project was to:  
- Learn **cloud security foundations** using IAM.  
- Write and test **JSON IAM policies** for fine-grained access control.  
- Use **tags** to manage access to EC2 instances.  
- Explore the **IAM Policy Simulator** for safe policy testing.  
- Validate how policies work with both **authorized and unauthorized actions**.  

## 🛠️ Tools & Services Used  
- **AWS IAM** – Users, Groups, JSON Policies, Account Alias, Policy Simulator  
- **Amazon EC2** – Instances for testing IAM policies  
- **IAM Policy Simulator** – Safe environment to test policies before deployment  

## 📖 Steps Completed  
1. Created **IAM users** and grouped them for streamlined permission management.  
2. Defined a **JSON IAM policy** that:  
   - ✅ Allowed actions (start/stop/describe) on EC2 instances tagged with `development`.  
   - ❌ Denied create/delete tag actions.  
   - ❌ Denied access to EC2 instances tagged with `production`.  
3. Attached the policy to a user group, so all users in the group inherit permissions.  
4. Configured an **account alias** for a cleaner login URL.  
5. Logged in as IAM users to test restricted/allowed actions.  
6. Used the **IAM Policy Simulator** to validate permissions without disrupting active instances.  

## ✅ Key Learnings  
- IAM policy structure with `Effect`, `Action`, and `Resource`.  
- How **tags** (e.g., `Env=development` vs `Env=production`) help enforce least privilege.  
- Benefits of **IAM groups** for easier permission management.  
- Using **IAM Policy Simulator** for controlled policy testing.  
- The difference between **policy-based denial** vs **lack of permission**.  

## 🚀 How to Reproduce  
1. Create IAM **users** and assign them to a **group**.  
2. Write a **JSON IAM policy**. Example:  
   ```json
   {
     "Version": "2012-10-17",
     "Statement": [
       {
         "Effect": "Allow",
         "Action": [
           "ec2:StartInstances",
           "ec2:StopInstances",
           "ec2:DescribeInstances"
         ],
         "Resource": "*",
         "Condition": {
           "StringEquals": {
             "ec2:ResourceTag/Env": "development"
           }
         }
       },
       {
         "Effect": "Deny",
         "Action": [
           "ec2:CreateTags",
           "ec2:DeleteTags"
         ],
         "Resource": "*"
       }
     ]
   }
## 📂 Project Structure 
├── Cloud Security with AWS IAM.pdf  # Documentation of steps & learnings

└── README.md                          # Project overview
