# Query Data Sources (App)
In this tutorial, you will use Terraform to deploy a workspace containing a VPC and security groups on AWS in the `us-east-1` region. Next, you will use the `aws_availability_zones` data source to configure your VPC's Availability Zones (AZs), allowing you to deploy this configuration in any AWS region. Then, you will use the `terraform_remote_state` data source to deploy another workspace containing your application infrastructure to your VPC. Finally, you will use the `aws_ami` data source to configure the correct AMI for the current region.

### Configure Terraform remote state
- Add a `terraform_remote_state` data source to the `main.tf` file.
- Replace the hard-coded region configuration in `main.tf` with the region output from the VPC workspace.
- Configure the load balancer security group and subnet arguments with the corresponding outputs from your VPC workspace.

### Reference
https://learn.hashicorp.com/tutorials/terraform/data-sources
