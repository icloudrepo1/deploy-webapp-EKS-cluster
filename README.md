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

Go to aws cli website and download aws cli for linux (ubuntu user)


```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
```


## step-4 :- unzip the installer


```
sudo apt update

sudo apt install unzip

unzip awscliv2.zip

sudo ./aws/install

aws --version
```

```
aws configure
```

( provide your access key and secret access key )


## step-5 :- install k8s tool


### install kubectl


`https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/`

```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"
echo "$(cat kubectl.sha256)  kubectl" | sha256sum --check
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
kubectl version --client
```


### install eksctl



```
sudo apt update && sudo apt upgrade -y
```

```
# for ARM systems, set ARCH to: `arm64`, `armv6` or `armv7`
ARCH=amd64
PLATFORM=$(uname -s)_$ARCH

curl -sLO "https://github.com/eksctl-io/eksctl/releases/latest/download/eksctl_$PLATFORM.tar.gz"

# (Optional) Verify checksum
curl -sL "https://github.com/eksctl-io/eksctl/releases/latest/download/eksctl_checksums.txt" | grep $PLATFORM | sha256sum --check

tar -xzf eksctl_$PLATFORM.tar.gz -C /tmp && rm eksctl_$PLATFORM.tar.gz

sudo mv /tmp/eksctl /usr/local/bin
```


```
eksctl version
```


## step-6 :- create k8s cluster


```
eksctl create cluster --name mycluster --region ap-south-1 --node-type t2.micro --nodes-min 2 --nodes-max 3
```


## step-7 :- list of existing cluster


```
eksctl get clusters
```


## step-8 :- delete a cluster


```
eksctl delete cluster --name mycluster
```


---------
