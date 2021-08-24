# aws-marketplace-evaluation

## Synopsis

The
[aws-cloudformation-database-cluster](https://github.com/Senzing/aws-cloudformation-database-cluster)
AWS Cloudformation template creates an AWS VPC
and Aurora Postgres serverless database deployment.
The Cloudformation does not deploy Senzing.
Rather, it deploys a database than can be used by other AWS Cloudformations
which do deploy Senzing such as
[aws-cloudformation-ecs-senzing-stack-basic](https://github.com/Senzing/aws-cloudformation-ecs-senzing-stack-basic).

## Overview

The `aws-cloudformation-database-cluster` AWS Cloudformation template creates the following resources:

1. AWS infrastructure
    1. VPC
    1. Subnets
    1. IP address and NAT Gateway
    1. Internet Gateway
    1. Routes
    1. IAM Roles and Policies
    1. Security Groups
    1. Logging
1. AWS services
    1. AWS Relational Data Service (RDS) Aurora Postgres Serverless

The following diagram shows a simplified representation of this deployment.

![Image of architecture](architecture.png)

GitHub repository for
[aws-cloudformation-database-cluster](https://github.com/Senzing/aws-cloudformation-database-cluster).

### Contents

1. [Preamble](#preamble)
    1. [Legend](#legend)
1. [Expectations](#expectations)
1. [Demonstrate using AWS Console](#demonstrate-using-aws-console)
1. [Using deployment](#using-deployment)
1. [Additional topics](#additional-topics)
1. [Parameters](#parameters)
1. [Outputs](#outputs)

## Preamble

At [Senzing](http://senzing.com),
we strive to create GitHub documentation in a
"[don't make me think](https://github.com/Senzing/knowledge-base/blob/master/WHATIS/dont-make-me-think.md)" style.
For the most part, instructions are copy and paste.
Whenever thinking is needed, it's marked with a "thinking" icon :thinking:.
Whenever customization is needed, it's marked with a "pencil" icon :pencil2:.
If the instructions are not clear, please let us know by opening a new
[Documentation issue](https://github.com/Senzing/aws-marketplace-evaluation/issues/new?template=documentation_request.md)
describing where we can improve.   Now on with the show...

### Legend

1. :thinking: - A "thinker" icon means that a little extra thinking may be required.
   Perhaps there are some choices to be made.
   Perhaps it's an optional step.
1. :pencil2: - A "pencil" icon means that the instructions may need modification before performing.
1. :warning: - A "warning" icon means that something tricky is happening, so pay attention.

## Expectations

- **Time:** Budget 40 minutes to get the demonstration up-and-running.
- **Background knowledge:** This repository assumes a working knowledge of:
  - [AWS Cloudformation](https://github.com/Senzing/knowledge-base/blob/master/WHATIS/aws-cloudformation.md)

## Demonstrate using AWS Console

### Launch AWS Cloudformation

1. :warning: **Warning:** This Cloudformation deployment will accrue AWS costs.
   With appropriate permissions, the
   [AWS Cost Explorer](https://aws.amazon.com/aws-cost-management/aws-cost-explorer/)
   can help evaluate costs.
1. Visit [AWS Cloudformation with Senzing template](https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=senzing-db&templateURL=https://s3.amazonaws.com/public-read-access/aws-cloudformation-database-cluster/cloudformation.yaml)
1. At lower-right, click on "Next" button.
1. In **Specify stack details**
    1. In **Parameters**
        1. In **Senzing installation**
            1. If speed is desired over lower cost, choose "Multiple".
            1. If lower cost is desired over speed, choose "Single".
        1. In **Security responsibility**
            1. Understand the nature of the security in the deployment.
            1. Once understood, enter "I AGREE".
    1. At lower-right, click "Next" button.
1. In **Configure stack options**
    1. At lower-right, click "Next" button.
1. In **Review senzing-db**
    1. Near the bottom, in **Capabilities**
        1. Check ":ballot_box_with_check: I acknowledge that AWS CloudFormation might create IAM resources."
    1. At lower-right, click "Create stack" button.

## Using deployment

1. By itself, this deployment doesn't do much.
   It is simply the database deployment to be used by subsequent Cloudformations.
1. Example subsequent deployments:
    1. [aws-cloudformation-ecs-senzing-stack-basic](https://github.com/Senzing/aws-cloudformation-ecs-senzing-stack-basic)
    1. [aws-cloudformation-ecs-senzing-stack-choices](https://github.com/Senzing/aws-cloudformation-ecs-senzing-stack-choices)
    1. [aws-marketplace-evaluation](https://github.com/Senzing/aws-marketplace-evaluation)

## Additional topics

1. [How to migrate an AWS RDS database](https://github.com/Senzing/knowledge-base/blob/master/HOWTO/migrate-aws-rds-database.md)

### Review AWS Cloudformation

The AWS resources created by the
[cloudformation.yaml](https://github.com/Senzing/aws-cloudformation-database-cluster/blob/main/cloudformation.yaml)
template can be see in the [AWS Management Console](https://console.aws.amazon.com).

1. CloudFormation
    1. [Stacks](https://console.aws.amazon.com/cloudformation/home?#/stacks)
1. CloudWatch
    1. [Log groups](https://console.aws.amazon.com/cloudwatch/home?#logsV2:log-groups)
1. Elastic Compute Cloud (EC2)
    1. [Network interfaces](https://console.aws.amazon.com/ec2/v2/home?#NIC)
1. Identity and Access Management (IAM)
    1. [Roles](https://console.aws.amazon.com/iam/home?#/roles)
1. Relational Data Service (RDS)
    1. [Databases](https://console.aws.amazon.com/rds/home?#databases:)
    1. [Parameter groups](https://console.aws.amazon.com/rds/home?#parameter-groups:)
    1. [Subnet groups](https://console.aws.amazon.com/rds/home?#db-subnet-groups-list:)
1. Virtual Private Cloud (VPC)
    1. [Internet gateways](https://console.aws.amazon.com/vpc/home?#igws)
    1. [Network ACLs](https://console.aws.amazon.com/vpc/home?#acls)
    1. [Route Tables](https://console.aws.amazon.com/vpc/home?#RouteTables)
    1. [Security Groups](https://console.aws.amazon.com/vpc/home?#SecurityGroups)
    1. [Subnets](https://console.aws.amazon.com/vpc/home?#subnets)
    1. [VPCs](https://console.aws.amazon.com/vpc/home?#vpcs)

### View results

1. Visit [AWS Cloudformation console](https://console.aws.amazon.com/cloudformation/home).
1. Choose appropriate "Stack name"
1. Choose "Outputs" tab.
    1. For descriptions of outputs, visit [Outputs](#outputs) further down this page.

## Parameters

Technical information on AWS Cloudformation parameters can be seen at
[Parameters](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/parameters-section-structure.html).

### AcceptEula

1. **Synopsis:**
   To use the Senzing code, you must agree to the End User License Agreement (EULA).
   This step is intentionally tricky to ensure that you make a conscious effort to accept the EULA.
1. **Required:** Yes
1. **Type:** String
1. **Allowed values:** See [SENZING_ACCEPT_EULA](https://github.com/Senzing/knowledge-base/blob/master/lists/environment-variables.md#senzing_accept_eula).
1. **Default:** None
1. **Where used:**
    1. `cloudformation-senzing-basic.yaml`

### CidrInbound

1. **Synopsis:** A Classless Inter-Domain Routing
   ([CIDR](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing))
   value used to limit access to the system.
   This restricts the inbound traffic to requests from specified IP ranges.
   Examples:
    1. A system with the value `0.0.0.0/0` allows access from anywhere.
       Because of its "wide-open" nature, it is considered to be insecure.
    1. A system with the value `45.26.129.0/24` will allow access from IP addresses in the range `45.26.129.0` to `45.26.129.255`
    1. A system with the value `45.26.129.200/32` will allow access from a single IP address `45.26.129.200`.
1. **Required:** Yes
1. **Type:** String
1. **Allowed pattern:** Letters and numbers. Specifically: `'(?:\d{1,3}\.){3}\d{1,3}(?:/\d\d?)?'`
1. **Allowed values:** String in IPv4 [CIDR format](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing).
1. **Example:** 45.26.129.200/32
1. **Default:** None
1. **Where used:**
    1. `cloudformation-senzing-basic.yaml`

### CognitoAdminEmail

1. **Synopsis:**
   An email address of the person administrating this Cloudformation.
   The email address will be used when email is sent to additional users via the
   [AWS Cognito web console](https://console.aws.amazon.com/cognito/users/#/pool/u).
1. **Required:** Yes
1. **Type:** String
1. **Allowed values:**
    1. A string in email format.
1. **Example:** `me@example.com`
1. **Default:** None
1. **Where used:**
    1. `cloudformation-senzing-basic.yaml`

### DatabaseStack

1. **Synopsis:**
   The name of the cloudformation stack deployed with the
   [aws-cloudformation-database-cluster](https://github.com/Senzing/aws-cloudformation-database-cluster)
   cloudformation template.
   The DatabaseStack exported output values are used by the
   [aws-cloudformation-ecs-senzing-stack-basic](https://github.com/Senzing/aws-cloudformation-ecs-senzing-stack-basic).
1. **Required:** Yes
1. **Type:** String
1. **Example:** `senzing-db`
1. **Default:** None
1. **Where used:**
    1. `cloudformation-senzing-basic.yaml`

### MultipleDatabases

1. **Synopsis:**
   Choose single database or Senzing database cluster.
   For increased performance and/or high volume, choose "Multiple".
   For lower cost, choose "Single".
   For more information see:
   <https://senzing.zendesk.com/hc/en-us/articles/360010599254-Scaling-Out-Your-Database-With-Clustering>
1. **Required:** Yes
1. **Type:** Choice
1. **Allowed values:**
    1. "Multiple"
    2. "Single"
1. **Default:** Multiple
1. **Where used:**
    1. `cloudformation-database.yaml`

### SecurityResponsibility

1. **Synopsis:**
   The Senzing proof-of-concept AWS Cloudformation uses
   [AWS Cognito](https://aws.amazon.com/cognito/) for authentication,
   and HTTPS (using a self-signed certificate) for encrypted network traffic
   to expose services through a single, internet-facing AWS Elastic Load Balancer.
   With exception of the
   [senzing/sshd](https://github.com/Senzing/docker-sshd) container,
   no tasks in the AWS Elastic Container Service (ECS) have public IP addresses.

   To enable additional security measures for the deployment in your specific environment,
   you'll need to consult with your AWS administrator.
   Examples of additional security measures:
    - [AWS Route53](https://aws.amazon.com/route53/) with genuine X.509 certificate
    - [AWS Web Application Firewall (WAF)](https://aws.amazon.com/waf/)
    - [AWS Shield](https://aws.amazon.com/shield/)
    - [AWS Firewall Manager](https://aws.amazon.com/firewall-manager/)
    - [Amazon API Gateway](https://aws.amazon.com/api-gateway/)
    - Restrictive value for [CidrInbound](#cidrinbound)
1. **Required:** Yes
1. **Type:** String
1. **Allowed values:**
    1. "I AGREE"
1. **Default:** None
1. **Where used:**
    1. `cloudformation-database.yaml`
    1. `cloudformation-senzing-basic.yaml`

### SenzingLicenseAsBase64

1. **Synopsis:**
   To ingest more than 100,000 records, a Senzing license is required.
   A binary version of the Senzing license, `g2.lic`, is not usable as a parameter in the text entry field.
   Instead, a [Base64](https://en.wikipedia.org/wiki/Base64) representation of the information is needed.
   An example of how to produce base64 from `g2.lic` on Linux and macOS:

   ```console
   base64 /opt/senzing/etc/g2.lic
   ```

   Copy the entire output from the command and paste into the text entry field.
1. **Required:** Yes if ingesting more than 100,000 records, otherwise no.
1. **Type:** String
1. **Allowed pattern:** Empty or Base64 characters. Specifically `^$|[^-A-Za-z0-9+/=]|=[^=]|={3,}$`
1. **Allowed values:** Base64 encoded string
1. **Example:**

   ```console
   AQAAADgCAAAAAAAAU2VuemluZwAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
   AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
   AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
   AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
   AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAARGVtbyBFeHBpcmVkAAAAAAAA
   AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADIwMjAtMTItMTYA
   AAAAAAAAAAAARVZBTAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
   AAAAAAAAAAAAAAAAAAAAAFNUQU5EQVJEAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
   AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAKCGAQAAAAAAMTk3Ni0wMS0wMQAAAAAAAAAAAABN
   T05USExZAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
   AAAAAAAARkdIST5XYOZ90kbyAbU7wM7XvPCwq/FgORZIekwFMg8zi3tCD0V5+12q72aqk0E6JOct
   +cPAq/T50N5Pf5nvJZ6TaW3TzQbnH/z5f/ALsWLydE2DPNvq3HuAjkjZpg2h7mb4OUqorGxDI9RX
   TX8hPjzYrBfMdOgl1DlRBVG36WwdpB8AnSfaegbYU+U/vfof+ff6mJk8gzPg+OGPwg21/S6i2TT4
   RbTCSYP/TpfXyJGE6dbQWEC9rFhYuWq3mFF3z7zFEcmxpNfZuBtYsxni8P3sDZ706RA+wcQF7TVg
   giJoK03W8kd6mk3X+fvc4ARJo9RarYInsAvSHKlr1KpxeebuirfqgSz+uEW6pqOD1fV0oHnFncdf
   jV2k2CqmIfThB/ONQcn/4/EIlhdzXqxSlXAGz6C7ApHq6xUCdLILx/NfdUEypHIfyabrpXKOKOPx
   zekhGztEzB0gSJNebEa++EKxHDOc1Sc0YD9q9KvcaGSPTjlCJeaNhufg9Sz/iXZMP+d4Vkp+Bn6p
   mfUPG7tKharEoRChUNfRms8wVyNxmz6LRw5Uy14Dlodd0LyBQRB9Tx8FVYMh5AElwjbQOoDOIRvi
   IQIGsUNp/ZkP7PdBxc/b9o3rjUsZCzyCtP+jflZSqMenzXCsTI1Xay6On2wSVwQdJ1/2eIwKEfCF
   hj4DZlY5+jSo
   ```

1. **Default:** None
1. **Where used:**
    1. `cloudformation-senzing-basic.yaml`

### SenzingVersion

1. **Synopsis:**
   The version of Senzing installed onto the AWS Elastic File System.
   More information at [Senzing API Version History](https://senzing.com/releases/#api-releases).
1. **Required:** Yes
1. **Type:** Choice
1. **Default:** Latest version in the list.
1. **Where used:**
    1. `cloudformation-senzing-basic.yaml`

## Outputs

### 0penFirst

1. **Synopsis:**
   An alias for [UrlWebApp](#urlwebapp).
   Since it's one of the first things to look at, it is listed first.
1. **Details:**
   It is listed first in alphabetical order because the name "cheats" and uses a zero instead of a capital "o".
1. **Where used:**
    1. `cloudformation-senzing-basic.yaml`

### AccountID

1. **Synopsis:**
   The identifier of the AWS account used to create the cloudformation stack.
1. **Details:**
   This information will match the
   [AWS Management Console](https://console.aws.amazon.com/console/home)
   user dropdown "My Account" value.
1. **Where used:**
    1. `cloudformation-database.yaml`
    1. `cloudformation-senzing-basic.yaml`

### CertificateArn

1. **Synopsis:**
   Amazon Resource Name (ARN) of certificate used for SSL support.
1. **Details:**
   More information at
   [AWS LoadBalancer Console](https://console.aws.amazon.com/ec2/v2/home#LoadBalancers).
   Select a load balancer, view the "Listeners" tab, then click "View/edit certificates".
1. **Where used:**
    1. `cloudformation-senzing-basic.yaml`

### DatabaseHostCore

1. **Synopsis:**
   One of 3 Senzing databases that hold the Senzing Model.
1. **Details:**
   See the database cluster having a Name in the form `{StackName}-aurora-senzing-core-cluster` in the
   [AWS RDS Console](https://console.aws.amazon.com/rds/home?#databases:).
   If a "Single" database was deployed, it will point to the single database host.
1. **Where used:**
    1. `cloudformation-database.yaml`

### DatabaseHostLibfeat

1. **Synopsis:**
   Two of 3 Senzing databases that hold the Senzing Model.
1. **Details:**
   See the database cluster having a Name in the form `{StackName}-aurora-senzing-libfeat-cluster` in the
   [AWS RDS Console](https://console.aws.amazon.com/rds/home?#databases:).
   If a "Single" database was deployed, it will point to the single database host.
1. **Where used:**
    1. `cloudformation-database.yaml`

### DatabaseHostRes

1. **Synopsis:**
   Three of 3 Senzing databases that hold the Senzing Model.
1. **Details:**
   See the database cluster having a Name in the form `{StackName}-aurora-senzing-res-cluster` in the
   [AWS RDS Console](https://console.aws.amazon.com/rds/home?#databases:).
   If a "Single" database was deployed, it will point to the single database host.
1. **Where used:**
    1. `cloudformation-database.yaml`

### DatabaseName

1. **Synopsis:**
   The name of the database.
   It is same name across all database servers.
1. **Details:**
   Usually "G2".
1. **Where used:**
    1. `cloudformation-database.yaml`

### DatabasePassword

1. **Synopsis:**
   The randomly-generated administrative password for authenticating with the database.
1. **Where used:**
    1. `cloudformation-database.yaml`

### DatabasePortCore

1. **Synopsis:**
   The port used to access the [DatabaseHostCore](#databasehostcore) database.
1. **Details:**
   See the database cluster having a Name in the form `{StackName}-aurora-senzing-core-cluster` in the
   [AWS RDS Console](https://console.aws.amazon.com/rds/home?#databases:).
   If a "Single" database was deployed, it will point to the single database port.
1. **Where used:**
    1. `cloudformation-database.yaml`

### DatabasePortLibfeat

1. **Synopsis:**
   The port used to access the [DatabaseHostLibfeat](#databasehostlibfeat) database.
1. **Details:**
   See the database cluster having a Name in the form `{StackName}-aurora-senzing-libfeat-cluster` in the
   [AWS RDS Console](https://console.aws.amazon.com/rds/home?#databases:)
   If a "Single" database was deployed, it will point to the single database port.
1. **Where used:**
    1. `cloudformation-database.yaml`

### DatabasePortRes

1. **Synopsis:**
      The port used to access the [DatabaseHostRes](#databasehostres) database.
1. **Details:**
   See the database cluster having a Name in the form `{StackName}-aurora-senzing-res-cluster` in the
   [AWS RDS Console](https://console.aws.amazon.com/rds/home?#databases:).
   If a "Single" database was deployed, it will point to the single database port.
1. **Where used:**
    1. `cloudformation-database.yaml`

### DatabaseUsername

1. **Synopsis:**
   Username to access any of the databases.
1. **Details:**
   More information at [AWS RDS Console](https://console.aws.amazon.com/rds/home).
1. **Where used:**
    1. `cloudformation-database.yaml`

### Ec2InternetGateway

1. **Synopsis:**
   For use in Cloudformation `AWS::EC2::Route` declarations.
1. **Details:**
   See the route table having a "Name" in the form `{StackName}-ec2-route-table-private` in the
   [AWS VPC Console](https://console.aws.amazon.com/vpc/home?#RouteTables).
1. **Where used:**
    1. `cloudformation-database.yaml`

### Ec2SecurityGroupInternal

1. **Synopsis:**
   For use in Cloudformation declarations such as `AWS::EC2::SecurityGroupIngress`.
1. **Details:**
   See the security group having a "Name" in the form `{StackName}-ec2-security-group-internal` in the
   [AWS VPC Console](https://console.aws.amazon.com/vpc/home?#SecurityGroups ).
1. **Where used:**
    1. `cloudformation-database.yaml`

### Ec2Vpc

1. **Synopsis:**
   The AWS Resource ID of the Virtual Private Cloud (VPC).
1. **Details:**
   See the VPC having a "Name" in the form `{StackName}-ec2-vpc` in the
   More information at [AWS VPC Console](https://console.aws.amazon.com/vpc/home?#vpcs:).
1. **Where used:**
    1. `cloudformation-database.yaml`

### Ec2VpcCidrBlock

1. **Synopsis:**
   For use in Cloudformation `AWS::EC2::SecurityGroup` declarations.
1. **Details:**
   See the "IPV4 CIDR" having a "Name" in the form `{StackName}-ec2-vpc` in the
   [AWS VPC Console](https://console.aws.amazon.com/vpc/home?#vpcs).
1. **Where used:**
    1. `cloudformation-database.yaml`

### Host

1. **Synopsis:**
   The hostname of the loadbalancer that is a proxy to all of the services.
1. **Details:**
   More information at [AWS Load Balancers console](https://console.aws.amazon.com/ec2/v2/home?#LoadBalancers:).
   Also used as the `host` value when using [UrlSwagger](#urlswagger).
1. **Where used:**
    1. `cloudformation-senzing-basic.yaml`

### QueueDeadLetter

1. **Synopsis:**
   The queue to which records that are not able to be ingested into Senzing Engine are sent.
   In otherwords, if the JSON message is malformed or Senzing denied inserting into the Senzing Engine.
1. **Details:**
   More information at [AWS SQS Console](https://console.aws.amazon.com/sqs/v2/home?#/queues).
1. **Where used:**
    1. `cloudformation-senzing-basic.yaml`

### QueueInput

1. **Synopsis:**
   The queue from which records are ingested into Senzing Engine.
   In otherwords, this is the queue where records are sent to be inserted into the Senzing Engine.
1. **Details:**
   More information at [AWS SQS Console](https://console.aws.amazon.com/sqs/v2/home?#/queues).
1. **Where used:**
    1. `cloudformation-senzing-basic.yaml`

### QueueOutput

1. **Synopsis:**
   The queue that is populated with responses from inserting records into the Senzing Engine.
   This is commonly called "WithInfo" information.
1. **Details:**
   More information at [AWS SQS Console](https://console.aws.amazon.com/sqs/v2/home?#/queues).
1. **Where used:**
    1. `cloudformation-senzing-basic.yaml`

### QueueRedoerDeadLetter

1. **Synopsis:**
   The queue to which redo records that are not able to be redone by the Senzing Engine are sent.
   In otherwords, if the message is malformed or Senzing denied redoing the message.
1. **Details:**
   More information at [AWS SQS Console](https://console.aws.amazon.com/sqs/v2/home?#/queues).
1. **Where used:**
    1. `cloudformation-senzing-basic.yaml`

### QueueRedoerInput

1. **Synopsis:**
   The queue populated by the `redoer` with records the Senzing Engine identified as needing
   reevaluation.
   The queue will be consumed by the fleet of `redoers` that read from the queue and send
   to the Senzing Engine for reprocessing.
   The results will be sent to the [QueueRedoerOutput](#queueredoeroutput).
1. **Details:**
   More information at [AWS SQS Console](https://console.aws.amazon.com/sqs/v2/home?#/queues).
1. **Where used:**
    1. `cloudformation-senzing-basic.yaml`

### QueueRedoerOutput

1. **Synopsis:**
   The queue that is populated with responses from reprocessing records.
   This is commonly called "WithInfo" information from the `redoer`.
1. **Details:**
   More information at [AWS SQS Console](https://console.aws.amazon.com/sqs/v2/home?#/queues).
1. **Where used:**
    1. `cloudformation-senzing-basic.yaml`

### SshPassword

1. **Synopsis:**
   The [SshUsername](#sshusername)'s password to be used when logging into the SSHD container.
1. **Where used:**
    1. `cloudformation-senzing-basic.yaml`

### SshUsername

1. **Synopsis:**
   User ID to be used when logging into the SSHD container.
1. **Details:**
   Usually "root".
   Logging in also requires the [SshPassword](#sshpassword) value.
1. **Where used:**
    1. `cloudformation-senzing-basic.yaml`

### SubnetPrivate1

1. **Synopsis:**
   The first of two private subnets created.
1. **Details:**
   See the subnet having a Name in the form `{StackName}-ec2-subnet-private-1` in the
   [AWS Virtual Private Cloud console](https://console.aws.amazon.com/vpc/home?#subnets:).
1. **Where used:**
    1. `cloudformation-database.yaml`

### SubnetPrivate2

1. **Synopsis:**
   The second of two private subnets created.
1. **Details:**
   See the subnet having a Name in the form `{StackName}-ec2-subnet-private-2` in the
   [AWS Virtual Private Cloud console](https://console.aws.amazon.com/vpc/home?#subnets:).
1. **Where used:**
    1. `cloudformation-database.yaml`

### SubnetPublic1

1. **Synopsis:**
   The first of two public subnets created.
1. **Details:**
   See the subnet having a Name in the form `{StackName}-ec2-subnet-public-1` in the
   [AWS Virtual Private Cloud console](https://console.aws.amazon.com/vpc/home?#subnets:).
1. **Where used:**
    1. `cloudformation-database.yaml`
    1. `cloudformation-senzing-basic.yaml`

### SubnetPublic2

1. **Synopsis:**
   The second of two public subnets created.
1. **Details:**
   See the subnet having a Name in the form `{StackName}-ec2-subnet-public-2` in the
   [AWS Virtual Private Cloud console](https://console.aws.amazon.com/vpc/home?#subnets:).
1. **Where used:**
    1. `cloudformation-database.yaml`
    1. `cloudformation-senzing-basic.yaml`

### UrlApiServer

1. **Synopsis:**
   A URL showing how to reach the
   [Senzing API Server](https://github.com/Senzing/senzing-api-server)
   directly.
1. **Where used:**
    1. `cloudformation-senzing-basic.yaml`

### UrlApiServerHeartbeat

1. **Synopsis:**
   A URL showing how to reach the
   [Senzing API Server](https://github.com/Senzing/senzing-api-server)'s
   `/heartbeat` URI path.
   This demonstrates that the API server is responding.
1. **Details:**
   For more URIs, see
   [SwaggerUrl output value](#urlswagger).
1. **Where used:**
    1. `cloudformation-senzing-basic.yaml`

### UrlJupyter

1. **Synopsis:**
   A URL showing how to reach the
   [Senzing Jupyter notebooks](https://github.com/Senzing/docker-jupyter).
1. **Where used:**
    1. `cloudformation-senzing-basic.yaml`

### UrlSwagger

1. **Synopsis:**
   A URL showing how to reach the
   [Swagger User Interface](https://github.com/swagger-api/swagger-ui).
   By default, SwaggerUI is not enabled in the Cloudformation template.
   To enable, in the Cloudformation template set `Mappings.Constants.Run.Swagger` to "Yes"
   before deploying.
1. **Usage:**
   To access the Senzing API server
    1. Using the URL, visit the `UrlSwagger` webpage.
    1. In **Servers**
        1. From the drop-down, select `{protocol}://{host}:{port}{path}`.
        1. **protocol:** https
        1. **host:** Enter the value of [Host](#host)
        1. **port:** 443
        1. **path:** /api
    1. The HTTP URIs will now access the deployed Senzing API server.
1. **Where used:**
    1. `cloudformation-senzing-basic.yaml`

### UrlWebApp

1. **Synopsis:**
   A URL showing how to reach the
   [Senzing Entity Search Web App](https://github.com/Senzing/entity-search-web-app).
1. **Where used:**
    1. `cloudformation-senzing-basic.yaml`

### UrlXterm

1. **Synopsis:**
   A URL showing how to reach the
   [Senzing Xterm](https://github.com/Senzing/docker-xterm).
1. **Usage:**
   From this Linux terminal, `G2Command.py`, `G2Explorer.py`, `G2ConfigTool.py`,
   can be run.
1. **Where used:**
    1. `cloudformation-senzing-basic.yaml`

### UserInitPassword

1. **Synopsis:**
   The one-time password for the [UserName](#username).
1. **Details:**
   When the one-time password is used, the user is prompted for a new password.
   Once a new password is submitted, the one-time password has no value.
1. **Where used:**
    1. `cloudformation-senzing-basic.yaml`

### UserName

1. **Synopsis:**
   The user name submitted for the [CognitoAdminEmail](#cognitoadminemail).
   It is the initial user created to access the system.
1. **Details:**
   To add users, see [UserPool](#userpool)
1. **Where used:**
    1. `cloudformation-senzing-basic.yaml`

### UserPool

1. **Synopsis:**
   The specific [UserPool](https://console.aws.amazon.com/cognito/users/#/pool/u) URL.
   It can be used to add, manage, or delete users for this Cloudformation.
1. **Where used:**
    1. `cloudformation-senzing-basic.yaml`
