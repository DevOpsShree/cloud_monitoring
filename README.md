Cloud Native Monitoring Application On Kubernetes!

In this Project, one can learn about the Deployment of Python applications.

I understood this project to have four major classifications as follows:
1. Build: Code Development
2. Docker: Creation of container
3. Elastic Container Registry: Moving the local files to the cloud
4. Kubernetes: Deployment of the application

![DevopsShree](https://github.com/DevOpsShree/cloud_monitoring/assets/125661746/8ec2bd35-4674-462d-9197-7c370b31e327)

Prerequisites: 
1. To Begin, Create an AWS account and download and Configure AWS CLI. Please refer to the document for the same:
https://aws.amazon.com/cli/
https://docs.aws.amazon.com/cli/latest/reference/configure/

2. There is a requirement.txt file that holds all prerequisites need to be installed for the project, hence run 
pip install -r requirement.txt
Fun Fact: -r allows pip install to open requirements. txt and install the packages inside of it.

1. Build: Code Development(app.py)
   app.py has the code required to run the monitoring system for CPU and Memory usage. Cpu, memory utilization is retrieved using the cross-platform library psutil. Flask is used to build the presentable UI.
   After running one can find the application in http://localhost:5000/

![image](https://github.com/DevOpsShree/cloud_monitoring/assets/125661746/b962cef4-a6d3-4819-ba4d-3db10fc1d7d0)

2. Docker: Creation of container(DockerFile)
   DockerFile -> Image -> Container
     Set the Base Image(python:3.9-slim-buster), working directory (/app), copy and run requirement.txt to fulfill the container dependencies, set environment and port in for the application,
     Command to run
   
   we need to build the Image from Dockerfile using
       docker build -t cloudmonitoring .
   Confirm the creation of docker image using
       docker images

   Run the container from the created image using
     docker run -p 5000:5000 a62edb7168f8
     docker run -p 5000:5000 <imageId>

3.  Elastic Container Registry: Moving the local files to cloud (ecr.py)
   Instead of using the ideal way to create a repository (https://docs.aws.amazon.com/AmazonECR/latest/userguide/repository-create.html), Boto3 (Python package) is used to create ECR.
   https://boto3.amazonaws.com/v1/documentation/api/latest/index.html
   Define the Client and repository, get repositoryUri from the response, and run ecr.py to create the repository.
   Find and run all the "view push commands" on aws to push the image into the created repository
   ![image2 repo](https://github.com/DevOpsShree/cloud_monitoring/assets/125661746/274a0148-421d-4f55-bd52-82ba50162ea5)
   ![image](https://github.com/DevOpsShree/cloud_monitoring/assets/125661746/15cfc119-2d17-4d5d-8e6c-23851c2644f7)


5.  Kubernetes: Deployment of the application
   --> Clusters can be created using AWS management console, AWS CLI, eksctl commands according to the requirement. 
    https://docs.aws.amazon.com/eks/latest/userguide/create-cluster.html
    Proper AWS roles, regions, and security groups must be added.
    ![cluster1](https://github.com/DevOpsShree/cloud_monitoring/assets/125661746/61e884cd-8cd6-49ee-9c6d-4b47a3086291)
    ![cluster2](https://github.com/DevOpsShree/cloud_monitoring/assets/125661746/1bd76b69-ac80-41ce-a1aa-941748656007)


   --> Creation of nodegroup can be done using AWS management console, eksctl commands according to the requirement. 
    https://docs.aws.amazon.com/eks/latest/userguide/create-managed-node-group.html
    ![node](https://github.com/DevOpsShree/cloud_monitoring/assets/125661746/20ea6311-ee76-4988-a628-74909346affc)

   
   --> Creation of Kubernetes Deployment and Services on Kubernetes can be done using yaml (https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) or python(eks.py).
    ![imp cmd](https://github.com/DevOpsShree/cloud_monitoring/assets/125661746/fb0a9bf8-bca7-4734-ae56-d2c1663d38c4)
    ![CMD](https://github.com/DevOpsShree/cloud_monitoring/assets/125661746/0620c354-cadb-4f28-a6ac-e3103b1e3235)
    ![screen 2](https://github.com/DevOpsShree/cloud_monitoring/assets/125661746/cb79149f-de77-40a9-b122-9c925445bf44)

    Credits: Youtube channels: Cloud Champ, Abhishek.Veeramalla



   
   
   
   
