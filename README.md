# aws-marketplace-evaluation

If you are beginning your journey with [Senzing],
please start with [Senzing Quick Start guides].

You are in the [Senzing Garage]
where projects are "tinkered" on.
Although this GitHub repository may help you understand an approach to using Senzing,
it's not considered to be "production ready" and is not considered to be part of the Senzing product.
Heck, it may not even be appropriate for your application of Senzing!

## Synopsis

The `aws-marketplace-evaluation` repo contains two AWS Cloudformation templates
to deploy Senzing. These templates rely on an AWS Marketplace subscription to install.
To deploy Senzing without a Marketplace subscription take a look at our [Web App Demo Repo].

This stack provides a web application interface to the senzing engine. It allows
records to be loaded and entities and their connections explored through the web
application.

For additional information, see [Senzing Evaluation Edition on AWS].

## How to deploy without much thinking

For more details, see [details of deployment].

1. :warning: **Warning:**
   This Cloudformation deployment will accrue AWS costs.
   With appropriate permissions, the [AWS Cost Explorer]
   can help evaluate costs.
1. :warning: **Warning:**
   This Cloudformation deployment only runs in [supported AWS Regions].

## Install the Database Stack

1. Download the Database Stack [AWS Cloudformation template example] from this repository to your local device. Example:

   ```console
   curl -X GET \
       --output ~/cloudformation.yaml \
       https://raw.githubusercontent.com/Senzing/aws-marketplace-evaluation/main/cloudformation-senzing-database.yaml
   ```

1. It is highly suggested to take a look at the AWS Cloudformation Template that has been downloaded. This template is an example that deploys and configures a number of services and facilities. While it is a working example, each business may have different requirements and their account may not have all the privileges required to deploy it. Furthermore, the examples change over time and these files are meant to be treated as code files so they should be put under source control.
1. Visit the [AWS Cloudformation home].
1. At the upper-right, click the "Create stack" drop-down and choose "With new resources (standard)".
1. In the "Specify template" area choose the "Upload a template file" radio button.
1. Select the "Choose file" button and choose the AWS Cloudformation template that was downloaded previously.
1. At lower-right, click on "Next" button.
1. In **Specify stack details**
   1. In **Stack name**
      1. Choose a stack name that is unique to you and 21 characters or less. (Several resource types have a limit of 32 character names. The CFT uses the stack name and an 11 character suffix to name resources uniquely.)
   1. In **Parameters**
      1. In **Senzing installation**
         1. If you plan on loading billions of records, choose "Multiple".
         1. Otherwise, choose "Single".
      1. In **Security responsibility**
         1. Understand the nature of the security in the deployment.
         1. Once understood, enter "I AGREE".
   1. At lower-right, click "Next" button.
1. In **Configure stack options**
   1. At lower-right, click "Next" button.
1. In **Review senzing database stack**
   1. Near the bottom, in **Capabilities**
      1. Check ":ballot_box_with_check: I acknowledge that AWS CloudFormation might create IAM resources."
   1. At lower-right, click "Create stack" button.

## Install the Basic Senzing Stack

1. Download the Basic Stack [AWS Cloudformation template senzing basic example] from this repository to your local device. Example:

   ```console
   curl -X GET \
       --output ~/cloudformation.yaml \
       https://raw.githubusercontent.com/Senzing/aws-marketplace-evaluation/main/cloudformation-senzing-basic.yaml
   ```

1. It is highly suggested to take a look at the AWS Cloudformation Template that has been downloaded. This template is an example that deploys and configures a number of services and facilities. While it is a working and complete example, each business may have different requirements and their account may not have all the privileges required to deploy it. Furthermore, the examples change over time and these files are meant to be treated as code files so they should be put under source control.
1. Visit the [AWS Cloudformation home].
1. At the upper-right, click the "Create stack" drop-down and choose "With new resources (standard)".
1. In the "Specify template" area choose the "Upload a template file" radio button.
1. Select the "Choose file" button and choose the AWS Cloudformation template that was downloaded previously.
1. At lower-right, click on "Next" button.
1. In **Specify stack details**
   1. In **Stack name**
      1. Choose a stack name that is unique to you and 21 characters or less. (Several resource types have a limit of 32 character names. The CFT uses the stack name and an 11 character suffix to name resources uniquely.)
   1. In **Parameters**
      1. In **Senzing installation**
         1. Accept the End User License Agreement.
         1. Optionally, choose a version of Senzing to install.
         1. Optionally, add a license string.
      1. In **Identify existing resources**
         1. Enter the stack name of the previously deployed Database Cloudformation stack.
            Example: `senzing-db`
      1. In **Security**
         1. Provide the email address for the administrative user. Example: `me@example.com`
         1. Provide the permitted IP address block allowed to connect using CIDR notation. Note: to open the installation to any IP address use: `0.0.0.0/0`. For more on CIDR, see [Classless Inter-Domain Routing]
      1. In **Security responsibility**
         1. Understand the nature of the security in the deployment.
         1. Once understood, enter "I AGREE".
   1. At lower-right, click "Next" button.
1. In **Configure stack options**
   1. At lower-right, click "Next" button.
1. In **Review senzing stack**
   1. Near the bottom, in **Capabilities**
      1. Check ":ballot_box_with_check: I acknowledge that AWS CloudFormation might create IAM resources."
   1. At lower-right, click "Create stack" button.

## Additional topics

1. [Details of deployment]
1. [How to load AWS Cloudformation queue]

## Security

### Permissions

1. Overall
   1. application-autoscaling:DeleteScalingPolicy
   1. application-autoscaling:DeregisterScalableTarget
   1. application-autoscaling:DescribeScalableTargets
   1. application-autoscaling:DescribeScalingPolicies
   1. application-autoscaling:PutScalingPolicy
   1. application-autoscaling:RegisterScalableTarget
   1. cognito-idp:CreateUserPool
   1. cognito-idp:CreateUserPoolClient
   1. cognito-idp:CreateUserPoolDomain
   1. cognito-idp:DeleteUserPool
   1. cognito-idp:DeleteUserPoolClient
   1. cognito-idp:DeleteUserPoolDomain
   1. cognito-idp:DescribeUserPoolClient
   1. ec2:AllocateAddress
   1. ec2:AssociateRouteTable
   1. ec2:AttachInternetGateway
   1. ec2:AuthorizeSecurityGroupEgress
   1. ec2:AuthorizeSecurityGroupIngress
   1. ec2:CreateInternetGateway
   1. ec2:CreateNatGateway
   1. ec2:CreateNetworkInterface
   1. ec2:CreateRoute
   1. ec2:CreateRouteTable
   1. ec2:CreateSecurityGroup
   1. ec2:CreateSubnet
   1. ec2:CreateTags
   1. ec2:CreateVpc
   1. ec2:CreateVpcEndpoint
   1. ec2:DeleteInternetGateway
   1. ec2:DeleteNatGateway
   1. ec2:DeleteNetworkInterface
   1. ec2:DeleteRoute
   1. ec2:DeleteRouteTable
   1. ec2:DeleteSecurityGroup
   1. ec2:DeleteSubnet
   1. ec2:DeleteVpc
   1. ec2:DeleteVpcEndpoints
   1. ec2:DescribeAccountAttributes
   1. ec2:DescribeAddresses
   1. ec2:DescribeAvailabilityZones
   1. ec2:DescribeInternetGateways
   1. ec2:DescribeNatGateways
   1. ec2:DescribeRouteTables
   1. ec2:DescribeSecurityGroups
   1. ec2:DescribeSubnets
   1. ec2:DescribeVpcs
   1. ec2:DetachInternetGateway
   1. ec2:DisassociateRouteTable
   1. ec2:ModifyVpcAttribute
   1. ec2:ReleaseAddress
   1. ec2:ReplaceRouteTableAssociation
   1. ec2:RevokeSecurityGroupEgress
   1. ec2:RevokeSecurityGroupIngress
   1. ecs:CreateCluster
   1. ecs:CreateService
   1. ecs:DeleteCluster
   1. ecs:DeleteService
   1. ecs:DeregisterTaskDefinition
   1. ecs:DescribeClusters
   1. ecs:DescribeServices
   1. ecs:DescribeTaskDefinition
   1. ecs:RegisterTaskDefinition
   1. ecs:RunTask
   1. ecs:UpdateService
   1. elasticfilesystem:CreateFileSystem
   1. elasticfilesystem:CreateMountTarget
   1. elasticfilesystem:DeleteFileSystem
   1. elasticfilesystem:DeleteMountTarget
   1. elasticfilesystem:DescribeBackupPolicy
   1. elasticfilesystem:DescribeFileSystemPolicy
   1. elasticfilesystem:DescribeFileSystems
   1. elasticfilesystem:DescribeLifecycleConfiguration
   1. elasticfilesystem:DescribeMountTargets
   1. elasticloadbalancing:\*
   1. iam:AttachRolePolicy
   1. iam:CreateRole
   1. iam:CreateServiceLinkedRole
   1. iam:DeleteRole
   1. iam:DeleteRolePolicy
   1. iam:DeleteServerCertificate
   1. iam:DetachRolePolicy
   1. iam:GetRole
   1. iam:GetRolePolicy
   1. iam:GetServerCertificate
   1. iam:ListServerCertificateTags
   1. iam:ListServerCertificates
   1. iam:PassRole
   1. iam:PutRolePolicy
   1. iam:TagRole
   1. iam:TagServerCertificate
   1. iam:UntagRole
   1. iam:UntagServerCertificate
   1. iam:UpdateServerCertificate
   1. iam:UploadServerCertificate
   1. lambda:CreateFunction
   1. lambda:DeleteFunction
   1. lambda:GetFunction
   1. lambda:GetFunctionConfiguration
   1. lambda:InvokeFunction
   1. logs:CreateLogGroup
   1. logs:CreateLogStream
   1. logs:DeleteLogGroup
   1. logs:DescribeLogGroups
   1. logs:DescribeLogStreams
   1. logs:GetLogEvents
   1. logs:GetLogGroupFields
   1. logs:GetLogRecord
   1. rds:AddTagsToResource
   1. rds:CreateDBCluster
   1. rds:CreateDBClusterParameterGroup
   1. rds:CreateDBClusterSnapshot
   1. rds:CreateDBSnapshot
   1. rds:CreateDBSubnetGroup
   1. rds:DeleteDBCluster
   1. rds:DeleteDBClusterParameterGroup
   1. rds:DeleteDBClusterSnapshot
   1. rds:DeleteDBSnapshot
   1. rds:DeleteDBSubnetGroup
   1. rds:DescribeDBClusterParameters
   1. rds:DescribeDBClusterSnapshots
   1. rds:DescribeDBClusters
   1. rds:DescribeDBSubnetGroups
   1. rds:ModifyDBClusterParameterGroup
   1. route53:AssociateVPCWithHostedZone
   1. s3:GetObject
   1. sqs:CreateQueue
   1. sqs:DeleteQueue
   1. sqs:GetQueueAttributes
   1. sqs:TagQueue
   1. ssm:AddTagsToResource
   1. ssm:DeleteParameter
   1. ssm:DescribeParameters
   1. ssm:GetParameter
   1. ssm:GetParameters
   1. ssm:ListTagsForResource
   1. ssm:PutParameter
   1. ssm:RemoveTagsFromResource
1. `cloudformation-senzing-database.yaml` Cloudformation template
   1. ecr:BatchCheckLayerAvailability
   1. ecr:BatchGetImage
   1. ecr:GetAuthorizationToken
   1. ecr:GetDownloadUrlForLayer
   1. ecs:DescribeTasks
   1. ecs:RunTask
   1. iam:PassRole
   1. logs:CreateLogStream
   1. logs:PutLogEvents
   1. rds:ModifyDBCluster
1. `cloudformation-senzing-basic.yaml` Cloudformation template:
   1. acm:ListCertificates
   1. cognito-idp:AdminCreateUser
   1. ec2:DescribeSubnets
   1. ecr:BatchCheckLayerAvailability
   1. ecr:BatchGetImage
   1. ecr:GetAuthorizationToken
   1. ecr:GetDownloadUrlForLayer
   1. ecs:DescribeTasks
   1. ecs:RunTask
   1. elasticfilesystem:DescribeFileSystems
   1. elasticfilesystem:DescribeMountTargets
   1. iam:PassRole
   1. iam:UploadServerCertificate
   1. logs:CreateLogGroup
   1. logs:CreateLogStream
   1. logs:DescribeLogGroups
   1. logs:DescribeLogStreams
   1. logs:PutLogEvents
   1. route53:GetHostedZone
   1. sqs:DeleteMessage
   1. sqs:GetQueueAttributes
   1. sqs:ReceiveMessage
   1. sqs:SendMessage

[AWS Cloudformation home]: https://console.aws.amazon.com/cloudformation/home
[AWS Cloudformation template example]: cloudformation-senzing-database.yaml
[AWS Cloudformation template senzing basic example]: cloudformation-senzing-basic.yaml
[AWS Cost Explorer]: https://aws.amazon.com/aws-cost-management/aws-cost-explorer/
[Classless Inter-Domain Routing]: https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing
[details of deployment]: docs/README.md
[How to load AWS Cloudformation queue]: https://github.com/senzing-garage/knowledge-base/blob/main/HOWTO/load-aws-cloudformation-queue.md
[Senzing]: https://senzing.com/
[Senzing Evaluation Edition on AWS]: https://docs.senzing.com/aws_marketplace/
[Senzing Garage]: https://github.com/senzing-garage
[Senzing Quick Start guides]: https://docs.senzing.com/quickstart/
[supported AWS Regions]: https://github.com/senzing-garage/knowledge-base/blob/main/lists/aws-supported-regions.md
[Web App Demo Repo]: https://github.com/senzing-garage/aws-cloudformation-webapp-demo
