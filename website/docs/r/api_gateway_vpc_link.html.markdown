---
layout: "aws"
page_title: "AWS: aws_api_gateway_vpc_link"
sidebar_current: "docs-aws-resource-api-gateway-vpc-link"
description: |-
  Provides an API Gateway VPC Link.
---

# aws_api_gateway_vpc_link

Provides an API Gateway VPC Link.

## Example Usage

```hcl
resource "aws_lb" "example" {
  name = "example"
  internal = true
  load_balancer_type = "network"

  subnet_mapping {
    subnet_id = "12345"
  }
}

resource "aws_api_gateway_vpc_link" "example" {
  name = "example"
  description = "example description"
  target_arns = ["${aws_lb.example.arn}"]
}
```

## Argument Reference

The following arguments are supported:

* `name` - (Required) The name used to label and identify the VPC link.
* `description` - (Optional) The description of the VPC link.
* `target_arns` - (Required, ForceNew) The list of network load balancer arns in the VPC targeted by the VPC link. Currently AWS only supports 1 target.

## Attributes Reference

The following attributes are exported:

* `id` - The identifier of the VpcLink.
