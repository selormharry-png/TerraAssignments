# TerraAssignments

## Overview

This repository contains a Terraform assignment that provisions a simple AWS network and compute environment. It creates a VPC with one public subnet, one private subnet, route tables, an internet gateway, a security group, and an EC2 instance.

## What it provisions

- AWS VPC (`aws_vpc.selorm_vpc`)
- Internet Gateway (`aws_internet_gateway.igw`)
- Public subnet (`aws_subnet.public_subnet`)
- Private subnet (`aws_subnet.private_subnet`)
- Public route table with internet route (`aws_route_table.public_rt`)
- Private route table (`aws_route_table.private_rt`)
- Route table associations for public and private subnets
- Security group allowing SSH and HTTP ingress
- EC2 instance in the public subnet

## Files

- `main.tf` - Core Terraform configuration and AWS resource definitions
- `variables.tf` - Input variables with default values
- `output.tf` - Terraform outputs for created resources
- `provider.tf` - Present in the repository but currently empty
- `terraform.tfstate` - Terraform state file generated after apply
- `.terraform.lock.hcl` - Provider dependency lock file
- `Asignment.pdf` - Assignment description or specification document

## Requirements

- Terraform 1.x
- AWS credentials configured in your environment (for example via `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` or shared credentials file)
- AWS provider version `6.55.0`

## Usage

1. Initialize Terraform:

   ```bash
   terraform init
   ```

2. Review the execution plan:

   ```bash
   terraform plan
   ```

3. Apply the configuration:

   ```bash
   terraform apply
   ```

4. Destroy the infrastructure when finished:

   ```bash
   terraform destroy
   ```

## Variables

The configuration exposes the following variables with defaults:

- `aws_region` - AWS region to deploy into (`eu-north-1`)
- `vpc_cidr` - CIDR block for the VPC (`10.0.0.0/16`)
- `public_subnet_cidr` - CIDR block for the public subnet (`10.0.1.0/24`)
- `private_subnet_cidr` - CIDR block for the private subnet (`10.0.2.0/24`)
- `instance_type` - EC2 instance type (`t3.micro`)

## Outputs

- `vpc_id` - ID of the created VPC
- `ec2_public_ip` - Public IP address of the EC2 instance
- `security_group_id` - ID of the EC2 instance security group

## Notes

- The EC2 instance AMI is hard-coded in `main.tf` as `ami-0aba19e56f3eaec05`.
- The public subnet is configured to assign public IP addresses automatically.
- The private subnet has no internet route, keeping it isolated within the VPC.

---

> This README is intended to document the Terraform work in the `TerraAssignments` repository and help users understand and run the configuration.
