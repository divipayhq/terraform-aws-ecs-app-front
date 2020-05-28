# terraform-aws-ecs-app-front

[![Lint Status](https://github.com/DNXLabs/terraform-aws-ecs-app-front/workflows/Lint/badge.svg)](https://github.com/DNXLabs/terraform-aws-ecs-app-front/actions)
[![LICENSE](https://img.shields.io/github/license/DNXLabs/terraform-aws-ecs-app-front)](https://github.com/DNXLabs/terraform-aws-ecs-app-front/blob/master/LICENSE)

AWS ECS Application Module (frontend component)

This module is designed to be used with `DNXLabs/terraform-aws-ecs` and `DNXLabs/terraform-aws-ecs-app`.

<!--- BEGIN_TF_DOCS --->
## Requirements

| Name | Version |
|------|---------|
| terraform | >= 0.12.20 |

## Providers

| Name | Version |
|------|---------|
| aws | n/a |
| aws.us-east-1 | n/a |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| alarm\_cloudfront\_500\_errors\_threshold | Cloudfront 500 Errors rate threshold (use 0 to disable this alarm) | `number` | `5` | no |
| alarm\_sns\_topics\_us | Alarm topics to create and alert on metrics on US region | `list` | `[]` | no |
| alb\_cloudfront\_key | Key generated by terraform-aws-ecs module to allow ALB connection from CloudFront | `any` | n/a | yes |
| alb\_dns\_name | ALB DNS Name that CloudFront will point as origin | `any` | n/a | yes |
| certificate\_arn | Certificate for this app to use in CloudFront (US), must cover `hostname`. | `any` | n/a | yes |
| cloudfront\_forward\_headers | Headers to forward to origin from CloudFront | `list` | <pre>[<br>  "*"<br>]</pre> | no |
| cloudfront\_logging\_bucket | Bucket to store logs from app | `string` | `null` | no |
| cloudfront\_logging\_prefix | Logging prefix | `string` | `""` | no |
| cloudfront\_origin\_keepalive\_timeout | The amount of time, in seconds, that CloudFront maintains an idle connection with a custom origin server before closing the connection. Valid values are from 1 to 60 seconds. | `number` | `5` | no |
| cloudfront\_origin\_read\_timeout | The amount of time, in seconds, that CloudFront waits for a response from a custom origin. The value applies both to the time that CloudFront waits for an initial response and the time that CloudFront waits for each subsequent packet. Valid values are from 4 to 60 seconds. | `number` | `30` | no |
| cloudfront\_web\_acl\_id | Optional web acl (WAF) to attach to CloudFront | `string` | `""` | no |
| cluster\_name | Name of existing ECS Cluster to deploy this app to | `any` | n/a | yes |
| dynamic\_custom\_origin\_config | Configuration for the custom origin config to be used in dynamic block | `any` | `[]` | no |
| dynamic\_ordered\_cache\_behavior | Ordered Cache Behaviors to be used in dynamic block | `any` | `[]` | no |
| hosted\_zone | Existing Hosted Zone domain to add hostnames as DNS records | `any` | n/a | yes |
| hostname | Hostname to create DNS record for this app | `any` | n/a | yes |
| hostname\_create | Create hostname in the hosted zone passed? | `bool` | `true` | no |
| hostname\_redirects | List of hostnames to redirect to the main one, comma-separated | `string` | `""` | no |
| iam\_certificate\_id | Specifies IAM certificate id for CloudFront distribution | `string` | `null` | no |
| minimum\_protocol\_version | The minimum version of the SSL protocol that you want CloudFront to use for HTTPS connections. <br>    One of SSLv3, TLSv1, TLSv1\_2016, TLSv1.1\_2016 or TLSv1.2\_2018. Default: TLSv1.2\_2018. <br>    NOTE: If you are using a custom certificate (specified with acm\_certificate\_arn or iam\_certificate\_id), <br>    and have specified sni-only in ssl\_support\_method, TLSv1 or later must be specified. <br>    If you have specified vip in ssl\_support\_method, only SSLv3 or TLSv1 can be specified. <br>    If you have specified cloudfront\_default\_certificate, TLSv1 must be specified. | `string` | `"TLSv1.2_2018"` | no |
| name | Name of your ECS service | `any` | n/a | yes |
| restriction\_location | The ISO 3166-1-alpha-2 codes for which you want CloudFront either to distribute your content (whitelist) or not distribute your content (blacklist) | `list` | `[]` | no |
| restriction\_type | The restriction type of your CloudFront distribution geolocation restriction. Options include none, whitelist, blacklist | `string` | `"none"` | no |

## Outputs

| Name | Description |
|------|-------------|
| cloudfront\_distribution\_hostname | The hostname of the CloudFront Distribution (use for DNS CNAME). |
| cloudfront\_distribution\_id | The ID of the CloudFront Distribution. |
| cloudfront\_zone\_id | The Zone ID of the CloudFront Distribution (use for DNS Alias). |

<!--- END_TF_DOCS --->


## Authors

Module managed by [DNX Solutions](https://github.com/DNXLabs).

## License

Apache 2 Licensed. See [LICENSE](https://github.com/DNXLabs/terraform-aws-ecs-app-front/blob/master/LICENSE) for full details.