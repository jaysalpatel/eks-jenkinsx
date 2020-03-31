Continuous Delivery with AWS EKS and Jenkins X

Goal: have a EKS cluster deployed exposed using ELB and Route 53 domain mapping. Inside cluster, we want a jenkins server (triggers to Git changes) whic starts kubgernetes-based builds which end up as docker images pushed into ECR. Then, jenkins will deploy our application image into an EKS cluster and expose it via ingress to the outside world. 
Persistence of infrastructure and applications handled by AWS services. 

1. Configure the project domain in Route 53
    - Create name of public hosted zone

2. Install the Jenkins X cli client
    - On mac os/linux use "brew install jenkins-x/jx/jx"


3. Creating the Kubernetes cluster
    - once you have the jx client installed, you are ready to create the EKS cluster which will be use dto run the jenkins X server, CI builds, and the application itself.
    - Setup your AWS credentials
        - export AWS_ACCESS_KEY_ID=myaccessid
        - export AWS_SECRET_ACCESS_KEY=mysecret
    - Create the new kubernetes cluster with this EKS command
        - jx create cluster eks --cluster-name=jenkinsx-kubernetes --skip-installation=true
    - View the cluster with this command
        - jx get eks

4. Installing the jenkins x platform into your kubernetes cluster
