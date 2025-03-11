# deploy-webapp-EKS-cluster


## step-1 :- create an ec2-instance

   - AMI = ubuntu
   - INSTANCE TYPES = t2.micro
   - KEY-PAIR = ubuntu-key1.pem
   - SG = ubuntu-sg1 (all traffic --> anywhere)
   - Launch Your Instance
   - Connect Your Instance


## step-2 :- set-up AWS environment

   - Create one iam-user and provide administrator access
   - Generate your Access-key & Secret Access-key (for CLI access)


## step-3 :- download the AWS cli installer

   - Go to aws cli website and download aws cli for linux (ubuntu user)

   - `curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"`


## step-4 :- unzip the installer

   - `sudo apt update`

   - `sudo apt install unzip`

   - `unzip awscliv2.zip`

   - `sudo ./aws/install`

   - `aws --version`

   - `aws configure`
     ( provide your access key and secret access key )
