# Query Data Sources (App)
In this tutorial, you will use Terraform to deploy a workspace containing a VPC and security groups on AWS in the `us-east-1` region. Next, you will use the `aws_availability_zones` data source to configure your VPC's Availability Zones (AZs), allowing you to deploy this configuration in any AWS region. Then, you will use the `terraform_remote_state` data source to deploy another workspace containing your application infrastructure to your VPC. Finally, you will use the `aws_ami` data source to configure the correct AMI for the current region.

### Configure Terraform remote state
- Add a `terraform_remote_state` data source to the `main.tf` file.
- Replace the hard-coded region configuration in `main.tf` with the region output from the VPC workspace.
- Configure the load balancer security group and subnet arguments with the corresponding outputs from your VPC workspace.

### Scale EC2 instances
- The configuration in `main.tf` only uses a single EC2 instance.
- Update the configuration to use multiple EC2 instances per subnet.

### Configure region-specific AMIs
- Use an `aws_ami` data source to load the correct AMI ID for the current region. Add the following to `main.tf`.
- Replace the hard-coded AMI ID with the one loaded from the new data source.

### Configure EC2 subnet and security groups
- Update the EC2 instance configuration to use the subnet and security group configuration *from the VPC workspace*.
- `terrform init`
- `terraform apply`
- After a few minutes, the load balancer health checks will pass, and will return the example response.
- `curl $(terraform output -raw lb_url)`

> Note: You must destroy the application workspace before the VPC workspace. Since the resources in the application workspace depend on those in the VPC workspace, the AWS API will return an error if you attempt to destroy the VPC first.

### Reference
https://learn.hashicorp.com/tutorials/terraform/data-sources
