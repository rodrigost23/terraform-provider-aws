---
subcategory: "CloudFront"
layout: "aws"
page_title: "AWS: aws_cloudfront_realtime_log_config"
description: |-
  Provides a CloudFront real-time log configuration resource.
---


<!-- Please do not edit this file, it is generated. -->
# Resource: aws_cloudfront_realtime_log_config

Provides a CloudFront real-time log configuration resource.

## Example Usage

```typescript
// DO NOT EDIT. Code generated by 'cdktf convert' - Please report bugs at https://cdk.tf/bug
import { Construct } from "constructs";
import { Token, TerraformStack } from "cdktf";
/*
 * Provider bindings are generated by running `cdktf get`.
 * See https://cdk.tf/provider-generation for more details.
 */
import { CloudfrontRealtimeLogConfig } from "./.gen/providers/aws/cloudfront-realtime-log-config";
import { DataAwsIamPolicyDocument } from "./.gen/providers/aws/data-aws-iam-policy-document";
import { IamRole } from "./.gen/providers/aws/iam-role";
import { IamRolePolicy } from "./.gen/providers/aws/iam-role-policy";
class MyConvertedCode extends TerraformStack {
  constructor(scope: Construct, name: string) {
    super(scope, name);
    const assumeRole = new DataAwsIamPolicyDocument(this, "assume_role", {
      statement: [
        {
          actions: ["sts:AssumeRole"],
          effect: "Allow",
          principals: [
            {
              identifiers: ["cloudfront.amazonaws.com"],
              type: "Service",
            },
          ],
        },
      ],
    });
    const example = new DataAwsIamPolicyDocument(this, "example", {
      statement: [
        {
          actions: [
            "kinesis:DescribeStreamSummary",
            "kinesis:DescribeStream",
            "kinesis:PutRecord",
            "kinesis:PutRecords",
          ],
          effect: "Allow",
          resources: [Token.asString(awsKinesisStreamExample.arn)],
        },
      ],
    });
    const awsIamRoleExample = new IamRole(this, "example_2", {
      assumeRolePolicy: Token.asString(assumeRole.json),
      name: "cloudfront-realtime-log-config-example",
    });
    /*This allows the Terraform resource name to match the original name. You can remove the call if you don't need them to match.*/
    awsIamRoleExample.overrideLogicalId("example");
    const awsIamRolePolicyExample = new IamRolePolicy(this, "example_3", {
      name: "cloudfront-realtime-log-config-example",
      policy: Token.asString(example.json),
      role: Token.asString(awsIamRoleExample.id),
    });
    /*This allows the Terraform resource name to match the original name. You can remove the call if you don't need them to match.*/
    awsIamRolePolicyExample.overrideLogicalId("example");
    const awsCloudfrontRealtimeLogConfigExample =
      new CloudfrontRealtimeLogConfig(this, "example_4", {
        dependsOn: [awsIamRolePolicyExample],
        endpoint: {
          kinesisStreamConfig: {
            roleArn: Token.asString(awsIamRoleExample.arn),
            streamArn: Token.asString(awsKinesisStreamExample.arn),
          },
          streamType: "Kinesis",
        },
        fields: ["timestamp", "c-ip"],
        name: "example",
        samplingRate: 75,
      });
    /*This allows the Terraform resource name to match the original name. You can remove the call if you don't need them to match.*/
    awsCloudfrontRealtimeLogConfigExample.overrideLogicalId("example");
  }
}

```

## Argument Reference

This resource supports the following arguments:

* `endpoint` - (Required) The Amazon Kinesis data streams where real-time log data is sent.
* `fields` - (Required) The fields that are included in each real-time log record. See the [AWS documentation](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/real-time-logs.html#understand-real-time-log-config-fields) for supported values.
* `name` - (Required) The unique name to identify this real-time log configuration.
* `samplingRate` - (Required) The sampling rate for this real-time log configuration. The sampling rate determines the percentage of viewer requests that are represented in the real-time log data. An integer between `1` and `100`, inclusive.

The `endpoint` object supports the following:

* `kinesisStreamConfig` - (Required) The Amazon Kinesis data stream configuration.
* `streamType` - (Required) The type of data stream where real-time log data is sent. The only valid value is `Kinesis`.

The `kinesisStreamConfig` object supports the following:

* `roleArn` - (Required) The ARN of an [IAM role](iam_role.html) that CloudFront can use to send real-time log data to the Kinesis data stream.
See the [AWS documentation](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/real-time-logs.html#understand-real-time-log-config-iam-role) for more information.
* `streamArn` - (Required) The ARN of the [Kinesis data stream](kinesis_stream.html).

## Attribute Reference

This resource exports the following attributes in addition to the arguments above:

* `id` - The ID of the CloudFront real-time log configuration.
* `arn` - The ARN (Amazon Resource Name) of the CloudFront real-time log configuration.

## Import

In Terraform v1.5.0 and later, use an [`import` block](https://developer.hashicorp.com/terraform/language/import) to import CloudFront real-time log configurations using the ARN. For example:

```typescript
// DO NOT EDIT. Code generated by 'cdktf convert' - Please report bugs at https://cdk.tf/bug
import { Construct } from "constructs";
import { TerraformStack } from "cdktf";
class MyConvertedCode extends TerraformStack {
  constructor(scope: Construct, name: string) {
    super(scope, name);
  }
}

```

Using `terraform import`, import CloudFront real-time log configurations using the ARN. For example:

```console
% terraform import aws_cloudfront_realtime_log_config.example arn:aws:cloudfront::111122223333:realtime-log-config/ExampleNameForRealtimeLogConfig
```

<!-- cache-key: cdktf-0.20.0 input-be02677fb3ad25ac1055ce131b85e8c78a124b0a2ec359c977c007200fc38e11 -->