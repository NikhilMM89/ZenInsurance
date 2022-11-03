# ecs-terraform


This repo consists of a simple node js application, containerized using Docker and deployed to AWS ECS

## Set of folders:
./src: Containing Source Code and Docker file

./terraform: IAC configuration

./.github: Pipeline scripts

Functionality:

Terraform: 
Consists of 2 modules
- Creation of ECS cluster(creates a VPC if not created) using EC2 instances
- Creation of ALB and creation of target group to expose the service of ECS cluster later.

Github Workflow
Consists of 2 files
- terraform_workflow.yaml which observes the changes in ./terraform folder and makes the changes to infrastructure
- deploy_workflow.yaml which observes changes in ./src folder and builds the image pushes to ECR repo and deploy to ECS cluster.

Terraform commands on Manual run locally

1.terraform init

2.terraform workspace new dev

3.terraform plan --var-file .\environments\dev.tfvars

4.terraform apply --var-file .\environments\dev.tfvars --auto-approve

TO destroy:

1.terraform destroy --var-file .\environments\dev.tfvars --auto-approve

Note:--auto-approve is used when u dont wnat to answer confirmation prompt
# CodeBuild
