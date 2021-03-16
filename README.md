# symbol-aws-cloudformation

## Build Symbol Server in New AWS VPC

* VPC
  * public network subnet
* SecurityGroup
* IAM Role(SSM)
* Elastic IP
* EC2 Instance

![image](https://user-images.githubusercontent.com/20014134/102791637-a388ec80-43ea-11eb-8aac-45fc965af90c.png)

## How to

1. Create AWS Account

    https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account/?nc1=h_ls

2. Create EC2 Key-Pair

    https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html#prepare-key-pair

3. Launch Stack and click the cloud symbol “CreateStack”.

    [![image](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/designer/home?templateURL=https://symbol-in-aws.s3.amazonaws.com/stack.cfn.yaml)

4. Set Parameter

    |Parameter|Description|
    |---|---|
    |Stack Name|Name for this Stack|
    |Service Name|Name of the service created by this stack.This is used as the title for all resources.|
    |AvailabilityZone1| AWS AvailabilityZone |
    |PublicLocationIP| IP address that is allowed to connect to symbol-rest API(3000). This IP addresses can be defined in a range (e.g. /24)|
    |DefaultUnixUser| The user name to use for the instance.|
    |KeyName| EC2 KeyPair|
    |symbolInstanceType| EC2 Instance Type|
    |symbolRootVolumeSize| EC2 Instance root volume disk size|
    |symbolDataVolumeSize| EC2 Instance data volume disk size|
    |SymbolNetwork| Symbol Network|
    |SymbolAssembly| Symbol Assembly api or peer or dual|
    |SymbolBootstrapVersion| symbol-bootstrap version https://github.com/nemtech/symbol-bootstrap|
    |SymbolFriendlyName| Symbol FriendlyName when empty, set random name |
    |SymbolCreateVotingFile| Create voting file. not keylink transaction|
    |SymbolSuperNodeSettings| Create Super Node Agent(Container api-node-agent)  and Add SecurityGroup Ingress port 7880. not announce enrol transaction|

5. Fill the two check items

    ![image](https://user-images.githubusercontent.com/20014134/102793499-565a4a00-43ed-11eb-8bff-1a8352bb9979.png)

6. Create Stack

    It should take about 15 minutes to complete.

7. click the "Outputs" on the stack

    ![image](https://user-images.githubusercontent.com/20014134/102836222-30a86180-443c-11eb-94a0-9f7c4f5d4d60.png)

## FAQ

### Q. I want to login to the server remotely, how do I do it?

A. You can login via the session manager on AWS System Manager Service, on the AWS console screen.

### Q. Where's the Symbol data?

A. You can find the data in this directory.

```shell
/mnt/symbol/data
```
