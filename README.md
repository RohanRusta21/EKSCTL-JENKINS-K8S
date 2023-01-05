# EKSCTL-DEMO-TODO

#### Pre-requisites: 
  - an EC2 Instance (Note : If Using Ubuntu EC2 Instance instead of Amazon Linux then Make Sure to have **aws-iam-authenticator** installed.

#### AWS EKS Setup 
1. Setup kubectl   
   a. Download kubectl  
   b. Grant execution permissions to kubectl executable   
   c. Move kubectl onto /usr/local/bin   
   d. Test that your kubectl installation was successful    
   ```sh 
   curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.19.6/2021-01-05/bin/linux/amd64/kubectl
   chmod +x ./kubectl
   mv ./kubectl /usr/local/bin 
   kubectl version --short --client
   ```
2. Setup eksctl   
   a. Download and extract the latest release   
   b. Move the extracted binary to /usr/local/bin   
   c. Test that your eksclt installation was successful   
   ```sh
   curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
   sudo mv /tmp/eksctl /usr/local/bin
   eksctl version
   ```
  
3. Create an IAM Role and attache it to EC2 instance    
   `Note: create IAM user with programmatic access if your bootstrap system is outside of AWS`   
   IAM user should have access to   
   IAM   
   EC2   
   VPC    
   CloudFormation

4. Create your cluster and nodes 
   ```sh
   eksctl create cluster --name cluster-name  \
   --region region-name \
   --node-type instance-type \
   --nodes-min 2 \
   --nodes-max 2 \ 
   --zones <AZ-1>,<AZ-2>
   
   example:
   eksctl create cluster --name todo-cluster \
   --region ap-south-1 \
   --node-type t2.small \
   --nodes-min 2 \
   --nodes-max 2
    ```




## Docker

To build a docker image for the todo-list-app and run it inside a container execute

```sh
docker build -t dockerhub9876/todo .
```


## Kubernetes

To Apply deployment.yaml

```sh
kubectl apply -f deployment.yaml
```


To Apply service.yaml

```sh
kubectl apply -f service.yaml
```


## Screenshots

![image](https://user-images.githubusercontent.com/110477025/210777006-6ba03c54-4a2f-462c-bb48-14fb6176cc91.png)


![image](https://user-images.githubusercontent.com/110477025/210777445-8e9dfb45-4983-4e54-8be7-b506207f105c.png)


![image](https://user-images.githubusercontent.com/110477025/210777477-f7bcd5df-5e47-468d-ab80-d88677b6b37b.png)


![image](https://user-images.githubusercontent.com/110477025/210777531-5f000aba-556d-457e-b01a-27255c6b48a4.png)





