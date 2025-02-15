---
subcategory: "EventBridge"
layout: "aws"
page_title: "AWS: aws_cloudwatch_event_connection"
description: |-
  Provides an EventBridge connection data source.
---


<!-- Please do not edit this file, it is generated. -->
# Data Source: aws_cloudwatch_event_connection

Use this data source to retrieve information about an EventBridge connection.

~> **Note:** EventBridge was formerly known as CloudWatch Events. The functionality is identical.

## Example Usage

```typescript
// DO NOT EDIT. Code generated by 'cdktf convert' - Please report bugs at https://cdk.tf/bug
import { Construct } from "constructs";
import { TerraformStack } from "cdktf";
/*
 * Provider bindings are generated by running `cdktf get`.
 * See https://cdk.tf/provider-generation for more details.
 */
import { DataAwsCloudwatchEventConnection } from "./.gen/providers/aws/data-aws-cloudwatch-event-connection";
class MyConvertedCode extends TerraformStack {
  constructor(scope: Construct, name: string) {
    super(scope, name);
    new DataAwsCloudwatchEventConnection(this, "test", {
      name: "test",
    });
  }
}

```

## Argument Reference

* `name` - Name of the connection.

## Attribute Reference

This data source exports the following attributes in addition to the arguments above:

* `name` - Name of the connection.

* `arn` - ARN (Amazon Resource Name) for the connection.

* `secretArn` - ARN (Amazon Resource Name) for the secret created from the authorization parameters specified for the connection.

* `authorizationType` - Type of authorization to use to connect. One of `API_KEY`,`BASIC`,`OAUTH_CLIENT_CREDENTIALS`.

<!-- cache-key: cdktf-0.20.0 input-c28a6e87c62c9016e5553ac80ba81f240b8c76ab8a07aa2ea802508e58427f58 -->