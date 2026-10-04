# Terraform AWS VPC Infrastructure

## Overview

This project provisions a basic AWS VPC networking infrastructure with:

- A custom VPC
- Public and private subnets
- Internet Gateway
- Public route table
- Route table associations for public subnets

The infrastructure provides a foundation for deploying AWS resources such as EC2 instances and other services in a structured public/private network architecture.

## Usage

```hcl
module "my-vpc" {
  source = "module url"

  vpc_config = {
    cidr_block = "10.0.0.0/16"
    name       = "your-vpc-name"
  }

  subnet_config = {
    public-subnet = {
      cidr_block = "10.0.1.0/24"
      az         = "us-east-1a"

      # Set public = true to make this a public subnet
      public = true
    }

    private-subnet = {
      cidr_block = "10.0.2.0/24"
      az         = "us-east-1b"

      # Set public = false for a private subnet
      public = false
    }
  }
}
```

### Notes

- `vpc_config` defines the VPC name and CIDR block.
- `subnet_config` defines the subnet CIDR, Availability Zone, and whether the subnet is public.
- Set `public = true` for a public subnet.
- Set `public = false` for a private subnet.
- Make sure subnet CIDR blocks do not overlap.
