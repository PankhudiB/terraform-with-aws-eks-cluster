Break down the requirements :

    VM -> EC2
    For any machine you need :
    os -> no specific choice [they ll use amazon linux]
    h/w -> type of machine -> t2.small
    no of machine - 2 worker | (masters created by eks)
    storage -> EBS -> for permanent
    ram - bare minimum
    cpu - bare minimum
    n/w :
        1. separate n/w -> isolated from other n/w
        2. able to specify ip ranges
        3. CIDR for master node , worker node in k8s
        4. in aws -> VPC --> gives you isolated n/w |
        4.a inside vpc - subnets  ---> will give us cidr -> to isolate traffic
        5. private endpoints to aws services -> s3 storage, ecr ->  (artifactory for aws assets)

For k8s eks
     
    master
    worker count
    api server of k8s
    artifactory access
    docker installation

Overall plan:
- VPC Creation
- Subnets creation - vpc module
- Private Endpoints
    * STS
    * ECR
    * EC2
    * S3
- Security Groups
    * Endpoint SG (Open all)
    * EKS Cluster SG (Access b/w control plane & Worker nodes)
  

    Learn TF with EKS : git clone https://github.com/hashicorp/learn-terraform-provision-eks-cluster
    
    Graph visualiser for terraform : 
    Clone : https://github.com/im2nguyen/rover
    Run : docker run --rm -it -p 9000:9000 -v $(pwd):/src im2nguyen/rover

