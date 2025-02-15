---
subcategory: "ElastiCache"
layout: "aws"
page_title: "AWS: aws_elasticache_subnet_group"
description: |-
  Provides information about a ElastiCache Subnet Group.
---


<!-- Please do not edit this file, it is generated. -->
# Resource: aws_elasticache_subnet_group

Provides information about a ElastiCache Subnet Group.

## Example Usage

```typescript
// DO NOT EDIT. Code generated by 'cdktf convert' - Please report bugs at https://cdk.tf/bug
import { Construct } from "constructs";
import { TerraformStack } from "cdktf";
/*
 * Provider bindings are generated by running `cdktf get`.
 * See https://cdk.tf/provider-generation for more details.
 */
import { DataAwsElasticacheSubnetGroup } from "./.gen/providers/aws/data-aws-elasticache-subnet-group";
class MyConvertedCode extends TerraformStack {
  constructor(scope: Construct, name: string) {
    super(scope, name);
    new DataAwsElasticacheSubnetGroup(this, "example", {
      name: "my-subnet-group",
    });
  }
}

```

## Argument Reference

The following arguments are required:

* `name` - (Required) Name of the subnet group.

## Attribute Reference

This data source exports the following attributes in addition to the arguments above:

* `id` - Name of the subnet group.
* `arn` - ARN of the subnet group.
* `description` - Description of the subnet group.
* `subnetIds` - Set of VPC Subnet ID-s of the subnet group.
* `tags` - Map of tags assigned to the subnet group.

<!-- cache-key: cdktf-0.20.0 input-a10cc3d3cb3b8626a11dcf295b29f911836bff7d00ed1bca0e896ee84c058643 -->